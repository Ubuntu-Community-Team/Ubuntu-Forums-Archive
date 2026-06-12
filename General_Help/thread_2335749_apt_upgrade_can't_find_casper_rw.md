---
title: "apt upgrade can't find casper rw"
date: 2016-08-31
forum: General Help
---

### Post by msalko on 2016-08-31
Hi. I have a ubuntu live cd (16.04 LTE) and I'm using it as persistent image.

When running apt upgrade I found out that packages that rely on casper folder don't work.

i.e. casper is not in ```
/cdrom/casper
``` but in ```
/cdrom/multiboot/ubuntu-16.04.1-desktop-i386/casper
```

the issue might be that cp doesn't know the correct path, witch gives an error:
```
update-initramfs: deferring update (trigger activated)
**cp: cannot create regular file '/cdrom/casper/initrd.gz.new': No such file or directory**
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on initramfs-tools | linux-initramfs-tool; however:
  Package initramfs-tools is not configured yet.
  Package linux-initramfs-tool is not installed.
  Package initramfs-tools which provides linux-initramfs-tool is not configured yet.

```
doesn't know where the casper is

I've tryed to remount cdrom, and to softlink the folder but evrything faield.

---

### Post by reese1379 on 2016-09-01
You cannot u[COLOR=#000000]*pdate initramfs on a live system. I doubt it's even possible to do a full *[/COLOR][COLOR=#000000]upgrade either, as new files are stored in casper-rw and overlaid over the live cd image as a [/COLOR][FONT=&quot]loop device.[/FONT]

---

### Post by sudodus on 2016-09-01
Please have a look at the following link:

[Ask Ubuntu: Unattended-upgrades broke persistent live media](https://askubuntu.com/questions/817750/unattended-upgrades-broke-persistent-live-media/817820#)

---

### Post by msalko on 2016-09-01
no i have full access to that to the whole file system, even the stuff that's on the usb drive.
I can manually delete the whole kernel with ease.

---

### Post by sudodus on 2016-09-01
I'm sorry, but I don't understand. Please tell us if there is a problem now, and in that case, describe it. Is it the same problem as in the first post, or something else.

(As described in the link in my previous post, updating and upgrading works works for me in a persistent live system. But the new kernel version cannot be used, and some other things associated to the boot process fail too.)

---

