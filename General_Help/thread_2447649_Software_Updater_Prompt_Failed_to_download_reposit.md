---
title: "Software Updater Prompt: Failed to download repository information"
date: 2020-07-23
forum: General Help
---

### Post by Shadius on 2020-07-23
Hi Ubuntu Community,

I'm getting this prompt everytime I run Software Updater:

[ATTACH=CONFIG]286522[/ATTACH]

I click OK and it'll update, but why am I getting this everytime and how can I correct it?

---

### Post by Dennis N on 2020-07-23
I would investigate the output of **sudo apt update** to see if some repository is unreachable.

---

### Post by ActionParsnip on 2020-07-23
The GUI hides a lot of detail. What is the output of
```

sudo apt update 

```
Thanks

---

