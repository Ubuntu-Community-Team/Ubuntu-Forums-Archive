---
title: "Extra linux kernel visible to Grub"
date: 2014-02-10
forum: General Help
---

### Post by echo59 on 2014-02-10
Hi, I'm running Ubuntu 12.04 on a Dell Studio 17 which dual-boots with Windows Vista.  I have three partitions, my Ubuntu OS, my Windows OS and a data partition that's accessed by both OSs.  My problem is there seems to be an old linux kernel which keeps appearing when I run update-grub.  I've searched for this kernel on Synaptic and using Ubuntu Tweak but it isn't listed so I can't seem to remove it that way.

When I run *update-grub* I get the following output:
> Found linux image: /boot/vmlinuz-3.2.0-59-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-59-generic-pae
Found linux image: /boot/vmlinuz-2.6.31-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda3

When I run *dpkg --list | grep linux-image* I get the following output:
> rc  linux-image-2.6.35-22-generic-pae             2.6.35-22.35                                 Linux kernel image for version 2.6.35 on x86
rc  linux-image-2.6.35-24-generic-pae             2.6.35-24.42                                 Linux kernel image for version 2.6.35 on x86
rc  linux-image-2.6.35-25-generic-pae             2.6.35-25.44                                 Linux kernel image for version 2.6.35 on x86
rc  linux-image-2.6.35-26-generic-pae             2.6.35-26.46                                 Linux kernel image for version 2.6.35 on x86
rc  linux-image-2.6.35-27-generic-pae             2.6.35-27.48                                 Linux kernel image for version 2.6.35 on x86
rc  linux-image-2.6.35-28-generic-pae             2.6.35-28.50                                 Linux kernel image for version 2.6.35 on x86
rc  linux-image-2.6.35-29-generic-pae             2.6.35-29.51                                 Linux kernel image for version 2.6.35 on x86
rc  linux-image-2.6.35-30-generic-pae             2.6.35-30.61                                 Linux kernel image for version 2.6.35 on x86
rc  linux-image-2.6.35-31-generic-pae             2.6.35-31.62                                 Linux kernel image for version 2.6.35 on x86
rc  linux-image-2.6.38-13-generic-pae             2.6.38-13.52                                 Linux kernel image for version 2.6.38 on x86
ii  linux-image-3.2.0-59-generic-pae              3.2.0-59.90                                  Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic-pae                       3.2.0.59.70                                  Generic Linux kernel image

When I try to use *apt-get* to remove the kernel 2.6.31-22 listed in *update-grub* I get error messages saying that the package could not be located.

Looking in my /boot folder I see the following contents:
> root@echo59-Studio17:/boot# dir
abi-3.2.0-59-generic-pae 
        memtest86+.bin
boot.0820 
                            memtest86+_multiboot.bin
config-3.2.0-59-generic-pae 
    System.map-3.2.0-59-generic-pae
debian.bmp 
                          vmlinuz-2.6.31-22-generic
grub 
                                    vmlinuz-3.2.0-59-generic-pae
initrd.img-3.2.0-59-generic-pae

So there seems to be a vmlinuz file for the "offending" kernel in the /boot directory.

How can I get rid of this kernel from my Grub menu?  Is it a case of deleting the *vmlinuz-2.6.31-22-generic *file (3.9MB size) and re-running *update-grub*?  As I said before, the usual methods of using apt-get, Synaptic and Ubuntu Tweak hasn't worked.

---

### Post by NM5TF on 2014-02-10
from the Ask Ubuntu web site, they say this will remove ALL kernels EXCEPT the current one:

```
sudo apt-get remove --purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d'
```

you should read the article at the site before proceeding to insure you are comfortable doing this....go here:

[http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu](http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu)

tommy

---

### Post by echo59 on 2014-02-10
No joy.  As I said before, the package for that kernel doesn't seem to exist so I couldn't get rid of it using *apt-get*.  Thanks though.

---

### Post by oldfred on 2014-02-10
Those must be left over from an old install, either an upgrade or an install that did not reformat. But now those kernels are not in dpkg, and then cannot be removed.

You will have to manually remove and then empty root's trash.

I had to do this, from my history, with some lines with typos removed. :)
Be very careful with gksudo nautilus to only remove old files and with rm as even typos can have it do things to unexpected places.

 Show files:
find $HOME -type f -name "*~" -print
Delete those files, careful with any rm command.
find $HOME -type f -name "*~" -print -exec rm {} \; 

   1253  dpkg -S /usr/src/*
 1254  uname --kernel-release
 1255  sudo apt-get update
 1256  sudo apt-get upgrade
 1257  sudo apt-get -s autoclean
 1258  sudo apt-get autoclean
 1259  sudo apt-get -s autoremove
 1260  sudo apt-get  autoremove
 1261  df -h
 1263  gksudo nautilus
 1268  sudo chown -R fred /root/.local/share/Trash/
 1274  sudo rm -rf /root/.local/share/Trash/
 1275  df -h
 1276  history

---

### Post by The Cog on 2014-02-10
If it were me, I would make a folder in /boot to move the "unwanted" files to. Then if you mobe something wrong, a live CD can drag them back again. If things still work, you can then delete the folder and contents.

---

### Post by echo59 on 2014-02-10
Fred, your suggestion worked a treat.

Guys, thanks for your advice.

---

