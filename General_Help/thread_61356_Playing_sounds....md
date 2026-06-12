---
title: "Playing sounds..."
date: 2005-08-31
forum: General Help
---

### Post by Elrohir on 2005-08-31
ok, here's the deal...

I want to play sounds on GAIM... but when I read GAIM FAQs, they say to use some command that I have to implement by downloading the source and compiling from scratch... hell no! [-X

but when I put  ```
xmms %s
``` it plays on XMMS which is good... \\:D/

is there an inline sound player? that just plays the sound, no GUI, no nothing.. just plays the sound and ends??

---

### Post by adamsnoopy on 2005-08-31
If you have alsa, you can do this:

aplay %s


Works for me.

Adam

---

### Post by Elrohir on 2005-08-31
hmm... have the following alsa packages installed:

alsa-base
alsaplayer
alsaplayer-alsa
alsaplayer-common
alsaplayer-gtk
alsaplayer-oss
alsa-utils

but still no sound...

---

### Post by alphonce on 2005-09-08
I have the same problem, it used to work with aplay %, but no more.
everything else sounds fine, must be a gaim related problem.

read this bug to fix the problem.
[http://bugzilla.ubuntu.com/show_bug.cgi?id=14954](http://bugzilla.ubuntu.com/show_bug.cgi?id=14954)

---

### Post by rafakl on 2005-09-08
Thats a very bad bud.

I can hear xmms playing my mp3, but if i do that gaim stops playing sounds.

And is a problem with many software, sometimes one is blocking another from using the sound.

---

