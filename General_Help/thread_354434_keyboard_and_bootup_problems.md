---
title: "keyboard and bootup problems"
date: 2007-02-06
forum: General Help
---

### Post by JacksonL on 2007-02-06
Hello! I've just installed (after much toil) Ubuntu on a friend's computer. I set up a dual-boot for him on two partitions (the other is Windows XP Home). The only problem I had with installing was that the keyboard, regardless of what I did, would *not* work while using the Edgy i386 LiveCD. I got around that obstacle by copy/pasting information and changing stuff later via the mouse, but now that it's installed the keyboard only works sporadically. Sometimes when I boot it up the keyboard will work, and other times it will not. Adding to the problem is the fact that only about 1/8 of the time I boot into Ubuntu does it start -- every other time the computer decides to restart itself. This does not happen with his Windows XP. The only semi-relevant problem I know of is that his BIOS thinks there's something wrong with his CPU and he has to press F1 every time he boots to get past a weird diagnostic screen.

Does anyone have any idea how to fix this horrible problem?

---

### Post by MoLE on 2007-02-11
What kind of keyboard is it? USB or PS/2 connector.  If it is a USB keyboard, you most likely need to have legacy USB keyboard support enabled in the BIOS.  It's possible that that 'weird diagnostic screen' at bootup is a BIOS error saying 'no keyboard detected', which is likely if it is a USB keyboard. 

If you can't enable legacy USB keyboard support in the BIOS for this machine, you can work around the problem with a cheap PS/2 keyboard.

---

