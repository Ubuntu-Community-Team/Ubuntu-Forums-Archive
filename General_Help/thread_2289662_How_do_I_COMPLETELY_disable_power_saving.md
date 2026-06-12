---
title: "How do I COMPLETELY disable power saving?"
date: 2015-08-06
forum: General Help
---

### Post by 42dorian2 on 2015-08-06
Okay.  Here goes.  If this is in the wrong forum, and I've made a mistake, Mods please move it to the appropriate one.  I'm a little tired right now, and may have made a mistake.

I have Xubuntu 12.04, and my computer will not run any newer versions.  I want to disable power saving.  I don't want the computer to ever turn itself off.  I have one particular hard drive that is very sensitive.  It doesn't always turn back on, and it stores my Home directory.

I have done the following in an effort to do this:

As myself:  
Set all Power Saving settings to "Never" or "Off", as appropriate.
Removed Power Manager from Application Autostart.
Removed ACPI, and all Power Managers from Synaptic.
Removed xscreensaver as a whole from the computer.
Disabled all Power Saving in Settings Editor.

As Root:
Set all Power Saving settings to "Never" or "Off", as appropriate.
Removed Power Manager from Application Autostart.
Disabled all Power Saving in Settings Editor.
Added "acpi=off" to GRUB.

Problem:  Still goes to Standby/Sleep after 15 minutes of no mouse/keyboard activity.

This is still a problem, because I listen to MP3s as I sleep, played by the Computer.  As it currently sits, I am unable to do this, since the "Standby" mode spins down the Hard Drives and puts the PC to sleep after 45 minutes.  I am still trying to stop this, because I want my PC active, and for the power to not be interrupted for that very touchy Hard Drive holding my Home directory.  My Computer is old enough that it doesn't like being turned off.  When I do, things stop working, no matter what I do to it.

---

### Post by Bucky Ball on 2015-08-06
Have you tried doing a search in Synaptics for 'power manager' and completely removing any you have installed? Also, remove xscreensaver (do a search for 'screensaver' in case you have others installed).

Unfortunately, you will need to re-boot after this I would think.

---

### Post by mc4man on 2015-08-06
12.04 is long gone in this mind here, a site search here shows several opposite requests for 12.04. (how to set a spin down time.
seems hdparm was a common tool - maybe it can also set to never? or a very long time...

---

### Post by 42dorian2 on 2015-08-06
I have tried both.  Removed every trace of a screensaver or power manager.  Both as my user, and as root.  It still blanks the screen into power saving mode every 15 minutes.  I'm at a loss to figure anything else at this point.

---

### Post by Bucky Ball on 2015-08-06
So you have completely removed the screensaver and power manager packages using Sypnatpic Package Manager? xscreensaver (probably) and xfce4-powermanager, if they are installed?

---

### Post by Dennis N on 2015-08-06
>  I have one particular hard drive that is very sensitive. It doesn't always turn back on, and it stores my Home directory.

Is this a USB-connected hard drive?

2083=P[314]

---

### Post by 42dorian2 on 2015-08-06
> **Bucky Ball said:**
> So you have completely removed the screensaver and power manager packages using Sypnatpic Package Manager? xscreensaver (probably) and xfce4-powermanager, if they are installed?

Yep.  Completely removed.  Same with ACPI.

And @Dennis N, no this is a Hard Drive connected inside the machine.  IDE, connected to a Molex 4-pin power connector.  Just, with the age of the machine, and the stiffness of the wires on average, when the machine heats up, or cools down, beyond certain thresholds, this connector/hard drive coupling tends to move just enough that the Hard Drive loses power and shuts off.  Then, when rebooting to try and restore power to it, that connector is in just the wrong place, and the CMOS doesn't detect it being there.  So, I lose access to it.  Which starts a whole procedure of rebooting, holding the power connector in JUST the right place, and getting the system to detect it again.

My machine is just old, and I'm too short on funds to build a new one.  If it was an option to just replace the whole thing, I would.


UPDATE:  I did manage to get it not to spin down the Hard Drives last night.  It is still blanking the screen after 15 minutes or so.

---

### Post by mc4man on 2015-08-06
> **42dorian2 said:**
> 


UPDATE:   It is still blanking the screen after 15 minutes or so.
check DPMS - [http://ubuntuforums.org/showthread.php?t=1483345&p=10307995&viewfull=1#post10307995](http://ubuntuforums.org/showthread.php?t=1483345&p=10307995&viewfull=1#post10307995) & down

---

### Post by 42dorian2 on 2015-08-06
> **mc4man said:**
> check DPMS - [http://ubuntuforums.org/showthread.php?t=1483345&p=10307995&viewfull=1#post10307995](http://ubuntuforums.org/showthread.php?t=1483345&p=10307995&viewfull=1#post10307995) & down

That appears to have done the trick!  Thank You So Much!!

---

