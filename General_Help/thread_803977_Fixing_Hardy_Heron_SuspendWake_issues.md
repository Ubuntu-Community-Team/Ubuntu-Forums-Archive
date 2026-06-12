---
title: "Fixing Hardy Heron Suspend/Wake issues"
date: 2008-05-22
forum: General Help
---

### Post by maeks84 on 2008-05-22
Having some trouble here and am not getting very far with help just from Google.  I'm having multiple issues, but I'm going to try to address only one at a time.

A bit about my setup...
     Running Ubuntu Hardy Heron 8.04, freshly installed and fully updated
     NVIDIA Restricted Drivers are enabled.  (Screen will not wake without.)
     Motherboard - ASUS A8S-x
     Graphics Card - NVIDIA GeForce 6200 LE

This box will mostly be a DVR running MythTV and so I hope to get the computer to power down and wake as needed.

First issue.... is screen locking

     After restarting, I tell the computer to "Suspend", wait for it to power down, and then press the power button to tell it to resume.  It's slow (later issue), but it will eventually show a box asking for my password.  I enter my password and it resumes fine.  Tell the computer to suspend again, wait, and press power button.  Wait and a white screen appears.  Without seeing anything, I can enter my password, hit return, and all is well.  The desktop appears as normal.

     I  don't want the screen to lock at all, so I'm hoping that if this is disabled, the desktop will always appear as it should, with no white screen.  So, my question is "How do I disable the screen locking?"

     I've tried...
          ```
sudo gedit /etc/default/acpi-support
```
          Changed
          ```
LOCK_SCREEN=true
```
          to
          ```
# LOCK_SCREEN=true
```
          (Also tried changing to  *LOCK_SCREEN=false*  )
          Saved
          Rebooted
          **Result** = No change in behavior

     I also checked...
          ```
gconfig-editor
```
          *apps* > *gnome-power-manager* > *lock*
          *gnome_keyring_suspend* is unchecked

I don't know if there is any logs that I can post that might help?  If so, let me know and I'll post them.
Grateful for any and all help.
Thanks,
Matthew

---

### Post by maeks84 on 2008-05-23
Also tried
```
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_on_blank_screen false
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_use_screensaver_settings false
```
No change.

Now I can't launch *gconfig-editor*.  Started to reinstall Hardy Heron, install locks up :mad: on "Configuring apt..." or something like that.  I've got to quit thinking about this for a while.  I'll try again later.

---

### Post by maeks84 on 2008-05-23
Got the clean install again, updated, and enabled the NVIDIA hardware drivers.  Ran
```
gconf-editor
```
Unchecked all options under *apps* > *gnome-power-manager* > *lock*
and under *desktop* > *gnome* > *lockdown* I checked *disable_lock_screen*

and :) YAY!  The desktop appears as it should after suspend without asking for a password or showing a white screen.

So, on the the second issue.... slow resume

Now, I tell the computer to suspend and it behaves fine.  Then I press the power button and it resumes slowly, but everything seems to function.  While resuming though it shows some error messages.  However, they disappear too fast for me to read.  I'm guess that they should appear in some log file somewhere?  If so, which one?

I'm pretty sure that the issue must have something to do with the internal card reader I have installed.  When I tell the computer to wake, the red activity led on the reader lights up solid.  When it goes off the errors soon display and the computer wakes up.  Any ideas?

This isn't a major issue for my situation, but I wanted to try and get at least some information on it.

---

### Post by maeks84 on 2008-05-26
Okay then, third issue.... Wake/Poweron at set time

I've tried setting the wake time several ways based on different guides and each one with various BIOS settings.  I couldn't get any of them to work.  Only way I can get a boot at a set time is by setting a wake time in the BIOS.  So I was thinking to change the time set in the BIOS.

I think that this can be done via
```
hwclock
```
I also thought that
```
hwclock --show
```
would show the time of the RTC in the BIOS.  Instead it shows me the current time.  The same as reported by the OS.  The RTC view in the BIOS reports 00:00:00 at 7:00pm.  I guess I want to know, How to tell what time does the RTC have? and How to change the RTC to a specific time?

---

### Post by maeks84 on 2008-05-27
No one has a clue on any of this?  Talking to myself seems to help a bit though.  I guess. :neutral:  Maybe someone else will get some use of it.

```
hwclock --localtime
```
shows the time in the BIOS/RTC except that it is not in the 24hr format.

```
sudo hwclock --set --date="5/27/2005 09:00:00
```
changes the time reported by --localtime to the time/date specified.  However, in the BIOS the time and date remain unchanged and after a reboot the --localtime reports the current date/time.  (Not the date/time I set)

Problem is that the time is not actually being changed in the RTC.

edit:  Could the command ```
sudo hwclock --systohc
``` be being run automatically at shut down?  This might explain why the time does not seem to be being changed in the BIOS since my changes would be overwritten.

---

### Post by danwood76 on 2008-05-27
The second issue you are on about is a known bug:
[https://bugs.launchpad.net/ubuntu/+bug/226279](https://bugs.launchpad.net/ubuntu/+bug/226279)

Just have to wait for an update on that one.

Never tried settings BIOS wake up alarms so I cant help you there.

---

### Post by maeks84 on 2008-05-27
Thanks for the response danwood.  It seemed to me that the bug related might relate more to the "first issue".  I suppose the first and the second could be related though.  Overall, I think your right these issues just need fixes and more time.  They're working to some extent now so I can accept that without tearing out much more hair.  I'm starting to think that my MoBo won't wake from Suspend at a set time anyway, so I'll probably have to just shutdown each time and wait for it to boot when I want it on.

Some more on the third issue.

I looked in /etc/init.d and saw a script called hwclock.sh.  I created a backup of this file and removed the original.  I then set the time using the hwclock command and rebooted.  The command used to get the correct time into the BIOS was```
hwclock --set --localtime --date="9/27/2008 13:54:00"
```  I have it manually set in the BIOS to power on at 00:00:00 so it should be possibly to modify the time to get the correct power on in x minutes.

I suspect that this wasn't the best way to do it since some errors popped up the first time I rebooted, (but not the second) yet it seems to work.  If someone knows the correct way to stop setting the hwclock on shutdown, please let me know.

---

