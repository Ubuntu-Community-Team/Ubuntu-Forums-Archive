---
title: "Problem with BMPx"
date: 2005-10-16
forum: General Help
---

### Post by haaglin on 2005-10-16
Hi. 

I downloaded and installed BMPx for Ubuntu 5.10, but when i try to run it, i get this error message: 

*** glibc detected *** double free or corruption (fasttop): 0x083364c0 ***
Aborted (SIGABRT)

Does anyone know how to fix this?

---

### Post by christooss on 2005-10-16
try installing it through repositories

[http://ubuntuforums.org/showthread.php?t=76796&highlight=bmpx](http://ubuntuforums.org/showthread.php?t=76796&highlight=bmpx)

---

### Post by haaglin on 2005-10-17
Still the same problem :(

---

### Post by Iuliux on 2005-10-17
try to compile it.

---

### Post by christooss on 2005-10-17
NO can do. I couldn't compile it. Something vrong with taglibs

---

### Post by haaglin on 2005-10-18
I tried to compile it, no problem with taglibs, but still the same error.

---

### Post by haaglin on 2005-10-20
If i try to run it as root, i get this error:

*** glibc detected *** corrupted double-linked list: 0xb7ba9938 ***
Aborted (SIGABRT)

---

### Post by gharco on 2006-09-13
I was having a slightly better luck. Installation (through repositories) went OK, I could start the BMPx and change settings etc.

But after I picked up a song and started to play it BMPx crashed (exactly after 10 seconds) with similar
*** glibc detected *** double free or corruption ..etc
message. 

I was able to fix this by removing the selection in Preferences - Miscellaneous - Options - Display Notification popups. Afterwards BMPx has behaved perfectly.

I can't tell if this helps if you cannot get the BMPx running at all, but you can do this change directly to the BMPx's config file (/home/user/.config/bmpx/config.xml) by changing the line
<key id="display-notifications" type="boolean">TRUE</key>
to
<key id="display-notifications" type="boolean">FALSE</key>

---

### Post by christooss on 2006-09-14
Which version do you have. How did you install it?

---

### Post by gharco on 2006-09-14
> **christooss said:**
> Which version do you have. How did you install it?

It's version 0.20.3 and I installed it using instructions found from [BMPx website]("http://bmpx.beep-media-player.org/site/Downloads#Ubuntu")

But I'm using Kubuntu 6.06 now and not 5.10 anymore, so it's a bit off from the original topic.

---

