<template>
    <label
        class="b-checkbox checkbox"
        :class="[size, { 'is-disabled': disabled }]"
        ref="label"
        :disabled="disabled"
        @click="focus"
        @keydown.prevent.enter="$refs.label.click()">
        <input
            v-model="computedValue"
            :indeterminate.prop="indeterminate"
            type="checkbox"
            ref="input"
            @click.stop
            :autocomplete="autocomplete"
            :disabled="disabled"
            :required="required"
            :name="name"
            :value="nativeValue"
            :true-value="trueValue"
            :false-value="falseValue"
            :aria-labelledby="ariaLabelledby">
        <span class="check" :class="type" />
        <span :id="ariaLabelledby" class="control-label"><slot/></span>
    </label>
</template>

<script>
import CheckRadioMixin from '../../utils/CheckRadioMixin.js'

export default {
    name: 'BCheckbox',
    mixins: [CheckRadioMixin],
    props: {
        indeterminate: Boolean,
        ariaLabelledby: String,
        trueValue: {
            type: [String, Number, Boolean, Function, Object, Array],
            default: true
        },
        falseValue: {
            type: [String, Number, Boolean, Function, Object, Array],
            default: false
        },
        autocomplete: {
            type: String,
            default: 'on'
        }
    }
}
</script>
