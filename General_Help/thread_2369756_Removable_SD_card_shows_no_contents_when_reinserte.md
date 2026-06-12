---
title: "Removable SD card shows no contents when reinserted"
date: 2017-08-26
forum: General Help
---

### Post by youlookgreattoday on 2017-08-26
I'm using Crouton / XFCE on an ACER Chromebook.  Ubuntu 16.04.2 xenial

I have an SD card with many files on it that works great after I boot up.  If I remove the card to add / remove / copy files elsewhere, when I reinsert it the contents don't show up.  I can do an ls at /media/removable/ and it will show SD Card in the ls.  If I cd /media/removable/SD Card/ and then do ls it will show nothing.  If I reboot the SD card will once again show all of its contents.  Obviously my preferred outcome would be to insert and remove the card at will with the contents being available to me every time I reinsert the card.

Thanks for any help you can provide.

---

### Post by Autodave on 2017-08-26
What formatting is used on the card?

---

### Post by ajgreeny on 2017-08-26
Do you always unmount or eject the sd card before removing it from the other systems, and what systems are they?

---

### Post by youlookgreattoday on 2017-08-27
#1
The SD card is formatted as FAT32.
Sorry for the slow response but I'm new to linux and it took me a little while to ID the SD card drive and figure out how to determine the file system used on the card.

#2
I never eject the card from any system before removing it.  I use it between a windows desktop and the linux laptop.  It's worked fine this way historically between a windows desktop and a windows laptop, and it doesn't seem to have a problem on the windows side, and it doesn't seem to affect the linux side as long as I reboot.

Thanks to both for you help.

---

### Post by SeijiSensei on 2017-08-27
You should start using eject then.  If the device appears as /dev/sdb, you can use
```
sudo eject /dev/sdb
```
from the prompt.  If you do not properly unmount the device before removing it, you can lose data.

You should follow the same procedure in Windows.  Make sure you use the options to remove the device safely.

---

### Post by youlookgreattoday on 2017-08-31
Will the card automatically remount when I reinsert it or will I have to do a manual mount?

Do you believe this will address my issue or is this just general good advice?

I appreciate your feedback.  That last question is not intended to be sarcastic.

---

