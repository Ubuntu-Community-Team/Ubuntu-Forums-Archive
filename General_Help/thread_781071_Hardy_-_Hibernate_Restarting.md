---
title: "Hardy - Hibernate Restarting?"
date: 2008-05-04
forum: General Help
---

### Post by pmaconi on 2008-05-04
Whenever I attempt to hibernate, my computer reboots instead. Has anyone else had this problem/found a solution?

---

### Post by pmaconi on 2008-05-05
Does anyone else have this problem?

---

### Post by Mattmate on 2008-05-08
I too have this problem. :(

---

### Post by cespinal on 2008-05-09
bump

---

### Post by pmaconi on 2008-05-16
I know that this isn't a problem with my Hardy install - I've done three separate installs and they all have this problem (Wubi, alternate, and normal).

---

### Post by pmaconi on 2008-05-28
Bump.

---

### Post by pmaconi on 2008-06-20
Bump.

---

### Post by nogasbiker on 2008-09-01
I also have this problem.  Hardy on Dell Latitude D610 laptop.

When hibernating, all looks fine.  I see disk activity, followed by a power down.  When trying to resume from the hibernate, it does a fresh reboot???

---

### Post by nogasbiker on 2008-09-01
> **nogasbiker said:**
> I also have this problem.  Hardy on Dell Latitude D610 laptop.

When hibernating, all looks fine.  I see disk activity, followed by a power down.  When trying to resume from the hibernate, it does a fresh reboot???

I should add that the following works fine on my laptop

- Hardy Suspend/Resume
- Gutsy Suspend/Resume
- Gutsy Hibernate/Resume

---

### Post by dhoulder on 2008-10-05
Check your /boot/grub/menu.lst - do you have kernel lines like this?

```
kernel          /boot/vmlinuz-2.6.24-19-386 root=UUID=d5e0406e-f8c8-4a5a-aa0b-dcaa24495422 ro quiet nosplash resume=UUID=971efceb-6ef7-46c3-8b17-6aedffd70a25
```It seems that you need resume= to make resume from hibernate work in Hardy. This tells the kernel where the saved image is, and the UUID=whatever tells it to look in your swap partition. The UUID of your swap partition should be listed in your /etc/fstab. If not, I think you can use resume=/dev/$your_swap_partition

The resume= was missing after my upgrade from Dapper. To fix...

[LIST]
[*]Become root with ```
 sudo -s
```
[/LIST]
 
[LIST]
[*]Backup your /boot/grub/menu.lst in case you screw it up
[/LIST]

[LIST]
[*]Get the UUID of your swap partition from /etc/fstab or by looking at the target of the symlinks in /dev/disk/by-uuid/
[*]Open /boot/grub/menu.lst in your favourite editor
[*]Find the line ```
## ## Start Default Options ##
``` then look for a following
```
# defoptions= .....
``` line.
[*]Edit that to look like ```
# defoptions=quiet nosplash resume=UUID=the-hex-uuid-of-your-swap

``` Note the leading hash - see the explanation and warnings in menu.lst.
[*]Save the file and quit the editor
[*]Run ```
update-grub 
``` If you get any complaints from it, check that you've changed only the # defoptions line.
[*]Check that update-grub has added resume=... options to all "kernel" lines in menu.lst
[*]Exit your root shell with ```
exit
```
[*]Hibernate your computer
[*]Wait 10 seconds (or a day, or a week, or ...) and restart your computer
[*]Hopefully you will see a boot message like 
"kinit: trying to resume from...", and after the disk stops spinning (and maybe some strange colours and patterns on your screen) you should have a resumed session (in my case, KDE locks the screen and I type my password to unlock).
[/LIST]
**Caveats**: I've only just put this in place, and tested it once (Dell Inspiron 9400 + nvidia graphics + proprietary nvidia driver with twinview enabled and external vga display). Seems OK - just needed to reconnect to my wireless network by choosing it from the network manager right-click menu. I might try taking out the nosplash to make it boot with the pretty ubuntu usplash.

**Background**: Grub loads the kernel and an initial RAM-disk /boot/initrd.img-$kernel_version into memory. Once the kernel is loaded, it runs the "init" shell script in the RAM disk with all those options from the "kernel" line. The initrd is just a gzipped cpio archive, so if you gunzip it and extract it with cpio you can follow the code paths fairly easily - if there's no resume= it doesn't attempt resume.

---

