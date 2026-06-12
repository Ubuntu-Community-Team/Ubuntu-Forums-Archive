---
title: "can't write to external hard drive"
date: 2007-06-04
forum: General Help
---

### Post by attentionwandered on 2007-06-04
hey, im relatively new but i understand my way a little around linux

my external hard drive is read and writeable but when i write it says "some storage is read only"

ive tried using  "sudo chmod -R brooks:users '/media/some storage/'"to change owners and it goes through all of my files but nothing changes in the gui permissions menu (brooks is username some storage is drive name)

ive also tried using "gksudo nautilus"  and changing the permission through the gui but  nothing works. through the privileged browser window  every file on my computer is writeable except this drive.

i feel like linux is treating the drive as if it were a cd, i cant even change the owner from "99" to my username or admin through "gksudo nautilus" because it says the drive is read only

i can use it in mac os x perfectly fine but i really need to be able to use it in linux.  any suggestions?

(sorry if there is an explanation somewhere else, ive looked everywhere and couldnt find one)

---

### Post by indytim on 2007-06-04
I'm not 100% sure this will get you where you want to be.  I just mounted my external and checked the properties of the primary folders.  I see that I have set up the permissions on each folder to allow others to read and write. Just a thought, you may have closed the access on the external folders.

Hope this helps,

IndyTim

---

### Post by bvanaerde on 2007-06-04
I'm not sure if this is your problem, but I thought I'd share it anyway.

A lot of external hard drives are already formatted to NTFS when buying them.
You'll need ntfs-3g to be able to write to them (which is in the repositories, in feisty).

[HOWTO: NTFS with read/write support using ntfs-3g (easy method) ]("http://ubuntuforums.org/showthread.php?t=217009")

---

### Post by Wim Sturkenboom on 2007-06-04
Which filesystem on the HD?
Which version of Ubuntu?

One of the things can be that the disk is mounted as root user and you will not have permissions to write it. You can start of with the eprmissions on /media and /media/some storgae to see if they're OK (who owns it and whos has what kind of access.

---

### Post by vanadium on 2007-06-04
Post the output of 

sudo fdisk -

here. Perhaps also tell us how you mount the drive. Eventually post its line in /etc/fstab. When changing permissions as you described, did you have error messages or did everything look as if it all went well?

---

### Post by attentionwandered on 2007-06-04
im pretty sure its hfs+.  definately not fat32 or anything.

im running feisty, 7.04 with ppc architecture.

permissions for /media are root, some storage the owner is "99"

everything looked fine when changing permissions.

input: sudo fdisk '/media/some storage/'
output: fdisk: Can't read block 0 from file (is a directory)
                /media/some storage

input: sudo fdisk -l
output: 
/dev/sdb
        #                    type name                  length   base      ( size )  system
/dev/sdb1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/sdb2          Apple_Driver43 Macintosh                 56 @ 64        ( 28.0k)  Driver 4.3
/dev/sdb3          Apple_Driver43 Macintosh                 56 @ 120       ( 28.0k)  Driver 4.3
/dev/sdb4        Apple_Driver_ATA Macintosh                 56 @ 176       ( 28.0k)  Unknown
/dev/sdb5        Apple_Driver_ATA Macintosh                 56 @ 232       ( 28.0k)  Unknown
/dev/sdb6          Apple_FWDriver Macintosh                512 @ 288       (256.0k)  Unknown
/dev/sdb7      Apple_Driver_IOKit Macintosh                512 @ 800       (256.0k)  Unknown
/dev/sdb8           Apple_Patches Patch Partition          512 @ 1312      (256.0k)  Unknown
/dev/sdb9              Apple_Free                       262144 @ 1824      (128.0M)  Free space
/dev/sdb10              Apple_HFS Apple_HFS_Untitled_1 321408976 @ 263968    (153.3G)  HFS    [<--- this one looks like it]
/dev/sdb11             Apple_Free                           16 @ 321672944 (  8.0k)  Free space

Block size=512, Number of Blocks=321672960
DeviceType=0x0, DeviceId=0x0
Drivers-
1: @ 64 for 23, type=0x1
2: @ 120 for 36, type=0xffff
3: @ 176 for 21, type=0x701
4: @ 232 for 34, type=0xf8ff

/dev/hda
        #                    type name                 length   base     ( size )  system
/dev/hda1     Apple_partition_map Apple                    63 @ 1        ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled               1954 @ 64       (977.0k)  NewWorld bootblock
/dev/hda3         Apple_UNIX_SVR2 untitled           74837891 @ 2018     ( 35.7G)  Linux native
/dev/hda4         Apple_UNIX_SVR2 swap                3300251 @ 74839909 (  1.6G)  Linux swap

Block size=512, Number of Blocks=78140160
DeviceType=0x0, DeviceId=0x0



im gonna try to cdmod the media folder and ill report back.   thanks for all the help!

---

### Post by attentionwandered on 2007-06-04
just tried to modify permissions of /media using chown and it didnt work

tried modifying permissions of /media with gksudo nautilus and it didnt work either.

:-/


oh and i almost forgot.  im mounting it by just plugging it in and letting ubuntu mount it. if that means anything

---

### Post by Wim Sturkenboom on 2007-06-05
As you're using Feisty, I'm not sure if I can help you. In Dapper, you set the permissions in /etc/fstab, but I don't think that that will work in Feisty. But you can have a look.

---

### Post by attentionwandered on 2007-06-06
im really stuck.  no one has any ideas?

---

### Post by bvanaerde on 2007-06-07
The hard disk has a hfs+ filesystem, which is mostly used on Macintosh computers.
By default, it is possible to read this drive, but you can't write to it.

I can't tell you what to do, as I've never done this before.
But there are some threads about hfs+ that may help you:
[Mounting OS X partition in Ubuntu]("http://ubuntuforums.org/showthread.php?t=220742")
[Permissions of hfsplus partition]("http://ubuntuforums.org/showthread.php?t=224663")
[Trying to mount HFS+ LaCie drive as read/write]("http://ubuntuforums.org/showthread.php?t=98286")
[HowTo check and repair HFSplus in Ubuntu]("http://ubuntuforums.org/showthread.php?p=2346494#post2346494")

Hopefully you'll find what you need there...

---

