---
title: "reverse backup problems"
date: 2007-07-25
forum: General Help
---

### Post by nomad5000 on 2007-07-25
Hi everybody!
I made a backup of my linux / partition like it was said in a tutorial I found in this forum. But afterwards I repartitioned my hard drive. I untared my backup onto the new partition and reinstalled grub. Now I get the grub menu and I can select my ubuntu (to boot) but after I try to boot it It gives me the black screen with the big ubuntu logo and the bar that shows the progress but nothing more happens, that is the bar stays as it is and doesn't show any progress. What can I do to get an error message to at least be able to know what went wrong?

Any help will be greatly appreciated!!!

Michael

---

### Post by kuja on 2007-07-26
Try booting in recovery mode, or select the regular and press 'e' to edit, go to the kernel line and press 'e' on it, remove quiet and splash from the end, press enter, then press 'b' to boot.

---

### Post by HermanAB on 2007-07-26
Uhmmm... usually it is best to only backup your data and not the whole bloomin system.  You can easily install the system from scratch with the added advantage that you then have the latest and greatest system and it minimizes the amount of data to backup, which saves you a lot of time and storage media.

Cheers,

Herman

---

### Post by krismatth3 on 2007-07-26
I disagree. Whole system images are incredibly convenient. See g4u : [http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

As for the immediate problem, what happens in recovery mode?

---

### Post by kuja on 2007-07-26
More or less the same thing, except it gives the user a single, root, tty, I think it's a different runlevel too (seeing as most of the startup scripts won't be run)

---

### Post by nomad5000 on 2007-07-26
OK now I booted with all error messages, the error message ÇI get now is the following.

Check root= bootarg cat /proc/cmdline
or missing modules, device: cat /proc/modules ls /dev
ALERT! does not exist. Dropping to a shell

what does this mean??

---

