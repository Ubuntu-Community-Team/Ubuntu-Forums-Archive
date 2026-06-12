---
title: "Black screen booting up &amp; Can't use virtual consoles"
date: 2008-03-15
forum: General Help
---

### Post by kevind23 on 2008-03-15
I use Debian myself and I suppose you could say I'm an 'experienced' Linux user. But I need something simple for my mother to use so I installed Kubuntu and I'm having some problems with it.

Whenever I boot up, I get a blank, black screen even though I uninstalled usplash and removed all the quiet/splash lines from my grub configuration. In addition, I can't use any of my virtual consoles -- excluding tty7 for Xorg, all the other consoles are simply black screens with a grey blinking underscore.

Any suggestions? Thanks in advance :-)

---

### Post by kevind23 on 2008-03-15
Oh, and I should mention, chvt **does** change virtual consoles but all I see is a bunch of skewed pixels from Xorg.

---

### Post by BoA CoNsTrIcToR on 2008-03-28
I installed Gutsy and had a similar problem since day1.

Blank screen while bootup and I cannot access ttys from the GUI.

Blank screen was solved by changing the /etc/usplash.conf to my required resolution and rebuilding the initramfs for the new resoultion. This was found out from one of the discussion in the community. I'm am sorry I can't find that now. :(

But the problem with the inaccessible ttys is still persisting.

---

