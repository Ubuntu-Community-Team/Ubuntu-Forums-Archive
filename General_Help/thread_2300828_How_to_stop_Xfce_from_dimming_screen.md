---
title: "How to stop Xfce from dimming screen?"
date: 2015-10-28
forum: General Help
---

### Post by william_estrada on 2015-10-28
Hello,
I installed Ubuntu then installed Xfce because of the bloat in Gnome. That is the set up.

Xfce has this feature of dimming the screen after a small amount of time.  I was to stop the dimming, how?

---

### Post by Dennis N on 2015-10-28
In XFCE, there is a brightness reduction setting, which could be activated on laptops or other devices with batteries.

[B]Settings > Power Manager > Display Tab > Brightness Reduction
[/B]
And there you find two adjustments. **Reduce after: Never** would turn the dimming off.

My Reference System: Xubuntu 14.04 (XFCE desktop environment)

---

### Post by mystics on 2015-10-28
Just in case you can't find the option, my computer has it in a different place than

> **Dennis N said:**
> **Settings > Power Manager > Display Tab > Brightness Reduction**

For me, I have to go to

**All Settings (also called Settings Manager) -> Power Manager -> [On AC]/[On Battery] -> Monitor**

The final option is a slider that will allow you to both set the time for when it will start dimming and set how much it dims by. In this case, you would need to give separate settings to both "On AC" and "On Battery". Also note that "Never" is done by pulling it all the way to the left.

 I'm not sure why my options are little different than Dennis's since I'm also running Xubuntu 14.04, but I figured I should point that out in case your settings are set up differently.

---

### Post by coldraven on 2015-10-28
AFAIR Xubuntu has something called Lightlocker in the Settings. Have a look at that.

---

### Post by Dennis N on 2015-10-28
> I'm not sure why my options are little different than Dennis's since I'm also running Xubuntu 14.04, but I figured I should point that out in case your settings are set up differently.

The interface you describe was xfce4 Power Manager 1.2.0 in the original release version. Mine is using 1.4.3 from the xfce-4.12 upgrade. 

```
dmn@Kayleigh:~$ apt-cache policy xfce4-power-manager
xfce4-power-manager:
  Installed: 1.4.3-0ubuntu1~14.04.1
  Candidate: 1.4.3-0ubuntu1~14.04.1
  Version table:
 *** 1.4.3-0ubuntu1~14.04.1 0
        500 http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu/ trusty/main i386 Packages
        100 /var/lib/dpkg/status
     1.2.0-3ubuntu4.1 0
        500 http://mirrors.xmission.com/ubuntu/ trusty-updates/universe i386 Packages
     [COLOR="#FF0000"]1.2.0-3ubuntu4 0
        500 http://mirrors.xmission.com/ubuntu/ trusty/universe i386 Packages[/COLOR]


```That would account for the difference. The older 1.2.0 version was also affected by DPMS system blanking the screen after 10 minutes for some users. This could also be the cause of the problem, and if so it can be fixed by upgrading to xfce 4.12 from the ppa and getting the newer version.

A thread on the DPMS problem:    
[http://ubuntuforums.org/showthread.php?t=2293331](http://ubuntuforums.org/showthread.php?t=2293331)

Fixed with xfce power manager version 1.4.2 or later.

---

### Post by william_estrada on 2015-11-10
Thanks for all of the replies.  I got it fixed.

---

