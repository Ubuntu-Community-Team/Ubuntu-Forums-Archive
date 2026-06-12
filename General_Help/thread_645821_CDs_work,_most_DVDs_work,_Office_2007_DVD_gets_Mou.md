---
title: "CDs work, most DVDs work, Office 2007 DVD gets Mount: not a directory."
date: 2007-12-20
forum: General Help
---

### Post by Mysticle31 on 2007-12-20
I've been getting my windows VM up and running in my Virtualbox on gutsy.  I use office 2007 because of OneNote and my Tablet PC.

Anyhow, I have had no issues mounting CDs.  I just mounted my TurboTax CD, my Ubuntu CD, and another random CD that I have misplaced in 2 minutes.  Oh, and I had no issues mounting my Windows CD when I installed Windows on the VM.

I have had no issues with mounting a Fedora DVD.  I had no problems mounting a video DVD just now.  However when I mount my office DVD I get:.

"mount: block device /dev/scd0 is write-protected, mounting read-only"
Which is a standard deal I think, because we are mounting a read-only medium

and I get:

"mount: Not a directory"

So I've read up on "mount: Not a directory" and found that it means "The local path is not a directory. Check the spelling in your command, and run ls to check if local path is a directory or not." (from here [http://ou800doc.caldera.com/en/NET_nfs/nfsC.mount_err_msgs.html](http://ou800doc.caldera.com/en/NET_nfs/nfsC.mount_err_msgs.html))

Well, how can I mount the other mediums and not have and problems and have a problem with my office disk?  How do I check if local path is a directory?  Why don't I have problems with other mediums?  How do I fix this?

---

### Post by cdenley on 2007-12-20
try this:

```

sudo mkdir /media/office
sudo mount -o ro,uid=1000 /dev/scd0 /media/office

```

That should mount it. If you want to know why it won't mount automatically, it might help to provide this output:

```

sudo vol_id /dev/scd0
ls -l /media

```

---

### Post by Mysticle31 on 2007-12-20
steve@Desktop:~$ sudo mkdir /media/office
steve@Desktop:~$ sudo mount -o ro,uid=1000 /dev/scd0 /media/office
mount: Not a directory


Same thing.

Here are the outputs.

 sudo vol_id /dev/scd0
[sudo] password for steve:
ID_FS_USAGE=filesystem
ID_FS_TYPE=iso9660
ID_FS_VERSION=Joliet Extension
ID_FS_UUID=
ID_FS_UUID_ENC=
ID_FS_LABEL=Office2007
ID_FS_LABEL_ENC=Office2007
ID_FS_LABEL_SAFE=Office2007

It is a burned media, my dad has the original at his house.  He bought it for Christmas as my tablet came with 2003 and OneNote is a good deal better in 2007.  It's not stolen.  I tend to do bad things to CDs so I image everything on my hard drives and use burned ones.


ls -l /media
total 16
drwxrwxrwx 2 root  root       6 2007-12-20 11:19 cdrom0
drwxrwx--- 1 root  plugdev 8192 2007-12-20 01:22 data
drwxr-xr-x 2 root  root       6 2007-12-16 00:45 floppy0
drwxr-xr-x 2 root  root       6 2007-12-16 00:45 movies
drwxrwxr-x 2 steve mythtv  4096 2007-12-20 00:30 tv

if it means anything, I have tried running chmod 777 on both /media and /media/cdrom0

---

### Post by cdenley on 2007-12-21
I was thinking that it mounted with the volume label, but I was wrong. The only thing I see different about your system is you don't have a link named cdrom to cdrom0, but I don't think it matters. If you have an image of the cd-rom, try mounting that:

```

sudo mount -o loop,ro,uid=1000 /path/to/image.iso /media/office

```

If that works, it's a media problem. If it doesn't, then I don't know.

---

### Post by Mysticle31 on 2007-12-21
Oh, I had a link cdrom to cdrom0.  I deleted it.

Thanks for your advice.  I'll have by dad send me the original.

Can I work with the DVD without mounting it?

---

