---
title: "Cannot mount DVD-R"
date: 2007-10-31
forum: General Help
---

### Post by dmbfan511 on 2007-10-31
Here's the error I get when trying to access a data DVD-R.

Cannot mount volume.
Unable to mount the volume 'UDF Volume'.

I can click details:

mount: block device /dev/scd0 is write-protected, mounting read-only mount: wrong fs type, bad option, bad superblock on /dev/scd0, missing codepage or helper program, or other error     In some case useful info is found in syslog -try   dmesg /tail or so

Thanks in advance for any help you can provide.

---

### Post by troyer81 on 2007-10-31
I'm not sure I can completely answer your question, but it looks like the mount is trying to mount the actual partition (i.e. /dev/scd**0**).  I don't believe that is typical since DVDs and CDs usually need to be mounted on the entire device (i.e. /dev/scd -- without the 0).  If you can mount the disc manually by using a command similar to:
```
sudo mount /dev/scd /media/dvd
```Assuming /media/dvd is a valid directory, and everything mounts successfully, then the disc/drive/mount is okay.  The issue then becomes trying to figure out why Ubuntu is trying to mount the partition instead of the drive.  Let me know if you need to research that next question.

---

### Post by dmbfan511 on 2007-11-01
mount point /media/dvd does not exist

is the error I get...Thanks alot for helping.

KMR

---

### Post by troyer81 on 2007-11-01
That's why I said /media/dvd has to exist.  You can only mount a drive on an empty directory (that already exists).  If you want to test the mount, you can create the /media/dvd folder via the following:

```
sudo mkdir /media/dvd
```And then try mounting the drive again.  The other option is to use one of the other folders that exist in /media (perhaps /media/cdrom?).  For help on the actual structure of the mount command, you should be able to type:

```
man mount
```Let me know if you still have troubles.

---

