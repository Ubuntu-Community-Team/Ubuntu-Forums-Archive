---
title: "Wubi help"
date: 2008-04-04
forum: General Help
---

### Post by ekmon1582 on 2008-04-04
When I start Ubuntu (Wubi) it starts Heron, and it says 'installing system'. does that mean it's trying to delete windows and install Ubuntu? Or does it just mean it's installing Ubuntu so I can dual boot?

---

### Post by eriqjaffe on 2008-04-04
> **ekmon1582 said:**
> When I start Ubuntu (Wubi) it starts Heron, and it says 'installing system'. does that mean it's trying to delete windows and install Ubuntu? Or does it just mean it's installing Ubuntu so I can dual boot?It's installing so you can dual boot.

---

### Post by ekmon1582 on 2008-04-04
So there's no reason for me to worry about losing anything right? Thanks for the reply by the way. Also, when I want to get rid of it, all I have to do is boot my PC in windows and get rid of Wubi? And that'll take care of all of it right?

---

### Post by eriqjaffe on 2008-04-04
Yep.  WUBI just creates a file on your hard drive (in c:\ubuntu or c:\wubi) and mounts that as a volume when you boot into Ubuntu by modifying your hidden boot.ini file.  When you remove Wubi from Add/Remove Programs, it'll remove that file/directory and undoes its changes to boot.ini.

---

### Post by ekmon1582 on 2008-04-04
Alright, thank you very much for all your help!

---

### Post by gpilkay on 2008-04-04
I highly recommend using Wubi's own section of the forum:

[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

It's a great product, but like all open-source, has its interesting quirks, like not booting at all if you do a hard shutdown or try to hibernate, but it's easily fixed, too.

It's under '3rd party projects' too, jus tin case the link number changes.

---

### Post by ekmon1582 on 2008-04-04
Oh didn't notice Wubi had it's own section. When you say not booting at all, do you mean my computer, or just Ubuntu?

---

### Post by eriqjaffe on 2008-04-04
> **gpilkay said:**
> I highly recommend using Wubi's own section of the forum:

[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)Why, oh, why, is that buried under "Ubuntu Forums > The Ubuntu Forum Community  > Other Community Discussions  > 3rd Party Projects  > Projects"?  Considering that WUBI is part of the LiveCD, that forum really deserves to be brought to the fore - at least move it up to the "3rd Party Projects" section so it's visible from the forum's main page...

---

### Post by ekmon1582 on 2008-04-04
Indeed, last question I have, do I need to make a backup (disc image) of Windows? Or do I not have to worry that anything will go wrong and do something to Windows? I can't lose or mess up Windows at all.

---

### Post by eriqjaffe on 2008-04-05
> **ekmon1582 said:**
> Indeed, last question I have, do I need to make a backup (disc image) of Windows? Or do I not have to worry that anything will go wrong and do something to Windows? I can't lose or mess up Windows at all.You shouldn't **need** to make a backup, but it's never a bad idea before makng any significant changes to your system.  I do Windows tech support for a living (oh, the irony), and imaging has been one of the best ways of disaster recovery.

---

### Post by ekmon1582 on 2008-04-07
How would I go about making an image? Of Windows?

---

