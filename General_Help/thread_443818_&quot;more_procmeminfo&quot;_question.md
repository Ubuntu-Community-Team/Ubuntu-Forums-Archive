---
title: "&quot;more /proc/meminfo&quot; question"
date: 2007-05-14
forum: General Help
---

### Post by rscott5 on 2007-05-14
Hi all,

This is kind of random, but I was using someone's Ubuntu machine about a month ago, and I noticed that they had a command running in the terminal which would constantly update with memory and process information. I am fairly certain that the command they were running was: ```
more /proc/meminfo
``` But when I do this it just show the data and then ends. Is there a way to get this to keep updating, or is there something else I should run instead? I just want to see current memory and process information. Thanks in advance for your help.

---

### Post by scrooge_74 on 2007-05-14
use the "top" command

---

### Post by rscott5 on 2007-05-14
> **scrooge_74 said:**
> use the "top" command

Awesome! That was exactly what I was looking for. Thanks so much.

---

### Post by DoktorSeven on 2007-05-14
Also, watch:

**watch cat /proc/meminfo**

---

