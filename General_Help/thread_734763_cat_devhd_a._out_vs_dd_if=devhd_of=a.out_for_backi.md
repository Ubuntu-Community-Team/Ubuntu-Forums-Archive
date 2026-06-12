---
title: "cat /dev/hd* a. out vs dd if=/dev/hd* of=a.out for backing up"
date: 2008-03-25
forum: General Help
---

### Post by ayampanggang on 2008-03-25
is there any differences between using cat and dd in copying data?

i just used dd to backup my dvd game, but just now i thought using cat would be a better idea since it is at higher level/less chance to mess my hdd.

opinions?


and btw, is there any chance of dd to ruin my partition if i run that command above?

thank you. :)

---

### Post by dcstar on 2008-03-25
> **ayampanggang said:**
> is there any differences between using cat and dd in copying data?

i just used dd to backup my dvd game, but just now i thought using cat would be a better idea since it is at higher level/less chance to mess my hdd.

opinions?


and btw, is there any chance of dd to ruin my partition if i run that command above?

thank you. :)

**cat** is a command to output text data, it is problematic it will work with binary data and certainly not on raw hard disk data, that is what **dd** is for.

---

### Post by ayampanggang on 2008-03-25
i see. thank you for your explanation :)

---

