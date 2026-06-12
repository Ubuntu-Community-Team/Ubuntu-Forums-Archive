---
title: "Backup strategy for dual boot"
date: 2007-01-02
forum: General Help
---

### Post by sarc on 2007-01-02
I dual boot Edgy and WinXP Home, each OS can read/write files of the other (using a Linux file reader in Windows), on a single disk.  I would like to back up the System partitions (not the Home folders; I keep data on separate partitions) for both OSes (about 12GB each) to USB hard disk or DVD.  It should be easy to use one OS to backup the other, but I tried to use WinRAR from WinXP to make a zipped archive of my Ubuntu drive and it complained that several folders were not accessible.  Thanks!

---

### Post by MikeBenza on 2007-01-02
I don't know how to help you, but someone who does would probably want to know which folders, and what linux file reader you're using.  Also, have you checked the reader's site?  I read fs-driver (fs-driver.com) won't let you access special files (sockets, symlinks, etc)

- Mike

---

### Post by aysiu on 2007-01-02
I would use *ddrescue* or PartImage.
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by tagra123 on 2007-01-02
> **aysiu said:**
> I would use *ddrescue* or PartImage.
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

See my post in another question.  

I've posted a fairly easy to understand solution / how to.


[http://www.ubuntuforums.org/showthread.php?t=321375](http://www.ubuntuforums.org/showthread.php?t=321375)

---

### Post by sarc on 2007-01-03
I use Ext2IFS.  Not a bad idea to block access to special Linux files anyway... Windoze is a nasty little bugger towards other OSes...

---

