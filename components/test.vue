<template>
  <div class="example">
    <client-only>
      <codemirror
        v-model="code"
        class="codemirror"
        :options="cmOption"
        @cursorActivity="onCmCursorActivity"
        @ready="onCmReady"
        @focus="onCmFocus"
        @blur="onCmBlur"
      />
    </client-only>
    <div v-html="code"></div>
  </div>
</template>

<script>
// import dedent from 'dedent'
export default {
  data() {
    return {
      cmOption: {
        tabSize: 4,
        styleActiveLine: true,
        lineNumbers: true,
        line: true,
        mode: 'text/html',
        theme: 'base16-dark',
      },
      code: 'const a = 100',
    }
  },
  methods: {
    onCmCursorActivity(codemirror) {
      console.debug('onCmCursorActivity', codemirror)
    },
    onCmReady(codemirror) {
      console.debug('onCmReady', codemirror)
    },
    onCmFocus(codemirror) {
      console.debug('onCmFocus', codemirror)
    },
    onCmBlur(codemirror) {
      console.debug('onCmBlur', codemirror)
    },
  },
}
</script>

<style scoped>
.example {
  display: flex;
  height: 100%;
}
.codemirror,
.pre {
  width: 50%;
  height: 100%;
  margin: 0;
  overflow: auto;
}
.pre {
  display: block;
  padding: 1rem;
  font-size: 14px;
  line-height: 1.6;
  word-break: break-all;
  word-wrap: break-word;
}
</style>
