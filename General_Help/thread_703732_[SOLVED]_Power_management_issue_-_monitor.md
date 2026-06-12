---
title: "[SOLVED] Power management issue - monitor"
date: 2008-02-21
forum: General Help
---

### Post by meazz1 on 2008-02-21
I have my monitor set to never in power management but it still blanks out after 5 minutes of inactivity.
Do I need to set that under sudo?
If so,
What would be the command to bring up power management configuration screen?

---

### Post by prince_niceguy on 2008-02-21
it is under system --> preferences --> power management. Increase the time to whatever you like.

---

### Post by meazz1 on 2008-02-21
> **prince_niceguy said:**
> it is under system --> preferences --> power management. Increase the time to whatever you like.

I have taken it to max, but still monitor goes to sleep mode.

---

### Post by Shazaam on 2008-02-21
Does your monitor come back up if you move the mouse?
The reason I ask is my monitor will go blank after about 10 to 15 minutes of inactivity but will come back if I move my mouse. Disabled screensaver, turned power management to Never, etc. I am currently looking for a setting in the pc's BIOS as I think this may be the cause. Unfortunatly most motherboard manuals are vague when dealing with power managment settings.

---

### Post by hvacr on 2008-02-21
I have the same issue. I have all set things up to not use a screen saver, and have the screen never put to sleep. I think this is a bug in the 64 bit Ubuntu.

---

### Post by NIT006.5 on 2008-02-21
> **hvacr said:**
> I have the same issue. I have all set things up to not use a screen saver, and have the screen never put to sleep. I think this is a bug in the 64 bit Ubuntu.

Don't think it's anything to do with 64-bit. I'm having the same issue and I'm not running 64-bit.

---

### Post by meazz1 on 2008-02-21
Yes, if I move mouse, it comes right back.
I just don't like the monitor to go blank after such a short time.

---

### Post by Shazaam on 2008-02-22
It has nothing to do with 32 or 64 bit systems.

meazz1......
Thats what I thought. I think it's a bios issue pertaining to DPMS. Wiki link---
[http://en.wikipedia.org/wiki/VESA_Display_Power_Management_Signaling](http://en.wikipedia.org/wiki/VESA_Display_Power_Management_Signaling)

---

### Post by soldats on 2008-02-22
basically you have to edit your xorg.conf file and either add a Section "ServerFlags" then input some options to make the screen not blank. it should look like this

Section "ServerFlags"
        Option      "BlankTime"           "0"
        Option      "StandbyTime"      "0"
        Option      "SuspendTime"     "0"
        Option      "OffTime"              "0"
EnsSection

this should make the screen never turn off.  the "0" is the timeset value so you can edit that as well to turn off whenever you need it to. "man xorg.conf" should explain this further if you need more help. for some reason the gnome-power-manager doesnt work too well on dpms management monitors. hope this helps

---

### Post by meazz1 on 2008-02-23
> **soldats said:**
> basically you have to edit your xorg.conf file and either add a Section "ServerFlags" then input some options to make the screen not blank. it should look like this

Section "ServerFlags"
        Option      "BlankTime"           "0"
        Option      "StandbyTime"      "0"
        Option      "SuspendTime"     "0"
        Option      "OffTime"              "0"
EnsSection

this should make the screen never turn off.  the "0" is the timeset value so you can edit that as well to turn off whenever you need it to. "man xorg.conf" should explain this further if you need more help. for some reason the gnome-power-manager doesnt work too well on dpms management monitors. hope this helps

thanks, that did the trick for me.

---

