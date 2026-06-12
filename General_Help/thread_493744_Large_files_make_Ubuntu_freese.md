---
title: "Large files make Ubuntu freese"
date: 2007-07-06
forum: General Help
---

### Post by KnightOnline on 2007-07-06
My Ubuntu 7.04 is having troubles handling large files.

When I try to copy a file (over 600 MBs) from a windows network drive into my local hard drive, Ubuntu freezes. It also freezes  if i try to unzip a compressed file if one of the output files is very large.

Its not lack of hard disk space, i have over 40GBs free.

I only started noticing this issue when copying/unziping DVDs, so maybe is some sort of filesize limitation? like in FAT32? I think my disk is formated as a EXT3 partition. (I just let Ubuntu partition my disk automatically when I installed)

Can anyone help shed some light on this issue? Its really driving me nuts as this is the only pc I got with a DVD burner. I'm sorry if this is a very basic question, i'm really a Linux Noob.

Many thanks in advance.

---

### Post by Dr. Octagon on 2007-07-06
What does your mount script look like?

---

### Post by KnightOnline on 2007-07-06
> **Dr. Octagon said:**
> What does your mount script look like?

As I mentioned in my previous post, i'm a noob. so i'm not sure what you mean by mount scrip. Do you mean the /etc/fstab file?

It looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=6f3c0f27-977b-4db6-aeb7-26563a7f5f98 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=0b04b997-a6e5-4bd2-b736-a0c4a1917a2c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

This is still exactly as Ubuntu set it up when i installed it.

---

### Post by Dr. Octagon on 2007-07-06
I use samba for mounting my windows network shares.

```
 sudo apt-get install smbfs 
```

Here is a script I found a while back that I use to mount my windows shares.  Just ensure that you have the text file (/.smbcredentials) and directories (/home/user/mounts/etc.) it calls for.  I just created it in nano, but any text editor will do.

```
sudo mount //192.168.1.0/mount /home/user/mounts/windows/ -o uid=user,credentials=/root/.smbcredentials,lfs
```

Here is what my /.smbcredentials file looks like:

```
username="user"
password="passwd"
```

The user name and password you provide in this file must correspond with your user / pass on your windows shares.  I run this every time I log on to my box.  It seems to work well if you access more than a few network shares which authenticate with the same user and password. 

The lfs at the end of the script solved my file size limitation woes.

---

### Post by KnightOnline on 2007-07-11
Thanks for all the advice.

At the end I managed to figure out that the problem was that my ext3 partition wasn't formated with the largefiles4 tag, so it didn't support large files after all. I've resized it to 50% and created a xfs partition with the rest of the space because I was told xfs is the best to store large files.

Now i use the xfs partition to store my DVD images and other large files and it works great.

---

