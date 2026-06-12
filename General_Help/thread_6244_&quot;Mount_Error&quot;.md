---
title: "&quot;Mount Error&quot;"
date: 2004-11-26
forum: General Help
---

### Post by onestep on 2004-11-26
I want to be able to access my Windows partition hde1. Following suggestions in these forums I created a folder /mnt/hde1 and added the following line to my /etc/fstab file;  

/dev/hde1       /mnt/hde1       vfat    users,unmask=000        0       0

When I try to mount hde1 I get the following error message:

"Unable to mount the selected volume. The volume is probably in a format that cannot be mounted. mount: wrong fs type, bad option, bad superblock on /dev/hde1,
       or too many mounted file system"

Any ideas what else I should do?

---

### Post by jiyuu0 on 2004-11-26
Windows Section
[http://kitech.com.my/ubuntu/4.10/index.html](http://kitech.com.my/ubuntu/4.10/index.html)

The examples there are based on hda1... so just replace it with hde1

---

### Post by onestep on 2004-11-26
Thanks!... I now have access to my Windows partition via /mnt/windows.
Any idea how I can get an icon for "windows" to display on my desktop, and in the "Computer Place"?

---

### Post by jiyuu0 on 2004-11-26
Icon on desktop is quite easy

Right click -> Create launcher 

Name: Windows
Command: nautilus /mnt/windows
Icon: something_u_like

---

### Post by Jongi on 2004-11-26
[QUOTE=jiyuu0]Icon on desktop is quite easy

Right click -> Create launcher 

Name: Windows
Command: nautilus /mnt/windows
Icon: something_u_like[/QUOTE]
 Does this work for mounting a floppy as well?

---

