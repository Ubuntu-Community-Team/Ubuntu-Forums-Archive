---
title: "Norton GHOST"
date: 2007-02-03
forum: General Help
---

### Post by Angelaki on 2007-02-03
I have two HDD in my pc. HD=40GB and HDB=10GB. I have install Kubuntu 6.10 in HDB and work fine. Then i clone the HDB in HDA. Now i cant boot in HDA. I take an error 15. In HDB i can boot without prob. I need your help.
[COLOR="Red"]
My menu.lst[/COLOR]


default 0
timeout 10

title Kubuntu (hda), kernel 2.6.15-26-386 (on /dev/hda1)
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-386
savedefault
boot


## ## End Default Options ##

title Ubuntu, kernel 2.6.17-10-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd1,0)
kernel /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

[COLOR="Red"]
sudo fdisk -l[/COLOR]

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 4801 38564001 83 Linux
/dev/hda2 4802 4865 514080 82 Linux swap / Solaris

Disk /dev/hdb: 10.2 GB, 10248118272 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 * 1 1190 9558643+ 83 Linux
/dev/hdb2 1191 1245 441787+ 82 Linux swap / Solaris



[COLOR="Blue"]I have following th follow instruction to reinstall Grub[/COLOR]

[COLOR="Red"]
root (hd0,0) 
setup (hd0) 
quit[/COLOR]


[COLOR="Blue"]but still i cant boot from hda. Still i take the error 15.[/COLOR]

Except this i have and a new problem. If i want to restart my pc and boot again in Kubuntu in HDB i must pull over the power cable for 5 sec and then to power on the PC. If i dont do it the PC halt in the first line in Kubuntu.

Maybe my pc has GHOST!!!!:) :) :) 


P.S. Please HELP ME!!:( :( :( :(

---

### Post by HereInOz on 2007-02-03
I take it you have used Norton Ghost.  This doesn't always work.  There is an excellent utility, on sourceforge I think, called Ghost4Linux.

I have used it on a number of occasions and it worked fine.  The only thing that you will find is that if you ghost a 10GB HDD to a 40GB HDD, you will have a 10GB partition with 30 GB free space.  You will then need to use GParted, again on sourceforge, from memory, to resize the partition.

Hope this helps.

---

### Post by jeremy on 2007-02-03
I always use partimage, it is very good indeed.

---

### Post by rvjcallanan on 2007-02-06
Norton Ghost actually works well with Ubuntu and other Linux distros, but you must avoid the latest versions of Ghost. Apparently Symantec merged their Ghost codebase with DriveImage (having taken over PowerQuest) and this has caused many problems, not least re: Linux compatibility.

I know Norton Ghost 2003 (and probably other versions of similar vintage) works well, but only for EXT2/3 partitions and then only when you image and restore Linux partitions in sector-by-sector mode (-ial) including the complete MBR (-ib) and disabling LILO patch (-nolilo). You should also prevent partition resizing on restore using szeE option. This works regardless of whether you're using LILO or GRUB or any other boot manager for that matter. Make sure to use compression when imaging (-z option) as this will take some of the pain out of using sector-by-sector mode. Just before creating an image, make sure there is no spurious data in unused sectors by issuing the following commands:

# dd if=/dev/zero of=0bits bs=10M
# rm 0bits
# touch /forcefsck
#reboot

The last step will ensure file system is clean before imaging (make sure any file system errors are fixed before imaging)

It is also a good idea to keep your root partition to a reasonable size e.g. 5GB might be a good choice for a server if OS and apps take up less than 2GB and main data is stored on a second drive. This lean approach also makes it possible to clone to a different hard drive model (including a smaller one), overcoming one of the biggest disadvantages of sector-by-sector images. This works 99% of the time because most hard drives nowadays have identical sector sizes nowadays.

Imaging is a clean, reliable and sensible solution for admin backups, rollouts and updates, particularly when you have a ready-made boot disk for the job. You can take a snapshot and restore a previous snapshot in a matter of minutes. Ghost is generally a more rugged choice and is a more mature product, with a number of useful features not found elsewhere but, as I say, avoid recent versions which have lost their way competely, particularly with Linux.

In multi-boot sceanarios, the -ial option above ensures that non-linux partitions (i.e. Windows) are imaged in normal file-based mode which Ghost is good at.

---

### Post by rvjcallanan on 2007-02-06
Oops!

---

