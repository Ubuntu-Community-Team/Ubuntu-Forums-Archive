---
title: "Help! Ubuntu screen is frozen at installation :/"
date: 2022-02-19
forum: General Help
---

### Post by wazzup45 on 2022-02-19
Hi! New user here was installing Ubuntu 20.04 on my Dell XPS, when I accidentally took the usb out by accident. This was during the part of the process where you clicked on “Try Ubuntu” or “Install Ubuntu.”
This caused my screen to freeze and now I can’t click on anything or use my keyboard. They only thing I can do is move my mouse. :/ anyone know any fixes to this? Help a newb out, ty.

---

### Post by grahammechanical on 2022-02-19
Some more information, please

What option did you choose? Try or Install? If you chose install, what option did you choose? Erase disc and install Ubuntu, install alongside or something else? If you were installing Ubuntu at what point in the install process did you remove the USB stick?

The Ubuntu live session runs in system memory but it needs to access data on the USB stick. Removing the USB stick they way you did may have damaged the file system on the USB stick so that Ubuntu on the USB is now unusable.

You have options. You can try pressing Ctrl + Alt + Del. And wait to see what happens. You can switch off the machine and reboot and see what happens. You can plug the USB stick back in to see what happens.

Regards

---

### Post by ActionParsnip on 2022-02-20
Test your RAM health as a good first step. Also make sure you check the installation media integrity

---

### Post by MAFoElffen on 2022-02-20
> **wazzup45 said:**
> Hi! New user here was installing Ubuntu 20.04 on my Dell XPS, [COLOR=#ff0000]when I accidentally took the usb out by accident. This was during the part of the process where you clicked on &#8220;Try Ubuntu&#8221; or &#8220;Install Ubuntu.&#8221;[/COLOR]
This caused my screen to freeze and now I can&#8217;t click on anything or use my keyboard. They only thing I can do is move my mouse. :/ anyone know any fixes to this? Help a newb out, ty.
LOL. Just reboot the computer and try again... Meaning, turn off the computer and turn it on again. Start over.

You removed the USB Flash drive in a place where it was not writing anything to your computer, it would have been trying to load temporary system files. And at that point in the USB LiveCD media, the filesystem of such is in a read-only state for the USB thumb drive (it would have not been writing to the USB thumb drive)... Luckily, no fault no harm (there). Please do not make a habit of this, as other places would have meant differently.

Other's suggestions? I don't think they read your post carefully, and might have mistaken what you said. No disrespect meant to anyone at all. Just what I understand of the LiveCD process, and what I saw and read in the OP's post. Odds are, everything is fine.

---

