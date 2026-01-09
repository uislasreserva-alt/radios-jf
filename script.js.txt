// BUSCA
const searchInput = document.getElementById("search");
searchInput.addEventListener("input", function() {
  const radios = document.querySelectorAll(".radio-card");
  const query = this.value.toLowerCase();
  radios.forEach(radio => {
    const name = radio.dataset.name.toLowerCase();
    radio.style.display = name.includes(query) ? "block" : "none";
  });
});

// PLAYER ÚNICO
const playButtons = document.querySelectorAll(".play-btn");
let currentAudio = null;

playButtons.forEach(btn => {
  btn.addEventListener("click", function() {
    const audio = this.nextElementSibling;
    if (currentAudio && currentAudio !== audio) {
      currentAudio.pause();
      currentAudio.currentTime = 0;
    }
    if (audio.paused) {
      audio.play();
      currentAudio = audio;
      this.textContent = "⏸️ Pausar";
    } else {
      audio.pause();
      this.textContent = "▶️ Tocar";
    }
  });
});

// FAVORITOS
const favButtons = document.querySelectorAll(".fav-btn");
favButtons.forEach(btn => {
  btn.addEventListener("click", function() {
    this.classList.toggle("active");
    if(this.classList.contains("active")) {
      this.textContent = "⭐ Favorito";
    } else {
      this.textContent = "☆ Favorito";
    }
  });
});
