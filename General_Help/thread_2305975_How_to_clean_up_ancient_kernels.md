---
title: "How to clean up ancient kernels"
date: 2015-12-11
forum: General Help
---

### Post by 7-webmaster on 2015-12-11
The contents of my /boot directory is:

```
abi-3.11.0-19-generic
abi-3.13.0-24-generic
abi-3.13.0-39-generic
abi-3.16.0-23-generic
abi-3.16.0-24-generic
abi-3.16.0-25-generic
abi-3.16.0-28-generic
abi-3.19.0-39-generic
abi-4.2.0-19-generic
config-3.11.0-19-generic
config-3.13.0-24-generic
config-3.13.0-39-generic
config-3.16.0-23-generic
config-3.16.0-24-generic
config-3.16.0-25-generic
config-3.16.0-28-generic
config-3.19.0-39-generic
config-4.2.0-19-generic
grub
initrd.img-3.11.0-19-generic
initrd.img-3.13.0-24-generic
initrd.img-3.13.0-39-generic
initrd.img-3.16.0-23-generic
initrd.img-3.16.0-24-generic
initrd.img-3.16.0-25-generic
initrd.img-3.16.0-28-generic
initrd.img-3.19.0-39-generic
initrd.img-4.2.0-19-generic
memtest86+.bin
memtest86+.elf
memtest86+_multiboot.bin
System.map-3.11.0-19-generic
System.map-3.13.0-24-generic
System.map-3.13.0-39-generic
System.map-3.16.0-23-generic
System.map-3.16.0-24-generic
System.map-3.16.0-25-generic
System.map-3.16.0-28-generic
System.map-3.19.0-39-generic
System.map-4.2.0-19-generic
vmlinuz-3.11.0-19-generic
vmlinuz-3.13.0-24-generic
vmlinuz-3.13.0-39-generic
vmlinuz-3.16.0-23-generic
vmlinuz-3.16.0-24-generic
vmlinuz-3.16.0-25-generic
vmlinuz-3.16.0-28-generic
vmlinuz-3.19.0-39-generic
vmlinuz-4.2.0-19-generic

```
How do I clean this up.  They are no longer tracked by the package system.  I only want to keep my last 15.04 kernel and the new 15.10 kernel.  Can I just delete the ancient files and manually rebuild Grub?

---

### Post by leunam12 on 2015-12-11
Try installing Ubuntu Tweak and then use the Janitor to clean your system. Maybe that will take care of it.

---

### Post by SirMoo on 2015-12-11
You can try the manual method and see if that clears those files as well. [https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)

---

### Post by ian-weisser on 2015-12-11
> **7-webmaster said:**
> They are no longer tracked by the package system
That seems worrisome. What leads you to this conclusion?

Usually, a simple 'apt-get autoremove' will clean out older kernels.
A great deal of effort went into that simple solution, so let us know if it does not work for you.
No additional software or scripts or other voodoo needed.

---

### Post by Enigma12 on 2015-12-12
First, heed the advice of the more knowledgeable people here ahead of what I offer. I stil have LOTS to learn. But I read a post months ago about old kernels building up and the post-er requested a solution. The advice he/she was given was to run the following in terminal: 

sudo apt-get purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1) --assume-yes

I have not yet attempted to understand all the details of that command, but I have used this 3 or 4 times without problems. Although it was stated that this command would remove all but the latest two kernels, it has always removed every kernel except the latest. I wait until that latest kernel works without problems before I run that command.

---

