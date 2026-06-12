---
title: "mp3 and Rythmbox"
date: 2014-10-28
forum: General Help
---

### Post by pull0betty on 2014-10-28
For some reason I can't import mp3 files to Rythmbox.. they only play in the video application. Am I missing something? FLAC works fine in Rythmbox.

---

### Post by JazzPotato on 2014-10-28
Any error messages? Or do they just not play?
Did you tick "install third party plugins" at install?
You could try installing the "ubuntu-restricted-extras" package

---

### Post by pull0betty on 2014-10-28
yeah no i did not tick that at install, but when I open the file by double clicking, which will open them in the video player those third party plugins are being installed. No, as a matter of fact no error message, mouse curser shows loading for some seconds and nothing happens.. I'll look at the restricted extra package. It is not installed as I can see. I just don't want the flash-player on my System but I guess I can uninstall it later..

---

### Post by pull0betty on 2014-10-28
Installing the restricted extras just crashed software center.. btw the same happens when I add wine repo and install wine 1.7.. it crashes

---

### Post by pull0betty on 2014-10-28
ok restarting software center and it finished the package install. mp3s are still not playing. the restricted-extras also installs something about java? I hope it is not the runtime environment as I do not want that either on my system.. btw. this is a complete fresh install of Ubuntu 14.10 Gnome (just installed it this afternoon [again :])

---

### Post by pull0betty on 2014-10-28
should I dare try a reboot?

---

### Post by pull0betty on 2014-10-28
I know what causes the crash of the software center... its ttf-mscorefonts-installer, since it needs the eula to be confirmed (seems to be the same issue with wine 1.7. solution to that is uninstalling it, and installing it using the terminal where you get to confirm the eula.. unfortunately after reboot and having successfully installed the extras I still can't play mp3s in Rythmbox.. Also now the Xorg drivers for my graphics card don't seem to work anymore. Proprietary drivers work tho..

---

### Post by pull0betty on 2014-10-28
there a way to post a log file so it is readable for everybody (not just one long worm)? sry for being such a noob.. :)

---

