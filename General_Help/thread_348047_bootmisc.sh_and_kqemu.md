---
title: "bootmisc.sh and kqemu"
date: 2007-01-28
forum: General Help
---

### Post by wxnker on 2007-01-28
I would like kqemu (qemu acceleration) to start up with Ubuntu to avoid: [COLOR="RoyalBlue"]"Could not open '/dev/kqemu' - QEMU acceleration layer not activated"[/COLOR] when starting win 2000 with qemu. I tried using -kernel-kqemu when starting but qemu still starts  with no acceleration.

So I read that adding the below mentioned lines to **/etc/init.d/bootmisc.sh** should do the trick in Ubuntu. 

_Lines to add:_

# Start Qemu with KQemu accelerator
/sbin/modprobe kqemu
mknod /dev/kqemu c 250 0 # Create the KQEMU device
chmod 666 /dev/kqemu # Make it accessible to all users

Where do I add these lines in **bootmisc.sh**?

---

### Post by wxnker on 2007-01-28
I solved this by making an executable script "**kqemu.sh**". 

Then I copied the script to /etc/init.d/ and ran:

[COLOR="Blue"]$  sudo update-rc.d kqemu.sh defaults[/COLOR]

---

### Post by frühstück on 2007-05-01
That's exactly what i was looking for, thanks!

---

