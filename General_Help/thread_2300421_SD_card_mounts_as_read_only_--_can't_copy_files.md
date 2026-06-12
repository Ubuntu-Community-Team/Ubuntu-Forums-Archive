---
title: "SD card mounts as read only -- can't copy files"
date: 2015-10-25
forum: General Help
---

### Post by jsleotti on 2015-10-25
Hello,

I've been on a lot of forum posts about this issue but have not been able to find the solution by implementing any of the suggestions. I have a 16gb SD card that I cannot copy files to. If I connect to Windows 8 it works perfectly but not on Ubuntu or Mint - convincing me it's a Linux issue. I don't really understand why Linux would be designed to automatically do that and provide no easy way to change it. It completely baffles me. I have the same results regardless of what position the physical switch is on the card.

Help is appreciated. Thanks.

---

### Post by yancek on 2015-10-26
What filesystem is on the SD Card?
What is on it, just data files?
How exactly do you try to copy files to it?
Did you check the owner:group and permissions for the SD Card?

---

### Post by jsleotti on 2015-10-26
I've tried formatting as FAT32 and NTFS with the same results. Nothing is on the card right now, but I did successfully copy some test files via Windows to make sure the card itself was working.

I've tried clicking and dragging the file from the desktop to the folder and using dd=if; both failed. 

If I go to properties then permissions, folder access says NONE. Trying to change it just gives an error message.

---

