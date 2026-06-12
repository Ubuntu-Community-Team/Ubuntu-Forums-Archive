---
title: "Can't click or type after resuming from suspend in Xenial"
date: 2016-04-24
forum: General Help
---

### Post by unflavored on 2016-04-24
I installed 16.04 on a HP Compaq nc6000. I am using Gnome Flashback Session (Metacity) because [Compiz is even worse.]("http://ubuntuforums.org/showthread.php?t=2321590") But I still have a problem with suspend in Metacity.

After waking from suspend, I can't click on anything or type. The cursor does move around, and if the screen is shut off due to inactivity, then pressing a key will turn the screen back on, but key presses don't do anything else.

I have tried [these workarounds:]("http://www.bleepingcomputer.com/forums/t/569703/fix-keyboard-and-mouse-freeze-after-suspend-in-ubuntu-1404-tip/") 
```
sudo apt-get install --reinstall xserver-xorg-input-all
```

```
/etc/systemd/logind.conf HandlePowerKey=ignore
HandleSuspendKey=ignore
HandleHibernateKey=ignore
HandleLidSwitch=ignore 
```

Didn't work. Any suggestions?

---

### Post by RobGoss on 2016-04-24
Have you try changing your Gnome session to the default one

I have seen a few post with people using Flashback Session -Metacity [COLOR=#000000]and they all seem to be having this issue[/COLOR]

---

### Post by unflavored on 2016-04-24
Unfortunately if I use the default (Compiz), I have what I consider an [even worse bug:]("http://ubuntuforums.org/showthread.php?t=2321590") if the screen turns off for inactivity, it never turns back on.  Suspend is not entirely reliable in Compiz either.

---

