---
title: "mounting internal &amp; external hard drives"
date: 2013-06-18
forum: General Help
---

### Post by jodiver on 2013-06-18
History: New white box with AMD quad core, 8g of ram & 320g HD. It came with Win8. I used a disc with Ubuntu 12.04 on it to dual install. I have 124g partition (created by the disc) for Win8 & 187g for Ubuntu & 8g undefined (swap?). All went well as far as I could tell (newbee).  Problem: I plugged a 500g USB HD & ubuntu recognized it & opened the files. I could view word files, pictures but not video clips. I didn't know about mounting/unmounting so I simply closed the files & shut the machine down normally. When I started the machine back up & turned on the USB hard drive Neither Ubuntu nor win8 will recognize it. Ubuntu says it's in hibernation mode. I also installed an internal 500g HD (sata) that's only recognized when I'm using the Ubuntu start up  disc---file manager, I think. When using the disc (only) I can see the partitions (which I would like to make the Win partiton smaller but the choice it gives me is very cryptic so I didn't use it). When using Ubuntu without the disc I can't find "administer" or any of the suggestions I found in the forums. I tried command lines that I got from the forums & a book I have but most of them don't work. The few that do work print out information that's jiberish to me. I do get an "error 14". The USB HD does work in my other machine running xp & it's farmated NTFS. If you can help me I would be exstatic as I really want to go all Linux. The only reason I'm using the Win program is for my Phoenix flight sim    P.S. Please let me know how to follow this thread as the instruction section leaves me gasping for air!! It took me almost two weeks to figure out how to get hear!

---

### Post by oldfred on 2013-06-18
Post this from command line.

       sudo blkid -c /dev/null -o list

 cat /etc/fstab

Then we can give more specific directions.

Lots of detail or background.

 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by jodiver on 2013-06-19
oldfred: I tried the terminal string (?) you gave me & in different ways but no go. I took a shot of the terminal out put. I have no idea what I'm doing wrong. I'm hoping "insert image" is the way to get the pic on here. Nope. They just want me to do gobs more reading. Here's the way I put it in; sudo blkid-c/dev/null-o list cat/etc/fstab  It asked for & I entered password then got this; sudo blkid-c/dev/null-o: command not found. I did it different ways,non worked & one said "no such file or directory. I'll stay connected (dial up) for the next four hours,just in case. I can't work both systems at one time so I keep going back & forth between the two machines. That's why I'm so slow.

---

### Post by Alex Carroll on 2013-06-19
```
sudo blkid -c /dev/null -o list
```

and then

```
cat /etc/fstab
```

copy and paste the first line, execute it, then copy-paste the second line and execute it. ensure all spaces are kept in the right places.

---

### Post by oldfred on 2013-06-19
And then copy & paste back. Better than a screenshot. Also if longer or formatted better to use Advanced reply highlight like copy and click on # which adds code tags around the text.

You can use screenshots for gui output like a gparted screen, but have to use Advanced reply to attach them with the paper clip icon.

---

### Post by jodiver on 2013-06-20
I'll work on it tonight. Can't copy/paste as the new machine isn't set up to go online yet. I'm bouncing back & forth between the two machines & one set of peripherals. Sorry about that. I take a digital camera pic on the new machine then reconnect everything to the old machine then go online to send the shot. I can't think of another way to do it right now. I'm going to try alex's comands then try to figure out what oldfred's orders mean(not quite clear to me)-----I know, dumb newbee!

---

### Post by oldfred on 2013-06-20
Does live installer not connect to Internet with wired Ethernet connection? 
It almost always does, but wifi often has issues and has to use wired connection to download extra drivers for wireless.

If you have a flash drive you can copy terminal text to file and copy file to flash drive. Then upload from flash drive.

---

### Post by jodiver on 2013-06-21
[ATTACH=CONFIG]244016[/ATTACH]The explanation on the commands worked. If you can't enlarge this to read it I'll just go ahead & type the whole thing out. I would use the suggestion about a flash drive (need to get one) but without the ability to mount it I don't see it as working, also would it be readable on my xp machine? I am absolutely delighted that I got this readout---thanks people!

---

### Post by oldfred on 2013-06-21
No other drives are shown in blkid command, so cannot help.
Is new internal drive shown in BIOS? If not in BIOS no system will mount it.
External drives are normally mounted just by clicking with Nautilus. Often best not to add to fstab as it may not be connected when rebooting. You can manually mount if specific ownership or permissions are required.

I prefer to label partitions so those not mounted with fstab, will be default mounted by label. I try to remember to label when creating partitions with gparted. If I forget I use Disks or Disk Utility to add labels.

Part of my partitions with labels.

```
fred@fred-Precise:~$ sudo blkid -c /dev/null -o list
[sudo] password for fred: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    WinXP    (not mounted)  04B05B70B05B6768
/dev/sda2  ext3    backup   (not mounted)  13a684e4-2849-4566-9528-21cd07028a9a
/dev/sda4  vfat    SHARE    (not mounted)  46CD-C9B2
/dev/sdb1  vfat    EFI32    (not mounted)  2404-8A43
/dev/sdb3  ext4    sys32    /media/sys32   e2156d09-329e-4262-9549-f72a05d97f93
/dev/sdb4  ext4    data32   /media/data32  b1b11cef-6fc6-4cd8-8343-e7c1852de805
/dev/sdc2  ext4    Maverick (not mounted)  0eea4e95-ea0a-4745-80d4-57bf2bbc9d69

```

---

### Post by moujlo22 on 2013-06-22
Thanks to share this great information

[TABLE="width: 242"]
[TR]
   [TD="width: 242"]http://www.mouzlo.com/pre-workout.html
[/TD]
 [/TR]
[/TABLE]

---

### Post by jodiver on 2013-06-22
Thanks for trying people. I'll plod along as long as I can & try to get it done.

---

### Post by jodiver on 2013-11-15
just a follow up to let everyone know what I did. Couldn't get anything to work so installed easus partitioning tool (free) & was able to separate all three drives, recognize them & recognize externals when hooked up. Right now I'm running win8 alone on drive one. I feel (can't prove it) that the problem was caused by not letting win8 create the partition. Still want to run Ubuntu (learn it) & will do so in virtual box, as I feel that will be safer. Hope I was able to benefit someone.

---

