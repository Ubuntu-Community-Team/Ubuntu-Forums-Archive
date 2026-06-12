---
title: "DPMS 'Off' settings keep resetting"
date: 2007-03-27
forum: General Help
---

### Post by Rhombuss on 2007-03-27
I have my DPMS set for 'Off' at 10 minutes idle.  However everytime I restart Ubuntu, the settings revert back to 'Off: 0', and I have to "'xset dpms 0 0 600" afterwards.  This a known bug?

EDIT:  Actually, it reverts back to 'Off: 0' even before a restart, I didn't time it but it's somewhere around 2 hours and it'll revert.

---

### Post by kerry_s on 2007-03-27
put "xset dpms 0 0 600" in the session startup. I use xset dpms 0 0 300 in my session startup. If you use the screen saver or media player you might want to create a launcher with "xset +dpms dpms off" this will turn dpms back on and turn off the screen manually.

---

### Post by Rhombuss on 2007-03-27
I tried putting it in the session startup, however upon restart it still defaults to dpms 0 0 0.  Strange.

---

### Post by kerry_s on 2007-03-27
Check the power manager settings.

---

### Post by Rhombuss on 2007-03-27
It has my monitor "put to sleep" at 40 minutes.  However, this doesn't seem to be linked to my DPMS settings, since they keep showing up as 0 0 0.

---

### Post by Rhombuss on 2007-03-28
I've been searching around, and apparently most other people are having problems with DPMS automatically multiplying their timings by 5.  I haven't seen anyone else with this problem, but I'm hoping it's not an isolated case.

Any additional insight would be appreciated.

---

### Post by Rhombuss on 2007-04-01
Giving this another shot, hopefully someone knows :P.

---

### Post by PhilOSparta on 2007-04-07
Increment the count!  I also have this problem.  I can use xset dpms 0 0 60 and the screen will shut off in 60 seconds.  That's good.  Placing xset dpms 0 0 600 in the session startup hasn't worked.  Just after  boot  xset q  in the terminal shows dpms as 0 0 0.    Anyone found a fix for this yet?

Thanks in advance.

Phil

---

### Post by Rhombuss on 2007-04-07
Seems like the Power Management settings for monitor standby override the DPMS settings.  I haven't fiddled with my DPMS for about a week now (still at 0 0 0), but the Power Management has it off at 10 minutes, and it seems to work.

Would still like to know the reason for this, however :P.

---

### Post by prkfriryce on 2008-01-14
> **Rhombuss said:**
> It has my monitor "put to sleep" at 40 minutes.  However, this doesn't seem to be linked to my DPMS settings, since they keep showing up as 0 0 0.

this is appearing for me as well.  Power Management has put display to sleep @ 40 min.

xset q
```
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On

```

after 40 minutes though, the monitor turns blank with a green light, but not standby with the yellow power light.

executing `vbetool dpms off` does turn the monitor blank with yellow light.

Why isn't the power management working as configured?

**edit**

I just checked my desktop at work, and the xset q is the same:
```
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On

```

but i noticed that the DPMS is commended out:
```
$ grep DPMS /etc/X11/xorg.conf
#Option         "DPMS"
```

i'll change the xorg.conf setting onthe other machine to see if it fixes it as well.

---

### Post by prkfriryce on 2008-01-16
that didn't work.

How can I enable the gnome settings to overide Xorg?

I set Xorg with

Option "DPMS"

Section "ServerFlags"
    Option      "BlankTime" "10"
    #Option      "StandbyTime" "0"
    #Option      "SuspendTime" "0"
    Option      "OffTime" "12"
EndSection

but my monitor still only displays the blank screen and does not shut off.

---

