---
title: "The startup screen."
date: 2006-12-13
forum: General Help
---

### Post by Absurd on 2006-12-13
You know the start up screen with the logo and the progress bar on the bottom? How can I get rid of that and use a verbose start up screen without the logo? 

I used usplash-minimalistic_0.1 and used update-alternatives to switch to it but the start up screen is still there.

---

### Post by LLRNR on 2006-12-14
You'd just need to edit out a few words in your /boot/grub/menu.lst file. At least this is how I did it in Edgy to enable a clear, plain text boot (I love it).

You'll find a line that should look like this:
```
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
```

I just deleted the "quiet" and "splash" words...

HTH,

LLRNR

---

### Post by Absurd on 2006-12-14
Thanks.

---

