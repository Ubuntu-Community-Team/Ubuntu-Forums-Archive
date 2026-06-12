---
title: "ntfs-3g"
date: 2006-11-02
forum: General Help
---

### Post by markr on 2006-11-02
I've read some information on this, and it seems too good to be true!

I was planning on installing Ubuntu, but want to retain all my data on my NTFS drive (until I take the full plunge); read/write for NTFS is therefore critical to my setup.

From what I have read in this forum and other sites, this driver will effectively allow me to treat my NTFS partition as I would an ext3 in linux (i.e. read, write, create/delete/move directories); however I am nervous.

Is anyone using this driver full time?  What is the reliability like?  what is perfomance like?

I have a lot of business documents, photos etc which I really don't want to lose/corrupt (I do have a backup, but it only takes one problem to corrupt a file between backups).

Any advice?

Mark.

---

### Post by galileon on 2006-11-02
hello, i tested it by formatting my old usbstick to ntfs, and it worked great (i  had to compile a latest release of fuse though)...

i can't say more, because I no longer have any ntfs/doze partition :)

---

### Post by szaka on 2006-11-02
> **markr said:**
> I have a lot of business documents, photos etc which I really don't want to lose/corrupt (I do have a backup, but it only takes one problem to corrupt a file between backups).
I don't know about ntfs-3g problems but the Windows NTFS driver can corrupt your data: [http://support.microsoft.com/kb/925308](http://support.microsoft.com/kb/925308)

Make backups, or use Linux more often ;-)

---

### Post by jeppester on 2006-11-02
I'm using ntfs-3g and I haven't had any problems yet... as you, I fear for my data, so I have only changed a few files on the ntfs-drive, but no problems yet... :-)
maybe you could create a fat32 partition and put your your important data there. Then you can read/write with both windows and linux

---

### Post by galileon on 2006-11-02
> **szaka said:**
> I don't know about ntfs-3g problems but the Windows NTFS driver can corrupt your data: [http://support.microsoft.com/kb/925308](http://support.microsoft.com/kb/925308)

Make backups, or use Linux more often ;-)

lmao, it seems that the opensource drivers for ntfs are more reliable than the m$ ones then?!?!?!!!!!

---

### Post by seldon77 on 2006-11-02
I've just been using ntfs-3g for a few days, and my NTFS drive doesn't contain crucial data (just a few windows games)... but no problems so far - seems to work great reading and writing. I don't know why it wasnt included by default in edgy.

* Install ntfs-3g from repos
* Then just change the "ntfs" reference in /etc/fstab to "ntfs-3g"

---

