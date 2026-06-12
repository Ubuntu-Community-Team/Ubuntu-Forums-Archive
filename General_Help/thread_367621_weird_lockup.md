---
title: "weird lockup"
date: 2007-02-22
forum: General Help
---

### Post by gozzerd on 2007-02-22
This seems weird to me. I had beryl installed, but not active, usng metacity, was working as a normal user on the desktop and got a few lockups requiring a restart, no keyboard response or mouse. After restart, when ntloader's boot menu came up, (I call grub from there) the keyboard was still unresponsive. I had to restart again, then I could move the menu choice around. I uninstalled Beryl, thinking it might be the culprit, but had the same thing happen again. The activity preceding the lock involves different apps, but if i am remembering correctly, I think I might have been initiating a copy and paste, so maybe clipboard.  In the last instance, Gimp was the active app, I had selected something, no copy yet, was opening a new file to paste it into and it froze on the 'new file' click. 

I have a dual cpu machine running the generic kernel on edgy. There is a gig of ram and I  think the swap partition has never been written to. Rarely exceed 400 megs of memory usage. The new -11 kernel was not working for me, so I commented it out of the grub menu and don't use it. using 2.6.17-10.

The weird part is that the unresponsive keyboard symptom persists after the restart key is pressed, and doesn't go away until the second restart.  Are there keyboard sniffers that load into the mbr?

I use my machine for work, and have lost hours of work. I have lost the same data 4 times in a row now in one spreadsheet, so it's getting a little frustrating.

Any ideas what I should try?

I don't think there was an occurence before the -11 kernel update, but I am not sure about that.

Geoff

---

