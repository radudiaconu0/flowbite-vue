<script setup>
import FwbInputExample from './input/examples/FwbInputExample.vue'
import FwbInputExampleSize from './input/examples/FwbInputExampleSize.vue'
import FwbInputExampleDisabled from './input/examples/FwbInputExampleDisabled.vue'
import FwbInputExampleHelper from './input/examples/FwbInputExampleHelper.vue'
import FwbInputExampleBlockClasses from './input/examples/FwbInputExampleBlockClasses.vue'
import FwbInputExamplePrefix from './input/examples/FwbInputExamplePrefix.vue'
import FwbInputExampleSuffix from './input/examples/FwbInputExampleSuffix.vue'
import FwbInputExampleRequired from './input/examples/FwbInputExampleRequired.vue'
import FwbInputExampleValidation from './input/examples/FwbInputExampleValidation.vue'
</script>

# Vue Input - Flowbite

#### Get started with a collection of input fields built with Tailwind CSS to start accepting data from the user based on multiple sizes, variants, and input types

---

:::tip
Original reference: [https://flowbite.com/docs/forms/input-field/](https://flowbite.com/docs/forms/input-field/)
:::

The input field is an important part of the form element that can be used to create interactive controls to accept data from the user based on multiple input types, such as text, email, number, password, URL, phone number, and more.

On this page you will find all of the input types based on multiple variants, styles, colors, and sizes built with the utility classes from Tailwind CSS and components from Flowbite.

## Default

<fwb-input-example />
```vue
<template>
  <fwb-input
    v-model="name"
    placeholder="enter your first name"
    label="First name"
  />
</template>

<script lang="ts" setup>
import { ref } from 'vue'
import { FwbInput } from 'flowbite-vue'

const name = ref('')
</script>
```

## Size

<fwb-input-example-size />
```vue
<template>
  <fwb-input v-model="name" label="Small" placeholder="enter your name" size="sm" />
  <fwb-input v-model="name" label="Medium" placeholder="enter your name" size="md" />
  <fwb-input v-model="name" label="Large" placeholder="enter your name" size="lg" />
</template>

<script lang="ts" setup>
import { ref } from 'vue'
import { FwbInput } from 'flowbite-vue'

const name = ref('')
</script>
```

## Disabled

<fwb-input-example-disabled />
```vue
<template>
  <fwb-input
    v-model="name"
    disabled
    label="First name"
    placeholder="enter your first name"
  />
</template>

<script lang="ts" setup>
import { ref } from 'vue'
import { FwbInput } from 'flowbite-vue'

const name = ref('')
</script>
```

## Required

<fwb-input-example-required />
```vue
<template>
  <fwb-input
    v-model="name"
    label="First name"
    placeholder="enter your first name"
    required
  />
</template>

<script setup>
import { ref } from 'vue'
import { FwbInput } from 'flowbite-vue'

const name = ref('')
</script>
```

## Error Messages

- Set validation status via `validationStatus` prop, which accepts `'success'` or `'error'`.
- Add error messages directly via `error-message` prop.
- Add success messages directly via `success-message` prop.
- Control visibility of messages with the `hide-details` prop.

<fwb-input-example-error-message />
```vue
<template>
  <!-- Direct error message prop -->
  <fwb-input
    v-model="username"
    label="Username"
    placeholder="Enter your username"
    validation-status="error"
    error-message="This username is already taken"
  />
  
  <!-- Direct success message prop -->
  <fwb-input
    v-model="email"
    label="Email"
    placeholder="Enter your email"
    validation-status="success"
    success-message="Email format is valid"
  />
  
  <!-- Form validation example -->
  <fwb-input
    v-model="password"
    type="password"
    label="Password"
    placeholder="Enter your password"
    :validation-status="passwordError ? 'error' : 'success'"
    :error-message="passwordError"
    :success-message="passwordError ? '' : 'Password meets requirements'"
  />
  
  <!-- Hide details example -->
  <fwb-input
    v-model="phone"
    label="Phone Number"
    placeholder="Enter your phone number"
    validation-status="error"
    error-message="Please enter a valid phone number"
    hide-details
  />
</template>

<script lang="ts" setup>
import { computed, ref } from 'vue'
import { FwbInput } from 'flowbite-vue'

// Form values
const username = ref('')
const email = ref('')
const password = ref('')
const phone = ref('')

// Form validation
const passwordError = computed(() => {
  if (!password.value) return 'Password is required'
  if (password.value.length < 8) return 'Password must be at least 8 characters'
  return ''
})
</script>
```

## Extra CSS classes

Sometimes it is required to add some customization to the input or the input wrapper.
By default, `class` attribute is bound to the input element. To customize the input wrapper you can use the `block-classes` property.
It accepts the values as the `class` attribute

<fwb-input-example-block-classes />
```vue
<template>
  <fwb-input
    v-model="name"
    label="First name"
    placeholder="enter your first name"
    required
    class="bg-green-200"
    block-classes="border-2 border-green-500 p-2 rounded-lg"
  />
</template>

<script setup>
import { ref } from 'vue'
import { FwbInput } from 'flowbite-vue'

const name = ref('')
</script>
```

## Slot - Helper

<fwb-input-example-helper />
```vue
<template>
  <fwb-input
    v-model="name"
    label="First name"
    placeholder="enter your first name"
  >
    <template #helper>
      We'll never share your details. Read our
      <fwb-a href="#" color="text-blue-600 dark:text-blue-500">
        Privacy Policy
      </fwb-a>.
    </template>
  </fwb-input>
</template>

<script lang="ts" setup>
import { ref } from 'vue'
import { FwbA, FwbInput } from 'flowbite-vue'

const name = ref('')
</script>
```

## Slot - Prefix

<fwb-input-example-prefix />
```vue
<template>
  <fwb-input v-model="name" label="Search" placeholder="enter your search query">
    <template #prefix>
      <svg aria-hidden="true" class="w-5 h-5 text-gray-500 dark:text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
        <path d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" />
      </svg>
    </template>
  </fwb-input>
</template>

<script lang="ts" setup>
import { ref } from 'vue'
import { FwbInput } from 'flowbite-vue'

const name = ref('')
</script>
```

## Slot - Suffix
<fwb-input-example-suffix />
```vue
<template>
  <fwb-input
    v-model="query"
    label="Search"
    placeholder="enter your search query"
    size="lg"
  >
    <template #prefix>
      <svg aria-hidden="true" class="w-5 h-5 text-gray-500 dark:text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
        <path d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" />
      </svg>
    </template>
    <template #suffix>
      <fwb-button>Search</fwb-button>
    </template>
  </fwb-input>
</template>

<script lang="ts" setup>
import { ref } from 'vue'
import { FwbButton, FwbInput } from 'flowbite-vue'

const query = ref('')
</script>
```

## Slot - Validation

- Set validation status via `validationStatus` prop, which accepts `'success'` or `'error'`.
- Add validation message via `validationMessage` slot.

<fwb-input-example-validation />
```vue
<template>
  <fwb-input
    v-model="email"
    required
    placeholder="enter your email address"
    label="Email"
    validation-status="success"
  />
  <hr class="mt-4 border-0">
  <fwb-input
    v-model="email"
    required
    placeholder="enter your email address"
    label="Email"
    validation-status="error"
  >
    <template #validationMessage>
      Please enter a valid email address
    </template>
  </fwb-input>
</template>

<script lang="ts" setup>
import { ref } from 'vue'
import { FwbInput } from 'flowbite-vue'

const email = ref('')
</script>
```
