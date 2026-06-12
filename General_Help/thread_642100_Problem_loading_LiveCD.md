---
title: "Problem loading LiveCD"
date: 2007-12-16
forum: General Help
---

### Post by Dr. Lucien Sanchez on 2007-12-16
I've just burnt 7.10 (x86) on to a DVD-RW for the third time, yet when ever I try and boot up the LiveCD it prompts me for a username and password. If I enter nothing it loads up the desktop for a split second and goes back to the login prompt. I've checked the disc for any defects and there are none. Any ideas? Any help much appreciated.

---

### Post by Dr. Lucien Sanchez on 2007-12-19
bump

---

### Post by Gotenks on 2007-12-19
login prompt?.. I don't know about gutsy, but on previous versions, when you boot up live/installation cd, firstly, you get menu, either to install/boot live cd, or choose other options..

---

### Post by Sef on 2007-12-19
1) Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the download? (Makes sure the download is good.)

2) Did you burn it at 4x or less? (Faster can corrupt the download.)

3) Did you try burning it on a cd?

---

### Post by Dr. Lucien Sanchez on 2007-12-20
> **Gotenks said:**
> login prompt?.. I don't know about gutsy, but on previous versions, when you boot up live/installation cd, firstly, you get menu, either to install/boot live cd, or choose other options..

This is after I've chosen the 'Start or Install Ubuntu' option.

[QUOTE=Sef]1) Did you md5sum the download? (Makes sure the download is good.)

2) Did you burn it at 4x or less? (Faster can corrupt the download.)

3) Did you try burning it on a cd?[/QUOTE]

I've done an md5sum and it passed, and I've just burnt it onto a new CD-R on the lowest speed (8x). I'm still having the same trouble. I haven't had this trouble with any of the previous LiveCDs.

Some system specs (if needed):
AMD64 3200+
1GB RAM
RS482-M Motherboard
ATI Radeon Xpress (on-board graphics)

Again, all help much appreciated.

---

### Post by Dr. Lucien Sanchez on 2007-12-24
Bump?

---

### Post by burbankmarc on 2007-12-24
There's something wrong with your burn process, because the cd isn't booting, it's your current ubuntu install.

Are you using linux to burn it? If so what are you using? K3B?

---

### Post by Dr. Lucien Sanchez on 2007-12-24
I'm using Windows XP and the program I'm using to burn it is Ashampoo Burning Studio 7.

---

### Post by burbankmarc on 2007-12-24
Make sure you're burning it as an ISO and not a data cd. Also, go into your BIOS and make sure your cdrom is set to boot before your hard drive.

---

### Post by Dr. Lucien Sanchez on 2007-12-25
I've just burnt a freshly downloaded copy of the iso, checked the md5sum, burnt it to a CD-R at lowest speed (8x) using Nero 8 Micro and made sure it was burnt as an iso and not a data CD. And it still comes up with the login prompt. Things look bleak.

---

