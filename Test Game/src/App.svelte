<script>
  import { user } from './store.js';
  import Scroller from './ScrollerCustom.svelte';
  import Chartjs from 'chart.js/auto';
  import { onMount } from 'svelte';

  let num = 0;
  let count;
let index;
let offset;
let progress;


  let chartValues = [2, 2, 2, 12, 15, 16, 19, 19, 15, 7, 2, 2, 2, 1, 1];
let chartLabels = [10, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 30];
let ctx;
let chartCanvas;

onMount(async (promise) => {
    ctx = chartCanvas.getContext('2d');
    var chart = new Chartjs(ctx, {
      type: 'bar',
      data: {
          labels: chartLabels,
          datasets: [{
              label:"usia rata-rata memakai lipstik karena keinginan sendiri",
              backgroundColor: "#e74554",
              borderColor: "#e74554",
              color: "#000000",
              data: chartValues
          }]
      },
      options: {
        plugins: {
          customCanvasBackgroundColor: {
            color: 'white',
          }
        }
      },
      plugins: [plugin],
  });

});

const plugin = {
  id: 'customCanvasBackgroundColor',
  beforeDraw: (chart, args, options) => {
    const {ctx} = chart;
    ctx.save();
    ctx.globalCompositeOperation = 'destination-over';
    ctx.fillStyle = options.color || '#99ffff';
    ctx.fillRect(0, 0, chart.width, chart.height);
    ctx.restore();
  }
};

let box;
	
	function scrollToTop() {
		box.scrollIntoView();
	}

  let a = 0
const aPlus = () => {
  a += 1
}
    let data = [
  { 
          id: 0, 
          name: "1-5",
          desc : "Wah, kamu banyak temennya nih. Setengah dari responden kami juga punya jumlah lipstik yang sama kaya kamu",
          clr : "#e6b8afff" 
      },
  { 
          id: 1, 
          name : "6-10",
          desc : "Lumayan banyak yang sama kayak kamu, setidaknya 1/3 dari jumlah responden kami",
          clr : "#f4ccccff"
  },
  { 
          id: 2, 
          name : "11-20" ,
          desc : "wah, kamu pasti punya banyak koleksi lipstik yang menarik! sama kayak 12,8% responden kami",
          clr : "#dd7e6bff"
  },
      { 
          id: 3, 
          name : ">20" ,
          desc : "tenang aja, kamu gak sendiri kok. setidaknya 5 dari 100 orang di luar sana juga sama kayak kamu",
          clr : "#e06666ff"
  }
];
let selected = 0;

  let data1 = [
  { 
      id: 0, 
      name: "Dibuang ke tong sampah",
      a: "Lebih dari setengah responden kami juga melakukan ini. Memang, saat ini hanya ada sedikit opsi untuk mengelola sampah plastik yang kita hasilkan.",
      b: "Hanya saja, menurut Kementerian PUPR, timbunan sampah secara nasional yaitu 175.000 ton per hari dan 15 persen diantaranya berasal dari plastik sekali pakai, seperti kemasan kosmetik kita",
      c: "Sampah plastik yang terkumpul di TPA baru akan terurai setelah puluhan tahun. Padahal, masa pakai kosmetiknya saja tidak sampai 5 tahun.",
      clr : "#e6b8afff"  
  },
  { 
      id: 1, 
      name : "Dibakar di depan rumah",
      a: "Kamu dan setidaknya 3,2% warga DKI Jakarta melakukan hal ini.",
      b: "Kami paham, timbunan sampah rumah tangga pasti mengganggu pemandangan di rumah.",
      c: "Sayangnya, kemasan plastik yang dibakar akan mengeluarkan zat beracun yang dapat mengganggu pernapasan kamu dan keluarga serta Gas Rumah Kaca yang akan merusak lapisan ozon dan memperparah perubahan iklim.",
      clr : "#f4ccccff"
},
  { 
      id: 2, 
      name : "Dibuang ke badan air (sungai, kali, atau got)" ,
      a: "Pilihan yang tidak umum, tapi setidaknya 1,14% warga Jakarta masih melakukan ini.",
      b: "Penelitian dari Universitas Diponegoro menemukan adanya sejumlah mikroplastik di perairan Karimun Jawa yang berasal dari golongan HDPE, PVC, Polypropylene (PP), Polystrene (PS), ABS, Latex, LDPE, Nitrile, dan Nylon. HDPE, PP, PS, dan ABS adalah bahan plastik yang sering digunakan di kemasan kosmetik",
      c: "Efek buruknya, ya, mikroplastik itu kemungkinan saat ini sudah masuk ke piring makan kamu melalui ikan dan garam laut.",
      clr : "#dd7e6bff"
},
  { 
      id: 3, 
      name : "Dikumpulkan untuk didaur ulang" ,
      a: "Terima kasih! Kamu telah membantu mengurangi timbulan sampah agar tidak berakhir di landfill.",
      b: "Apakah kamu tahu, kemana sampah-sampah plastik yang telah kamu kumpulkan tersebut pergi?",
      c: "Ikuti liputan kami selengkapnya",
      clr : "#e06666ff"
}
];

let pilih = "";

const changePilih = (color) => {
  pilih = color
}
</script>


<div class="demo">
  <Scroller
  bind:count
  bind:index
  bind:offset
  bind:progress
  >
  <div slot="background">
    {#if index <=4 || index >= 6 && index <= 11}
    <div class="center-image"><img style="height: 100vh;" src='https://i.postimg.cc/qqRXHhmj/cover-medium.png' alt="cover"></div>
    {/if}
    {#if index >= 12 && index <= 14}
    <div class="center-image"><img class="image" src='https://i.postimg.cc/DwZSBgXW/sampah.png' alt="sampah"></div>
    
    {/if}
    {#if index == 15}
    <div class="center-image"><img class="image"  src='https://i.postimg.cc/k5gvNKnw/lipstick.png' alt="lipstick"></div>
    {/if}
    {#if index == 16}
    <div class="center-image"><img class="image"  src='https://i.postimg.cc/hGX7Pr4F/merge-2.png' alt="lipsticks"></div>
    
    {/if}
    {#if index == 17}
    <div class="center-image"><img class="image"  src='https://i.postimg.cc/wjcs1ZHm/chart1.png' alt="chart1"></div>
    {/if}
    {#if index == 22}
    <div class="center-image"><img class="image"  src='https://i.postimg.cc/kDPB4Fps/chart2.png' alt="chart2"></div>
    {/if}
    {#if index == 23 || index == 24}
    <div class="center-image"><img class="image"  src='https://i.postimg.cc/qJmZFBSz/chart3.png' alt="chart3"></div>
    {/if}
    {#if index === 18}
    <div class="center-image"><div style="position:relative;"><img class="image"  src='https://i.postimg.cc/BQJL1sZB/phone.png' alt="phone"><span class="phone-text">
    Salah satu faktor penting yang mengubah pola konsumsi kosmetik di Indonesia, menurut narasumber kami Margaretha Untoro, yaitu semakin banyaknya influencer kecantikan khususnya di Youtube. Sehingga membuat orang-orang memiliki ketertarikan lebih kepada tren kecantikan dan akhirnya menciptakan peluang pasar baru.</span></div></div>
    {/if}
    {#if index === 19}
    <div class="center-image"><div style="position:relative;"><img class="image"  src='https://i.postimg.cc/BQJL1sZB/phone.png' alt="phone"><span class="phone-text">
      Pangsa pasar Indonesia untuk industri kosmetik meningkat dari Rp36 triliun pada 
      2016 menjadi Rp46,4 triliun pada 2017. Kemenperin mencatat adanya pertumbuhan sebesar 7,36% 
      pada kuartal I 2018 dan diperkirakan pasar kosmetik lokal ini akan mencapai Rp77,3 triliun pada 2022.</span></div></div>
    {/if}
    {#if index === 20}
    <div class="center-image"><div style="position:relative;"><img class="image"  src='https://i.postimg.cc/BQJL1sZB/phone.png' alt="phone"><span class="phone-text">
      Total jumlah produk kosmetik yang terdaftar di BPOM hingga saat ini mencapai 
      lebih dari 330ribu jenis, baik dari produsen lokal maupun impor.</span></div></div>
    {/if}
    {#if index === 21}
    <div class="center-image"><div style="position:relative;"><img class="image"  src='https://i.postimg.cc/BQJL1sZB/phone.png' alt="phone"><span class="phone-text">
      Sepanjang 2021 hingga Juli 2022, perusahaan kosmetik yang terdaftar di BPOM 
      juga mengalami pertambahan dari 819 menjadi 913. Peningkatan industri kosmetik tersebut 
      didominasi oleh UKM, yakni sebesar 83%.</span></div></div>
    {/if}
    {#if index === 25}
    <div class="center-image"><div style="position:relative;"><img class="image"  src='https://i.postimg.cc/BQJL1sZB/phone.png' alt="phone"><span class="phone-text">
      Terdapat peningkatan yang berbanding lurus antara jumlah kosmetik yang 
      terdaftar dengan jumlah produk lipstik di BPOM selama tahun 2017-2021.</span></div></div>
    {/if}
    {#if index === 26}
    <div class="center-image"><div style="position:relative;"><img class="image"  src='https://i.postimg.cc/BQJL1sZB/phone.png' alt="phone"><span class="phone-text">
      Di balik besarnya potensi cuan industri kosmetik, ada potensi timbulan 
      sampah yang menghantuinya.</span></div></div>
    {/if}
    {#if index === 27}
    <div class="center-image"><div style="position:relative;"><img class="image"  src='https://i.postimg.cc/BQJL1sZB/phone.png' alt="phone"><span class="phone-text" style="font-size: : 8px;">
      Tapi angka tersebut hanyalah sekitar 15% dari seluruh produk kosmetik 
      yang beredar di Indonesia. Mengutip dari Katadata, Perhimpunan Perusahaan dan 
      Asosiasi Kosmetika Indonesia (PPAK) menduga terdapat 85% lainnya yang merupakan 
      produk kosmetik ilegal yang tidak memiliki izin edar ataupun yang merupakan tiruan 
      dari merek lain. Artinya, potensi timbulan sampah kosmetik yang sebenarnya, 
      lebih besar dari yang tercatat di BPOM.</span></div></div>
    {/if}
    {#if index == 31}
    <div class="center-image"><img class="image"  src='https://i.postimg.cc/Y9cj2Byg/table1.png' alt="table1"></div>
    {/if}
    {#if index >= 28 && index <= 30 || index == 32}
    <div class="center-image"><img class="image" src='https://i.postimg.cc/YCb1S01F/merge-1.png' alt="lipsticks2"></div>
    {/if}
  </div>

<div id="foreground" slot="foreground">
  <div>
    <section>
      <div class="center-div" bind:this={box}><h1 style="font-size: 52px;text-align: center; color:aliceblue;">Yang Tersisa dari Bibir Merona</h1>
  </div>
    </section>
</div>

  <div>
      <section style="display: flex;">
        <div class="center-div"><label class="prompt">Halo Namaku <input type="text" bind:value={$user.name}/></label></div>
      </section>
  </div>
<div>
<section><div class="center-div"><div class="prompt" style="background-color: {data[selected].clr};"> Hingga saat ini, aku memiliki  
<select bind:value={selected}>
  {#each data as d}
    <option value={d.id}>
      {d.name}
    </option>
  {/each}
</select> buah produk kosmetik bibir
</div>
</div>
</section>
</div>
<div>
  <section>
    <div class="center-div"><div class="prompt" style="background-color: {data[selected].clr};">{data[selected].desc}</div>
    </div>
  </section>
</div>
<div>
  <section>
    <div class="center-div">
      <label class="prompt">Saya dengan sadar menggunakan lipstik sejak usia <input type="text" bind:value={$user.usia}/> tahun</label>
    </div>
  </section>
  </div>

  <div><section>
    <div class="center-div">
    <div style="width: 90vw; height: 70vh;display: flex;
    flex-direction: column;
    align-items: center;"><p>
      Berdasarkan hasil survei daring kami kepada 117 orang, rata-rata memakai lipstik 
    karena keinginan sendiri ketika menginjak bangku SMA atau usia 15-19 tahun</p><canvas bind:this={chartCanvas} id="myChart"></canvas>
  </div>
  </div> 
  </section>    
  </div>
<div>
<section><div class="center-div"><div class="prompt" style="background-color: #ffe2e2ff;">Apakah kamu memperhatikan masa kadaluarsa produk kosmetik bibir yang kamu miliki?</div>
  <div style="    display: flex;
  width: 80%;
  justify-content: space-between;"><button style="background-color: #e6b8afff; width: 100px" on:click={() => changePilih("#e6b8afff")}>Ya</button>
    <button style="background-color: #e06666ff; width: 100px" on:click={() => changePilih("#e06666ff")}>Tidak</button></div>
</div>
</section>
</div>
<div>
<section><div class="center-div"> <div class="prompt" style="background-color: {pilih}"> 67,5% responden kami mengaku mengetahui dan/atau memperhatikan Period After Opening (PAO) 
  atau masa simpan produk kosmetik yang mereka miliki. Sementara 32,5% sisanya tidak mengetahui 
  ataupun memperhatikan masa pakai setelah membuka produk kosmetik mereka.</div> </div></section>
</div>
<div>
  <section>
  
  <div class="center-div">
  <div class="prompt"> 
      Produk lipstik rata-rata memiliki PAO 12-24 bulan. Lalu apa yang kamu lakukan jika produk kosmetik yang kamu miliki telah melewati masa pakai atau tanggal kadaluarsanya?
    </div>
    <div style="display: flex;
    width: 80%;
    justify-content: space-between;"> 
      <button style="background-color: {data1[0].clr}" on:click={() => {num = 0}}>Dibuang ke tong sampah</button>
  <button style="background-color: {data1[1].clr}" on:click={() => {num = 1}}>Dibakar di depan rumah</button>
  <button style="background-color: {data1[2].clr}" on:click={() => {num = 2}}>Dibuang ke badan air (sungai, kali, atau got)</button>
  <button style="background-color: {data1[3].clr}" on:click={() => {num = 3}}>Dikumpulkan untuk didaur ulang</button>  
    </div></div>    
</section>
  </div>
<div>
<section><div class="center-div"> <div class="prompt" style="background-color: {data1[num].clr}">{data1[num].a}</div></div> </section>
</div>
<div>
<section><div class="center-div"> <div class="prompt" style="background-color: {data1[num].clr}">{data1[num].b}</div></div> </section>
</div>
<div>
<section><div class="center-div"> <div class="prompt" style="background-color: {data1[num].clr}">{data1[num].c}</div></div> </section>
</div>
<div>
<section><div class="center-div"> <div class="prompt"><p>Saat ini sebenarnya Kementerian Lingkungan Hidup dan Kehutanan (KLHK) 
  melalui Permen LHK Nomor 75 Tahun 2019 sudah menargetkan pengurangan timbulan 
  sampah hingga sebesar 30 persen pada tahun 2030.</p></div></div> </section>
</div>
<div>
<section><div class="center-div"> <div class="prompt"><p>Kementerian LHK mewajibkan produsen untuk mengurangi sampah dengan 
  cara menggunakan produk kemasan atau wadah yang mudah diurai oleh alam, mendaur 
  ulang sampah mereka, menggunakan bahan baku produksi hasil daur ulang, serta 
  menarik kembali sampah dan produk kemasan atau wadah dari konsumen untuk didaur ulang.  
  Termasuk dalam industri manufaktur yang diatur oleh Permen ini yaitu industri 
  kecantikan dan perawatan tubuh atau personal care.</p></div></div> </section>
</div>
<div>
<section><div class="center-div"><div class="prompt"><p>Memang beberapa tahun belakangan ini industri kecantikan di Indonesia 
  sedang mengalami kenaikan yang sangat pesat. Data yang dirilis oleh Nielsen 
  and Euromonitor menunjukkan adanya pertumbuhan penjualan sebesar 11,99% pada 
  tahun 2017 di Indonesia, yang memberikan kontribusi sebesar Rp19 triliun atau 
  setara USD 1,4 miliar. Lebih tinggi dari rata-rata pertumbuhan sektor kosmetik 
  enam tahun sebelumnya, yaitu hanya 10%. </p></div></div> </section>
</div>
<div>
<section><div class="center-div"> <div class="prompt"><p>Kenaikan tersebut juga tergambar dari data produk kosmetik yang terdaftar 
  di BPOM sejak tahun 2017-2021. Dari hasil analisis, kami menemukan???</p></div></div> </section>
</div>
<div>
<section><div class="center-div"><div class="prompt"><p>Jumlah produk kosmetik yang terdaftar di BPOM melonjak lima kali lipat dari 2017 ke 2021. </p></div></div></section>
</div>
<div>
<section><div class="center-div" style="justify-content: flex-start;"><div class="prompt"><p>Informasi Data Kosmetika Terdaftar di cekbpom.pom.go.id</p></div></div></section>
</div>
<div>
<section><div class="center-div"></div></section>
</div>
<div>
<section><div class="center-div"></div></section>
</div>
<div>
<section><div class="center-div"></div></section>
</div>
<div>
<section><div class="center-div"></div></section>
</div>
<div>
<section><div class="center-div" style="justify-content: flex-start;"><div class="prompt"><p>Jumlah produk dengan kata kunci ???lip??? untuk produk dekoratif bibir yang 
  terdaftar di cekbpom.pom.go.id</p></div></div></section>
</div>
<div>
<section><div class="center-div" style="justify-content: flex-start;"><div class="prompt"><p>Perbandingan rata-rata produk kosmetik dan lipstik yang terdaftar per hari 
  di cekbpom.pom.go.id</p></div></div></section>
</div>
<div>
<section><div class="center-div" style="justify-content: flex-start;"><div class="prompt"><p>Industri lipstik lokal mulai berjaya di tahun 2019. Dari 155 jenis kosmetik 
  yang terdaftar, 21 di antaranya adalah produk kosmetik bibir. </p></div></div></section>
</div>
<div>
<section><div class="center-div"></div></section>
</div>
<div>
<section><div class="center-div"></div></section>
</div>
<div>
<section><div class="center-div"></div></section>
</div>
<div>
<section><div class="center-div"><div class="prompt"><p>Kami juga merangkum 10 merek kosmetik lokal favorit berdasarkan survei 
  Populix, yaitu Wardah, Emina, Make Over, Somethinc, Purbasari, Y.O.U, 
  Dear Me Beauty, Sariayu, Luxcrime, dan Mustika Ratu. Dari ke-10 merek tersebut, 
  baru Wardah, Emina, Somethinc yang memiliki program daur ulang melalui kerja sama 
  dengan Waste4Change. Sisanya seperti Make Over, Y.O.U, Dear Me Beauty, masih 
  mengandalkan program daur ulang yang disediakan oleh platform Sociolla. Sedangkan 
  Purbasari, Luxcrime, Sariayu, dan Mustika Ratu, belum memiliki kampanye untuk 
  mendaur ulang produk mereka.</p></div></div></section>
</div>
<div>
<section><div class="center-div"><div class="prompt"><p>Dari hasil wawancara kami dengan Waste4Change, salah satu kriteria produk 
  kemasan lipstik yang mudah didaur ulang yaitu menggunakan warna transparan atau putih, 
  agar tidak menghasilkan bijih plastik hasil daur ulang yang downgrade terlalu jauh dari 
  kualitas plastik baru. </p></div></div></section>
</div>
<div>
<section><div class="center-div"><div class="prompt"><p>Dari ke-10 produk lokal favorit ada sekitar 94 jenis produk kosmetik dekoratif bibir. 
  Namun hanya kurang lebih 38 produk yang menggunakan plastik transparan untuk kemasannya. 
  Sisanya memakai kemasan berwarna hitam, atau warna-warna terang sesuai dengan warna produk 
  lipstik di dalamnya. </p></div></div></section>
</div>
<div>
<section><div class="center-div" style="justify-content: flex-start;"><div class="prompt"><p>Perbandingan jumlah produk kosmetik bibir dengan kemasan transparan dari merek lokal favorit</p></div></div></section>
</div>
<div>
<section><div class="center-div"> <div class="prompt"><p>Kemasan kosmetik yang berwarna tetap bisa didaur ulang. Hanya saja, dibutuhkan 
  usaha ekstra untuk memisahkan sampah plastik tersebut sesuai warna dan jenis bahannya. </p></div></div> </section>
</div>
<div>
<section><div class="center-div"> <div class="prompt"><p>Jadi, sampah kosmetik harusnya dikemanain?</p></div> 
  <div style="display: flex;
  width: 80%;
  justify-content: space-between;"><button on:click={scrollToTop}>Pilih lagi cara membuang sampah kosmetikmu</button>
  <div class="prompt">atau</div>
  <div style="position: relative;"><img class="image" style="height: 20vh; width:30vw" src='https://i.postimg.cc/5NXVf60n/unnamed-15.png' alt="lipbam"><div style="position: absolute; top:0; left:0;display: flex;
    justify-content: center;
    align-items: center;
    padding: 0 90px;
    width: 100%;
    height: 100%;
    box-sizing: border-box;">Klik di sini untuk menonton dokumenter kami</div></div></div></div></section>
</div>
</Scroller>
</div>

<style>

.image{
    height: 80vh;
    align-items: center;
    justify-content: center;
  }

[slot="background"] {
  background-color: #346b71;
  border-top: 2px solid #346b71;
  border-bottom: 2px solid #346b71;
  font-size: 1.4em;
  overflow: hidden;
      height: 100vh;
      width: 100vm;
}

[slot="foreground"] {
  scroll-snap-type: y mandatory;
  height: 100vh;
    overflow-y: auto;
}

[slot="foreground"] section {
  pointer-events: all;
}

.center-div{
  width: 100%;
    display: flex;
    align-items: center;
    height: 100%;
    justify-content: center;
    flex-direction: column;
    position: absolute;
    top: 0;
    left: 0;
}

.center-image{
  width: 100%;
    display: flex;
    align-items: center;
    height: 100%;
    justify-content: center;
    flex-direction: column;
}

.prompt {
  border-radius: 5px;
    background-color: #eeeeee;
    color: black;
    padding: 10px 30px;
    border: 2px solid;
    max-width: 1000px;
}

.phone-text {
  position: absolute;
  top: 10%;
  left: 27%;
  font-size: 0.8rem;
  width: 20%;
  color: black;
}

section {
  height: 100vh;
  scroll-snap-align: start;
  position: relative
}
</style>