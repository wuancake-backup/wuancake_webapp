<template>
    <div class="page-index">
        <div class="btn-box">
            <label class="box-title">按钮组件展示</label>
            <w-button>按钮</w-button>
            <w-button type="default">default</w-button>
            <w-button :iconLeft="icon">icon</w-button>
            <w-button type="ghost">ghost</w-button>
            <w-button type="warning">warning</w-button>
            <w-button width="200" type="ghost">ghost + width</w-button>
            <w-button type="primary">primary</w-button>
            <w-button iconLeft="&#xe62b;" iconRight="&#xe60f;" type="ghost">按钮</w-button>
            <w-button type="default" :disabled="true">禁用</w-button>
        </div>
        <div class="btn-box">
            <w-button type="default" @click="goHome">去首页</w-button>
        </div>
        <div class="input-box">
            <label class="box-title">input组件展示</label>
            <w-input @on-input="handleInput" @on-change="handleChange" @on-focus="handleFocus" @on-blur="handleBlur"></w-input>
            <w-input placeholder="textarea" type="textarea" :row="3"></w-input>
            <w-input placeholder="password" type="password"></w-input>
            <w-input placeholder="set width" :width="200"></w-input>
            <w-input placeholder="输入新昵称" type="line" :width="200"></w-input>
        </div>
        <div class="cell-box">
            <label class="box-title">cell组件展示</label>
            <w-list>
                <w-icon value="&#xe62b;" slot="left-icon"></w-icon>
                <span slot="left-text">hahah</span>
            </w-list>
        </div>
    </div>
</template>

<script>
import { getGroupList } from '../api/group.js'
import WButton from '../components/WButton'
import WInput from '../components/WInput'
import WList from '../components/WLIst'
import WIcon from '../components/WIcon'
function setState(store) {}

export default {
    name: 'index',
    metaInfo: {
        title: 'Home',
        titleTemplate: '%s - Lavas',
        meta: [
            {name: 'keywords', content: 'lavas PWA'},
            {name: 'description', content: '基于 Vue 的 PWA 解决方案，帮助开发者快速搭建 PWA 应用，解决接入 PWA 的各种问题'}
        ]
    },
    async asyncData({store, route}) {
        setState(store);
    },
    components: {
        WButton,
        WInput,
        WList,
        WIcon
    },
    data () {
        return {
            icon: '&#xe62b;'
        }
    },
    mounted() {
        this.query()
    },
    methods: {
        query () {
            getGroupList().then(res => {
                console.log(res)
            })
        },
        handleInput (event) {
            console.log(event)
        },
        handleChange (event) {
            console.log(event)
        },
        handleFocus (event) {
            console.log(event)
        },
        handleBlur (event) {
            console.log(event)
        },
        goHome () {
            this.$router.push('home')
        },
    }
};
</script>

<style lang="stylus" scoped>

.page-index
    display flex
    justify-content center
    align-items center
    flex-direction column

    h2
        font-size 46px
        font-weight 500
        margin-bottom 0
    
    .btn-box,
    .input-box,
    .cell-box
        width 730px
        padding 20px
        border 1px solid #f1f1f1
        margin 10px
        text-align left
        *
            margin 10px 0
        .box-title
            text-align left
            display block
            color #aaaaaa
            font-size 16px
</style>
