---
title: "Can't kill &quot;X&quot; screensaver in Xubuntu"
date: 2007-12-13
forum: General Help
---

### Post by kmoz on 2007-12-13
Hello,

I've recently finished setting up Xubuntu to power a converted laptop to digital photo frame.  The photos are displayed with feh, and my .xsessions looks like this:

xset s off &  (had this with and without the "&", didn't make a difference)
xset s noblank & (had this with and without the "&", didn't make a difference)
/home/foo/start_slideshow.sh &
xfwm4 2> /dev/null

The laptop auto logs in, then lauches the photos with no issues, and without going into xfce.

Now, after the pictures have been displayed for a while (say 20 min), a big "X" appears on the screen and periodically moves around.  I've completely removed xscreensaver, xscreensaver-demo and gscreensaver.  But some sort of X screensaver keeps coming back.  Any ideas how to kill this thing?

---

### Post by der_joachim on 2007-12-13
It's a long shot, but it could be a xorg setting.  Try setting the following lines in the ServerLayout section  in your xorg.conf. 

```

    Option         "BlankTime" "0"
    Option         "StandbyTime" "0"
    Option         "OffTime" "0"

```

You might want to doublecheck the xorg.conf man page for the correct options though.

---

### Post by kmoz on 2007-12-13
Hi there,

I followed this page:

[http://ubuntuforums.org/showthread.php?t=597832#post3673565](http://ubuntuforums.org/showthread.php?t=597832#post3673565)

and put this into my xorg.conf:

Section "ServerFlags"
	Option		"blank time" "0"
	Option		"standby time" "0"
	Option		"suspend time" "0"
	Option		"off time" "0"
EndSection

But that didn't do the trick.  I'll take a look and see if it has to go into the ServerLayout section.  I'm just not sure what other screen saver could be running.

running "xset q"  gives this as output:

Screen Saver:
    prefer blanking: no             allow exposures:      yes      timeout:   0       cycle:    600

DPMS:
   Standby:   0       Suspend:   0     Off:        0
   DPMS is Enabled
   Monitor is On

---

### Post by gwpritch on 2007-12-13
I would have thought that```
 xset s off 
``` would have done the trick, but Try adding this to your .xsession:
```
xset -dpms
```

---

### Post by kmoz on 2007-12-14
So the intial output of ```
xset q
``` reported 

Standby Time: 1800   

whereas everything else was "0"

Sure enough, I had misspelled "time" in the xorg.conf file.  So even when all other screen savers have been removed, a user needs to edit xorg.conf and add the appropriate server flags.  

Thanks for the help.

---

### Post by HermanAB on 2007-12-14
Xscreensave is a daemon called appropriately "xscreensaver".  Check with "ps -e" to see whether it is still running.  If so, then you have to find out how it is booted.

---

### Post by gwpritch on 2007-12-14
since you are setting all the dpms parameters to "0" you might as well just disable dpms altogether, either by removing the option from xorg.conf or using xset -dpms.

---

