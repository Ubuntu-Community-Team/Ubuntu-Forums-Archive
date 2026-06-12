---
title: "I want to creat a windows partition in a unbuntu/windows duel boot"
date: 2008-06-11
forum: General Help
---

### Post by TheLastAlive on 2008-06-11
Like my title suggests, I want to create a ubuntu/windows duel boot.  Currently I only have ubuntu.  How would I go about installing windows also?

---

### Post by spiritfox on 2008-06-11
Depending on how much effort you want to put into this, you may want to back up everything on your existing partition, install windows normally and then install Ubuntu.  Windows isn't smart enough to recognize when you already have an operating system set up, so it modifies the master boot record to only allow Windows to load.  You would need some way of either stopping windows from doing this or fixing your mbr.

---

### Post by overdrank on 2008-06-11
> **TheLastAlive said:**
> Like my title suggests, I want to create a ubuntu/windows duel boot.  Currently I only have ubuntu.  How would I go about installing windows also?

HI and you can use the live cd to create a partition for window. You can resize your ubuntu partition and then create a partition for window. Then for recovering after the windows installation
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
You may also consider using a virtual machine like Virtual Box or VMWare

---

### Post by Dougie187 on 2008-06-11
[http://apcmag.com/how_to_dual_boot_l...lled_first.htm](http://apcmag.com/how_to_dual_boot_l...lled_first.htm)

---

### Post by overdrank on 2008-06-11
> **Dougie187 said:**
> [http://apcmag.com/how_to_dual_boot_l...lled_first.htm](http://apcmag.com/how_to_dual_boot_l...lled_first.htm)

Hi and I get bad request from your link.:(

---

### Post by meierfra. on 2008-06-11
> Hi and I get bad request from your link.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm")

---

