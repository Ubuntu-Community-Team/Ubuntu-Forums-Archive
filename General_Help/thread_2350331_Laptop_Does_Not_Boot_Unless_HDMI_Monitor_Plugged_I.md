---
title: "Laptop Does Not Boot Unless HDMI Monitor Plugged In"
date: 2017-01-23
forum: General Help
---

### Post by ezacharyk on 2017-01-23
I have been using my laptop as my primary computer for a long time now. I have had very little issue using it at all. However, over the last week, my laptop no long boots unless the HDMI monitor is plugged into the HDMI port. If I remove the monitor it hangs during boot up and there is nothing I can do. I don't get any errors when the monitor is not plugged in. 

Any suggestions on a fix or how I can debug this properly?

---

### Post by Keith_Helms on 2017-01-25
I wonder if you have somehow set the hdmi monitor as the primary screen.  What kind of graphics card does your laptop have?

Your system may not actually be hung, it may just be waiting for you to sign in and it's trying to display the login prompt on the non-connected hdmi monitor.  Just to see what happens, wait a few seconds and then type your password and hit enter.  You might find that the laptop screen then comes up.

---

### Post by ezacharyk on 2017-01-25
I have a NVidia Geforce GTX 660M graphics card with the proprietary driver 367.57 installed. Both my Ubuntu Display settings and my NVidia X Server Settings have the laptop screen set as the primary. When the monitor is plugged in, both screens display my wallpaper and the login screen is on the laptop display. I can try your suggestion and let you know what happens.

---

### Post by ezacharyk on 2017-01-25
Tried your suggestion and nothing happened.

---

### Post by Keith_Helms on 2017-01-25
Any errors in /var/log/syslog?

---

### Post by oldos2er on 2017-01-25
Thread moved to *General Help*

---

### Post by ezacharyk on 2017-01-25
> **Keith_Helms said:**
> Any errors in /var/log/syslog?

There is a lot in there, but here is what is at the end of the boot attempt:

> Jan 25 20:41:13 zachary-G55VW systemd[1]: Starting NVIDIA Persistence Daemon...
Jan 25 20:41:13 zachary-G55VW kernel: [   13.321870] ACPI Warning: \_SB_.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Jan 25 20:41:13 zachary-G55VW kernel: [   13.321904] ACPI Warning: \_SB_.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Jan 25 20:41:13 zachary-G55VW kernel: [   13.321918] ACPI Warning: \_SB_.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Jan 25 20:41:13 zachary-G55VW kernel: [   13.321931] ACPI Warning: \_SB_.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Jan 25 20:41:13 zachary-G55VW kernel: [   13.321951] ACPI Warning: \_SB_.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Jan 25 20:41:13 zachary-G55VW kernel: [   13.321963] ACPI Warning: \_SB_.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Jan 25 20:41:13 zachary-G55VW kernel: [   13.321976] ACPI Warning: \_SB_.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Jan 25 20:41:13 zachary-G55VW kernel: [   13.321990] ACPI Warning: \_SB_.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Jan 25 20:41:13 zachary-G55VW kernel: [   13.322018] ACPI Warning: \_SB_.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Jan 25 20:41:13 zachary-G55VW nvidia-persistenced: Verbose syslog connection opened
Jan 25 20:41:13 zachary-G55VW nvidia-persistenced: Now running with user ID 120 and group ID 129
Jan 25 20:41:13 zachary-G55VW systemd[1]: Started NVIDIA Persistence Daemon.
Jan 25 20:41:13 zachary-G55VW nvidia-persistenced: Started (1752)
Jan 25 20:41:13 zachary-G55VW kernel: [   13.354519] ACPI Warning: \_SB_.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
Jan 25 20:41:13 zachary-G55VW nvidia-persistenced: device 0000:01:00.0 - registered
Jan 25 20:41:13 zachary-G55VW nvidia-persistenced: Local RPC service initialized
Jan 25 20:41:13 zachary-G55VW kernel: [   13.482610] nvidia-modeset: Allocated GPU:0 (GPU-04acdf2b-0d67-96e0-922e-e7883b20b863) @ PCI:0000:01:00.0
Jan 25 20:41:16 zachary-G55VW colord[1275]: (colord:1275): Cd-WARNING **: failed to get session [pid 1318]: No such device or address
Jan 25 20:41:16 zachary-G55VW NetworkManager[1134]: <info>  [1485398476.5337] WiFi hardware radio set enabled
Jan 25 20:41:16 zachary-G55VW NetworkManager[1134]: <info>  [1485398476.5337] WWAN hardware radio set enabled
Jan 25 20:41:17 zachary-G55VW kernel: [   17.169375] nvidia-modeset: Freed GPU:0 (GPU-04acdf2b-0d67-96e0-922e-e7883b20b863) @ PCI:0000:01:00.0
Jan 25 20:41:17 zachary-G55VW failsafeXServer[1714]: (EE)
Jan 25 20:41:17 zachary-G55VW failsafeXServer[1714]: Fatal server error:
Jan 25 20:41:17 zachary-G55VW failsafeXServer[1714]: (EE) no screens found(EE)
Jan 25 20:41:17 zachary-G55VW failsafeXServer[1714]: (EE)
Jan 25 20:41:17 zachary-G55VW failsafeXServer[1714]: Please consult the The X.Org Foundation support
Jan 25 20:41:17 zachary-G55VW failsafeXServer[1714]: #011 at [http://wiki.x.org](http://wiki.x.org)
Jan 25 20:41:17 zachary-G55VW failsafeXServer[1714]:  for help.
Jan 25 20:41:17 zachary-G55VW failsafeXServer[1714]: (EE) Please also check the log file at "/var/log/Xorg.failsafe.log" for additional information.
Jan 25 20:41:17 zachary-G55VW failsafeXServer[1714]: (EE)
Jan 25 20:41:17 zachary-G55VW failsafeXServer[1714]: (EE) Server terminated with error (1). Closing log file.
Jan 25 20:41:17 zachary-G55VW nvidia-persistenced: Received signal 15
Jan 25 20:41:17 zachary-G55VW systemd[1]: Stopping NVIDIA Persistence Daemon...
Jan 25 20:41:17 zachary-G55VW nvidia-persistenced: Socket closed.
Jan 25 20:41:17 zachary-G55VW nvidia-persistenced: PID file unlocked.
Jan 25 20:41:17 zachary-G55VW nvidia-persistenced: PID file closed.
Jan 25 20:41:17 zachary-G55VW nvidia-persistenced: The daemon no longer has permission to remove its runtime data directory /var/run/nvidia-persistenced
Jan 25 20:41:17 zachary-G55VW nvidia-persistenced: Shutdown (1752)
Jan 25 20:41:17 zachary-G55VW systemd[1]: Stopped NVIDIA Persistence Daemon.
Jan 25 20:41:28 zachary-G55VW failsafeXServer[1714]: xinit: giving up
Jan 25 20:41:28 zachary-G55VW failsafeXServer[1714]: xinit: unable to connect to X server: Connection refused
Jan 25 20:41:28 zachary-G55VW failsafeXServer[1714]: xinit: server error
Jan 25 20:41:37 zachary-G55VW kernel: [   36.984191] usb 1-1.4: reset high-speed USB device number 5 using ehci-pci
Jan 25 20:41:38 zachary-G55VW systemd-timesyncd[952]: Synchronized to time server [2001:67c:1560:8003::c8]:123 (ntp.ubuntu.com).

This is the contents of the /var/log/Xorg.failsafe.log referenced:

[http://pastebin.com/P5caSmkR](http://pastebin.com/P5caSmkR)

---

### Post by papibe on 2017-01-25
Hi ezacharyk.

Do you have a custom /etc/X11/xorg.conf ?

If so, try to rename it:
```
sudo mv -iv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
and may be even the fail safe too:
```
mv -iv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf.failsafe.old
```
reboot, and let us know how it goes.
Regards.

---

### Post by Keith_Helms on 2017-01-25
For some reason it's not finding a screen it thinks it can use.  Have any files been changed recently in /usr/share/X11/xorg.conf.d or /etc/X11?  A config file with a recent date might be a clue as to what went wrong.

You can always try reinstalling the nvidia driver
```
sudo apt-get install --reinstall nvidia-367
```

---

### Post by ezacharyk on 2017-01-26
I don't have a xorg.conf file and I tried renaming the failsafe file but it didn't help.

---

### Post by ezacharyk on 2017-01-26
I tried switching out the graphics driver to the Nouveau driver and my laptop was able to boot without the HDMI monitor. However, the laptop screen resolution was locked at the lowest possible setting with no ability to change it. Switching back to the 367 driver didn't fix. I will try to run the reinstall command.

As for any changes I have made, I was trying to fix some bluetooth issues I was having and tried a few things from this askUbuntu thread:

askubuntu.com/questions/465442/bluetooth-is-disable-on-ubuntu-14-04

However, I reversed those changes when it didn't fix my issue. 

I honestly don't know how long this has been an issue with my laptop as I haven't taken it anywhere in months.

---

### Post by ezacharyk on 2017-01-26
Alright. Reinstalling the 367 driver didn't work. Switching to the 340 driver didn't work. I did another test and the laptop boots when a VGA monitor is plugged in. So it seems that the laptop is expecting some kind of external monitor whether VGA or HDMI.

---

