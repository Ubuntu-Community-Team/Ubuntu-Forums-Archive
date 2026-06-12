---
title: "HP Deskjet F340 Printer and hpijs driver"
date: 2007-05-01
forum: General Help
---

### Post by KoolPenguin on 2007-05-01
Hi - I just installed this HP F340 printer and everything works, including the scanning.  However it seems to print like it's printing a draft copy, the ink is light and not as dark as it was when I tested it under Vista.  I'm using OpenOffice as my word pro.  Any help would be appreciated.

- Chris

---

### Post by Rumor on 2007-05-16
I'm having this same issue with my hp 895C deskjet. Anything I print looks as though the printer is out of ink. Anything my family prints to it on our network comes out fine. I've tried all the options under drivers to no avail.

---

### Post by KoolPenguin on 2007-05-17
> **Rumor said:**
> I'm having this same issue with my hp 895C deskjet. Anything I print looks as though the printer is out of ink. Anything my family prints to it on our network comes out fine. I've tried all the options under drivers to no avail.

I managed to get it to work.  When you goto print the document or whatever select printer properties, then device and change the current value of "Resolution, Quality, Ink Type" to a higher dpi, for example with my printer I set it to "600 dpi, Color, Color Cartr." and it worked.  I have to do this with every new document until it's saved though.   This might work for you also.

- Chris

---

### Post by altonbr on 2007-07-10
Yeah, I used gnome-cups-manager and [http://localhost:631](http://localhost:631) with my Grandmother's HP Deskjet F340 and Ubuntu Dapper Drake (6.06.1) and is STILL prints grayish.

It's pretty hard on her old eyes, so I'd like to get this fixed ASAP.

My Brother MFC-8440 has similar options and it worked setting it to 300dpi or draft, etc. I wonder if it has to do with the hplip system driver installed.

I was considering upgrading her to Feisty (even though it doesn't have LTS), but you say it still prints gray eh?

I'll see what I can come up with. I think I used a custom-installed hplip-1.6.12 driver, so I'll see what the repositories have for me.

---

### Post by altonbr on 2007-07-10
Well, it's STILL gray, but if anyone is interested, the hplip download page is: [http://sourceforge.net/project/showfiles.php?group_id=149981&package_id=165777](http://sourceforge.net/project/showfiles.php?group_id=149981&package_id=165777)

PS: I upgraded from 1.6.12 (2006-12-16) to 2.7.6 (2007-06-22) [don't ask my why their versioning skips from 1.7.4a to 2.7.6] and it's still the same game.

---

### Post by 11hjpphty76lkjj on 2007-07-11
You should have an option for 600 dpi black, do you not have it?  You can also change the print options from the hp-toolbox.  Just run hp-toolbox, and click on print settings.

A

---

