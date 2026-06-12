---
title: "GRUB Error 22"
date: 2008-02-03
forum: General Help
---

### Post by lepard89 on 2008-02-03
Hi, I'v been duel booting ubuntu and m.vista for a while now with no problems.
But today I'v run into a big one. I think i did a booboo by deleting a partion via vista because now grub wont load. the screen just reads:> GRUB Loading stage1.5

GRUB loading, please wait...
Error 22

I cant do anything from here. I don't want to format my HDD because I have alot of files I don't want to loose. Is there a way to solve this error and go back to normal? or is there a way to save my files before formatting?... Is it possible and safe to reinstall ubuntu again without harming vista?

Many thanks to any responses.
  - L

---

### Post by Kevbert on 2008-02-03
Hi. My Windows XP became unstable after dual booting with Ubuntu.  I decide to remove Ubuntu by re-installing XP, only to find I got error 22.  It's due to the fact that you've lost your master boot record.
To recover XP you need to run Fixmbr.
To do this you need to get your original windows install disk and boot from it.  Go into recovery mode and type Fixmbr from the Dos prompt.
If you need to run Grub for Linux there are other posts on the forum on how to sort this.
Good luck.

---

