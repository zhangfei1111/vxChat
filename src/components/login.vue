<template>
  <div class="content">
    <el-form
      :model="ruleForm"
      :rules="rules"
      ref="ruleForm"
      label-width="100px"
      class="demo-ruleForm"
    >
      <el-tabs v-model="activeName" @tab-click="handleClick">
        <el-tab-pane label="登录" name="first"></el-tab-pane>
        <el-tab-pane label="注册" name="two"></el-tab-pane>
      </el-tabs>
      <el-form-item v-if="activeName=='first'" label="账户" prop="name">
        <el-input v-model="ruleForm.name"></el-input>
      </el-form-item>
      <el-form-item v-if="activeName=='first'" label="密码" prop="name">
        <el-input v-model="ruleForm.name"></el-input>
      </el-form-item>
      <el-form-item v-if="activeName=='two'" label="手机号" prop="name">
        <el-input v-model="ruleForm.name"></el-input>
      </el-form-item>
      <el-form-item v-if="activeName=='two'" label="验证码" prop="name">
        <el-input v-model="ruleForm.name"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button v-if="activeName=='first'" type="primary" @click="submitForm('ruleForm')">登录</el-button>
        <el-button v-if="activeName=='two'" type="primary" @click="submitForm('ruleForm')">注册</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  name: "login",
  data() {
    return {
      activeName: "first",
      ruleForm: {
        name: ""
      },
      rules: {
        name: [
          { required: true, message: " ", trigger: "blur" },
          { min: 3, max: 5, message: " ", trigger: "blur" }
        ]
      }
    };
  },
  methods: {
    submitForm(formName) {
      this.$refs[formName].validate(valid => {
        if (valid) {
          console.log("dd");
        } else {
          console.log("error submit!!");
          return false;
        }
      });
    },
    handleClick(tab, event) {
      console.log(tab, event);
    }
  }
};
</script>

<style scoped>
.content {
  width: 800px;
  background-color: #ccc;
  margin: 0 auto;
  height: 600px;
}
</style>
