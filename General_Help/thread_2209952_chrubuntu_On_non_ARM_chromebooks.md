---
title: "chrubuntu On non ARM chromebooks"
date: 2014-03-08
forum: General Help
---

### Post by rodolfo5 on 2014-03-08
Is it possible to install Ubuntu, through chrubuntu, in any non ARM chromebook? eg, the Toshiba cb30 or the HP 14. If so, I find no information of this two laptops running Ubuntu , how battery handles or any problem it may occur. Is it the same for all chromebooks non ARM, meaning, they all can run Ubuntu 13 with the same problems (suspend glitch)?

Regards to all the readers

---

### Post by endlessinstant on 2014-03-08
You can use chrubuntu on any of the Chromebooks.  There are actually different scripts depending on which model you have, though the information isn't well organized on the blog. If you have a newer chromebook that supports legacy boot (both the toshiba and HP 14 have this), you might be better to use legacy boot which loads a traditional BIOS and will let you boot a live USB and install Ubuntu without having to use any script voodoo like chrubuntu

Do you want to completely replace Chrome OS on your chromebook or would you rather dual boot?

---

### Post by rodolfo5 on 2014-03-08
Replace, I don't plan on using Chrome OS.

Thank you for the info.

---

### Post by rodolfo5 on 2014-03-08
So this means, if I get the new Toshiba cb30 (for example) and I go for an installation of Ubuntu, the installation will be as a regular computer. Yes?

---

### Post by leclerc65 on 2014-03-08
DON'T. You might run into driver problems.
Follow the Chrubuntu written specifically for Intel processor [here]("http://chromeos-cr48.blogspot.ca/2013/10/chrubuntu-for-new-chromebooks-now-with.html").

---

### Post by endlessinstant on 2014-03-08
[This is for Arch Linux on the Acer C720]("https://wiki.archlinux.org/index.php/Acer_C720_Chromebook") but the procedure is the same.   Enable dev mode, use the CLI to enable legacy boot.   

Beforehand make sure you have a Live USB.  I'd also recommend you burn a Chrome OS recover using chrome://imageburner in case you ever need to replace Chrome OS.   

Once dev mode is enabled, you hit CTRL+L at the boot screen to load into SeaBIOS.   SeaBIOS lets you boot from a Live USB to do the initial install (I believe you need to turn on USB booting as well, but don't quote me on that).   

leclerc65 is right that you might run into driver issues.  Toshiba is fairly new so not well documented yet if you have to start troubleshooting.   The chrubuntu script should take care of that stuff for you since certain fixes and other things are wrapped into the install be default that might not be available from a traditional install.

---

