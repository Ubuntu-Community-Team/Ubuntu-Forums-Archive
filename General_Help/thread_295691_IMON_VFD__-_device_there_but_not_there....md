---
title: "IMON VFD  - device there but not there..."
date: 2006-11-08
forum: General Help
---

### Post by barkerben on 2006-11-08
Hi,

I have been trying to isnatall the IMON VFD in Ubuntu. I have succeeded in installing the VFD module and installing LCDProc, all without errors,and after checking that /dev/lcd0 existed, I found that it did.

Using lsusb also shows the VFD to exist:

Bus 002 Device 003: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller

However, if I try logging in as superuser and doing:

echo "Hello World" > /dev/lcd0

It claims there is no such device. 

"bash: No such device"

However, the file is certainly there - it will even autocomplete the lcd0 for me when I press tab. from within the /dev directory.

Any ideas?

I'm running Edgy on a AMD62 X2 4200 system running the generic kernel...

Cheers,

Ben

---

