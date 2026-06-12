---
title: "Permision to read denied as root"
date: 2008-01-06
forum: General Help
---

### Post by Zespris on 2008-01-06
Hi

I have an external USB hard drive (NTFS) which i plug in sometimes to Ubuntu working as a Live-CD. The problem is, it won't let me read most of the data, it just says permission denied, even as root.

I tried to chmod a+r -R /media/disk, and all files have read permission, but I still can't read them as it says permission denied.

Even putting the hard drive under Windows says permission denied to read...

Any ideas?

Thanks

---

### Post by stzasnail on 2008-01-06
Well, I have this problem with my MP3 player (which is FAT32) and it's not a matter of your permissions on your system. Do you access the HDD with a Windows computer? If so, the files may be protected by Windows administrator rights. If this is the case, you just have to change the permissions on the Windows system.

---

