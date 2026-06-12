---
title: "How to mount file recovered from ddrescue"
date: 2017-12-19
forum: General Help
---

### Post by AwaitingUserInput on 2017-12-19
I have a USB drive and I think the partition table got corrupted. The partition editior that came with Kubuntu saw the USB drive, but told me there was not a partition table. Also, if I inserted it, fdisk -l would acknowledge /dev/sdc, but not /dev/sdc1. My windows computer does not recognize it, either, and it was formatted as FAT32.

After some googling, and trial and error, I installed package [gddrescue]("http://www.forensicswiki.org/wiki/Ddrescue#Debian_and_Ubuntu")

Then I did dd if=/dev/sdc of=/path/to/file.img

Then I ran ddrescue on the file.img. I don't remember the output, which scrolled by as it was working but disappeared when it finished, but it did look like it was working and finding the files, then writing them to another image.

My problem now is that I cannot figure out how to mount the "recovered" files. I would like to get them mounted, then copy them to a hard drive, repartition the USB drive and put them back. Any ideas on what to try?

```
[FONT=monospace][COLOR=#000000]$ fdisk -l rescued_file.img  [/COLOR]
[COLOR=#000000]**Disk reskewed.file: 58.4 GiB, 62742787072 bytes, 122544506 sectors**[/COLOR]
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

[/FONT]
```


Also....

```
[FONT=monospace][COLOR=#000000]$ sudo mount -t auto -o ro,loop [/COLOR][/FONT][COLOR=#000000][FONT=monospace]rescued_file.img[/FONT][/COLOR][FONT=monospace][COLOR=#000000] /media/user/usb-file/[/COLOR]

mount: /media/user/usb-file: wrong fs type, bad option, bad superblock on /dev/loop0, missing codepage or helper program, or other e
rror.

[/FONT]
```

---

### Post by AwaitingUserInput on 2017-12-20
I compared md5 hashes of the image I got from the dd command, and the one file that ddrescue produced. The MD5 hashes were the same. Apparently, I misunderstood the point of ddrescue. I'm trying testdisk now to see if it will bring back my partition table.

---

