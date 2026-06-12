---
title: "Clonezilla"
date: 2015-09-17
forum: General Help
---

### Post by daniell59 on 2015-09-17
I would appreciate assistance installing Clonezilla to my Flash Drive. I am somewhat confused what to do. I already downloaded Clonezilla live zip. I am at loss what to do now.

---

### Post by Li_Wu on 2015-09-17
just unzip it on a fat32 stick and call the script/exe to make it bootable. then boot it

---

### Post by daniell59 on 2015-09-17
> **Li_Wu said:**
> just unzip it on a fat32 stick and call the script/exe to make it bootable. then boot it
 Presently the download is on the hard drive. Should I copy and paste it to the flash drive?

---

### Post by Li_Wu on 2015-09-17
yes like the README states

---

### Post by tea for one on 2015-09-17
> **daniell59 said:**
> I would appreciate assistance installing Clonezilla to my Flash Drive. I am somewhat confused what to do. I already downloaded Clonezilla live zip. I am at loss what to do now.

Depending on exactly what you want to do, there are instructions on the Clonezilla website.

[http://clonezilla.org/clonezilla-live.php](http://clonezilla.org/clonezilla-live.php)

If there is something on the site, which is difficult to follow, then please ask in this thread.

---

### Post by VMC on 2015-09-18
After unzipping to the fat 32 usb flash drive, run the "makeboot.sh", located under "/utils/linux".
Make sure you select the correct dev number. From a terminal run "lsblk" to locate the correct usb flash drive.

---

