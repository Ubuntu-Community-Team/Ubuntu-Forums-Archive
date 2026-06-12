---
title: "&quot;Service Pack&quot;-like updates?"
date: 2007-12-01
forum: General Help
---

### Post by Lilyoftheshadow on 2007-12-01
Things seem a bit glitchy in 7.10, with OpenOffice not wanting to start anything other than Writer, Firefox crashing on popup windows and downloads, etc. Are there service-pack-like things for Ubuntu that fix glitches like these? I'm very new to Linux, and would also need a line-by-line walkthrough of how to go about installing these...

Many thanks in advance!

---

### Post by -grubby on 2007-12-01
did you check the update manager? (the orange sqare with some sort of cloudish thing in it?)

---

### Post by Lilyoftheshadow on 2007-12-01
Is that what that is?
I don't remember seeing it before, but then, I haven't booted up in Ubuntu in a few days. I'll run that through and see what it fixes. Thanks!

---

### Post by -grubby on 2007-12-01
it only appears when you have updates

---

### Post by Lilyoftheshadow on 2007-12-01
Okay, that did not help one problem at least:

OpenOffice freezes and crashes with no explanation when I try to doublespace highlighted text via Format>Paragraph. As soon as I click paragraph, it just stops. I can't find a bug report that seems to fit, and don't know what I would go about saying in a bug report.

---

### Post by paydaydaddy on 2007-12-01
Not an expert user by any stretch, but if it were me, I would uninstall/ re-install open office to see if that fixes it. It can be easily done using synaptic.

---

### Post by Lilyoftheshadow on 2007-12-01
..how easily?

I was serious in saying that I'm an absolute n00b. How would I do that?

---

### Post by -grubby on 2007-12-01
```
sudo apt-get remove openoffice
``` and then

```
sudo apt-get install openoffice
```

---

### Post by paydaydaddy on 2007-12-01
Nathangrubb has given you the codes to uninstall/re-install OpenOffice. Use the codes by opening a terminal (click "applications" then " terminal"). Cut and paste the remove command then hit enter. after the packages are removed, Then cut and paste the apt-get command and hit enter. If you are more comfortable using a graphical user interface then post back here and I'm sure you will get help in using synaptic.

---

### Post by Lilyoftheshadow on 2007-12-01
...is it seriously that easy?

Okay. So. Do I need the install CD/DVD to do the install?

Edit: Okay, so evidently it's a glitch relating to the theme, since I switched back from Crux to Human, it's alright.

---

### Post by -grubby on 2007-12-01
> **Lilyoftheshadow said:**
> ...is it seriously that easy?

Okay. So. Do I need the install CD/DVD to do the install?

no, you shouldn't

---

### Post by paydaydaddy on 2007-12-01
You do not need the install cd, but you do need to be connected to the internet to access the repositories where the installation packages are stored. This is taken care of automatically as long as you are connected to the internet.

---

