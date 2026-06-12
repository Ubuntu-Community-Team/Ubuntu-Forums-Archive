---
title: "Xkill destroyed my OS"
date: 2015-03-29
forum: General Help
---

### Post by David_OConnor on 2015-03-29
See this closed thread that was marked solved with "Reinstall Ubuntu": [http://ubuntuforums.org/showthread.php?t=1796170](http://ubuntuforums.org/showthread.php?t=1796170)

After googling how to kill an app in Ubuntu 14.10, (ie Windows' ctrl+shift+esc), I found 'xkill' in console. Used that on the sidebar icon, and now My Unity's messed up. Any progress since the thread I linked, or do I need to reinstall?

I can get to a recovery console, but the only thing I can do in the GUI is click desktop icons. No terminal with ctrl+alt+t.

apt-get install is broken too (Was working fine before the xkill incident). It can't find all the packages, regardless of which mirrors I put in sources.list. Ie i tried installig tweak utilities, unity, etc.

---

### Post by HermanAB on 2015-03-29
Overreaction much?

Xkill can stop any program.  Yes, it can even stop your whole desktop system.  

However, redemption is a mere logout and login away.

---

### Post by TheFu on 2015-03-29
+1 to HermanAB's

Killing processes is an extremely basic thing for Linux people to know and understand. There are a few ways to do it and each has a few different options (i.e. signals) to be sent to the problem program.  kill, xkill, top, htop killall, slay - each can kill processes - there must be many others.  Don't think xkill can be run at the console - it requires X/Windows.

---

### Post by David_OConnor on 2015-03-30
Rebooting doesn't fix it. Got apt-get working by selecting 'enable networking' before entering the root console in recovery mode.

Attempted fixes (didn't work) - 

sudo apt-get install unity-tweak-tool
unity-tweak-tool --reset-unity

sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity

---

### Post by dragonfly41 on 2015-03-30
In that old closed thread there was a suggestion to install gnome-session-flashback

[http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session](http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session)

and troubleshoot further from there. At least you will have a working desktop (Gnome Classic)

---

### Post by buzzingrobot on 2015-03-30
> **David_OConnor said:**
>  Got apt-get working by selecting 'enable networking'...

Yes, the package manager (apt) requires access to the repositories (servers) used by the system.

It seems much more likely that the damage -- whatever that is -- was done by whatever produced the crash that required use of xkill than by xkill itself. Xkill is a process killer.  All processes end on a reboot.

---

### Post by mc4man on 2015-03-30
I'd check that the unity plugin is enabled & the profile is set to unity in compizconfig-settings-manager (ccsm), the profile is set in ccsm > preferences, should be set on unity
Or start with a fresh default dconf settings. To do that, (the dconf user file can not be replaced in your normal session - 
boot up, go to a vt ( ctrl+alt+F3
login in
use these 2 commands, replace red with your actual username - 
```
mv /home[COLOR="#FF0000"]/username[/COLOR]/.config/dconf/user /home/[COLOR="#FF0000"]username[/COLOR]/.config/dconf/user.bak
```
```
sudo reboot
```

---

### Post by David_OConnor on 2015-03-30
> **mc4man said:**
> 
Or start with a fresh default dconf settings. To do that, (the dconf user file can not be replaced in your normal session - 
boot up, go to a vt ( ctrl+alt+F3
login in
use these 2 commands, replace red with your actual username - 
```
mv /home[COLOR=#FF0000]/username[/COLOR]/.config/dconf/user /home/[COLOR=#FF0000]username[/COLOR]/.config/dconf/user.bak
```
```
sudo reboot
```
Thanks bro; you fixed it.

---

