<template>
  <div>
    <h1>Data from MySQL Database</h1>
    <ul>
      <li v-for="item in data" :key="item.id">{{ item.name }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      data: []
    };
  },
  mounted() {
    // Daten vom PHP-Server abrufen
    fetch('https://ivm108.informatik.htw-dresden.de/ewa/g02/daten/beleg/get_data.php')
      .then(response => response.json())
      .then(data => {
        this.data = data;
      })
      .catch(error => console.error('Error:', error));
  }
};
</script>

