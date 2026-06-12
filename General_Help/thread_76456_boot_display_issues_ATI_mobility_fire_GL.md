---
title: "boot display issues ATI mobility fire GL"
date: 2005-10-15
forum: General Help
---

### Post by redeemingspirit on 2005-10-15
Hey all,

I'm having problems troubleshooting this issue.  Last release of Ubuntu installed fine on my IBM tpad t42p.  It's got an ATI mobility fire GL T2 card in it.  I installed one of the pre-releases of the windy whiskered beast and the install went fine, but once I rebooted, the screen went black when the fancy new boot screen came up, and there was no HDD or processor activity.  I thought I'd wait for the official release, and see what happened.

With the new official release, I can't even install!  The disk boots, and eventually the screen goes black and there's no activity at all.  Positive it's not an issue with the laptop, since I can boot the other OS ok, and I've installed several other distros with no problems.

Once the screen blackens, I can't CTRL-F? to any other console screens or anything, the box just seems dead, even though my little power light indicates the system is on.

Any guesses?

---

### Post by tielie on 2005-10-15
This has bto do with the usplash thingy

change this in grub conf file:


By remove splash option in /boot/grub/menu.lst


[QUOTE=redeemingspirit]Hey all,

I'm having problems troubleshooting this issue.  Last release of Ubuntu installed fine on my IBM tpad t42p.  It's got an ATI mobility fire GL T2 card in it.  I installed one of the pre-releases of the windy whiskered beast and the install went fine, but once I rebooted, the screen went black when the fancy new boot screen came up, and there was no HDD or processor activity.  I thought I'd wait for the official release, and see what happened.

With the new official release, I can't even install!  The disk boots, and eventually the screen goes black and there's no activity at all.  Positive it's not an issue with the laptop, since I can boot the other OS ok, and I've installed several other distros with no problems.

Once the screen blackens, I can't CTRL-F? to any other console screens or anything, the box just seems dead, even though my little power light indicates the system is on.

Any guesses?[/QUOTE]

---

