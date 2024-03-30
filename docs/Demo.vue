<template>
    <div class="flex flex-col gap-10px">
        <ElInput v-model="content" type="textarea" :rows="5"></ElInput>
        <div class="flex">
            <ElButton @click="genAndDownload">生成txt并下载</ElButton>
        </div>
    </div>
</template>

<script lang="jsx" setup>
import { downloadBlob } from '@/utils/blob'
import { ElButton, ElInput } from 'element-plus'
import { ref } from 'vue'

const content = ref('')

const genAndDownload = () => {
    const blob = new Blob([content.value], { type: 'text/plain' })

    downloadBlob(blob, `text-${new Date().getTime()}.txt`)

    content.value = ''
}
</script>

<style lang="scss" scoped></style>
