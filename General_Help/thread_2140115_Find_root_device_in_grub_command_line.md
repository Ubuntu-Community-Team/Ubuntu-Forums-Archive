---
title: "Find root device in grub command line"
date: 2013-04-28
forum: General Help
---

### Post by terminator14 on 2013-04-28
I'm messing around with my grub2 command line (the one that appears when you hit 'c' at the grub menu), trying to understand how to manually boot an OS. So far, the following seems pretty simple:
```

set root=(hd0,msdos1)					#The boot partition. Might be the same as the root partition if there's no separate boot partition
linux /boot/vmlinuz... root=/dev/sda1			#The kernel. The 'root=' part here is the root partition (where /usr, /bin, /sbin, etc. resides)
initrd /boot/initrd...					#The initial ramdisk image
boot							#Attempt to boot with the options above
```

The first line (boot partition) is pretty easy to find - as soon as you type "set root=(" and hit tab, it tells you what options are available. Using ls, you can actually check if it's the right partition or not.
The linux and initrd lines also allow easy tab completion.
The problem I'm seeing is that the device /dev/sda1 appears to be created further in the boot process than grub, so at this point, if I try to find /dev/sda1 with tab completion, or with ls, it doesn't exist. If I just guess that the kernel line is supposed to say "root=/dev/sda1", it works, but how am I supposed to actually use grub tools to figure this out?

---

### Post by terminator14 on 2013-04-30
The best (and only) solution I can think of right now is:

```
set root=(hd0,msdos1)
cat /etc/fstab
linux /boot/vmlinuz... root=UUID=[UUID from fstab]
initrd /boot/initrd...
boot
```

Is that the only way to do it?

---

### Post by Bashing-om on 2013-04-30
terminator14; Hi !

I am not too knowledgeable about grub (have not had to to this time) thus can not answer your question directly. May I be excused if I point you to the tutorials that will shed knowledge your way ?

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)[INDENT=2]
hope this helps

[/INDENT]

---

### Post by terminator14 on 2013-05-01
I suppose the other option is to just run it without the 'root=' part, instead adding 'break' to the kernel like so:

```
set root=(hd0,msdos1)
linux /boot/vmlinuz... break
initrd /boot/initrd...
boot
```

This will stop the boot process at an initrd shell, at which point you can use:

```
ls /dev/sd*
```

to see the available partitions, and mount them to a temp directory to see which is the right one. Once you find the right one, you can also use:

```
ls -l /dev/disk/by-uuid/
```

to find the disk's UUID if you are concerned that the device name might change after a reboot, which you will have to do to get back to the grub menu.

Technically, you don't even need the "break" part since the lack of "root=" on the kernel line will cause the boot process to stop at the initrd shell anyway, but I figure it's cleaner to ask it to stop than to wait until it tries to boot and fails.

> **Bashing-om said:**
> terminator14; Hi !

I am not too knowledgeable about grub (have not had to to this time) thus can not answer your question directly. May I be excused if I point you to the tutorials that will shed knowledge your way ?

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)[INDENT=2]
hope this helps

[/INDENT]

[QUOTE=http://ubuntuforums.org/showthread.php?t=1195275]
linux (hdX,Y)/vmlinuz root=/dev/sdXY ro
...
Drives start counting at 0 (sda=0, sdb=1, etc). Partitions start counting at 1 (1=1, etc). Substitute the correct drive letter for X, correct number for Y, and substitute the correct numbers for (hd0,1).[/QUOTE]

According to the guide from the first link, it is possible to simply translate one form to the other with the hope that it works. I realized this, but my concern with doing it this way is this: once in a while, device names change after a reboot (which is the reason a lot of people and files now use UUIDs instead). If a device name changes after a reboot, would grub's (hd0,0) form change along with it? Does anyone know?

Either way, thanks for the links Bashing-om.

---

