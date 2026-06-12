---
title: "Editing /etc/fstab"
date: 2005-04-06
forum: General Help
---

### Post by pfe1223 on 2005-04-06
I followed the directions given by the Ubuntu site on how to auto-mount Windows drives by editing the /etc/fstab.  When I mount the drive manually, the icon shows up on the desktop.  However, after I edited the /etc/fstab, no icon shows up.  Is this normal?

---

### Post by Gandalf on 2005-04-06
[QUOTE=pfe1223]I followed the directions given by the Ubuntu site on how to auto-mount Windows drives by editing the /etc/fstab.  When I mount the drive manually, the icon shows up on the desktop.  However, after I edited the /etc/fstab, no icon shows up.  Is this normal?[/QUOTE]
 i have the same problem, didn't bothered myself to find out why yet!!!

---

### Post by ioliver on 2005-04-06
Here is how I have done it -

# Put this in /etc/fstab - all on one line
# Note that the drive is mounted in /media so it appears on the desktop
//mediaserver/music /media/music smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777    0       0

The file /root/.smbcredentials contains -
username=guest
password = ""

Works fine for me.

Ian

---

### Post by francois.lavoie on 2005-04-08
[QUOTE=pfe1223]I followed the directions given by the Ubuntu site on how to auto-mount Windows drives by editing the /etc/fstab.  When I mount the drive manually, the icon shows up on the desktop.  However, after I edited the /etc/fstab, no icon shows up.  Is this normal?[/QUOTE]
 I would have like a pertinent answer to your question pfe1223. I have myself a problem to mount my windows fat32 volume. It seems to me that joliver does not give the right answer to your question. If it is the case just let me know.

---

