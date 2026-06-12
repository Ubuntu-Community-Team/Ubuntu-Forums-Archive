---
title: "Dual Booting"
date: 2007-07-28
forum: General Help
---

### Post by jan00b on 2007-07-28
Right now I used Ubuntu to format my corrupted windows partition and installed it on the second one. I reinstalled windows on the first one and it runs smoothly (wow that’s a first). Problem is it will ONLY boot into XP and does not give me the option of booting into Ubuntu. Who can I now boot into Ubuntu. If it requires reformatting Ubuntu I’m fine with that, I don't have anything important on it yet.

---

### Post by Happy_Man on 2007-07-28
Well... yes it does require reinstalling. Go ahead and do that.

---

### Post by merlinus on 2007-07-28
When you installed windows, it overwrote grub in the mbr.  You can probably reinstall grub, however, without reinstalling ubuntu.

This can be done from the live cd.

Open a terminal, and enter:

```

sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit

```Substitute your results for (hdx,x).  It will probably be something like (hd0,1).

-merlin

---

### Post by bodhi.zazen on 2007-07-28
> **Happy_Man said:**
> Well... yes it does require reinstalling. Go ahead and do that.

LOL

No you just need to restore grub as merlinus suggests.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

