---
title: "GParted Live CD Not Working"
date: 2006-11-10
forum: General Help
---

### Post by EGE-FB on 2006-11-10
Hi everyone, I'm new to this forum, so I apologize if I have opened this thread in the wrong place. 

My problem is that I wanted to partition my hard drive by using the GParted Live CD. I downloaded the .iso image of the latest version, burnt it on a CD-RW. I set my BIOS to boot from CD. When I restarted my computer, everything worked fine. The Live CD booted up and I went on to selecting Language, Keyboard lay-out, Color Depth and Screen Resolution. This is where everything stopped working. After selecting the screen resolution, after a few seconds, the screen turned black and nothing appeared on the screen for a long time. The CD even stopped spinning inside the CD-Drive. I burnt the image at the lowest speed possible so therefore there shouldn't be any problems there (I even tried erasing the disc and re-burning the image but that didn't help either). I can never get past the Screen Resolution part. Could it be because I burnt the image onto a CD-RW? 

Any help would be appreciated. :neutral:

---

### Post by K.Mandla on 2006-11-10
I don't know for sure, but if the screen stays black, it might be some kind of incompatibility with your video card. It's hard to say.

You might try asking on the [GPartEd forums]("http://gparted-forum.surf4.info/").

---

### Post by rsambuca on 2006-11-10
What settings are you using for the screen resolution input.  I found it best just to go with the default on the menu even if it was a little low.  When I selected a higher resolution with my system, the screen was kinda screwed up (but not black).

---

### Post by Sef on 2006-11-10
Did you md5sum the download?

---

### Post by ciscosurfer on 2006-11-10
Stick with the default options when prompted and then move your mouse around when you think it's loaded (when your screen goes black...sometimes monitors will go dark when there is no activity for awhile)

Also, try burning a new ISO, at a lower speed to see if that helps.  Try using a regular CD or DVD as well.

---

### Post by EGE-FB on 2006-11-11
Yep, found the answer to my problem. I went through the normal set up but this time I also set it up so that I had to select a video card (before it didn't have an option like this). I selected the default video card and it worked. 

Thanks everyone for your help.

---

