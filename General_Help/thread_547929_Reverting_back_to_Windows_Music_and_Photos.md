---
title: "Reverting back to Windows: Music and Photos"
date: 2007-09-10
forum: General Help
---

### Post by Marziepants on 2007-09-10
Hi, I used Ubuntu for a while, but have now gotten a new laptop with Windows XP and had my system with Ubuntu taken away. Before losing the system, I copied all my music and photos onto a memory stick with the view of saving these documents.

However, when I went to put these files onto my XP system, I got a message saying "Cannot copy file: cannot read from the source file or disk". Also, when I open the main folder to see what's inside, I see inaccessible folders named "{(É&#9492;Âul.&#9556;	" and the likes. 

Is there any way that I can save these files? Some way to change the encryption or something?

(If any sympathy vote is needed, every picture of my dead cat is stored somewhere within these files :( )

---

### Post by idauto-john on 2007-09-10
A quick test to see if it's a linux thing (fs?) is to load ubuntu on the new laptop using the LiveCD.  Once ubuntu is up, plug in the USB key in and see what it shows.

Hopefully, you can read the files.  In order fot ubuntu to be able to write to it and for windows to read it, the file system on the usb key must be vfat.  I've never seen it not be that, but weird things can happen.

That should be your first thing to try (loading the liveCD).  If that can read it, you'll at least know your data is safe.  as for how to get it off, you've got options.  Burning a CD or DVD would be simple and self contained.  Others would be an external HD or another USB key.

hope that helps and good luck

also, once you get them, i recommend burning DVDs every 6 months or so, just to be safe.  You never know when an HD may crater.

---

