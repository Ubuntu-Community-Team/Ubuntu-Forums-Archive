---
title: "new fstab mount option guide for fixed drives - suggestions/mistakes?"
date: 2007-04-18
forum: General Help
---

### Post by gregconquest on 2007-04-18
--------------------------------------
I'm trying to make a fairly simple guide to fstab. Other guides tend to explain options, but have very few examples, or they tend to have example fstabs written out, but there is little analysis. I'm trying to both here. Please help if you can. This is also at [http://www.linuxquestions.org/questions/showthread.php?p=2717224]("http://www.linuxquestions.org/questions/showthread.php?p=2717224")
[http://www.suseforums.net/index.php?showtopic=34332]("http://www.suseforums.net/index.php?showtopic=34332") is also a related post in the SUSE forums.
--------------------------------------
_**Example partition uses and typical fstab entries **_

Situation 1: **Windows partitions** (NT, 2000, XP, 2003, Vista)
1A ```
/dev/xxxx   /media/mountpoint   ntfs   user,ro,auto   0   0
```
(*user* allows anyone to mount, *ro* makes it read-only since ntfs is a MS-protected format, *auto* mounts it at boot automatically)
or
1B```
/dev/xxxx   /media/mountpoint   ntfs   nls=utf8,umask=0222   0   0
```
(*nls=utf8* includes unicode for non-English users, [COLOR="Red"]*umask=0222*[/COLOR] (-r-xr-xr-x) does what?)
or
1C```
/dev/xxxx   /media/mountpoint   ntfs   defaults,nls=utf8,umask=007,gid=46   0   1
```
(*nls=utf8* includes unicode for non-English users, [COLOR="Red"]*umask=007*[/COLOR] ??? Makes for 659 permissions?, [COLOR="Red"]*gid=46*[/COLOR] ??? )

Situation 2: **ntfs data partitions** (generally from Windows):
```
[COLOR="Red"](same as above???)[/COLOR]
```

Situation 3: **fat-32 data partitions** (ideal shared partition between linux, windows, and apple's mac os):
```
/dev/xxxx   /media/mountpoint   vfat   iocharset=utf8,umask=000   0   0
```
(*iocharset=utf8*  includes unicode for non-English users, *umask=000* allows most liberal file permissions)

Situation 4: **ext3 data partitions** (partitions shared between different linuxes, mac osx, and even Windows (using ["Ext2 Installable File System for Windows"]("http://www.fs-driver.org/"), for example)):
```
[COLOR="Red"]I don't know[/COLOR]. I can find no examples of this on the fstab tutorials.
Maybe
/dev/xxxx   /media/mountpoint   ext3   defaults   0   2
```

Situation 5: **other linuxes themselves**, their root partition:
```
[COLOR="Red"]???[/COLOR]
again, maybe
/dev/xxxx   /media/mountpoint   ext3   defaults   0   2
```

The **format of fstab** is also changing, from something like this:
```
/dev/sda2   /media/sda2   ntfs   defaults,nls=utf8,umask=007,gid=46   0   1
```
to something like this:
```
# /dev/sda2
UUID=9068AF8E68AF7220   /media/sda2   ntfs   defaults,nls=utf8,umask=007,gid=46   0   1
```
However, I cannot find any authoritative links on this:
[http://ubuntuforums.org/showthread.php?t=405630]("http://ubuntuforums.org/showthread.php?t=405630") (My device are now "sda" than "hda")
[http://www.linuxquestions.org/questions/showthread.php?t=544734]("http://www.linuxquestions.org/questions/showthread.php?t=544734") (ide drives show up as special device)
[COLOR="Red"]Can anyone point out where this transition is explained[/COLOR], please? An announcement somewhere?

Thank you,
Greg Conquest

key phrases: typical mount options, example fstab's, example fstab, 

references:
   *umask*
      [ http://www.zzee.com/solutions/linux-permissions.shtml]("http://www.zzee.com/solutions/linux-permissions.shtml") (linux permissions)
      [http://www.tech-faq.com/umask.shtml]("http://www.tech-faq.com/umask.shtml")
   *gid*
      [http://linux.about.com/cs/linux101/g/gid.htm]("http://linux.about.com/cs/linux101/g/gid.htm") (About.com's short note on GID)
   *uuid*
      [http://www.die.net/doc/linux/man/man1/uuid.1.html]("http://www.die.net/doc/linux/man/man1/uuid.1.html")  (man page for *uuid*)
   mount
      [http://www.die.net/doc/linux/man/man8/mount.8.html]("http://www.die.net/doc/linux/man/man8/mount.8.html") (man page for *mount*)
      

more links:
[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html") (top guide according to google -- no fixed-drive examples are given, though)
[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows") has several example fstab entries, but it has little to no explanation of those mount options.
[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131") (bodhi.zazen's *Understanding fstab*)
[http://www.linuxquestions.org/linux/answers/Hardware/etc_fstab_broken_down_and_explained]("http://www.linuxquestions.org/linux/answers/Hardware/etc_fstab_broken_down_and_explained") (another fstab tutorial)
[http://wiki.linuxquestions.org/wiki/Fstab]("http://wiki.linuxquestions.org/wiki/Fstab") (good guide with few examples)
[http://wiki.archlinux.org/index.php/Fstab]("http://wiki.archlinux.org/index.php/Fstab")
[http://doc.gwos.org/index.php/Understanding_fstab]("http://doc.gwos.org/index.php/Understanding_fstab")

(this article also posted at [http://www.linuxquestions.org/questions/showthread.php?t=547302]("http://www.linuxquestions.org/questions/showthread.php?t=547302"))

---

### Post by gregconquest on 2007-04-18
Wow! The dynamics here are amazing.  In less than one hour, a post will scroll off the front page. If it doesn't get answered soon, it gets lost easily. I hope some of you feel this post is worthwhile.
Greg

---

### Post by darksong on 2007-04-19
Nice post =) it will come in handy when i am messing around with getting my partitions working nicely together,

---

### Post by autocrosser on 2007-04-19
Lots of bugs today with Feisty being released to the wider circle :guitar:

As for some answers:
Feisty "really" wants UUID instead of /dev/whatever. Some things just work better that way.....There was a fair amount of threads when the kernel changed from IDE/ATA reference (dev/hda) to SATA reference (dev/sda)...I'm sure that many will be caught with this one:) & with UUID, all this becomes moot.

I'm including my /etc/fstab for you to look at:

# /etc/fstab: static file system information.
#
# <file system>                    <mount point>         <type> <options>                       <dump>  <pass>
proc                                      /proc           proc  defaults                           0       0
# /dev/hdb1
UUID=d4c465e8-62a9-47cd-89fc-11035d656290 /               ext3  defaults,errors=remount-ro,noatime 0       1
# /dev/hdb2
UUID=77dc92d4-3448-4bc6-8582-6c04b0face4b /home           ext3  defaults                           0       2
# /dev/hda1
UUID=D4A0829AA082832A                     /media/Windows  ntfs  defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=1b31b23b-4db9-42c1-84a8-fd1f21992500 /mnt/Edgy       ext3  defaults                           0       2
# /dev/hdb5
UUID=18c26e08-7085-4e50-a881-3d6d74b19c04 none            swap  sw                                 0       0
#/dev/hde1
UUID=4b0139b9-6d5e-4a00-bf38-06d1002e3325 /media/Storage  ext3  defaults                           0       2 
#/dev/sda1
UUID=b51b9252-a78c-416f-a734-9651fe2b7a27 /media/USBDrive ext3  defaults                           0       2


and for the "best" info on fstab....it's no further than in a terminal: man fstab ;)

---

### Post by gregconquest on 2007-04-20
(previous non-mounting problem resolved, so I altered the post)
I have managed to get my partitions labeled (using *e2label* for ext3 partitions, Windows Explorer for ntfs partitions, and *mtools* for fat32 partitions), and I have edited fstab to use the *LABEL* for mounting, not */dev/sdxx*. The ext3 and ntfs partitions mount happily. However, the fat32 partitions are not mounting by label.

At terminal, I also issued the command:
```

mount

```
and got the mounted partitions and the mount options more spelled out. I've added this data to the fstab comments:
```

# kubuntu
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#
# /dev/sda4     UUID=c5f974ed-2a52-46e1-9289-22f051a5cb9d     (root)
LABEL=kubuntu      /     ext3    defaults,errors=remount-ro 0       1
#                                  (rw,errors=remount-ro)
#
# /dev/sdb2     UUID=183edeb8-2557-4475-99fd-b4e71c22391b     (another linux installation)
LABEL=ubuntu     /media/ubuntu ext3    defaults        0       2
#                                        (rw)
#
# /dev/sdb5     UUID=8bebaccc-bb8a-4d07-8de5-0b170299706b     (a shared ext3 partition - for data)
LABEL=LnWnExt1      /media/LnWnExt1 ext3    rw,user        0       2
#                                    (rw,noexec,nosuid,nodev)
#
# /dev/sdd2     UUID=183edeb8-2557-4475-99fd-b4e71c22391b     (for testing installs)
LABEL=OStest3      /media/OStest3 ext3    defaults        0       2
#                                           (rw)
#
# /dev/sdd3     UUID=d9e47266-9d78-4236-b92c-f6fb6d9efaa8     (another linux installation)
LABEL=openSUSE      /media/openSUSE ext3    defaults        0       2
#                                             (rw)
#
# /dev/sda7     UUID=8C55-0200
# LABEL=LnWnFat0     /media/LnWnFat0     vfat     defaults,utf8,umask=007,gid=46     0     1 (LABEL is not working on fat32)
UUID=8C55-0200     /media/LnWnFat0 vfat    defaults,utf8,umask=007,gid=46 0       0
#                                             (rw,utf8,umask=007,gid=46)
#
# /dev/sdc1     UUID=12D7-0200
#LABEL=LnWnFat2       /media/LnWnFat2 vfat    defaults,utf8,umask=007,gid=46 0       0 (LABEL is not working on fat32)
UUID=12D7-0200       /media/LnWnFat2 vfat    defaults,utf8,umask=007,gid=46 0       0
#                                              (rw,utf8,umask=007,gid=46)
#
# /dev/sdd4     UUID=35C1-0200
#LABEL=LnWnFat3  /media/LnWnFat3 vfat    iocharset=utf8,umask=000 0       0 (LABEL is not working on fat32)
UUID=35C1-0200  /media/LnWnFat3 vfat    defaults,utf8,umask=007,gid=46 0       0
#                                         (rw,utf8,umask=007,gid=46)
#
# /dev/sdb1     UUID=4804A2DE04A2CDEE     (ntfs partition -- read only data)
LABEL=M_ntfs1     /media/M_ntfs1 ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
#                                          (rw,nls=utf8,umask=007,gid=46)     (should be read only)
#
# /dev/sdd1     UUID=0EA01647A01635A5     (ntfs partition -- read only data)
LABEL=H_ntfs3     /media/H_ntfs3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
#                                              (rw,nls=utf8,umask=007,gid=46)     (should be read only)
#
# /dev/sda1     UUID=FEF8D529F8D4E147     (WindowsXP Pro SP2 -- read only)
LABEL=WinXP     /media/WinXP     ntfs    defaults,nls=utf8,umask=007,gid=46     0       1
#                                         (rw,nls=utf8,umask=007,gid=46)     (should be read only)
#
# /dev/sda6	LinSwap     UUID=b2d411e0-26c5-464a-8f34-6c78308d97a5      (LABEL is not working on linux swap either)
UUID=b2d411e0-26c5-464a-8f34-6c78308d97a5 none            swap    sw              0       0
#
#
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


```

---

### Post by taiyo on 2007-04-20
Hello!

Thanks for this help regarding fstab, I have a closely related problem:

My dvd-writer drive doesn't work anymore, I followed some guides to load the necessary drivers (ide which shouldn't be needed anyways if I read correctly), but that only gave me an error message:
[  375.008000] ide0: I/O resource 0x3F6-0x3F6 not free.
[  375.008000] ide0: ports already in use, skipping probe
[  375.008000] ide1: I/O resource 0x376-0x376 not free.
[  375.008000] ide1: ports already in use, skipping probe

I do NOT have any sd* or sc* or cd* entry except for sda/sda1/sda2 which are my ext3 and swap partition.... My drive is connected and working as reported by the BIOS, so there has to be some problem with my /dev/ location of feisty.

Help is greatly appreciated,

(My original thread :[http://ubuntuforums.org/showthread.php?t=411731](http://ubuntuforums.org/showthread.php?t=411731))

---

### Post by autocrosser on 2007-04-20
You might look thru the closed Feisty Development forum. I remember some problems with IDE/ATA burners not working with the new SATA kernel spec. Also: I would file a bug on Launchpad & be sure to include the model of burner.

---

### Post by knightnet on 2007-04-20
You might like to include the fact that SMB shares with spaces in should be coded with "\040" in place of the space (minus the quotes of course).

You might also like to note that there seems to be a bug as well. I have a share (standard on the NSLU2 NAS box) of "disk 2". Coded as "disk\0402" in fstab fails to load even though loading the share through KDE desktop works fine.

Regards,
Julian

---

### Post by taiyo on 2007-04-20
Even tough it doesn't work properly yet, a kernel update to 20-15 brought the solution to the recognizing issue...
Additionally I had to resolve some nvidia-module related stuff, but that's another story...
Does somebody have a suggestion what to change about my fstab entry? It's an LG GSA H22L:
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto    0       0

EDIT: My fault... checked again... it works :)

---

### Post by gregconquest on 2007-04-20
I have found the source of one of my fstab problems. Two different partitions on my system, *sdc2* and *sda2*, have the same UUID!  I tried *sdc1* and *sda1* just to compare two other partitions on the same drives. Their UUID's are fine.

```
$ sudo vol_id -u /dev/sdc2
183edeb8-2557-4475-99fd-b4e71c22391b
$ sudo vol_id -u /dev/sda2
183edeb8-2557-4475-99fd-b4e71c22391b
$ sudo vol_id -u /dev/sdc1
4804A2DE04A2CDEE
$ sudo vol_id -u /dev/sda1
0EA01647A01635A5
```

What is wrong? I didn't set the UUID's.

Below I manged to change the *LABEL* of one the partitions, so they do have different labels and /dev/sdxx ID's, but the UUID remains non-unique.
```

$ sudo e2label /dev/sdc2              <-- checking label
ubuntu                                <-- results
$ sudo e2label /dev/sda2              <-- checking label
ubuntu                                <-- results, [COLOR="Red"]same label[/COLOR]
$ sudo e2label /dev/sda2 OStest3      <-- changing label
$ sudo e2label /dev/sda2              <-- checking label
OStest3                               <-- results, [COLOR="Blue"]label successfully changed[/COLOR]
$ sudo e2label /dev/sdc2              <-- checking label
ubuntu                                <-- results, still OK
$ sudo vol_id -u /dev/sda2            <-- checking UUID
183edeb8-2557-4475-99fd-b4e71c22391b  <-- results
$ sudo vol_id -u /dev/sdc2            <-- checking UUID
183edeb8-2557-4475-99fd-b4e71c22391b  <-- results, [COLOR="Red"]two partitions, two labels, one UUID[/COLOR]

```

---

### Post by autocrosser on 2007-04-21
Do a grep UUID of your /dev/whatever-it-is  & correct the fstab. I've noticed that Feisty sometimes is not getting it right:mad:.

Example: sudo /sbin/dumpe2fs /dev/sda2 | grep UUID 

Will give a result like:
dumpe2fs 1.40-WIP (14-Nov-2006)
Filesystem UUID:          1b31b23b-4db9-42c1-84a8-fd1f21992500

---

### Post by gregconquest on 2007-04-21
```
$ sudo /sbin/dumpe2fs /dev/sda2 | grep UUID
   dumpe2fs 1.40-WIP (14-Nov-2006)
   Filesystem UUID:          183edeb8-2557-4475-99fd-b4e71c22391b
$ sudo /sbin/dumpe2fs /dev/sdc2 | grep UUID
   dumpe2fs 1.40-WIP (14-Nov-2006)
   Filesystem UUID:          183edeb8-2557-4475-99fd-b4e71c22391b

```

Was it just a coincidence that these were set the same? This is astronomically unlikely, so could I have changed or masked the UUID somehow? I used e2label to label them, the same once, maybe. It seems unlikely that I could have mistakenly reset the UUID, though. UUID's must have a persistence -- not changing easily. It has happened before, though:
[Re: Question about duplicate UUIDs]("http://svn.haxx.se/users/archive-2004-10/0489.shtml") There, Donlan says,
> I don't know if it can cause a problem. but you can change the UUID at the top of a dump file.
I don't grep dumping uuid's, though. Is this what I should be doing? Trying to change the UUID?

---

### Post by autocrosser on 2007-04-21
I'd do some more checking about UUID. I'm not sure about changing them. I am sure that a bug should be filed & you should check to see if one has already been.

I was looking at launchpad & found this bug: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/90526](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/90526)

Not sure this would help, but looks like a good canidate.

---

### Post by gregconquest on 2007-04-21
I found out what had caused the duplicate UUID. I had used BootIt NG to essentially clone a partition (*image* and *paste* in BootIt terms). I cloned ubuntu as OStest3. Thus, both had the same UUID. I reformatted OStest3 and it now has its own UUID.

I also noticed in all this that since I didn't alter root's entry in fstab, that I was actually using BootIt to boot into one partition, and then having another actually running! OStest3 was going to ubuntu or vice versa.

I need to figure out the limitations and dangers on cloning partitions with BootIt, but the damage here has apparently all been undone :) 

Now I can get back to creating my optimal, annotated fstab along with example mountings -- and a few suggestions on using *UUID* vs. *LABEL* vs. */dev/sdxx*.

Thanks for the help, autocrosser =D>
Greg

---

### Post by autocrosser on 2007-04-22
I try to help in the forums as much as I can---Glad I was able to lend a hand!!!

---

### Post by ~sparkles~ on 2007-06-20
I found this was an excellent intro.

[http://gentoo-wiki.com/HOWTO_Mount_Windows_partitions_(DOS,_FAT,NTFS)](http://gentoo-wiki.com/HOWTO_Mount_Windows_partitions_(DOS,_FAT,NTFS))

---

