---
title: "Meaning of AMPD, ACPID and other notebook realated stuff on desktop..."
date: 2008-03-11
forum: General Help
---

### Post by 6205 on 2008-03-11
I'm little confused, what's the meaning of apmd or acpid in ubuntu ? Is necessary to have both these services installed and enabled ? Have they any advantage on deskop PC or are they useful only for notebooks ?

I have removed many notebook related packages from my Gutsy, like [COLOR="Blue"]acpi, acpid, apmd, pcmciautils, laptop hotkeys, laptop-mode-tools, powernow[/COLOR] or [COLOR="Blue"]radeontool[/COLOR] to minimize start-up services and speed up my system.

As far i can tell after 3 days, there's no noticeable difference in overall functionality of my desktop pc and many services are removed/disabled with BUM (Boot-Up Manager)

---

### Post by justleen on 2008-03-11
some packages are usefull on a desktop as well.

If you want to suspend your desktop, you will need APMD.
if you have  a keybaord with shortcuts, (i think) you need the laptop hotkeys 

If you want to know what the deamons do: man is your friend

```

$ man apmd
$ man acpid
$ man pcmciautils
etc

```

---

### Post by 6205 on 2008-03-11
Hmm...thanks for info...I wish only if ubuntu live cd installer give me option to choose from Desktop PC installation or Portable PC/Notebook optimized setup and if i select desktop, some packages will be skipped and OS services little tweaked for performance...On maybe this should do some post-install script before you restart away from live cd and boot from hdd.

Regarding laptop hotkeys, i believe i don't need that package, because some special button on my MS Natural KB 4000 don't work anyway and the rest is working without problems, configured in default gnome keyboard shortcuts settings GUI.

Also i don't need to suspend or hibernate my desktop, and i have in gconf-editor also turned off those options in turn-off screen (btw. with switch user too...)

---

### Post by 6205 on 2008-03-20
Today i had observed, that without these packages don't work power button on my desktop pc. Before that it was working the way i configured it, e.g. pressing power button has shut down pc or gave mi options what i want to do, but now nothing happens and only way to shutdown pc is click on power button on panel or in menu...

I can live without that feature :) but if you remove those packages, you should know that it will not work.

---

