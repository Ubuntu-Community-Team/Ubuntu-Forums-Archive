---
title: "2nd hard disk format/mount problems - please help"
date: 2007-01-18
forum: General Help
---

### Post by faradesla on 2007-01-18
Hi, I'm yet another recent linux convert.

I'm using Kubuntu 6.10, and it works great except for this new problem. When I initially installed, I only converted my primary disk to linux partitions, leaving my second drive as NTFS. I now wish to convert that drive over as well, but it's giving me all kinds of headaches.

The NTFS drive originally didn't work in Kubuntu, of course, so I found a little script on here I used to mount the NTFS drive. I'm afraid I can't remember that script now. Here's what the fstab file looks like today:

[FONT="Courier New"][B]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=49b10bf3-c08d-46c9-a976-cd7f6985dc80 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=28fa6f33-5805-4c48-a029-3ad595f23df1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
#Added by diskmounter utility
/dev/hdb1 /media/hdb1 ntfs ro,user,fmask=0111,dmask=0000 0 0[/B][/FONT]

I used **gparted** (regular, not live) to erase the NTFS partition, then create an ext3 partition in its place (if reiserfs is better for this, let me know). I made the partition successfully, then mounted the new partition with gparted.

Well, it mounted, but incorrectly. I couldn't do a thing with it - no read/write access. Also, it put a folder in there labeled "Lost+Found."

Now, I did see a thread in the archives already concerning this problem, and I went through all the same things that were suggested to the other guy. Nothing has worked for me, so far. To make matters worse - feel free to heap scorn upon me for this; but know I was very tired at the time - I typed the following line in, while root:

[FONT="Courier New"]**rm /dev/hdb1**[/FONT]

So that was stupid, and I don't know enough about linux to figure out how to restore that. Even if I did, I still have that blasted drive locked-down and with that lost & found folder.

So... can you  help me, please? I'd really appreciate it. Thanks in advance. ](*,) 
Let me know if you need more info. I'm logging off for tonight, but I'll be back tomorrow as soon as I get up. I've got Friday off.

---

### Post by taurus on 2007-01-18
Edit /etc/fstab with

```
kdesu kate /etc/fstab
```
and replace this line

```
/dev/hdb1 /media/hdb1 ntfs ro,user,fmask=0111,dmask=0000 0 0
```
with this line.

```
/dev/hdb1   /media/hdb1   ext3   defaults   0   1
```
Save it.  Then reboot.

---

### Post by faradesla on 2007-01-19
Thanks! Your solution was, in fact, all that was needed. I have since moved all my filed onto the now-useful partition. Balance is restored to the universe.

I really appreciate the assist. :D

---

