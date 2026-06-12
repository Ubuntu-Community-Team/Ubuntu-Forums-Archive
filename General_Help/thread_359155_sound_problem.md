---
title: "sound problem"
date: 2007-02-11
forum: General Help
---

### Post by mmoalem on 2007-02-11
hi there all - having a problem with sound, it seems to work at its own will... one boot it will and the next boot it wont. dont have a clue where to start diagnosing it...
hardware is intel laptop core2duo gma950 chipset (says something about HDA sound)
os is kubuntu with ubuntu-desktop installed and booted into ubuntu
cheers
michel

---

### Post by r4ik on 2007-02-11
Try,

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

or

[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide)

Good luck !

---

### Post by mmoalem on 2007-02-14
hi there and thanks for the info. unfortunatly it did not work...
i added the line to /etc/modules as suggested so it looks like that:

lp
sbp2
fuse
options snd-hda-intel model=m2-2

but after several reboots it again stoped producing sound

device manager indicates that the soundcard is intel 82801g (ICH7 family)
and something about sigmatel chipset...

any more ideas?

---

### Post by Ricky Yong on 2007-02-14
Try this.
Typed in "man alsamixer" at the Terminal screen

Read thru the manual...if you need help....email me at [email]cwyong1@streamyx.com[/email]

Chao

---

### Post by mmoalem on 2007-02-14
hi there and thank you very much for the advice and willingness to help... i have looked at the man file and cant really see how it solves my problem. i should say that i have installed alsamixergui and it works fine without throwing any errors so i dont think its an alsa issue. the fact that sounds work on some boots and not on others and when it doesnt work it simply an issue of no sound coming out of the speakers or headphones but mixer loads fine with no errors suggest to me that at the boot process something doesnt load correctly...
cheers
michel

---

