---
title: "[SOLVED] Hardy freezes on shutdown."
date: 2008-06-25
forum: General Help
---

### Post by walkeraj on 2008-06-25
After I took the most recent pack of low-level upgrades including the (2nd?) 2.24.19 Kernel update, my system doesn't finish shutting down.  The final splash screen appears and the bar gradually changes from orange to black, but upon reaching the last little section, it freezes and will remain in this state until hard-reset (I have tested it overnight).

Any ideas?

---

### Post by Het Irv on 2008-06-25
Does the screen display any text while shutting down?

---

### Post by walkeraj on 2008-06-25
Well, I can ctr-alt switch to tty7, but, after some text about failing to stop the HAL, it returns to the graphical display and becomes unresponsive.  I should mention that this actually only happens if I click "restart" and not "shutdown".  "Shutdown" works.  "restart" does not.

---

### Post by prshah on 2008-06-25
> **walkeraj said:**
> 
 my system doesn't finish shutting down.

Any ideas?

Try this command```
sudo reboot -hni
```, and if it works, (try it 2-3 times) then post back for how to make it permanent and/or more details.

This is the only way I can get reboot/shutdown to work on my Fujitsu laptop Hardy installation.

---

### Post by walkeraj on 2008-06-25
Nope.  Same result. This is a desktop system, btw.

---

### Post by bodhi.zazen on 2008-06-25
Is the problem kernel specific ? Boot and shutdown an older kernel.

Is the problem OS specific ? Boot a live CD and shutdown.

Hopefully that will isolate the problem to kernel or OS.

It would also help if we had more information.

Go to a console.

Shut down gdm :

```
sudo /etc/init.d/gdm stop
```

Then shut down :

```
sudo shutdown -h now
```

Any error messages ? Where does it get caught up ?

---

### Post by walkeraj on 2008-07-29
> **bodhi.zazen said:**
> Is the problem kernel specific ? Boot and shutdown an older kernel.

Is the problem OS specific ? Boot a live CD and shutdown.

Hopefully that will isolate the problem to kernel or OS.

It would also help if we had more information.

Go to a console.

Shut down gdm :

```
sudo /etc/init.d/gdm stop
```

Then shut down :

```
sudo shutdown -h now
```

Any error messages ? Where does it get caught up ?

Okay, sorry it has taken me so long to reply, but I was out of town and then I forgot about it for a while.  This is mostly because it only happens when I issue a reboot command.  If I do as you say, the system will turn itself off.  If, however, I issue

```
sudo reboot now
```

The system freezes.  I was forced to take a picture of the output as it only stays on the screen for a brief time and then the console immediately switches to the graphical shutdown screen where it remains frozen as before.  Here is the last screen of output the system put into my text terminal before this:

```

 * Saving the system clock
 * Stopping firewall: ufw... [OK]
 * Shutting down ALSA... [ OK ]
 * Unmounting any overflow tmpfs from /tmp [ OK ]
Stopping UPS power management: apcupsd.
 * Terminating all remaining processes...
NetworkManager: <WARN> nm_signal_handler(): Caught signal 15, shutting down normally.

NetworkManager: <info> Caught termination signal


NetworkManager: <debug> [1217339933.837750] nm_print_open_socks(): Open Sockets List:

NetworkManager: <debug> [1217339933.849331] nm_print_open_socks(): Open Sockets List Done.

NetworkManager: <WARN>  nm_hal_deinit(): libhal shutdown failed - Connection is closed

NetworkManager: <WARN> nm_dbus_init(): nm_dbus_init() could not get the system bus.  Make sure the message bus daemon is running!

```

At this point nothing happens for about 15-20 seconds.  Then, I am taken back to the graphical shutdown screen where the system freezes and becomes unresponsive.

---

### Post by Het Irv on 2008-07-29
Do you have any Windows shares mapped to mount automatically?
I remember having a problem similar to this because it shuts down the network drivers and then tries to shut down your drives, and if you are mounting the drive in fstab, it can't see the drive anymore and freezes.  There is a fix that works will, I just have to find it again.

---

### Post by walkeraj on 2008-07-29
> **Het Irv said:**
> Do you have any Windows shares mapped to mount automatically?
I remember having a problem similar to this because it shuts down the network drivers and then tries to shut down your drives, and if you are mounting the drive in fstab, it can't see the drive anymore and freezes.  There is a fix that works will, I just have to find it again.

No.  No windows shares mounted.  I do have NFS shares mounted, however it should be shutting those down before it attempts to power off. I had at one point changed the startup priority of automount because it was running before NIS/YP, but I haven't changed the shutdown priority.  Here are the priorities for automount:

```

Runlevel  Status  Priority

0         Stop    19
1         Stop    19
2         Start   30
3         Start   30
4         Start   30
5         Start   30
6         Stop    19

```

I deleted /var/messages in an attempt to trim it down somewhat and then restarted (it froze as usual) and I killed the power.  When I powered it back on, I went into single-user mode to try and further keep the information in /var/log/messages down.  Nothing caught my eye, so I issued a reboot.  It froze *again*, but this time, the last thing displayed was:

```
[  239.390913] Restarting system
```

So... it looks as if the kernel is somehow unable to reboot my system?

---

### Post by caljohnsmith on 2008-07-29
From those error messages that you gave, walkeraj, it seems like there is something going wrong with shutting down your networking processes. Try this before you reboot:
```
sudo /etc/init.d/networking stop
```

---

### Post by walkeraj on 2008-07-29
> **caljohnsmith said:**
> From those error messages that you gave, walkeraj, it seems like there is something going wrong with shutting down your networking processes. Try this before you reboot:
```
sudo /etc/init.d/networking stop
```

That can't be the problem.  As I said in my newest post, I booted it into single-user mode the second time and it still froze.  Networking is not enabled in single-user mode.

---

### Post by caljohnsmith on 2008-07-29
> **walkeraj said:**
> That can't be the problem.  As I said in my newest post, I booted it into single-user mode the second time and it still froze.  Networking is not enabled in single-user mode.
Am I missing something here? My networking is in /etc/rcS.d/S40networking, i.e. the "System" run level, which to my understanding means it will be run for all run levels, including single-user mode.

---

### Post by walkeraj on 2008-07-29
> **caljohnsmith said:**
> Am I missing something here? My networking is in /etc/rcS.d/S40networking, i.e. the "System" run level, which to my understanding means it will be run for all run levels, including single-user mode.

I stand corrected.  My understanding is a bit out of date, it seems.  I had assumed that, since my network was not configured at boot in single-user mode that it wasn't getting activated (much in the old way of doing things), yet there it is in rcS.d.  Interestingly enough, I still can't ping in single user mode until I issue 

```
/etc/rc.d/networking start
```

Thus the source of my confusion.  Regardless of that, I can shut down the computer just fine, so it's probably something with the way the machine is being rebooted rather than the way it's being shut down.

In short:

```
sudo shutdown now
```

works

```
sudo reboot now
```

does not

---

### Post by lavinog on 2008-07-29
I get those exact networkmanager messages on a couple of my systems, and they restart fine...I would look past them.
does disabling the splash screen show any other info?

in /boot/grub/menu.lst
change quiet splash to verbose

---

### Post by walkeraj on 2008-07-29
Solved it! The solution [here]("http://ubuntuforums.org/showthread.php?p=926719") solved the problem.  I've submitted a [bug]("https://bugs.launchpad.net/ubuntu/+bug/253114") to launchpad to reflect this.

---

### Post by victor.zamanian on 2008-08-18
Oh. My. Gosh. This solves the problem I've had ever since the day Hardy was released (and I installed it). A million thanks to all who participated in figuring out what to do about this!

Just to clarify the steps you have to take to fix this (or rather, what I did to fix this):
[LIST=1]
[*]Edit menu.lst (with a text editor of your choice. This example uses nano but 'gedit' would perhaps be easier for you if you're a beginner -- it's more like Notepad in Windows):
```
$ sudo nano /boot/grub/menu.lst
```
[*]Find the line that starts with "# kopt=" and add the option "reboot=b" (without the quotation marks) at the end of the line. **Take care not to remove the initial # or do anything to the line but add the option**! Options are separated by a simple space.
[*]Run
```
$ sudo update-grub
```
to have the GRUB menu entries updated.
[*]Shutdown then start up your computer, obviously, since "rebooting" won't work until you start your computer (load the kernel) again. :-) This last step is optional in the sense that you do this at your convenience.
[/LIST]

Thanks again, guys. All the best and happy camping!


Links:
[Instructions for adding a GRUB boot option]("https://help.ubuntu.com/community/BootOptions#Making%20Permanent%20changes")

---

### Post by victor.zamanian on 2008-08-18
Awh, DARN. That fixed one problem but created another one. Now when I hibernate the system, it automatically reboots and thereby "disables" the hibernation functionality for me since (re)booting after a hibernation just resumes the desktop again.

Problem stays unsolved for me.

---

