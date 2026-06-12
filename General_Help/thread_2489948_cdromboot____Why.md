---
title: "/cdrom/boot    Why?"
date: 2023-08-15
forum: General Help
---

### Post by hei17 on 2023-08-15
I have just installed Ubuntu 22.04 and have noticed that the boot folder is in the cdrom folder. When I updated the kernel the grub.cfg file was corrupted. Needed to reinstall grub. Still having problems. Is it possible to move the boot folder out of the cdrom folder? So, it would be like other distributions.  " /boot/grub/grub.cfg" Will be grateful for any help. :(

---

### Post by TheFu on 2023-08-15
I think there is some confusion.  Anything under /cdrom would be ON the cdrom storage.  Did you eject the optical disk after install finished, but before booting?

You can check this by running 
**df -Th** in a terminal.  Post the line with the /cdrom in it so we can see the file system and device involved.

BTW, please don't do anything fancy with the fonts or colors here. Many of us have custom handling to make it readable for our needs.

Of course, I could be completely misunderstanding the /cdrom issue.  Facts are better than attempted explanations.  Facts mean, running commands, posting the command, all options and the output.  When doing that, please wrap it all in forum code-tags.  The advanced editor has a button (#) for that.

---

### Post by hei17 on 2023-08-15
[SIZE=4][FONT=tahoma]When I use the ls command this is the result. ```
ls -R  /cdrom 
```[/FONT][/SIZE]```
boot

/cdrom/boot:
config-5.19.0-50-generic      memtest86+.elf
config-6.2.0-26-generic       memtest86+_multiboot.bin
grub                          System.map-5.19.0-50-generic
initrd.img                    System.map-6.2.0-26-generic
initrd.img-5.19.0-50-generic  vmlinuz
initrd.img-6.2.0-26-generic   vmlinuz-5.19.0-50-generic
initrd.img.old                vmlinuz-6.2.0-26-generic
memtest86+.bin                vmlinuz.old


/cdrom/boot/grub:
DejaVuSerif-Italic.pf2  gfxblacklist.txt  grubenv  linux_PNG27.png  unicode.pf2
fonts                   grub.cfg          i386-pc  locale


/cdrom/boot/grub/fonts:
unicode.pf2



```[SIZE=4][FONT=tahoma] The /cdrom folder holds the boot folder that holds the kernel to boot the system. [/FONT][/SIZE]

---

### Post by MAFoElffen on 2023-08-16
I would answer this, but the fonts used in this thread by the OP screw with my browser settings. He was asked to leave them as default. Can you please not do that?

Let's see output of these two commands
```

mount | grep 'boot'
ls /boot
grep 'boot' /etc/fstab

```
If you set the fonts again like this, I can not answer you, so i will leave instructions for others to lead you though correcting this.

- Check if he has a /boot folder and if it is populated or not. For it to be there, and be used...
- Check to see if it has any "referred mounts" to /boot, to other than /boot, which would be to /cdrom/boot if the OP is correct. Because the system still looks for /boot and uses that for both booting and for grub.
- Have him run the 'boot-info' script. From what he has said, it looks like Grub was installed as Legacy BIOS, not UEFI, and to cdrom instead of classic /boot. I don't know how someone does that on a default canned install. This is the first time I have seen this in over 18 years of using Grub (Grub Legacy and Grub2).
- rsync the contents to /boot. After a diff, remove the old from /cdrom
- Reinstall grub2, using /boot on that drive and /boot folder as the referred targets.
```

grub-install --boot-directory=/boot --force --bootloader-id=ubuntu --no-floppy --recheck /dev/sdX

```
- Update the intramfs images...

---

### Post by TheFu on 2023-08-16
> **hei17 said:**
> [SIZE=4][FONT=tahoma]When I use the ls command this is the result. ```
ls -R  /cdrom 
```[/FONT][/SIZE]


That wasn't the command requested. Any storage can be mounted to almost anywhere in the file system.  We need to see the mounts.  A plain, **ls** isn't really useful without showing the owner, group, permissions too.

Good luck.

---

### Post by hei17 on 2023-08-16
This is the results from the commands you posted.   ```
ls /boot
config-5.15.0-76-generic      System.map-5.15.0-76-generic
config-5.15.0-78-generic      System.map-5.15.0-78-generic
config-5.15.0-79-generic      System.map-5.15.0-79-generic
grub                          vmlinuz
initrd.img                    vmlinuz-5.15.0-76-generic
initrd.img-5.15.0-76-generic  vmlinuz-5.15.0-78-generic
initrd.img-5.15.0-78-generic  vmlinuz-5.15.0-79-generic
initrd.img-5.15.0-79-generic  vmlinuz.old
initrd.img

```  I am using Legacy BIOS. I also booted the .iso and installed to another logical partition. Can I just copy the boot directory to /?

---

### Post by hei17 on 2023-08-16
Sorry for last post it is the /boot of my mint distribution. The question still is can just mv /boot to /?

---

### Post by The Cog on 2023-08-16
> **hei17 said:**
> Sorry for last post it is the /boot of my mint distribution. The question still is can just mv /boot to /?
Huh? the boot directory is already in /. That's why there's a slash in front of it.

And you only answered one of MAFoElffen's questions - posting the output of these 3 commands:
```
mount | grep 'boot'
ls /boot
grep 'boot' /etc/fstab
```

What do you actually want to do? 
If you want to move the *contents* of /boot up to /, then without seeing the missing output I can't be sure, but I suspect it would never boot again if you did.

---

### Post by hei17 on 2023-08-16
Thank all that posted for their help.  The question is solved. Thank you!

---

### Post by TheFu on 2023-08-17
> **hei17 said:**
> Thank all that posted for their help.  The question is solved. Thank you!

And what was the answer?!!!!!

---

