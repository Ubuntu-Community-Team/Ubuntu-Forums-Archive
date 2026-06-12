---
title: "Lubuntu 13.10 Waking from suspend after lid close double take"
date: 2013-10-31
forum: General Help
---

### Post by hi_jact on 2013-10-31
First post, so if I violate any protocols, or this is the wrong place to ask, please lemme know. :)

So I semirecently updated to Lubuntu 13.10 on my netbook. Since I originally started using Lubuntu 13.04, I've had it set to suspend on closing the lid. Before the update it worked as expected. Open the lid, hit the button, type in the password, hit enter, go.
 
After the update, when I open the lid and hit the button it starts as normal, and then at the login screen, it suspends again. I have to hit the button a second time, upon which it shows up the login screen and behaves normally. 
What make it more strange is that if I use the shutdown menu to suspend, it works fine. Normal preupdate sequence, even if I close the lid after its suspended. 
The fact it worked fine before the update makes me think its less likely to be hardware. I also don't think its the specific program handling the log in because it happened both with xscreensaver (which I was under the impression the update removed :-? ) and lightDM and/or light-locker, not sure which took over after I uninstalled xScreensaver. Relatively new to linux in general so I'm having trouble diagnosing the issue.

Sorry if this has been resolved before, tried to search for the issue, but it was difficult to phrase.

Thanks in advance.

---

### Post by Toz on 2013-10-31
Hello and welcome to the forums.

I believe lubuntu uses xfce4-power-manager. In 13.10, systemd handles lid events. The problem is that xfce4-power-manager has not been patched to work with systemd, so you end up with two systems handling lid events - hence the double-suspend. Bug reports [here]("https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1222021") and [here]("https://bugzilla.xfce.org/show_bug.cgi?id=9335"). You have two possible workarounds until xfce4-power-manager is patched:

1. In xfce4-power-manager, disable all lid event handling and let systemd do it. These are the "When laptop lid is closed" options in xfce4-power-manager settings.

2. Disable systemd lid handling. In **/etc/systemd/logind.conf**, change the line that reads:
> #HandleLidSwitch=suspend
...to read:
```
HandleLidSwitch=ignore
```
...and reboot.

---

### Post by hi_jact on 2013-10-31
> **Toz said:**
> Hello and welcome to the forums.

1. In xfce4-power-manager, disable all lid event handling and let systemd do it. These are the "When laptop lid is closed" options in xfce4-power-manager settings.



This was the simplest and worked perfectly. Many thanks!

---

### Post by gene475001 on 2014-07-20
I'm having the same problem with Xubuntu 14.04.  Unfortunately this solution doesn't work.  I tried it and the result was that my laptop would no longer supsend when I closed the lid.  The screen still goes blank and I have to type or move the mouse to get it to come on.  As soon as I enter my password the screen goes blank and won't come back on.  I tried rebooting several times with the same result.  I'm running Xubuntu 14.04 with an Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller on my Lenovo T61.  The problem doesn't appear to be an issue with Gnubuntu or Kubuntu 14.04.  I've also tried an install with the standard Unity interface and had no problems.

I managed to find a temporary solution.  If I lock the screen before closing the lid I'm fine.  I MUST remember to lock the screen EVERY TIME or I'm stuck rebooting and lose what I was working on.  BTW, this is a fresh install of Xubuntu 14.04.

---

