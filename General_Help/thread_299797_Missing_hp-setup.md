---
title: "Missing hp-setup"
date: 2006-11-14
forum: General Help
---

### Post by madcap_magician on 2006-11-14
I'm struggling to get an HP Laserjet 3020 set up.  This is on a dapper server install so I don't have the luxury of doing it with Gnome's printer gui.

According to this page:[http://hplip.sourceforge.net/install/step4/setup/local.html](http://hplip.sourceforge.net/install/step4/setup/local.html)

after installing hplip which I did with `apt-get install hplip` I should be able to use `hp-setup -a` to automatically detect my printer (which is plugged into a usb port).

I can't find hp-setup on my system.  Is this not installed by the ubuntu package or is the documentation inaccurate?

---

### Post by tajreed on 2006-11-14
did u try a command line in console. hp-setup -a

---

### Post by madcap_magician on 2006-11-14
Using tab completeion on `hp` I get the following options.

```


madcap@revolution:~$ hp
hp-align     hp-colorcal  hpiod        hp-makeuri   hp-print     hpssd        hp-toolbox
hp-clean     hp-info      hp-levels    hp-photo     hp-probe     hp-testpage  hp-unload
madcap@revolution:~$ hp



```

---

### Post by koenn on 2006-11-14
did you also do steps 1 and 2 (install additional required packages ...) ?

---

### Post by tajreed on 2006-11-14
use hp-toolbox

---

### Post by fragos on 2006-11-14
Give hp-toolbox a try.

---

### Post by madcap_magician on 2006-11-14
Does hp-toolbox require a gui?  I don't have any window system installed at the moment.

---

### Post by tajreed on 2006-11-14
I have hplip and just tried HP-setup. It required my password, sudo, but then it came right up. Toolbox does require a GUI. Did u install HPLIP from the repos? That is where mine came from.

---

### Post by madcap_magician on 2006-11-14
Yes, I did `sudo apt-get install hplip`.

Where is hp-setup located for you?

---

### Post by tajreed on 2006-11-14
I just typed "sudo HP-setup" in a Terminal

---

