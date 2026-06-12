---
title: "NTFS Drive. Clementine Library Amnesia"
date: 2014-07-21
forum: General Help
---

### Post by JP_Foster on 2014-07-21
Hey all.

I'm a relative beginner to Ubuntu. After using a virtual machine for some time I have decided to dualboot my machine to Ubuntu (main). I have come into an indirect problem with clementine (music player) and the direct problem seems to be my NTFS drive where my music is stored, and shared with my windows dualboot. I can add the music library but when I reboot the computer can't remember the playlist (I have to remove and re-add the playlist location). 

I have heard I can use a easy NTFS configuration app artistically called NTFS configuration tool but it cannot seem to find my 1tb internal drive. Are there alternative ways to deal with this?

Thanks!

---

### Post by oldos2er on 2014-07-21
You probably need to edit your /etc/fstab file (make a backup first!) to have the NTFS partition automatically mounted at boot time. See [https://help.ubuntu.com/community/Fstab#ntfs](https://help.ubuntu.com/community/Fstab#ntfs) and [https://help.ubuntu.com/community/MountingWindowsPartitions#Configuring_.2BAC8-etc.2BAC8-fstab](https://help.ubuntu.com/community/MountingWindowsPartitions#Configuring_.2BAC8-etc.2BAC8-fstab)

---

### Post by JP_Foster on 2014-07-21
Would this action somehow alter the drives functionality on window's side?

And my mistake, I found out that I didn't see the NTFS drive because the drive itself is an "exfat" does your suggestion still apply?

---

