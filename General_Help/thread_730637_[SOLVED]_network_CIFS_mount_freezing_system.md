---
title: "[SOLVED] network CIFS mount freezing system"
date: 2008-03-21
forum: General Help
---

### Post by dlstrife on 2008-03-21
I'm running 7.10 gutsy. i'm trying to mount a network drive from a windows server. I'm adding the following line into /etc/fstab

//host/folder /home/user/folder cifs auto,credentials=/.credentials,fmask=0777,dmask=0777 0 0

The drive mounts fine from boot and I can access, copy, etc everything on it. However my system locks up after a minute or two of use. Everything freezes and my capslock and scrolllock keys blink. CTRL-ALT-BACKSPACE/DEL/F1 do nothing. I have to do a hard reboot with the power button to do anything with the system. When I remove this line and unmount the drive everything works fine, so this is definitely causing the freeze. Any ideas?

---

### Post by justleen on 2008-03-21
if you mount it manually, not through fstab, do you have the same problem?

---

### Post by dlstrife on 2008-03-22
it works if i manually mount it, and will now work for a while automounting, but after a while will start causing the system to lock up again. if i unmount it the freeze doesn't happen.

---

### Post by dlstrife on 2008-03-24
Mounted it as a server connection instead through nautilus of through /etc/fstab. Connects on boot and doesn't crash. :)

---

### Post by waffen on 2008-04-04
Hello,

I have a similar problem, what do you fixed?

Thanks!

---

