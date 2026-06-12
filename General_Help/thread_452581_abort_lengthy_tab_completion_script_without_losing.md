---
title: "abort lengthy tab completion script without losing typed command"
date: 2007-05-23
forum: General Help
---

### Post by HadroLepton on 2007-05-23
i have bash_completion enabled and i like it a lot. but every once in a while i press one tab too many and trigger the completion where i didn't want to.

for example
```

apt-g[TAB]
apt-get i[TAB]
apt-get install [TAB][TAB]

```
now the processor will go up to 100% for a few seconds and then ask me
```

Display all 24149 possibilities? (y or n)

```

during those few seconds the shell is unresponsive. i can abort the completion script with CTRL-C but then i also lose the typed command. is there any way to abort the completion script without losing the typed command?

---

### Post by fanatik on 2007-05-24
i know the problem... don't know of any solution other than patience! :(

---

