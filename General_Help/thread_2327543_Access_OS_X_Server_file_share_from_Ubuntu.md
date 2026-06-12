---
title: "Access OS X Server file share from Ubuntu"
date: 2016-06-12
forum: General Help
---

### Post by reldruH on 2016-06-12
I've been struggling with this for a while and I'm hoping somebody here has an answer. I have a Mac OS Server with file sharing turned on and everything as wide open as I can make it (777 permissions, guest access allowed, all protocols open). I can see the server from my ubuntu installation and when I click on it I'm asked for a username and password but there is no combination (valid user on either machine, empty username and password, admin accounts, default username and password, random junk) that lets me access the share. Other macs have no issues accessing it and, weirdly, multiple Windows 2000 computers have no issues accessing this share.

I've searched and searched and tried every configuration I can find but I can't figure out how to access this share from my ubuntu machine. Any ideas?

---

### Post by Morbius1 on 2016-06-12
It's a bug that was introduced in Samba 4.3.8/9: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1579540](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1579540)

What I do is add an entry in fstab to mount the share using cifs instead:
```
//mbp1.local/smbuser /media/MBP1-smbuser cifs username=smbuser,password=smbuserpw,uid=1000,noauto,nounix,user,uid=1000,vers=3.0 0 0
```
I set this up with a mount point under /media such that it won't mount at boot ( noauto ) but will mount when accessed by a normal user ( user ). I also took advantage of specifying the dialog of smb being used ( vers=3.0 ) since the file manger method and the default setting for cifs doesn't do that by default.

---

