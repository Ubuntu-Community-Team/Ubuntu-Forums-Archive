---
title: "Ubuntu freezes up when loading."
date: 2008-04-10
forum: General Help
---

### Post by svenofix on 2008-04-10
I recently was able to dual boot Ubuntu with WinXp instead of using Wubi. So I
had to do all those updates from the Update Manager again. And since the only place I can get for High
 Speed Internet is in school, I had to let the updates download there. However when it was about half
way through the installation process I had to go to my next class. This meant shutting down my
 computer, and I didn't know how to stop the installation process so I had to kill my laptop (jam the power
button into oblivion) which was probably a bad idea. However, later when I started my computer up again and selected Ubuntu from the
grub menu, it froze about 3/4 through the loading bar and switched to a page full of loading commands 
(If that's what you call it) which successfully loaded. However at the bottom it says starting up"conexant
 modem" and just stays there.

Can anyone help? Do I have to use the recovery mode? And if so how do I use it?

---

### Post by ryanhaigh on 2008-04-10
maybe try booting into recovery mode and using apt-get install -f to fix all the packages left partially installed. Turning off a computer like that is never a good idea there is always a way to cancel an update, for example if you do it in the terminal you can use ctrl+c to cancel basically any operation.

---

### Post by -Zeus- on 2008-04-10
You most likely totally killed your install... pulling the plug is never a good idea.  Doing that while installing an OS is infinitely worse.

---

### Post by svenofix on 2008-04-10
I tried using apt-get install -f, but that didn't work  me. I did eventually somehow get into Ubuntu through the recovery mode. The most likely problem was that I had selected a package to be installed from synaptec called mwavem which didn't want to be installed and thus stopped Ubuntu from booting up.

---

