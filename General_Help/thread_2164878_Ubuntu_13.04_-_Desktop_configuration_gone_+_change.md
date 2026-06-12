---
title: "Ubuntu 13.04 - Desktop configuration gone + changes prevented"
date: 2013-08-02
forum: General Help
---

### Post by mQzFFMP on 2013-08-02
Dear all,

Something very strange has happened to my Ubuntu 13.04 desktop environment. First, my previous desktop configuration has disappeared and been replaced (apparently) with default settings. More specifically:

- The desktop wallpaper has been reset to Ubuntu's default
- Buttons in the Unity panel have been replaced with those which are available after a fresh installation. Their size has also been reset to default.

However, all my software (with the right settings) appeared to be working fine, so initially I thought that this was no big deal and that I could very well "rebuild" my desktop manually.

*But* then I realise that actually I can no longer change anything. Unity does not allow me to remove or add any buttons to the panel. And my attempts to change the desktop wallpaper are simply ignored.

The problem occurred after a failed bootup. I had plugged a USB HD when the system was booting up and this apparently caused the booting process to freeze. So I had to switch off the machine. But, after that, no error messages where displayed when I first booted up the system.

Any clues as to what may have happened here and how to solve it?

Thanks & regards.

---

### Post by ibjsb4 on 2013-08-02
Nope, not a clue.  But if you want, you can try the classic look.  It configures easily.

 [http://www.ubuntugeek.com/how-to-install-classic-gnome-desktop-in-ubuntu-13-04-raring-ringtail.html](http://www.ubuntugeek.com/how-to-install-classic-gnome-desktop-in-ubuntu-13-04-raring-ringtail.html)

This is for 12o4 but will give you some ideas.

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by mcduck on 2013-08-02
Check the onwership & permissions of your home directory and the configuration files...

Any files without read access could result in using default settings instead, and any files without write access would prevent you from saving your settings.

---

