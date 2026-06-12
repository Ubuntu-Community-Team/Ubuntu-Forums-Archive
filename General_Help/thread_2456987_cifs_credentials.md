---
title: "cifs credentials"
date: 2021-01-23
forum: General Help
---

### Post by zkab on 2021-01-23
I have an issue with credentials when mounting a Windows file with cifs.
My fstab looks like this:

//triglyfen/Mina\040Mappar  /cifs/Mina_Mappar  cifs  credentials=/root/.cifscredentials_begonian,rw,iocharset=utf8,uid=1000,gid=1000 0  0

My /root/.cifscredentials_begonian look like this:

root@balder:/etc# ls -la /root/.cifscredentials_begonian 
-rw------- 1 root root 35 jan 23 17:09 /root/.cifscredentials_begonian

and has only 2 lines:
username=XXX
password=*****

The volume is mounted correctly but I get an error with the credential file ...

$ sudo mount -av
Credential formatted incorrectly: (null)
mount.cifs kernel mount options: ip=192.168.1.3,unc=\\triglyfen\Mina Mappar,iocharset=utf8,uid=1000,gid=1000,user=XXX,pass=********
/cifs/Mina_Mappar        : successfully mounted

I am running Ubuntu 20.10 (5.8.0-40-generic)

Where have I missed?

---

### Post by HermanAB on 2021-01-23
I see a typo space in the 'pass' parameter.

---

### Post by ActionParsnip on 2021-01-23
Press ENTER on the end of the password line too. File should show 3 lines

---

### Post by zkab on 2021-01-24
OK ... thanks

---

