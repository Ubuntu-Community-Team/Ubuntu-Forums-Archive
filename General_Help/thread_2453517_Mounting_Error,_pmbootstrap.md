---
title: "Mounting Error, pmbootstrap"
date: 2020-11-12
forum: General Help
---

### Post by scofisticated on 2020-11-12
Hello

I am trying to make a SD card to boot PostmarketOS from. I'm using Ubuntu 20.04 on a thumb drive. I'm posting this here to see if this is more an Ubuntu thing than a pmbootstrap thing. 

So when I get to the installation part of pmbootstrap, I put in [pmbootstrap install --sdcard= /dev/sdb]. Then bootstrap tries to prepare native chroot. Then an error happens 

"ERROR: Mount Failed: /proc -> /home/ubuntu/pine64 pine64-pinephone/chroot_native/proc"

The SD card is pretty new. I did format it. And it does show up on Gparted and in Files. The Micro SD card is in a "big" adapter, which is in a USB-SD adapter. 

And help is much appriciated. I can try to answer any questions.

---

### Post by TheFu on 2020-11-13
I don't think you can expect a chroot to work when the host is running amd64 CPU and the area you want to chroot is ARM-whatever.  OTOH, if you are booted on an ARM device with the same CPU, then I haven't any clue. Sorry.

CPU binary compatibility matters with chroot stuff.

---

