<template>
    <a-upload-dragger
        name="file"
        :multiple="true"
        action="https://www.mocky.io/v2/5cc8019d300000980a055e76"
        @change="handleChange"
    >
        <p class="ant-upload-drag-icon">
            <a-icon type="inbox" />
        </p>
        <p class="ant-upload-text">点击上传</p>
        <p class="ant-upload-hint">
            支持单选和多选，文件格式jpg、png、gif，单个文件大小限制5M。
        </p>
    </a-upload-dragger>
</template>

<script>
export default {
    data() {
        return {};
    },
    methods: {
        handleChange(info) {
            const status = info.file.status;
            if (status !== "uploading") {
                console.log(info.file, info.fileList);
            }
            if (status === "done") {
                this.$message.success(
                    `${info.file.name} file uploaded successfully.`
                );
            } else if (status === "error") {
                this.$message.error(`${info.file.name} file upload failed.`);
            }
        },
    },
};
</script>

<style lang="less" scoped>
.ant-upload-list {
    max-height: 300px;
    overflow-y: scroll;
}
</style>
