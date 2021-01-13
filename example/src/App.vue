<template>
  <div class="dt-wrapper">
    <date-picker
      v-model="value"
      lang="ru"
      format="YYYY-MM-DD HH:mm:ss"
      type="datetime"
      range
      confirm
      class="datepicker__width"
      :show-time-panel="showTimeRangePanel"
      @close="handleRangeClose"
    >
      <template v-slot:footer>
        <button class="mx-btn mx-btn-text" @click="toggleTimeRangePanel">
          {{ showTimeRangePanel ? 'select date' : 'select time' }}
        </button>
      </template>
    </date-picker>
  </div>
</template>

<script>
import DatePicker from 'vue2-datepicker';
// import 'vue2-datepicker/locale/ru';
import 'vue2-datepicker/index.css';

export default {
  name: 'App',
  components: {
    DatePicker,
  },
  data() {
    return {
      showTimeRangePanel: false,
      value: [],
    };
  },
  methods: {
    toggleTimeRangePanel() {
      this.showTimeRangePanel = !this.showTimeRangePanel;
    },
    handleRangeClose() {
      this.showTimeRangePanel = false;
    },
  },
};
</script>

<style>
.dt-wrapper .mx-input {
  font-size: 1rem;
  height: 2.5em;
  color: #363636;
}

.dt-wrapper * + * {
  margin-top: 0;
}
.mx-datepicker-popup table td {
  vertical-align: inherit;
  text-align: center;
}

.datepicker__width {
  min-width: 358px;
  max-width: 100%;
}

.dt-wrapper .mx-input:hover{
  border-top-color: rgb(181, 181, 181);
  border-right-color: rgb(181, 181, 181);
  border-bottom-color: rgb(181, 181, 181);
  border-left-color: rgb(181, 181, 181);
}

.dt-wrapper .mx-input:focus {
  border-top-color: rgb(50, 115, 220);
  border-right-color: rgb(50, 115, 220);
  border-bottom-color: rgb(50, 115, 220);
  border-left-color: rgb(50, 115, 220);
  box-shadow: 0 0 0 0.125em rgba(50, 115, 220, 0.25);
}
</style>
