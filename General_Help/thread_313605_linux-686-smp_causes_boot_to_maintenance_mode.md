---
title: "linux-686-smp causes boot to maintenance mode"
date: 2006-12-06
forum: General Help
---

### Post by Just Pete on 2006-12-06
I've got a poweredge 2650 with 2 multi-threaded processors and 12GB of RAM. 

I've successfully installed Dapper, and it boots just fine, but at first saw only 1 CPU.

So I did apt-get install linux-686-smp to get the multi-proc support. This worked just fine, but now I have a boot problem - the system boots to maintenance mode everytime. I get a prompt to enter the root password for maintenance mode, or press <ctrl-D> to continue. Actually pressing <ctrl-D> allows the system to finish booting without any other issues. /etc/inittab is set to go to runlevel 2, so I'm not sure what is causing this.

Any help is greatly appreciated!

---

### Post by Iowan on 2006-12-06
Check the **/boot/grub/menu.lst** file to see if the maintenance mode somehow got set as the default mode.

---

### Post by Just Pete on 2006-12-06
Nope. default boot is set to the following:

title           Ubuntu, kernel 2.6.15-27-686
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-686
savedefault
boot

Unless I've forgotton how to count - this is the 3rd 'title' in my grub menu, and the default value is set to 3 (this doesn't start counting at 0, I don't think...)

---

### Post by Iowan on 2006-12-06
> **Just Pete said:**
> 
(this doesn't start counting at 0, I don't think...)
Yup, it does...
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS")

---

### Post by Just Pete on 2006-12-06
Figures. I spent a couple hours last night and this morning puzzling over this, and didn't think of the '0' numbering until my last reply. Thanks for prodding my brain.

---

