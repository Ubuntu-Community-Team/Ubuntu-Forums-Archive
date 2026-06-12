---
title: "Can't boot up anymore (grub)"
date: 2007-07-19
forum: General Help
---

### Post by alex.de on 2007-07-19
Hi, I have Windows Vista and Ubuntu 7.04 on seperate hard drives on the same machine. Well, today I decided to remove grub because I've always had problems with it (I like the basic one that showed up before I installed grub). So I read a post by someone on how to remove it and it was basically:
```
sudo apt-get remove grub
```

Well, now I can't boot at all (I'm currently on another computer right now). It parses ERROR 17 and it stays there without anything happening.

I really need help because it's my main machine with music/pictures/personal documents.

Thank you very much

---

### Post by ddrichardson on 2007-07-19
Use the live cd to recover your documents, I can't think how to reinstall the boot loader after you've removed it infact I'm not sure its possible. The MBR is now pointing to a non existant boot loader so you may need to re-install Ubuntu.

---

### Post by confused57 on 2007-07-19
> **alex.de said:**
> Hi, I have Windows Vista and Ubuntu 7.04 on seperate hard drives on the same machine. Well, today I decided to remove grub because I've always had problems with it (I like the basic one that showed up before I installed grub). So I read a post by someone on how to remove it and it was basically:
```
sudo apt-get remove grub
```

Well, now I can't boot at all (I'm currently on another computer right now). It parses ERROR 17 and it stays there without anything happening.

I really need help because it's my main machine with music/pictures/personal documents.

Thank you very much

You can restore Window's IPL to your Windows drive's mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

It would probably be easier to reinstall Ubuntu, and you might want to install grub's IPL to the Ubuntu drive's mbr:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

You could probably reinstall grub, by chrooting into your root partition, using the live cd.

---

