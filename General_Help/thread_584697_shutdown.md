---
title: "shutdown"
date: 2007-10-21
forum: General Help
---

### Post by thamood on 2007-10-21
Hi guys i have a problem which is "Ubuntu wont shutdown"!! whenever i press the shutdown button from the close dialog it logs off and then the gives me the ubuntu logo and the status bar completes the i can hear the HDD power off!! but everything else it's still working!! and it wont shut down i've waited but nothing seem to happen...anyone else having this problem? 

I've read somewhere that i should add "acpi=force" to grub ... i did still nothing happens?

HELP!!! :confused::confused::confused:

---

### Post by BrixSat on 2007-10-23
Unfortunately i have a similar problem, i am unable to shutdown, the logout button appears and when i press the monitor get black and everything is working the same! i have to take off the power or press the power button for about 7 seconds!!!! That is so stupid! I know some friends having the same problem taking me to think that this may be a major bug or something!

Im using a fujitsu siemens amilo m7405 laptop!

:(

---

### Post by anaconda on 2007-10-23
I have the same problem IF and only if my usb-TV is connected. Reboot works perfectly even then. 

Does it help if you remove your removable devices first? I think that if this is the problem then it is possible to add something to the shutdown script to unmount that device..

---

### Post by BrixSat on 2007-11-06
I have my ubuntu updated and i still cant shutdown, i have to press the power buton for 7 seconds!!!! Does any one have a solution?

---

### Post by SanskritFritz on 2008-01-28
Same problem here on my brother's AMILO M7405. Anyone can help please?
The symptom: on shutdown, the screen goes blank, but the laptop is still running, and nothing happens. He has to force switch off the machine.
Ubuntu Gutsy 7.10

---

### Post by SanskritFritz on 2008-01-29
Bump. Anyone? Please? Pretty please?

---

### Post by confused57 on 2008-01-29
You could try this:
```
gksudo gedit /etc/modules
```

add this line:
```
apm power_off=1
```

May not work, but worth a try.

---

### Post by SanskritFritz on 2008-02-01
That didn't help, sadly. Any other ideas maybe? Please, people, help us! Thanks!

---

### Post by nick_h on 2008-02-01
Try shutting down from the command line with:
```
sudo shutdown -h now
```

---

### Post by SanskritFritz on 2008-02-07
> **nick_h said:**
> Try shutting down from the command line with:
```
sudo shutdown -h now
```Thanks, so far it works! So, what is the difference then between this shutdown and the graphical button?

---

### Post by Ashrael on 2008-02-09
i have the same problem (almost) when i am working with my pc everything works, then i press the shutdown/etc button and my computer freezes, no more menus etc... the only thing i can do is :<ctrl>+<alt>+<F1>  sudo shutdown -h now.... that works, i do not think this is a mayor issue for me, but it would be nice just to be able to click a button again...

any suggestions any one, maybe the command attached to the button is somehow wrong?

---

### Post by SanskritFritz on 2008-02-14
> **SanskritFritz said:**
> Thanks, so far it works! So, what is the difference then between this shutdown and the graphical button?Well, it turned out, that there is apparently no difference between the two shutdown methods, because the
[FONT=Comic Sans MS] sudo shutdown -h now[/FONT]
method brings the same problems.
Any ideas, please?
Just to cite the problem, so you dont have to read too much:
---
Same problem here on my brother's AMILO M7405. Anyone can help please?
The symptom: on shutdown, the screen goes blank, but the laptop is still running, and nothing happens. He has to force switch off the machine.
Ubuntu Gutsy 7.10
Any help appreciated!

---

### Post by Ashrael on 2008-02-21
I have found out that it must have something to do with desktop effects... If i switch it of the beforementioned behaviour occurs, I switch on desktop effects again and it does show me the shutdown/restart etc window... It does so very slow...

HTH

---

### Post by SanskritFritz on 2008-03-30
I have to mention, that after the latest updates of Gutsy, the problem is solved on our side. The laptop just shuts down nicely since a month or so. Great job, Ubuntu developers!

---

