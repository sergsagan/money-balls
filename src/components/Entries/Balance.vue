<script setup>
import { useAmountColorClass } from 'src/composables/useAmountColorClass.js'
import { useCurrencify } from 'src/composables/useCurrencify.js'
import { useStoreEntries } from 'stores/storeEntries.js'
import { useLightOrDark } from 'src/composables/useLightOrDark.js'

/* stores */
const storeEntries = useStoreEntries()
</script>
<template>
  <div
    class="row q-mb-sm q-px-md q-py-sm items-center"
    :class="useLightOrDark('shadow-up-3', 'bg-black')"
  >
    <div class="col text-grey-7 text-h6">
      Balance:
    </div>
    <div
      :class="useAmountColorClass(storeEntries.balance)"
      class="col text-h6 text-right">
      <div class="row">
        <div class="col">
          {{ useCurrencify(storeEntries.balance) }}
        </div>
      </div>
      <div v-if="storeEntries.balancePaid" class="row">
        <div class="col text-caption text-grey-6">
          Paid:
          <span
            class="text-weight-bold"
            :class="useAmountColorClass(storeEntries.balancePaid)"
          >
            {{ useCurrencify(storeEntries.balancePaid) }}
          </span>
        </div>
      </div>
    </div>
  </div>
</template>
