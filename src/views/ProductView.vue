<template>
  <h2>產品列表</h2>
  <div class="container">
    <!-- row 決定內層數量 -->
{{product}}
  </div>
</template>

<script>
export default {
  data() {
    return {
      product: {}
    }
  },
  methods: {
    getProduct() {
      console.log(this.$route)
      const { id } = this.$route.params
      this.$http(
        `${process.env.VUE_APP_API}api/${process.env.VUE_APP_PATH}/product/${id}`
      ).then((res) => {
        this.product = res.data.product
      })
    }
  },
  mounted() {
    this.getProduct()
  }
}
</script>
