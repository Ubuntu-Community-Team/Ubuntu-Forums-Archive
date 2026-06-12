---
title: "External USB listed twice? Help"
date: 2013-01-12
forum: General Help
---

### Post by ranito1980 on 2013-01-12
Short and sweet.  

1. When I acquired my external USB 3TB drive I labeled it in Gparted as "3tb".  Some months passed.

2. In the last day or so it showed up in terminal as both 3tb and 3tb1 which makes no sense! I must note that when using the -ls command, only 3tb1 listed all files while 3tb listed just two files. I've since deleted those two files. Still it lists two devices for the same external USB drive.

3. I renamed the label as "External". In terminal it still lists two listings as "3tb" and "External".

What is going on and how do I fix it?

Please see attached screenshot.  Any help is highly appreciated.

---

### Post by dcstar on 2013-01-12
> **ranito1980 said:**
> Short and sweet.  

1. When I acquired my external USB 3TB drive I labeled it in Gparted as "3tb".  Some months passed.

2. In the last day or so it showed up in terminal as both 3tb and 3tb1 which makes no sense! I must note that when using the -ls command, only 3tb1 listed all files while 3tb listed just two files. I've since deleted those two files. Still it lists two devices for the same external USB drive.

3. I renamed the label as "External". In terminal it still lists two listings as "3tb" and "External".

What is going on and how do I fix it?

Please see attached screenshot.  Any help is highly appreciated.

Users should not do anything in the /media folder, it is a system folder for exclusive use of the system for managing removable devices.

If you have created folders in /media and/or put entries /etc/fstab using /media then this sort of thing will occur.

---

### Post by ranito1980 on 2013-01-12
> **dcstar said:**
> Users should not do anything in the /media folder, it is a system folder for exclusive use of the system for managing removable devices.

If you have created folders in /media and/or put entries /etc/fstab using /media then this sort of thing will occur.

I think I may have fixed it.  I remember that I had CHMOD -R 777 /media/orion/3tb a day or so ago and that's when the issue began. However, I went in and did a "rm -r /media/orion/3tb" and the problem went away. Why? I have no idea but it seemed to have worked.

---

### Post by dcstar on 2013-01-12
> **ranito1980 said:**
> I think I may have fixed it.  I remember that I had **CHMOD -R 777 /media/orion/3tb** a day or so ago and that's when the issue began. However, I went in and did a "rm -r /media/orion/3tb" and the problem went away.** Why?** I have no idea but it seemed to have worked.

**Users should not do anything in the /media folder, it is a system folder for exclusive use of the system for managing removable devices.**

---

### Post by ranito1980 on 2013-01-12
> **dcstar said:**
> **Users should not do anything in the /media folder, it is a system folder for exclusive use of the system for managing removable devices.**

Now I see why. Thanks!

---

