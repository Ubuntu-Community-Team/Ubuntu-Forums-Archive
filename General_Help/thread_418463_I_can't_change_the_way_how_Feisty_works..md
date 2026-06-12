---
title: "I can't change the way how Feisty works."
date: 2007-04-22
forum: General Help
---

### Post by Marcos.Rufino on 2007-04-22
I've just installed Feisty from scratch but it seems that many important things are not working yet. 

I'm trying to avoid some applications of being automatically loaded by removing them from the "Sessions" manager (>Systems>Preferences>Sessions) but they come back afterwards. The same problem occurs when I try to add new applications to the list of "initial applications" inside "Sessions". I'm trying to add Glipper, Tomboy and amaroK but after a reboot nothing happens (and the "Sessions" dialog box appears in its previous form). 

A similar problem happens when I try to change the language of the entire system. Despite the fact I have successfully installed portuguese and english language in my Gnome system, I cannot come back to english anymore (after I had changed to portuguese). Inside the >Systems>Administration>Languages dialog box all seems to be correct (with the english language as the default language) but the menus and dialog boxes are still in portuguese. And yes, I've reboot the system after altering these stuffs.


Well, I'm afraid Feisty is half-backed enough to a public release. I would prefer to wait some time but to have a system really ready to use and change.

---

### Post by Crosbie on 2007-04-22
Probably a silly question, but you are choosing 'Save current session' on the Session Options tab - or ticked 'Automatically save'?

---

### Post by Marcos.Rufino on 2007-04-22
Yes Crosbie, I've ticked "Automatically save" and have also "save the current session", but it didn't help.

I've forgot to say that other problem is that the monitor is sleeping after some time (around 15 minutes) even after I had configured it not to sleep (in the management of energy).

Thanks

---

### Post by dreadlord_chris on 2007-04-22
> **Marcos.Rufino said:**
> I've forgot to say that other problem is that the monitor is sleeping after some time (around 15 minutes) even after I had configured it not to sleep (in the management of energy).

Thanks

I have this problem too - I've disabled all (that I know of, at least) Power Saving options - and still, after about 15 minutes of inactivity the monitor *usually* blanks.

I've checked my BIOS - there are no Power Saving options there. I've also turned off all Power Saving options on the monitor itself (HP vs15c)

It's odd though - while usually (like 90% of the time) the monitor blanks as described, sometimes I come back to my computer after a couple hours - and the monitor is still on...?

It did this in Edgy and continues in Feisty...

---

### Post by Marcos.Rufino on 2007-04-23
Does someone have any new information about this?

---

### Post by lettas on 2007-05-14
> **dreadlord_chris said:**
> I have this problem too - I've disabled all (that I know of, at least) Power Saving options - and still, after about 15 minutes of inactivity the monitor *usually* blanks.

I've checked my BIOS - there are no Power Saving options there. I've also turned off all Power Saving options on the monitor itself (HP vs15c)

It's odd though - while usually (like 90% of the time) the monitor blanks as described, sometimes I come back to my computer after a couple hours - and the monitor is still on...?

It did this in Edgy and continues in Feisty...

[http://en.wikipedia.org/wiki/VESA_Display_Power_Management_Signaling]("http://en.wikipedia.org/wiki/VESA_Display_Power_Management_Signaling")

```
sudo gedit /etc/X11/xorg.conf
```
Option	    "DPMS"
to
#Option	    "DPMS"

---

### Post by dreadlord_chris on 2007-05-19
> **lettas said:**
> [http://en.wikipedia.org/wiki/VESA_Display_Power_Management_Signaling]("http://en.wikipedia.org/wiki/VESA_Display_Power_Management_Signaling")

```
sudo gedit /etc/X11/xorg.conf
```
Option	    "DPMS"
to
#Option	    "DPMS"

Ya, you know what? That was one of the first (fairly obvious) things I tried. Didn't work. Actually I couldn't see that it had any effect at all.

But I did finally discover the *setting**s*** that must be changed in /etc/X11/xorg.conf:

First, in Section **ServerLayout** add the following options:
```

    Option 	   "BlankTime" "0"
    Option	   "StandbyTime" "0"
    Option 	   "SuspendTime" "0"
    Option	   "OffTime" "0"
    Option 	   "NoPM" "true"

```

Next scroll down to Section **Module** and look for the line:
```

    Load     "extmod"

```
change it to this:
```

    SubSection     "extmod"
	Option	   "omit DPMS"
    EndSubSection

```

Save & reload X - your monitor should now stay on until you actually turn it off.

---

