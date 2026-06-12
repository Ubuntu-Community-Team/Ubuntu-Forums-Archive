---
title: "firefox crashes"
date: 2006-10-10
forum: General Help
---

### Post by antimatter on 2006-10-10
hi, ive been using firefox on ubuntu for about two years now. never had any problems at all, but today after the update my firefox started to crash when loading certain websites. the console output looks like this

stefan@ky:~$ firefox
NP_Initialize
New
SetWindow
/usr/lib/firefox/firefox-bin: symbol lookup error: /usr/lib/mozilla/plugins/libflash-mozplugin.so: undefined symbol: XtWindowToWidget


anyone got an idea on how to fix this?

---

### Post by hw-tph on 2006-10-11
That's the free Flash plugin acting up. You can remove it by running **sudo apt-get remove libflash-mozplugin**. You can use Macromedia's (now Adobe's) own Linux plugin (package name flashplugin-nonfree) instead if you can stand the license.


Håkan

---

