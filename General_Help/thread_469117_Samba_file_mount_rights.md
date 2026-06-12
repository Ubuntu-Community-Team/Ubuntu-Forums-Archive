---
title: "Samba file mount rights"
date: 2007-06-09
forum: General Help
---

### Post by RudolfMDLT on 2007-06-09
Hi there,

I have mounted a Samba share on an XP machine on my Ubuntu PC, the thing is I can't paste or create folders on this drive if I'm not root. Here is an example of my frustration

> rudolf@rh:/$ sudo chmod 777 /netdrives/
rudolf@rh:/$ mkdir /netdrives/media
mkdir: cannot create directory `/netdrives/media': Permission denied
rudolf@rh:/$ sudo mkdir /netdrives/media
rudolf@rh:/$ 
rudolf@rh:/$ ????????????????


Even after chmod'ing the folder I'm still not getting the privileges. When I run Nautilus as root I still can't change the folder owner or who can write to it? Any ideas?

Thanks,

Rudolf

---

### Post by polt on 2007-06-10
I'm not exactly sure whether I understand your set up.  Is the drive you are trying to paste to NTFS by any chance?

---

### Post by RudolfMDLT on 2007-06-10
Yes it is - It's an NTFS drive on the network  on a windows XP machine.

---

### Post by polt on 2007-06-10
I recall having a similar problem having to do with NTFS being read only.  But it looks like that may not apply to you, because you are able to make the directory if you use sudo, true?  Have you tried putting in a -v option after the chmod to see if you are given any error messages?

---

