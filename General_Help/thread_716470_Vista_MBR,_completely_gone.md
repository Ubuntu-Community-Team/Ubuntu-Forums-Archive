---
title: "Vista MBR, completely gone"
date: 2008-03-05
forum: General Help
---

### Post by but2002 on 2008-03-05
I recently installed Ubuntu, with a 200 GB as the primary, and a 40 GB as the secondary

I installed Ubuntu to the secondary hoping that I could dual boot between it and Vista ( Which is on the Primary)  However, even though Ubuntu's files are on the 40 GB, the Grub loader is on the 200GB, and it completely overwrote the Vista MBR

I wanted a dual boot, and now I have a Vista install that isn't bootable, while ubuntu is working fine
Any clue how to fix, w/o reformatting?

---

### Post by WileyHunter on 2008-03-05
Just went through something similar here the other day...  I ended up having to disconnect my second drive, re-install Vista (yuck) on the main HD then Ubuntu...  It automatically came up with a dual boot option (from Ubuntu install).

I am now working on an install of the second drive, then to format it for use only with linux as I want to use it for media storage only.

If the above steps don't work, be patient and I know you can find the answers here.  I will look through my mass of notes from the last 2 weeks worth of browsing and see if I can find some specific messages that may help.

WH

---

### Post by Shazaam on 2008-03-06
No need for a reinstall look here......

[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

When you get that fixed you can add Ubuntu to the Vista bootloader. Search the forums here for that info.

---

### Post by but2002 on 2008-03-06
I sorta fixed it by booting Vista's DVD and running   BootRec /FixMbr

It Fixed my Vista install, but turned around and broke the Ubuntu Install. ..<

---

### Post by but2002 on 2008-03-06
> **Shazaam said:**
> No need for a reinstall look here......

[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

When you get that fixed you can add Ubuntu to the Vista bootloader. Search the forums here for that info.

I'm searching, but I can't find it.

Will you please provide me with some links?

---

### Post by Shazaam on 2008-03-06
Here.......

[http://ubuntuforums.org/showthread.php?t=569506](http://ubuntuforums.org/showthread.php?t=569506)

---

### Post by but2002 on 2008-03-06
Anything just a little bit easier?

---

