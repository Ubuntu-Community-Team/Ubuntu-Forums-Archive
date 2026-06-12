---
title: "mounting a samba share automatically"
date: 2008-06-22
forum: General Help
---

### Post by mooglinux on 2008-06-22
Here is the deal: i want to automatically mount a samba share on another computer on my home network. Mounting it is no problem by using nautilus to brows the network and open up the folder, but i want to mount it on bot so i can use mythtv to watch videos contained on the share. 

running ```
mount
``` gives me a slew of everything thats mounted, including the share i want:```
gvfs-fuse-daemon on /home/mooglinux/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mooglinux)

```
so my question is what i need to enter in my /etc/fstab to mount this on bootup, and i want to mount it to the location ```
/home/mooglinux/network-shares
```which browsing through nautilus doesnt do for me anyway. 

thanks in advance!

---

### Post by cariboo on 2008-06-22
Have a look at this it should help:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

Jim

---

### Post by plucky on 2008-06-22
This link might help 

[Setting up Samba](https://help.ubuntu.com/community/SettingUpSamba)

Good Luck

---

