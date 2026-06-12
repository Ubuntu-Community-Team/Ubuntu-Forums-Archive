---
title: "Video Card incompatibility (ATI X800 Pro)"
date: 2007-01-26
forum: General Help
---

### Post by geekusa on 2007-01-26
Hey. I just finished installing Ubuntu Edgy Eft 6.10 from an alternate install CD because the regular install CD could not configure my video card (256MB x800 pro ATI) during installation. I was told to use the alternate install CD because it would enable me to configure my video card after the installation. So my problem is that when Ubuntu is booting it just freezes and I have these (green, red) lines through my screen and Ubuntu's progress bar stops near the end. I think it's my video card, don't know. Can anyone help me with this? How do I go about configuring my video card so that it's compatible with Ubuntu?

Thank you.:o

---

### Post by bward1 on 2007-01-26
I think that your problem is probably in your X server configuration.  I have an ATI X800XL and it works (for the most part).  Try hitting ctrl-alt-F1 and see if that brings you to a terminal, if so, then it is your x config that is bad.

I used the regular (Live) CD for my install and it worked fine.  I suggest you give that a try if you haven't already.

---

### Post by igknighted on 2007-01-26
> **geekusa said:**
> Hey. I just finished installing Ubuntu Edgy Eft 6.10 from an alternate install CD because the regular install CD could not configure my video card (256MB x800 pro ATI) during installation. I was told to use the alternate install CD because it would enable me to configure my video card after the installation. So my problem is that when Ubuntu is booting it just freezes and I have these (green, red) lines through my screen and Ubuntu's progress bar stops near the end. I think it's my video card, don't know. Can anyone help me with this? How do I go about configuring my video card so that it's compatible with Ubuntu?

Thank you.:o

I also have an x800 and this is what I did to get it working:

1) install via the alternate CD

2) boot into recovery mode from the GRUB menu

3) issue these commands one at a time:
```
aptitude update
aptitude install xorg-driver-fglrx
aticonfig --initial
```

4) reboot into the normal system, should be good to go

---

