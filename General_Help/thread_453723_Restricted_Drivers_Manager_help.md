---
title: "Restricted Drivers Manager help"
date: 2007-05-24
forum: General Help
---

### Post by KManZ on 2007-05-24
Try to click on it, says I need to install "linux-restricted-modules-2.6.20-15-generic" for it to work. I tried to find it in Synaptic, but have no clue. My Wireless stopped working because of this, so any help would be much appreciated. Thanks!

Matt

---

### Post by angryfirelord on 2007-05-24
I think there was an upgrade, so now it's 2.6.20-16. Either way, search for *restricted modules* and you should see it.

---

### Post by KManZ on 2007-05-24
ok, I found the packages and downloaded them to my roomate's laptop, as my computer doesn't have internet due to tis problem. How do I install this package now?

---

### Post by angryfirelord on 2007-05-24
Open a terminal and type **sudo dpkg -i** *name_of_package*. 

If you don't know how to use terminal commands such as **cd** and **ls**, then double clicking on the package brings up a GUI installer. However, if there are missing dependencies, then you'll have to download those as well and install them.

---

### Post by KManZ on 2007-05-24
No luck here. I downloaded the 3 items on this page: [https://launchpad.net/ubuntu/feisty/+source/linux-restricted-modules-2.6.20/2.6.20.5-15.20](https://launchpad.net/ubuntu/feisty/+source/linux-restricted-modules-2.6.20/2.6.20.5-15.20)

After getting them onto my laptop via my thumbdrive, putting them on my desktop, and trying the command you posted above, nothing happened... I got "error exit status 2". 

This is some very un-intuitive stuff. I think re-installing will alleviate all of the frustrations here.

Edit: As I put my live CD into the drive, a window popped up saying that a CD-rom contained packages... is it possible to get the packages off the CD? I tried to get them through Synaptic, but it still kept searching the internet.

---

### Post by angryfirelord on 2007-05-24
Yes, under Edit, click "Add CD-ROM". Then, under Settings-->Repositories, uncheck everything in Ubuntu Software (that's the 1st Window), Third party software (if any), and Updates.

---

