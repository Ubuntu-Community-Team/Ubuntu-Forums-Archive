---
title: "USB stick not detected by 16.04 Ubuntu"
date: 2016-10-04
forum: General Help
---

### Post by raul-putnin on 2016-10-04
Hello everyone!

I have a 4GB USB flash drive, which is not being detected by my 16.04 Ubuntu. 

I am quite new with Ubuntu, so please give me step-by-step recommendations :D

Before I had Windows 8.1 and it was working fine.

I have thought that the problem might be that I am used to remove flash drives from USB ports without unmounting them, so I thought maybe it is possible to somehow reformat the stick, as it is done on Windows, but I don't know how.

Also if any more information is needed please let me know.

Am waiting for your feedback guys.

Best regards

---

### Post by sudodus on 2016-10-04
You can restore a USB drive (actually any drive) with the tool ***gparted***. You install it with the following command line (in a terminal window)

```
sudo apt-get install gparted
```

or via some graphical software installer (can be different depending on the flavour and version of Ubuntu).

An alternative is ***mkusb***. You install it with the following command lines. If you run standard Ubuntu, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb mkusb-nox usb-pack-efi
```

See also [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by raul-putnin on 2016-10-04
Thank you so much! It worked :D

---

### Post by raul-putnin on 2016-10-04
Ok, after all it didn't work as well as I thought it would xD

I got an error whilst reformatting it into FAT32. 

Here are the error details:

```
[COLOR=#000000][FONT=&amp]GParted 0.25.0 --enable-libparted-dmraid --enable-online-resize[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Libparted 3.2[/FONT][/COLOR]
[TABLE]
[TR]
[TD="colspan: 2"]**Format /dev/sdg1 as fat32**  00:00:13    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"]calibrate /dev/sdg1  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"][I]path: /dev/sdg1 (partition)
start: 32
end: 7886847
size: 7886816 (3.76 GiB)[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]clear old file system signatures in /dev/sdg1  00:00:01    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"]write 512.00 KiB of zeros at byte offset 0  00:00:00    ( SUCCESS )[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]write 4.00 KiB of zeros at byte offset 67108864  00:00:00    ( SUCCESS )[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]write 512.00 KiB of zeros at byte offset 4037279744  00:00:00    ( SUCCESS )[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]write 4.00 KiB of zeros at byte offset 4037935104  00:00:00    ( SUCCESS )[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]write 8.00 KiB of zeros at byte offset 4038041600  00:00:00    ( SUCCESS )[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]flush operating system cache of /dev/sdg  00:00:01    ( SUCCESS )[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]set partition type on /dev/sdg1  00:00:03    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"]*new partition type: fat32*[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]create new fat32 file system  00:00:09    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"]***mkfs.fat -F32 -v -I -n " " /dev/sdg1***  00:00:09    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"][I]mkfs.fat 3.0.28 (2015-05-16)
/dev/sdg1 has 125 heads and 62 sectors per track,
hidden sectors 0x0020;
logical sector size is 512,
using 0xf8 media descriptor, with 7886816 sectors;
drive number 0x80;
filesystem has 2 32-bit FATs and 8 sectors per cluster.
FAT size is 7687 sectors, and provides 983926 clusters.
There are 32 reserved sectors.
Volume ID is 3b80503c, volume label .
[/I][/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"][I]mkfs.fat: failed whilst writing FAT
[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[COLOR=#000000][FONT=&amp]========================================[/FONT][/COLOR]
```

---

### Post by sudodus on 2016-10-05
Try mkusb, the first option in the wipe menu,

**"Standard: create MSDOS partition table with FAT32 partition"**

[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

mkusb wipes things a bit differently, which might help. It is also worthwhile to unplug the USB flash drive and plug it back again, and try again. It might even help to reboot the computer and try again.

If none of these methods helps, I think something is wrong with the USB flash drive, for example that it 'pretends' that you can write to it, but maybe you can only write zeros, or maybe some memory cells are bad.

See also this link,

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

### Post by coffeecat on 2016-10-05
Not a Multimedia Software question.

*Thread moved to **General Help**.*

---

