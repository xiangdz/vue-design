<template>
    <div>
        <table-edit v-if="propData.type === 'table-widget'" :settingData="propData.options" @addChild="addChild"></table-edit>
        <table-column-edit v-if="propData.type === 'table-column-widget'" :settingData="propData.options" @addChild="addChild"></table-column-edit>
        <pagination-edit v-if="propData.type === 'pagination-widget'" :settingData="propData.options" @setProp="(key, value) => $emit('setProp', key, value)"></pagination-edit>
        <form-edit v-if="propData.type === 'form-widget'" :settingData="propData.options" @addChild="addChild"></form-edit>
        <form-item-edit v-if="propData.type === 'form-item-widget'" :settingData="propData.options"></form-item-edit>
        <col-edit v-if="propData.type === 'col-widget'" :settingData="propData.options"></col-edit>
        <tab-pane-edit v-if="propData.type === 'el-tab-pane'" :settingData="propData.options"></tab-pane-edit>
        <steps-edit :children="propData.children" v-if="propData.type === 'steps-widget'" :settingData="propData.options" @addChild="addChild"></steps-edit>
        <step-edit v-if="propData.type === 'el-step'" :settingData="propData.options"></step-edit>
        <tabs-edit v-if="propData.type === 'tabs-widget'" :settingData="propData.options" @addChild="addChild"></tabs-edit>
        <button-edit v-if="propData.type === 'button-widget'" :settingData="propData.options"></button-edit>
        <icon-edit v-if="propData.type === 'svg-icon'" :settingData="propData.options"></icon-edit>
        <input-number-edit v-if="propData.type === 'input-number-widget'" :settingData="propData.options"></input-number-edit>
        <input-edit v-if="['input-widget', 'select-widget', 'radio-group-widget', 'checkbox-group-widget'].includes(propData.type)" :settingData="propData.options" :type="propData.type" @addChild="addChild"></input-edit>
        <switch-edit v-if="propData.type === 'switch-widget'" :settingData="propData.options"></switch-edit>
        <option-edit v-if="propData.type === 'option-widget'" :settingData="propData.options"></option-edit>
        <date-picker-edit v-if="propData.type === 'date-picker-widget'" :settingData="propData.options"></date-picker-edit>
        <time-picker-edit v-if="propData.type === 'time-picker-widget'" :settingData="propData.options"></time-picker-edit>
        <slot-edit v-if="propData.type === 'slot'" :settingData="propData.options"></slot-edit>
        <dialog-edit v-if="propData.type === 'dialog-widget'" :settingData="propData.options"></dialog-edit>
        <drawer-edit v-if="propData.type === 'drawer-widget'" :settingData="propData.options"></drawer-edit>
        <divider-edit v-if="propData.type === 'divider-widget'" :settingData="propData.options"></divider-edit>
        <span-edit v-if="propData.type === 'span'" :settingData="propData.options"></span-edit>
        <link-edit v-if="propData.type === 'link-widget'" :settingData="propData.options"></link-edit>
        <template-edit v-if="propData.type === 'template'" :settingData="propData.options"></template-edit>
        <radio-edit v-if="['radio-widget', 'checkbox-widget'].includes(propData.type)" :settingData="propData.options"></radio-edit>
        <collapse-edit v-if="propData.type === 'collapse-widget'" :settingData="propData.options" @addChild="addChild"></collapse-edit>
        <collapse-item-edit v-if="propData.type === 'collapse-item-widget'" :settingData="propData.options"></collapse-item-edit>
        <cascader-edit v-if="propData.type === 'cascader-widget'" :settingData="propData.options"></cascader-edit>
    </div>
</template>

<script>
    import TableColumnEdit from '../setting-form/table-column-edit'
    import ColEdit from '../setting-form/col-edit'
    import FormEdit from '../setting-form/form-edit'
    import FormItemEdit from '../setting-form/form-item-edit'
    import InputEdit from '../setting-form/input-edit'
    import SwitchEdit from '../setting-form/switch-edit'
    import OptionEdit from '../setting-form/option-edit'
    import ButtonEdit from '../setting-form/button-edit'
    import RadioEdit from '../setting-form/radio-edit'
    import SlotEdit from '../setting-form/slot-edit'
    import TemplateEdit from '../setting-form/template-edit'
    import SpanEdit from '../setting-form/span-edit'
    import DialogEdit from '../setting-form/dialog-edit'
    import IconEdit from '../setting-form/icon-edit'
    import DatePickerEdit from '../setting-form/date-picker-edit'
    import TimePickerEdit from '../setting-form/time-picker-edit'
    import TableEdit from '../setting-form/table-edit'
    import TabPaneEdit from '../setting-form/tab-pane-edit'
    import StepsEdit from '../setting-form/steps-edit'
    import PaginationEdit from '../setting-form/pagination-edit'
    import InputNumberEdit from '../setting-form/input-number-edit'
    import TabsEdit from '../setting-form/tabs-edit'
    import StepEdit from '../setting-form/step-edit'
    import DrawerEdit from '../setting-form/drawer-edit'
    import DividerEdit from '../setting-form/divider-edit'
    import LinkEdit from '../setting-form/link-edit'
    import CollapseEdit from '../setting-form/collapse-edit'
    import CollapseItemEdit from '../setting-form/collapse-item-edit'
    import CascaderEdit from '../setting-form/cascader-edit'
    export default {
        name: 'prop-setting',
        components: { CascaderEdit, CollapseItemEdit, CollapseEdit, LinkEdit, DividerEdit, DrawerEdit, StepEdit, TabsEdit, InputNumberEdit, PaginationEdit, StepsEdit, TabPaneEdit, TableEdit, TimePickerEdit, DatePickerEdit, IconEdit, DialogEdit, SpanEdit, TemplateEdit, SlotEdit, RadioEdit, ButtonEdit, OptionEdit, SwitchEdit, InputEdit, FormItemEdit, FormEdit, ColEdit, TableColumnEdit },
        props: ['propData'],
        methods: {
            addChild(mode, type) {
                this.$emit('addChild', mode, type)
            }
        }
    }
</script>

<style scoped lang="scss">
    .setting-form /deep/ {
        .rule-item {
            width: 80%;
        }
    }
</style>
