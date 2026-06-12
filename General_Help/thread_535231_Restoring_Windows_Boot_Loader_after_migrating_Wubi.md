---
title: "Restoring Windows Boot Loader after migrating Wubi Ubuntu to a real partition w LVPM"
date: 2007-08-26
forum: General Help
---

### Post by hh93 on 2007-08-26
Hi All,

Just wanted to list here the steps i took to  replace Grub boot loader with Windows Boot loader after migrating Wubi Ubuntu to a real partition ([http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)). I guess these steps are also applicable to direct Ubuntu installation.

Once rebooted after LVPM (migration to real partition that is), i noticed that Grub took over as bootloader. I did the following the restore windows boot loader :

1. Restoring MBR-backup, while preserving partition table (i.e. to allow booting into Ubuntu partion)
- copy MBR-backup to root : sudo dd if=media/host/MBR-backup of=dev/sda bs=446 count=1
----- This command simply means "raw copy input file MBR-backup only to the first 446 places of the MBR as 1 block. 
- Rebooted and verified that Windows boot loader showed up instead of Grub's, booted into windows, and looked for for the presence of 2 files: Wubildr.mbr and Wubildr in c:\. Both of these file are installed by wubi installation and based on Grub4dos. Wubildr.mbr installed into master boot record and from there will look for wubildr and launch it. Wubildr look for and execute menu.lst. My understanding was that It will look first at root level, the whole partition and then the whole disk. Since the closest menu.lst will be the one inside wubi directory (c:\wubi/boot\grub\menu.lst), Wubildr will execute that and display Wubi menu instead of 'real' ubuntu menu. I had 2 options here, either to include 'real' Ubuntu within wubi menu, like tuxcantly suggested ([http://ubuntuforums.org/showthread.php?t=438591&page=6](http://ubuntuforums.org/showthread.php?t=438591&page=6)) or to somehow make wubildr directly executes the 'real' ubuntu menu.lst. Opted for the latter; had wanted to uninstal wubi to recover some drive space that means  no-more wubi menu.lst will be available, as wubi's grub directory will be deleted. 

2. Copying menu.lst from the 'real' Ubuntu partition into the root directory
Within Wubi Ubuntu, I ran nautilus with root priviledge (sudo nautilus). i Browsed the real partition of Ubuntu and went into /boot/grub. Checked out menu.lst (Grub boot menu), by double clicking it (this launched a pop up asking for action, chose display, the file opened with gedit), made sure it listed reference to the 'real' ubuntu rather than to wubi ubuntu (look to text next to kernel should be /boot'... rather than /wubi/boot/...), made a backup copy of it (in gedit chose save as menu.lst.backup) and dropped a copy onto root (in gedit chose saved as menu.lst in filesystem/media/host). 

Voila, upon reboot, i chose Ubuntu and it went straigth into 'real' ubuntu ( i left the time out option at 3 seconds and keep ubuntu menu hidden)

Now i am free to uninstall wubi ubuntu.

Hope this helps.... do leave feedback in any case.

hh93

---

### Post by tuxcantfly on 2007-08-26
Very interesting, I'll try adding it to LVPM as an option as soon as I see if it works properly (going off to test).

Only question is, exactly where did you get the "bs=446" option from? I thought it's supposed to be 512 for an MBR, though I may be wrong...

---

### Post by hh93 on 2007-08-26
> **tuxcantfly said:**
> Very interesting, I'll try adding it to LVPM as an option as soon as I see if it works properly (going off to test).

Only question is, exactly where did you get the "bs=446" option from? I thought it's supposed to be 512 for an MBR, though I may be wrong...

I was just following the guides from several  sites, most notable ones are below: 
[http://www.sysdesign.ca/guides/partitions.html](http://www.sysdesign.ca/guides/partitions.html)
[http://www.win.tue.nl/~aeb/partitions/partition_types-2.html](http://www.win.tue.nl/~aeb/partitions/partition_types-2.html)
[http://josephhall.org/grub_install_hda1.html](http://josephhall.org/grub_install_hda1.html)
[http://www.cpqlinux.com/mbr.html](http://www.cpqlinux.com/mbr.html)
[http://onkarjoshi.wordpress.com/2007/04/03/partitioning-help-for-multi-booting-ubuntu-linux-and-windows-xp-safely/](http://onkarjoshi.wordpress.com/2007/04/03/partitioning-help-for-multi-booting-ubuntu-linux-and-windows-xp-safely/)

Cheers!

---

### Post by tuxcantfly on 2007-08-26
I found a slightly easier method, here's how I did it (essentially the standard, unmodified grldr automatically searches for /boot/grub/menu.lst in the first place, so by moving the wubi components from their original place, so that it can be deleted later on, and installing grldr, the /boot/grub/menu.lst of the new, dedicated-partition install will automatically be used):

Relevant code from LVPM:

```
if [ "$instgb" = "no" ]; then
dd if=/media/host/MBR-backup of=$partdp bs=446 count=1
mv /media/host/boot.ini.bak /media/host/boot.ini
mv /media/host/wubi /media/host/wubi-backup
mv /media/host/wubildr /media/host/wubildr-backup
mv /media/host/wubildr.mbr /media/host/wubildr-backup.mbr
mv /media/host/wubildr.exe /media/host/wubildr-backup.exe
rm /media/host/menu.lst
cp /usr/share/lvpm/grldr* /media/host/
echo \
"
C:\grldr="Ubuntu"
" >> /media/host/boot.ini
sed -e 's/$/\r/' /media/host/menu.lst > /media/host/menu.lst
fi
```

I'll be posting the new version with the change, as well as the fix to the /media/host to /media/host0 issue soon...

---

### Post by tuxcantfly on 2007-08-26
[http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

LVPM version 77 should have the changes incorporated

to use, with the changed described in the posts above (no GRUB installation, use Windows bootloader instead):

```
sudo lvpm-real /dev/sda1 -nogrub
```

(change /dev/sda1 to target partition)

I haven't added the option to the GUI though, since it could potentially be a problematic option (I haven't had too good experiences with grldr, nor have I tested this option too thoroughly), I might add to the GUI after a bit more testing.

If you also want to get rid of the original Wubi install afterwards, just boot up Windows and remove the folder wubi-backup

also, another fix introduced in lvpm version 77: the host partition will be mounted to /media/host0 not /media/host to avoid it being misdetected as a wubi install

---

### Post by tormod on 2008-05-02
> **tuxcantfly said:**
> Only question is, exactly where did you get the "bs=446" option from? I thought it's supposed to be 512 for an MBR, though I may be wrong...

The disk's first sector (512 bytes) includes the master boot record (code for booting) as well as the partition table. The partition table starts at 446, and you don't want to overwrite it, in case it has been modified since you made the backup.

---

