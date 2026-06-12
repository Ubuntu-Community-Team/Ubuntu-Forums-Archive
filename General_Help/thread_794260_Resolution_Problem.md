---
title: "Resolution Problem"
date: 2008-05-14
forum: General Help
---

### Post by Ressurect on 2008-05-14
**Nevermind, it worked after I rebooted, I feel so stupid**

Hello, I have just installed Ubuntu 7.10 on my laptop. My graphics card is a Via/S3 Unichrome Pro IGP (or something like that, I can't use windows to check it as windows doesn't seem to be able to boot).

When I first booted into Ubuntu, it told me it had to run in 'low graphics mode' and the highest resolution I could choose was 800x600, which does not look very pleasing on my screen that was designed for 1024x768, but I have tried changing options and it doesn't allow me to change the resolution to that.

I've gone into System>Preferences>Screen Resolution and the highest is still 800x600.

I've also gone in to Screens and Graphics in Administration, and changed settings in their, but it just tells me that all users need to log off for effects to take place, and then reverts back to 800x600 when I log back in again.

(BTW, this did not happen when I had ubuntu 6.10 installed)

---

### Post by tyrion2323 on 2008-05-14
Unfortunately, I am STILL having this problem (though, in all fairness, I just installed on a new(ish) laptop tonight.)

So, here's the rub, I'm using a Sony VGN-S170P notebook.  I'm not sure about the components, but I've never had this problem before :(

Any help?

EDIT:  Installed the Radeon 9700 drivers, but no dice :(

---

### Post by IanShuttleworth on 2008-05-14
Try this command: sudo dpkg-reconfigure xserver-xorg
and skip through all the keyboard and mouse stuff, and when it lists resolutions, check the one you want, works for me 99% of the time.

EDIT: Also try installing restricted drivers. Usually reboots right into the highest resolution, which is usually the correct one.

---

### Post by Athanasius on 2008-05-14
The command that you gave does not work in Harty, I have the same problem and I have not found a fix other than manually changing the file which seems like a terrible pain.

---

