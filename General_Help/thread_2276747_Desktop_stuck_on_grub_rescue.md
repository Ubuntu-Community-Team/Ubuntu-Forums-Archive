---
title: "Desktop stuck on grub rescue"
date: 2015-05-04
forum: General Help
---

### Post by Camilia on 2015-05-04
I had the terminal open. I thought it was finished thus closed it. Now when I boot up I get message- unknown filesystem. Entering the rescue mode. grub rescue. I tried the rescue mode and boot menus with no success

---

### Post by yancek on 2015-05-04
The unknown filesystem error is generally shown when trying to boot a non-Linux filesystem.  You haven't indicated what you thought was finished when you closed the terminal which probably has a lot to do with the problem?

---

### Post by Camilia on 2015-05-04
I was in gparted trying to clean a flash drive which I had burned ISO last year. Recently reinstalled ubuntu using a DVD. If there is nothing I can do I can reinstall. But then I have to reinstall printer and other programs.

---

### Post by yancek on 2015-05-04
Are you sure you got the right disk when you were trying "to clean a flash drive"?  You could try booting the Ubuntu installation medium and going to the site below, downloading the boot repair software and selecting the option to Create a Bootinfo Summary then post it here as it will have details about your boot files. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Camilia on 2015-05-04
YES!! By booting the Ubuntu installation medium do you mean reinstall with the DVD? From those instruction at the link it seems I have to burn an ISO. I went through that last month with no success. Thus bought ubuntu disk on Ebay. I will just reinstall everything again.

---

### Post by CantankRus on 2015-05-05
What yancek is saying is boot to your ebay ubuntu dvd/cd so you're running live.
Then do the second option in yancek's link.
Once boot-repair is installed you can use it to create a boot info summary to show what has happened.

---

