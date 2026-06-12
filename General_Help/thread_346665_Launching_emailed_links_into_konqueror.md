---
title: "Launching emailed links into konqueror"
date: 2007-01-26
forum: General Help
---

### Post by pseudo_nz on 2007-01-26
I've been using Kmail with Firefox for several months, and want to give konqueror a go.  Importing bookmarks etc is fairly straightfoward, but getting kmail to co-operate seems to be more difficult.

I've gone to KDE components in System Settings and set Konqueror as the preferred application for internet access, but when I tried opening a link from an email Konqueror got stuck in a loop and I had to reboot (it slowed the computer down so much that I couldn't open a terminal to see what was going wrong).

I found one thread relating to this, [http://www.ubuntuforums.org/showthread.php?t=81893&highlight=opening+links+in+konqueror](http://www.ubuntuforums.org/showthread.php?t=81893&highlight=opening+links+in+konqueror) which suggested that things weren't as easy as they looked.  I followed the instructions in that thread, and now when I click a link a box appears, showing the progress of the link, which then opens - in firefox.

I've put firefox back in as the preferred component for now, but the progress box is still appearing (and seems to slow down the whole process).  I would like to try konqueror as a web browser, but would be happy at this point just to get rid of the popup progress box.

Cheers for any help with this.

---

### Post by bionnaki on 2007-01-26
open up the terminal
and enter the following command:

sudo update-alternatives --config x-www-browser

and follow the prompt

---

### Post by pseudo_nz on 2007-01-26
Thanks for the advice.  According to the prompt, konqueror was already the default, but I tried it anyway.  It changed the setting in System Settings - KDE Components from firefox to 'in an application based on the contents of the URL', but when I tried it, Firefox was still the program that opened.

I've unchecked the 'Make Firefox the default browser' in the firefox options, but not sure if there's still something I've missed.

Thanks anyway - guess I'm stuck with Mozilla for a while yet (not that there's anything wrong with that, lol).

---

