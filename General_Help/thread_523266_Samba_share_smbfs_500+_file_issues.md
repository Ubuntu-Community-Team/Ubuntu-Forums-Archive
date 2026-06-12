---
title: "Samba share smbfs 500+ file issues"
date: 2007-08-11
forum: General Help
---

### Post by daverab on 2007-08-11
Hi,

I'm using Ubuntu 7.04 and have a drive shared on a mac through Samba. I'm using smbfs to view the share and I have it in my fstab for auto-mounting on startup.

Anyways, here's my issue. It didn't happen before, but now it seems like any folder with 500 or more files within it won't open fully and a "The folder contents could not be displayed." error pops up. If I refresh the folder, I get a listing of maybe 100 items within the folder including nested folders.

I'm just curious if I'm missing a flag in my fstab or something, below is the line I'm using.

//192.168.0.110/Drive /media/Drive smbfs credentials=/home/pdurland/.smbpasswd,rw,lfs,uid=pdurland,gid=pdurland 0 0

---

### Post by daverab on 2007-08-11
I solved the issue. Incase anyone runs into the same problem, change the mount to a CIFS type. Additionally, use the noperm tag at the end of the line, so the fstab line now goes to this:

//192.168.0.110/Drive /media/Drive cifs credentials=/home/pdurland/.smbpasswd,iocharset=utf8,,uid=1000,gid=1000,noperm 0 0

---

