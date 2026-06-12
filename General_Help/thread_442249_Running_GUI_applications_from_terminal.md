---
title: "Running GUI applications from terminal"
date: 2007-05-13
forum: General Help
---

### Post by MiCovran on 2007-05-13
Sometimes I like to run even some GUI applications from terminal for practical reasons. However, I'm thinking if there's a way I can, for instance, run "evince foo.pdf" and still be able to use this same terminal before closing evince (I hope you understand what I'm trying to say). So, can this be done?

Thanks.

---

### Post by taurus on 2007-05-13
```
evince foo.pdf &
```
to send it to background.

---

### Post by 13u11fr09 on 2007-05-13
> **MiCovran said:**
> Sometimes I like to run even some GUI applications from terminal for practical reasons. However, I'm thinking if there's a way I can, for instance, run "evince foo.pdf" and still be able to use this same terminal before closing evince (I hope you understand what I'm trying to say). So, can this be done?

Thanks.

put an "&" at the end of a command you'd like to "run in the background"... using your example, you'd type:

```

evince foo.pdf &

```

EDIT: taurus is too quick ;)

---

### Post by MiCovran on 2007-05-13
Thanks, that's just what I wanted.

---

