---
title: "USB devices dead after sleep/hibernate"
date: 2007-03-01
forum: General Help
---

### Post by MasterOfMuppets on 2007-03-01
I've been messing around with things and I think I killed something important...
My mouse and keyboard, both USB, both non-wireless, just die when I come out of sleep/hibernate. But the problem is bigger - NO USB devices are recognized at all by the system.

Running kubuntu edgy on a T42 thinkpad. I've already tried to upgrade my BIOS - that didn't work.

I think the problem lies within the X restarting. Can anyone tell me how to make X "mount" the USB hubs? I'll add that to the resume.d script and I think that'll work...

---

### Post by giftnudel on 2007-03-01
Hi,

I also had this problem before. You said you have "been messing around with things". What does that mean exactly? Did it work before? If so, do you remember what you did? And what version of Ubuntu are you using?

Anyway, I don't think the problem is related to the X server but more related to the kernel. Can you try to unload the usb modules after resuming and see if the devices work then? If so, you may specify which modules you want to reload after suspend (but I don't remember where exactly).

If something is unclear, please ask since I don't know how familiar you are with linux.

Regards,
giftnudel

---

### Post by MasterOfMuppets on 2007-03-02
I'm not that familiar with linux, a fresh convert in fact. Managed to config my Kubuntu edgy nicely though, this is the only "bug" I have...

Whatever messing I've done, it's all gone now since I have undone things via backups.
How do I unload/load modules?

The resume script runs the following scripts:

10-thinkpad-standby-led.sh     
```
#!/bin/sh
. /usr/share/acpi-support/state-funcs
setLEDThinkpadSuspending 1

```
60-asus-wireless-led.sh
```
#!/bin/sh
. /usr/share/acpi-support/state-funcs
if isAnyWirelessPoweredOn ; then
    setLEDAsusWireless 1
else
    setLEDAsusWireless 0
fi

```
13-855-resolution-set.sh       
```

#!/bin/bash

if [ -x /usr/sbin/855resolution ]; then
    . /etc/default/855resolution
    if [ "$MODE" != "" ] && [ "$XRESO" != "" ] && [ "$YRESO" != "" ]; then
        /etc/init.d/855resolution start;
    fi
fi

```
62-ifup.sh
```
#!/bin/sh

# Bring up the interfaces (this should probably be left up to some policy
# manager, but at the moment we just bring back whatever we ifdowned)
for x in $INTERFACES; do
    ifup $x &
done
```
15-video-post.sh               
```
#!/bin/sh

# Post the video card
if [ x$POST_VIDEO = xtrue ]; then
  vbetool post
fi

```
65-console.sh
```
#!/bin/sh

# Some hardware needs another X/console switch in order to bring stuff back
chvt $CONSOLE;
if [ x$DOUBLE_CONSOLE_SWITCH = xtrue ]; then
  chvt 12;
  chvt $CONSOLE;
fi
```
17-video-restore.sh            
```

#!/bin/sh

# Attempt to restore some video card state
if [ x$SAVE_VBE_STATE = xtrue ]; then
  vbetool vbestate restore <$VBESTATE
  if [ $VBEMODE != "3" ]; then
    vbetool vbemode set $VBEMODE;
  else
    vbetool vgamode set 3;
  fi
fi

# Restore video PCI state
if [ x$SAVE_VIDEO_PCI_STATE = xtrue ]; then
  for x in /sys/bus/pci/devices/*; do
    if [ -f /var/run/vga-pci-`basename $x` ]; then
        cat /var/run/vga-pci-`basename $x` >$x/config;
    fi
  done

```
67-sound.sh
```
#!/bin/sh

# Get sound back
if [ -x /etc/init.d/alsa-utils ]; then
  /etc/init.d/alsa-utils start
fi

```
35-modules-load.sh             
```

#!/bin/sh

# Increase the firmware loading timeout while we're doing this
# Otherwise, swap thrash tends to lead to failure to start
if [ -f /sys/class/firmware/timeout ]; then
    timeout=`cat /sys/class/firmware/timeout`
    echo 100 >/sys/class/firmware/timeout
fi

# Load any drivers that we removed
for x in $MODULES; do
    modprobe $x;
done

# And reset the firmware timeout
if [ -f /sys/class/firmware/timeout ]; then
    echo $timeout >/sys/class/firmware/timeout
fi

```
69-services.sh
```

#!/bin/sh

# we need to restart our services after the network is back
for x in $STOP_SERVICES; do
        invoke-rc.d --quiet $x start
done

```
40-infra-red.sh                
```

#!/bin/sh

# Restart IR if necessary
if [ -f /var/run/irdadev ] && [ x$RESTART_IRDA = xtrue ]; then
    rm /var/run/irdadev;
    /etc/init.d/irda-setup start;
    /etc/init.d/irda-utils start;
fi;


```
72-acpi-pain.sh
```
# Some hardware gets unhappy about button events unless we do this
modprobe -r button
modprobe button

# Kick the fans
modprobe -r fan
modprobe -r thermal
modprobe fan
modprobe thermal

if [ "`grep ibm_acpi /proc/modules`" ]; then
    # No, I don't know why
    modprobe -r ibm-acpi
    modprobe ibm-acpi
fi

# NNGH FAN HATE
for x in /proc/acpi/fan/*; do
    if [ "`grep on $x/state`" ]; then
        echo -n 3 > $x/state;
        echo -n 0 > $x/state;
    fi
done

# Make sure that the drive power state is set correctly again
modprobe -r acpi_sbs
modprobe -r ac
modprobe ac
modprobe -r battery
modprobe battery
modprobe acpi_sbs
/etc/acpi/power.sh


```
49-855-resolution-set.sh       
```

#!/bin/bash

if [ -x /usr/sbin/855resolution ]; then
    . /etc/default/855resolution
    if [ "$MODE" != "" ] && [ "$XRESO" != "" ] && [ "$YRESO" != "" ]; then
        /etc/init.d/855resolution start;
    fi
fi

```
85-anacron.sh
```

#! /bin/sh

# This script makes anacron jobs start to run when the machine is
# plugged into AC power, or woken up.  For a laptop, these are the
# closest parallels to turning on a desktop.

# The /etc/init.d/anacron script now normally tries to avoid running
# anacron unless on AC power, so as to avoid running down the battery.
# (Things like the slocate updatedb cause a lot of IO.)  Rather than
# trying to second-guess which events reflect having or not having
# power, we just try to run anacron every time and let it abort if
# there's no AC.  You'll see a message on the cron syslog facility
# (typically /var/log/cron) if it does run.

/usr/sbin/invoke-rc.d anacron start >/dev/null


```
50-framebuffer-enable.sh       
```

#!/bin/sh

# And turn the framebuffer back on
for x in /sys/class/graphics/*; do
    if [ -f $x/state ]; then
        echo -n 0 >$x/state;
    fi
done


```
90-thinkpad-unstandby-led.sh
```

#!/bin/sh
. /usr/share/acpi-support/state-funcs
setLEDThinkpadSuspending 0
/etc/init.d/powernowd start


```
50-time.sh                     
```

#!/bin/sh

# Reset the time
hwclock --hctosys


```
90-xscreensaver.sh
```

#!/bin/sh

# now, we should poke xscreensaver so you get a dialog
if pidof xscreensaver > /dev/null; then
    for x in /tmp/.X11-unix/*; do
        displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
        getXuser;
        if [ x"$XAUTHORITY" != x"" ]; then
            export DISPLAY=":$displaynum"
            su $user -c "(xscreensaver-command -deactivate)"
        fi
    done
fi

```
50-tosh-restore-brightness.sh  
```

#!/bin/sh

if [ "x$TOSH_BRIGHTNESS" != "x" ]; then
  # To reset the brightness...
  echo 'brightness : '$TOSH_MAXBRIGHT > $TOSH_LCD
  echo 'brightness : 0' > $TOSH_LCD
  # And then restore it...
  echo 'brightness : '$TOSH_BRIGHTNESS > $TOSH_LCD
  unset TOSH_BRIGHTNESS TOSH_MAXBRIGHT
fi

unset TOSH_LCD

```
98-acpi-unlock.sh
```

#!/bin/sh

#Let acpid process events again
(sleep 10 && rm /var/lock/acpisleep)&


```
55-screen.sh
```

#!/bin/sh

# And make sure that the screen is on
if [ x$USE_DPMS = xtrue ]; then
  vbetool dpms on
fi


```

---

### Post by MasterOfMuppets on 2007-03-07
Bump.
I know this is a long post, but this is something I've seen alot of people run into and most of my friends (who have laptops) say this is the only problem preventing them from moving to Linux.
Help? :(

---

### Post by herbster on 2007-03-10
Yes! I have just encountered the same problem. I leave home with Ubuntu set to Hibernate after 30 mins, I come back last night and I press power to turn PC back on, it goes into Ubuntu all beautiful but my USB is all dead! What the heck?!

There has got to be a fix to this problem. Is it as simple as "restarting" USB on Ubuntu or something? Please, someone help!

---

### Post by cmavr8 on 2007-04-10
Still no news?

I have the exact problem when resuming from hibernation...

ANYONE?

---

### Post by albasj on 2007-04-23
Me too, but only with Feisty, on Edgy it was working well. 

Don't know what to do. :confused:  Please help.

---

### Post by dschie on 2007-04-26
same problem here on my thinkpad t23

everything looks ok, but even stuff that uses usb only as powersource wont work :/

00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)

---

### Post by ggardei on 2007-09-12
same here, though I rarely use the USB on this so it hasnt really bugged me.

---

### Post by MicheleZ on 2007-10-07
Also affected by the problem on a fresh installation of Feisty on a Compaq N610c

Cheers,

Michele

---

### Post by htnprm on 2007-10-15
Same for me with Feisty on an IBM Thinkpad A31. Recently fixed my 'no sound' problem after hibernation by setting "HIBERNATE_MODE=platform" in /etc/default/acpi-support. I suspect this USB problem will require some similar sort of change somewhere. Guess we may see what effect Gutsy has on the problem in s few days...

---

### Post by crf on 2007-11-01
I have this problem too. I just installed Ubuntu 6.06 yesterday, and I am a newbie with an old computer. My usb mouse, attached to a usb hub, will not work after resuming from hibernation.
 
Is there a workaround until it is fixed "for real"? Google seems to suggest using modprobe to solve similar problems. If that's so, or either way, could someone please fill in the details? Thanks :-)

---

### Post by simpsonsfan74 on 2007-11-01
I'm having this problem, too!  I'm running a (close to) fresh install of Gutsy with the newest 8.42.3 version of the fglrx driver.  Suspend/Hibernate wouldn't work, so I followed the advice for installing uswsusp.  I then ran s2both and it took me to a blinking cursor telling me the system was saving the state.  It stayed like that for a long time, and when I finally powered the laptop down and back up, USB devices no longer work!  I'm not sure what to try.  I did a rmmod ehci_hcd and usbcore and then modprobe'd them back, to no avail.  Any ideas?

[edit] Just to clarify, rebooting does not fix the issue. [/edit]

---

### Post by cmavr8 on 2007-11-01
I have Lenovo V100 and usb would be dead after hibernation. With Gutsy, 7.10 they seem to be working fine... (5 hibernation up to now)

crf, why did you install 6.06?

---

### Post by crf on 2007-11-01
> **cmavr8 said:**
> I have Lenovo V100 and usb would be dead after hibernation. With Gutsy, 7.10 they seem to be working fine... (5 hibernation up to now)

crf, why did you install 6.06?

I'll probably look into updating my computer (compaq armada m700) with Ubuntu 7.10 eventually. Here it may be a more involved process than would be typical, since there is very limited disk space, + a large broken file system I don't want to mess with yet and hopefully can recover. I just wondered if there was a quick workaround :) .

Windows98 used to be installed on the computer, but the file system broke, so I wiped its partition clean. There were also two other old linuxes on the computer, which were installed long ago by someone else, but something went wrong with the ext2 file system or disk partition, and they also wouldn't run. Since I had an ubuntu 6.06 which I'd ordered by mail, just to try out, I decided to install it, in order to have a usable computer for my family. I guess for me there is a large activation energy involved in switching OSes :D .

There is certainly a lot to like about ubuntu 6.06, even with the USB problem. Although probably it is not a security issue, the CD says it's supported for some time yet, so perhaps a fix for 6.06 will still come.

===
edit: I updated to edgy eft, following the advice on the wiki. I wasn't able to upgrade further though, due to disk space constraints.

---

### Post by crf on 2007-11-06
I got an external usb disk to move the data on the old partitions off, and redid the partitions to have enough space to successfully upgrade to 7.10. Now Suspend works (yay !). And my mouse revives itself after resuming.

---

### Post by wInddnIw on 2007-11-07
Hi !
Same thing here with a brand new Gutsy installation : after installing hibernate, I tried it and after reboot my usb mouse and keyboard didn't respond. Any workaround about this yet ?

wInd

---

### Post by Gwasanaethau on 2007-11-19
Did anyone find a solution to this problem in the end? This happens to me in both Feisty and Gutsy…

---

### Post by cmavr8 on 2007-11-20
> **Gwasanaethau said:**
> Did anyone find a solution to this problem in the end? This happens to me in both Feisty and Gutsy…

Tried fresh gutsy install?

I don't have the problem anymore...

---

### Post by Gwasanaethau on 2007-11-20
> **cmavr8 said:**
> Tried fresh gutsy install?

I don't have the problem anymore...

Yep, and also a fresh Feisty install too; no luck with either, unfortunately.

---

### Post by Gwasanaethau on 2007-11-29
Right, I think I might be getting somewhere with this&#8230;

After having a look at [this]("http://ubuntuforums.org/showthread.php?p=3660810") post, I tried the 'dmesg | grep usb' command and got:

```
[COLOR="DarkGreen"][ 6324.599523][ 6346.967254] usbhid 2-1:1.0: freeze
[ 6346.967257] usb 2-1: freeze
[ 6346.978055]  usbdev4.1_ep81: PM: suspend 0->1, parent 4-0:1.0 already 2
[ 6346.978060] hub 4-0:1.0: PM: suspend 2->1, parent usb4 already 2
[ 6346.978062]  usbdev4.1_ep00: PM: suspend 0->1, parent usb4 already 2
[ 6346.978064] usb usb4: PM: suspend 2-->1
[ 6346.978066]  usbdev3.1_ep81: PM: suspend 0->1, parent 3-0:1.0 already 2
[ 6346.978071] hub 3-0:1.0: PM: suspend 2->1, parent usb3 already 2
[ 6346.978073]  usbdev3.1_ep00: PM: suspend 0->1, parent usb3 already 2
[ 6346.978075] usb usb3: PM: suspend 2-->1
[ 6346.978079] usb usb2: freeze
[ 6346.978085]  usbdev1.1_ep81: PM: suspend 0->1, parent 1-0:1.0 already 2
[ 6346.978089] hub 1-0:1.0: PM: suspend 2->1, parent usb1 already 2
[ 6346.978091]  usbdev1.1_ep00: PM: suspend 0->1, parent usb1 already 2
[ 6346.978093] usb usb1: PM: suspend 2-->1[/COLOR]
[COLOR="RoyalBlue"][   49.676546] usb usb4: root hub lost power or was reset
[   50.438196]  usbdev1.1_ep00: PM: resume from 0, parent usb1 still 2
[   50.438199]  usbdev1.1_ep81: PM: resume from 0, parent 1-0:1.0 still 2
[   50.438201] usb usb2: resuming
[   50.438212] usb usb2: root hub lost power or was reset
[   50.501716]  usbdev3.1_ep00: PM: resume from 0, parent usb3 still 2
[   50.501719]  usbdev3.1_ep81: PM: resume from 0, parent 3-0:1.0 still 2
[   50.501721] usb usb4: resuming
[   50.532646] usb 2-1: resuming
[   50.532648]  usbdev2.3_ep00: PM: resume from 0, parent 2-1 still 1
[   50.532651] usbhid 2-1:1.0: PM: resume from 1, parent 2-1 still 1
[   50.532653] usbhid 2-1:1.0: resuming
[   50.532655]  usbdev2.3_ep81: PM: resume from 0, parent 2-1:1.0 still 1
[   50.533510] Restarting tasks ... <4>usb usb1: root hub lost power or was reset
[   50.908853] usb 2-1: USB disconnect, address 3
[   51.220153] usb usb3: root hub lost power or was reset[/COLOR]

```
The bit in green happens during the hibernation process, the bit in blue occurs on restart. It seems that the USB cards in the computer are not being reinitialised during the restart, and so everything connected to them seems to stop working. Is there any way to manually power-up the USB cards?

EDIT: Should add that this is in 7.04&#8230;

---

### Post by Gwasanaethau on 2007-12-02
SOLVED! With some hints from [this post]("http://216.239.59.104/search?q=cache:vT4cI2-RZ3IJ:www.devlib.org/forums/suspend-and-hibernate-t1753.html+usb+hibernate+ubuntu+resume&hl=en&ct=clnk&cd=34&gl=ie") (I've deliberately left the 'Google highlighting' in place), I was able to sort the 'USB devices not working after resume from hibernation' problem. It was fixed thus:
```
cd /etc/default
sudo cp -p acpi-support acpi-support.bak
sudo gedit acpi-support
```
Change [COLOR="Green"]**MODULES=""**[/COLOR] to [COLOR="Green"]**MODULES="ehci_hcd"**[/COLOR]

This works for me. If you have already done a hibernation/resume cycle without editing the 'acpi-support' file and you don't want to restart, simply unload and reload the 'ehci_hcd' module:
```
sudo modprobe -r -v ehci_hcd && sudo modprobe -v ehci_hcd
```
This will bring back USB functionality immediately.

Hope that helps anyone else who is stuck with it!

EDIT: **NB: This was originally written for Edgy/Feisty/Gutsy and should work fine on those versions. It seems other issues appear to have been introduced in Hardy/Intrepid causing the workaround outlined above to have little effect - read on for more details.**

---

### Post by morone on 2007-12-03
> **Gwasanaethau said:**
> SOLVED! 

Hope that helps anyone else who is stuck with it!

Just made the changes that you suggested.  Will see how it works.  Thanks for your post.

---

### Post by Gwasanaethau on 2007-12-06
No problem 'tall 'tall; glad to be of help! I hope it works for you! :)

---

### Post by morone on 2007-12-08
Everything working fine after the changes.  Thank you for the information - it solved a problem that was irritating me as I prefer to hibernate, rather than shutdown the laptop.

Thanks again!

Pete

---

### Post by Gwasanaethau on 2007-12-09
Good, I'm glad it worked for you too! You're very welcome - take care and all the best now! :D:cool:

---

### Post by tweedledee on 2008-01-02
> **Gwasanaethau said:**
> 
```
cd /etc/default
sudo cp -p acpi-support acpi-support.bak
sudo gedit acpi-support
```
Change [COLOR="Green"]**MODULES=""**[/COLOR] to [COLOR="Green"]**MODULES="ehci_hcd"**[/COLOR]


Perfect!  This solved the problem on my wife's desktop (recently converted), which is nearly identical to mine, yet has this problem upon returning from hibernate (but not sleep - go figure), whereas my desktop has not shown it once in over a year.  Of course, mine currently won't hibernate at all, but that's unrelated and recent.

---

### Post by xtracto on 2008-04-29
Hello, 

Just wanted to add two things about this problem. I am running HARDY HERON 8.04  so this bug is still in the latest version of Ubuntu.

I had this problem in my HP ZV5000 laptop, after resuming from hibernate the USB mouse and keyboard won't work. 

I followed the solution advice and it worked.


I just wanted to note that, when I went to the /etc/default/acpi-support to add the ehci_cd, there was a "ohci_hcd" specified in the MOUDLES=""  section. 

Maybe someone who knows more about Ubuntu should check that stuff.

---

### Post by andrewbrown22 on 2008-04-30
I followed the guide and it seemed to work for a day, however, I still have the issue of no onboard mouse or keyboard after a resume about 1/2 of the time..
```

# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES="ehci_hcd"

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

```

Should I add the "ehci_hcd" to the whitelist?

---

### Post by tweedledee on 2008-05-01
> **andrewbrown22 said:**
> I followed the guide and it seemed to work for a day, however, I still have the issue of no onboard mouse or keyboard after a resume about 1/2 of the time..
```

# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES="ehci_hcd"

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

```

Should I add the "ehci_hcd" to the whitelist?

You aren't likely to break anything if you try it, but I think there is a slightly different but related problem in Hardy I'm trying to track down - on a computer that did not problems with previous versions of Ubuntu, my USB mouse (but not keyboard) is always dead after resume, and playing with ehci_hcd has not helped in this case.

---

### Post by andrewbrown22 on 2008-05-01
> **tweedledee said:**
> You aren't likely to break anything if you try it, but I think there is a slightly different but related problem in Hardy I'm trying to track down - on a computer that did not problems with previous versions of Ubuntu, my USB mouse (but not keyboard) is always dead after resume, and playing with ehci_hcd has not helped in this case.

Well if you find anything out please let me know. It is the only negative thing about my switch from Vista.

---

### Post by Gwasanaethau on 2008-05-01
> **xtracto said:**
> Hello, 

Just wanted to add two things about this problem. I am running HARDY HERON 8.04  so this bug is still in the latest version of Ubuntu.

I had this problem in my HP ZV5000 laptop, after resuming from hibernate the USB mouse and keyboard won't work. 

I followed the solution advice and it worked.


I just wanted to note that, when I went to the /etc/default/acpi-support to add the ehci_cd, there was a "ohci_hcd" specified in the MOUDLES=""  section. 

Maybe someone who knows more about Ubuntu should check that stuff.

I think 'ehci' refers to the enhanced USB interfaces, with 'ohci' being the ordinary ones. I think it depends on the USB controllers (hardware) you're using as to which USB ports are ordinary ones and which ones have the 'enhanced' features. My last computer had a mixture of both; something may have detected the presence of ohci type USB ports on your computer and automatically configured them. If that's the case, then maybe there is some way to do the same for the ehci ones. Hmm…

I should say I'm not an expert in this by any stretch of the imagination, and could well be wrong saying most (or all) of the above. :lol: I'm also not a developer, so I have no way of even thinking about how to do this…

> **andrewbrown22 said:**
> I followed the guide and it seemed to work for a day, however, I still have the issue of no onboard mouse or keyboard after a resume about 1/2 of the time..
```

# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES="ehci_hcd"

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

```

Should I add the "ehci_hcd" to the whitelist?
> **tweedledee said:**
> You aren't likely to break anything if you try it, but I think there is a slightly different but related problem in Hardy I'm trying to track down - on a computer that did not problems with previous versions of Ubuntu, my USB mouse (but not keyboard) is always dead after resume, and playing with ehci_hcd has not helped in this case.

I originally tried adding 'ehci_hcd' to the whitelist (it seemed to make more sense than adding it to the modules list) but it didn't work for me (I was, however, using Feisty at the time). But, as tweedledee says, it probably won't break anything, so give it a try and see what happens. Either that or you could try adding 'ohci_hcd' as described above. No guarantees as to whether that will work, though…

---

### Post by haizaar on 2008-05-04
Same problem here with dell XPS m1330. Setting
MODULES_WHITELIST to "ehci_hcd uhci_hcd"
in /etc/default/acpi-support did not help

---

### Post by Gwasanaethau on 2008-05-04
Hmm, that's an interesting one. Unfortunately, I'm not using Hardy at the moment, so I can't really help. It's such a shame this is broken again as it took me ages to figure out how to fix it for Feisty/Gutsy! :(

---

### Post by publicskill on 2008-05-06
I thought I made it work on Hardy...

[I]
So, the trick is to restart appropriate modules when resuming.
In my case adding "ehci_hcd" or "ohci_hcd" to 
MODULES= 
in /etc/default/acpi-support didn't work. I had to add BOTH:
```
MODULES= "ehci_hcd ohci_hcd"
```

It helped, but my wireless network broke :/ Finaly I change to this:

MODULES="usbcore ndiswrapper"

and:

STOP_SERVICES="networking"

Why? "usbcore" restart both: "ehci_hcd" and "ohci_hcd" (and some more, put "lsmod | grep usbcore" in console to check). I use "ndiswrapper" for my WLAN. Restarting service: "networking" helped me in ubuntu 7.10, so I tried and in 8.04 it worked too :)
It worked...
[/I]

Unfortunately after second reboot this didnt work ;( :( 

But still I discovered, that when my usb mouse is dead

*sudo modprobe -r -v ohci_hcd && sudo modprobe -v ohci_hcd*

makes it works!! However adding it to /etc/default/acpi-support wont help... I will try harder and give some more info...

But can somebody answer me:
If I change /etc/default/acpi-support and save it, do I have  to reboot to apply changes?? Or will this work immediately for suspending??

---

### Post by vega_nsk on 2008-05-07
> **publicskill said:**
> 
But still I discovered, that when my usb mouse is dead

*sudo modprobe -r -v ohci_hcd && sudo modprobe -v ohci_hcd*

makes it works!! However adding it to /etc/default/acpi-support wont help... I will try harder and give some more info...

But can somebody answer me:
If I change /etc/default/acpi-support and save it, do I have  to reboot to apply changes?? Or will this work immediately for suspending??

Sorry for my bad English.

I found a solution. */etc/default/acpi-support* won't work cause Ubuntu 8.04 uses pm-utils for suspend and hibernate. So I added a file */usr/lib/pm-utils/sleep.d/98usb* with the following contents:

```

#!/bin/sh

case "$1" in
   resume|thaw)
      modprobe -r -v ohci_hcd
      modprobe -v ohci_hcd
      ;;
   *)
      ;;
esac

```

Than exec *chmod +x /usr/lib/pm-utils/sleep.d/98usb*. And now it works! :)

---

### Post by publicskill on 2008-05-07
Wow! Thanks, it works for me too!!!!!
Great job! :)

---

### Post by cmavr8 on 2008-05-07
Wow! amazing... I've been having all sorts of problems with suspend in 8.04, so I'll try it..

(problems non existant in the past)

Thanks. Will report back.

---

### Post by cmavr8 on 2008-05-07
Maybe one could do 
sudo gedit /usr/lib/pm-utils/defaults
and edit the first option (SUSPEND_MODULES="") instead of the script...

---

### Post by cmavr8 on 2008-05-07
Did it (my way) and it works pretty good...

Tried about 10 times and no problems. (when laptop is undocked. If I try with docked laptop I get strange things...)

I added ohci_hcd and iwl3945, my wifi driver.

Thanks vega!

---

### Post by cmavr8 on 2008-05-07
Guys, for the record, I did it (completely).
I mean, Suspend to ram works perfectly, even with all usb devices connected!
The problem was power!

Tried suspended 5-7 times. Perfect working.

More <useless> info:
I now have a usb docking station, with audio(not used), network, pseudo-vga (not used), COM (not used) and connected: Scanner, mouse, USB HUB (with connected: printer, keyboard, CUP heater) and it's all working! It's powered by a AC/DC 4.5V supplier...

Thanks everybody!

(Wanna help more? : [97C Temperature - Hot CPU!]("http://ubuntuforums.org/showthread.php?t=784369") or [Can't change keyboard layout bug]("http://ubuntuforums.org/showthread.php?t=288233") )

---

### Post by tweedledee on 2008-05-07
> **cmavr8 said:**
> Maybe one could do 
sudo gedit /usr/lib/pm-utils/defaults
and edit the first option (SUSPEND_MODULES="") instead of the script...

This approach worked for me as well (although I needed to use "uhci_hcd" instead of "ohci_hcd").  In addition, I simply copied the /usr/lib/pm-utils/defaults file to /etc/pm/config.d/ and edited it there.  Modifying the file in /etc will reduce the probability of overwrites with future updates (especially as I'm partly running Debian testing at the moment, where this fix worked in exactly the same way).

The script approach (although done manually) was useful for figuring out module was the problem, after looking at my choices from lsmod.

---

### Post by Gwasanaethau on 2008-05-09
Great job people! When I upgrade to Hardy I'll be sure to come back here and give your solutions a shot!

---

### Post by cmavr8 on 2008-05-12
Well, not so good new for me.. Suspend is broken. 

USB devices are ok IF the laptop wakes up. Usually it doesn't, so I just hard reset it..

Anyway, will return when I fix this problem..

---

### Post by PaganBlasphemy on 2008-05-15
suspend broke for me too a couple days ago, I think someone introduced a new bug in one of the updates.  

everything had been AOK for me, then after some updates my suspend/resume was broken, I managed to hack it back into working and now my USB doesn't resume, I'm getting to the point where I believe I may just reinstall and only install security updates. 

none of the variations in this thread have resumed my USB devices, my problem may be something unrelated (and unknowable for me unfortunately).  oddly enough, my USB hub indicates the laptop is sending power out, but the devices plugged into either the hub or directly into the computer are never recognized, just ignored.

---

### Post by Agathos on 2008-05-24
SUSPEND_MODULES="uhci_hcd"
in /etc/pm/config.d/defaults (copied from /usr/lib/pm-utils) worked for me and thanks for that.

---

### Post by TheBlackNoodle on 2008-06-14
Hey guys,

I just got a new laptop and I'm experiencing the same dead usb ports after resuming from Suspend. I'm running 8.04 with the proposed kernel 2.6.24-19, which I believe was supposed to fix all the hibernate issues. Well, I can't get the usb devices to work again at all. I tried all the tricks mentioned in the thread, and still nothing.

I did some tests of my own, none of which helped, but some give interesting results. I'm testing with a Microsoft Intellimouse 2 wireless USB mouse.

After resuming, if I do "sudo modprobe -r ohci_hcd", the power in the receiver turns on. I can tell because the green LED lights up. Normally, at this point, if I push the buttons on the mouse and receiver, they can sync. But pushing on the receiver doesn't have any effect; it should blink once or twice but instead remains solid.

If I do "sudo modprobe ehci_hcd" while ohci_hcd has been removed, the green light blinks once, but there seems to be no other effect.

If I do "sudo modprobe ohci_hcd", the LED blinks a few times and looks like it's going to work for about 2 seconds before it completely shuts off.

The other module changes don't seem to do anything. Does anyone know what's going on here?

EDIT: It seems the built in webcam (uvcvideo module) doesn't work after resuming either. It's one of the culprits in the usbcore module. ndiswrapper, however, DOES appear to be working, since my wireless card depends on it: it suspends and resumes no problem. Note my computer is the HP Pavilion dv9820us Notebook.

---

### Post by Jeffrey Magder on 2008-06-26
Before comming across this thread I came up with an alternate solution:

[INDENT][FONT="Courier New"]sudo rmmod usbhid ohci_hcd ehci_hcd usbcore
sudo modprobe ehci_hcd
sudo modprobe ohci_hcd[/FONT][/INDENT]But editing [FONT="Courier New"]/usr/lib/pm-utils/defaults[/FONT] and setting [FONT="Courier New"]SUSPEND_MODULES[/FONT] to an appropriate driver is a more elegant solution for 8.04.  Still, I thought I'd post my previous solution in case someone is using a different version or has problems with pm-utils.

---

