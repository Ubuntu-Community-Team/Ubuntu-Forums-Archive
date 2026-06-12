---
title: "Sound doesn't work. Will I have to format?"
date: 2007-06-26
forum: General Help
---

### Post by joy99 on 2007-06-26
Hello, I'm becoming crazy with my problem of sound. I've a SB Audigy ZS and, when I installed ubuntu sound worked fine, but after some upgrades it dissapeared. I've read posts of similar problems, but I don't reach the solution. I've tried to recompile alsa kernesl with emu10k1, I've deselected the option of "Audigy Analog/Digital Output Jack" in alsamixer, I've loaded the modules with "modprobe snd-emu10k1" manually, and it doesn't work. I don't want to format de hard disk because of this, but I can't work without the sound. So I need help. 

Do you have any idea of what can I do?

Lots of thanks.

---

### Post by aJayRoo on 2007-06-26
I have had a similar problem several times with Ubuntu 6.10 and 6.06, however not with the same sound card as you. I recall that fixing the issue was very frustrating and I tried many things but in the end I adjusted each setting in alsamixer individually until I found the cause. I'm afraid I don't quite remember what was to blame but a slow and tedious process of elimination in alsamixer may be all that is required to fix this. Good luck, I hope this advice is of some use.

---

### Post by kpkeerthi on 2007-06-26
If possible restore back to the stock alsa driver. Delete .asoundrc from you home folder and reboot and see if it helps. 

I had no sound when I "upgraded" to Feisty from Edgy. Deleting .asoundrc worked for me.

---

