---
title: "Saving to a file on a vfat mount"
date: 2006-10-22
forum: General Help
---

### Post by aknapp on 2006-10-22
Here is what I am trying to do. I have two partitions; winxp on one, and kubuntu on the other. I have Azureus on both of these and I would like for them to be able to share the same downloads, so that no matter which OS I am in, their both downloading the same files. 

I made a fat32 partition and mounted 
[QUOTE=fstab]/dev/sda5	/home/knapp/documents/dump	vfat user,fs=auto,iocharset=iso8859-1,dev,codepage=850,exec,umask=0 0 0[/QUOTE]

The problem is, is the file that Azureus is trying to download to is owned by root and you cannot change ownership of a file on a fat partition. Is there any other way I can achieve this? ](*,) 

Thanks.

---

### Post by taurus on 2006-10-22
Try "umask=0000"...

---

### Post by aknapp on 2006-10-22
No, same issue. The problem is, is that there's no write permission for users (other than root?).

---

### Post by aknapp on 2006-10-23
Anyone? I could really use some help on this.

---

