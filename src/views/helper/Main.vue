<template>
    <div>
        <el-card shadow="never" style="min-height: 600px;margin-bottom: 20px;">
            <el-collapse v-model="active" accordion>
                <el-collapse-item title="开发注意事项" name="deploy">
                    <div style="padding: 10px;line-height: 30px;color: #303133;font-size: 16px">
                        配置文件读取的总是与
                        <tt>index.html</tt> 同级的
                        <tt>./static/configuration.json</tt> , 而修改配置的时候是通过
                        <tt>github-api</tt> 修改
                        <tt>你的用户名.github.io</tt> 下的
                        <tt>/static/configuration.json</tt>, 所以本地
                        <tt>npm run dev</tt> 的时候会出现修改配置无效的情况, 如果需要修改的话修改本地的配置文件就行, 发布到
                        <tt>github</tt> 之后不影响</div>
                </el-collapse-item>
            </el-collapse>
        </el-card>
    </div>
</template>
<script>

    export default {
        data() {
            return {
                active: "deploy",
                deploy: {
                    status: "process",
                    active: 0,
                },
                use: {
                    status: "process",
                    active: 0,
                }
            }
        },
        mounted() {

        },
        methods: {
            deployChange(index) {
                this.deploy.status = index == 2 ? "success" : "process"
                this.deploy.active = index
            },
            useChange(index) {
                this.use.status = index == 2 ? "success" : "process"
                this.use.active = index
            }
        }
    }
</script>