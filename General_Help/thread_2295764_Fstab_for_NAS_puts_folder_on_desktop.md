---
title: "Fstab for NAS puts folder on desktop"
date: 2015-09-21
forum: General Help
---

### Post by lou6 on 2015-09-21
I've recently added a wd my cloud to my system (xubuntu 14.04 lts) and have been trying access methods to find the best for my situation. Mounting via gigolo is simple and works fine but seems a bit slow so I tried adding the device to /etc/fstab:

192.168.x.xxx:/nfs /home/lou/xyz nfs rw,udp,vers=3,soft,intr,rsize=8192,wsize=8192 0 0 

This also works fine with the added benefit of giving me an actual folder (xyz) in my home directory and the nfs connection is about 50% faster than with samba but, for some odd reason, a folder named xyz also appears on  the desktop and also links to the cloud device.

The folder isn't affecting anything but I'm wondering why it's there and how to remove it if I choose to.

TIA for any help...

---

### Post by sotiris2 on 2015-09-21
There is apparently a setting in righ click on Desktop - > Desktop Settings -> Icons about displaying drives in the Desktop. This will affect all drives though.

---

### Post by lou6 on 2015-09-21
Actually, I think you've solved it for me. I'll give it a try and see...

Thanks

---

