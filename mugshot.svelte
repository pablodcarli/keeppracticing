<script>
import { onMount } from "svelte";

export default {
  name: "ZoomableImage",
  props: {
    src: String,
    title: String,
  },
  onMount() {
    const img = this.$refs.img;
    img.addEventListener("mouseover", () => {
      img.style.transform = "scale(1.2)";
    });
    img.addEventListener("mouseleave", () => {
      img.style.transform = "scale(1)";
    });
  },
  render() {
    return (
      <div>
        <img
          ref="img"
          src={this.src}
          alt={this.title}
        />
        <div class="title">{this.title}</div>
      </div>
    );
  },
};
</script>

<style>
.title {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
  font-size: 20px;
}
</style>

<ZoomableImage
  src="/img/a-man-coding.jpg"
  title="Hombre Codeando"
/>