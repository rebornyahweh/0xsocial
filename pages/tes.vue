<template>
  <div class="h-screen grid grid-cols-3 divide-x">
    <div class="col-span-2 h-screen flex flex-col bg-slate-100">
      <div class="nav-wrapper" >
            <a href="index.html" aria-current="page" class="logo-link w-nav-brand w--current">
              <h1 class="heading-7 font-bold text-4xl" >$0X Social</h1>
            </a>
            <nav role="navigation" class="nav-menu w-nav-menu" style="margin-left: 290px;">
              <a href="index.html#about" class="nav-link w-nav-link">About</a>
              <a href="index.html#how" class="nav-link w-nav-link">How to Use</a>
              <a href="index.html#tokenomics" class="nav-link w-nav-link">Tokenomics</a>
              <a href="index.html#chart" class="nav-link w-nav-link">Chart</a>
              <a href="index.html#" class="button-secondary nave w-inline-block">
                <div class="button button1">
                </div>
              </a>
            </nav>
            <a href="tes" target="_blank" class="button-secondary hide-tablet w-inline-block">
              <div class="btn-icon-text-wrapper">
                <div>Dapps</div>
              </div>
            </a>
            <div class="menu-button w-nav-button">
              <div class="icon w-icon-nav-menu"></div>
            </div>
          </div>
      <div class="flex-1 overflow-y-auto p-8">
        <app-form-profile
          v-model:name="data.n"
          v-model:desc="data.d"
          v-model:image="data.i"
        />
        <app-form-hr />
        <app-form-social-links
          v-model:facebook="data.f"
          v-model:twitter="data.t"
          v-model:instagram="data.ig"
          v-model:github="data.gh"
          v-model:telegram="data.tg"
          v-model:linkedin="data.l"
          v-model:email="data.e"
          v-model:whatsapp="data.w"
          v-model:youtube="data.y"
        />
        <app-form-hr />
        <app-form-links v-model="data.ls" />
      </div>
      <div class="border-t bg-white flex items-center">
        <button
          @click="prefillDemoData"
          class="h-12 flex items-center space-x-2 px-4 border-r text-xs font-medium bg-white text-slate-700"
        >
          <span> Add demo data </span>
          <icon name="mdi:code-json" class="h-4 w-4" />
        </button>
        <button
          @click="publish"
          class="h-12 flex items-center space-x-2 px-4 border-r text-xs font-medium bg-white text-slate-700"
        >
          <span> Publish </span>
          <icon name="ph:paper-plane-tilt-bold" class="h-4 w-4" />
        </button>
      </div>
    </div>
    <app-form-preview :data="data" />
  </div>
</template>

<script setup>
import { encodeData } from "../utils/transformer";
const data = ref({
  n: "",
  d: "",
  i: "",
  f: "",
  t: "",
  ig: "",
  gh: "",
  tg: "",
  l: "",
  e: "",
  w: "",
  y: "",
  ls: [],
});

const prefillDemoData = () => {
  data.value = {
    n: "Elon Musk",
    d: "I’m Elon Musk, the most Riches man, also the pro memer.",
    i: "https://c.ndtvimg.com/2023-05/h4jfgs0o_elon-musk_625x300_12_May_23.jpg",
    f: "https://www.facebook.com/Elon_Musk",
    t: "https://twitter.com/elonmusk",
    ig: "https://www.instagram.com/elonmusk/",
    e: "mail@elon_musk.com",
    gh: "",
    tg: "",
    w: "",
    y: "https://youtube.com/@Elon_musk",
    l: "",
    ls: [
      {
        l: "My Website",
        i: "ph:globe-duotone",
        u: "https://example.com",
      },
      {
        l: "Amazon wishlist",
        i: "ant-design:amazon-outlined",
        u: "https://amazon.in",
      },
      {
        l: "React JS course",
        i: "grommet-icons:reactjs",
        u: "https://reactjs.org/",
      },
      {
        l: "Donate for our cause",
        i: "iconoir:donate",
        u: "https://who.int",
      },
      {
        l: "Download my resume",
        i: "ph:file-pdf",
        u: "https://google.com",
      },
    ],
  };
};

const publish = () => {
  const url = `${window.location.origin}/1?data=${encodeData(data.value)}`;
  navigator.clipboard.writeText(url).then(() => {
    alert("Link copied to clipboard");
  });
};
</script>
