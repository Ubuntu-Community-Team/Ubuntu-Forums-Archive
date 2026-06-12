---
title: "Screen brightness defaults to zero (black) at startup"
date: 2013-09-05
forum: General Help
---

### Post by Donny Bahama on 2013-09-05
On an HP laptop running Mint 13 Cinnamon, the screen brightness is turned all the way down to zero at startup. It's really annoying. I tried the solution posted [here]("http://unix.stackexchange.com/questions/65946/setting-default-brightness-level-on-startup-for-all-run-levels/65986#65986"), and it worked initially - but it doesn't work any more. (I've checked rc.local - the fix is still there... it just doesn't do its job any more.)

Can anyone suggest an alternative? Or troubleshooting measures to figure out why the original fix stopped working? This is really perplexing!

---

### Post by Toz on 2013-09-05
What model of hp laptop do you have?

Can you run the following commands in a terminal window and post back the results:

1. Your kernel boot parameter line:
```
cat /proc/cmdline
```

2. Your backlight interfaces:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; cat $i/actual_brightness; done
```

3. Your video card information:
```
lspci -k | grep -A3 VGA
```

---

### Post by Donny Bahama on 2013-09-05
Thanks so much for the help, Toz! The laptop is a g7-1310us.

```
 ~ $ cat /proc/cmdline
BOOT_IMAGE=/vmlinuz-3.2.0-23-generic root=UUID=c254b4b8-5b7e-4e53-9424-c513669fe3b5 ro quiet splash vt.handoff=7

```

```
 ~ $ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; cat $i/actual_brightness; done
/sys/class/backlight/acpi_video0
8
10
8
/sys/class/backlight/intel_backlight
4882
4882
3905

```
When I change the brightness manually, the value in acpi_video0/brightness changes, so the line I have in rc.local is:
```
echo 10 > /sys/class/backlight/acpi_video0/brightness
```
As I mentioned, this worked for a little while.

```
 ~ $ lspci -k | grep -A3 VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
    Subsystem: Hewlett-Packard Company Device 1671
    Kernel driver in use: i915
    Kernel modules: i915

```

---

### Post by Toz on 2013-09-05
> **Donny Bahama said:**
> 
When I change the brightness manually, the value in acpi_video0/brightness changes, so the line I have in rc.local is:
```
echo 10 > /sys/class/backlight/acpi_video0/brightness
```
As I mentioned, this worked for a little while.
Just to confirm: if you echo that value in manually after you're logged in, the brightness changes. Correct?

Can you post back the full contents of /etc/rc.local as well as:
```
ls -l /etc/rc.local
```

Also, have a look in syslog for a possible error message:
```
cat /var/log/syslog | grep -i acpi_video0
```

_Another suggestion:_
You have 2 backlight interfaces. You might want to try the **acpi_backlight=vendor** kernel parameter. This parameter should remove the acpi_video0 interface leaving only the intel_backlight interface. It might solve the blank screen on boot issue for you rendering this fix unneccessary. See the "Kernel Boot Parameters" link in my signature for more information on how to test the parameter.

---

### Post by matt_symes on 2013-09-05
Hi

Try all of Toz's suggestions first but if it is not fixed then move the brightness command into it's own file and call it from the lightdm configuration file.

You can copy and paste (and do copy and paste to eliminate errors) these commands into the terminal.

```
echo "echo 10 > /sys/class/backlight/acpi_video0/brightness" | sudo tee /usr/increase_brightness
```

```
sudo chmod 755 /usr/increase_brightness
```

```
sudo sed -i '/\[SeatDefaults\]/ a\display-setup-script=\/usr\/increase_brightness' /etc/lightdm/lightdm.conf
```

Hopefully that may fix it, if other fixes don't work.

EDIT:

If display-setup-script does not work then you can try session-setup-script but, IIRC, display-setup-script is the correct script to call.

Kind regards

---

### Post by Donny Bahama on 2013-09-06
> **Toz said:**
> Just to confirm: if you echo that value in manually after you're logged in, the brightness changes. Correct?
Sort of... it doesn't work with (or without) sudo, but if I su first, then it does.

> Can you post back the full contents of /etc/rc.local as well as:
```
ls -l /etc/rc.local
```

There's nothing else (other than comments) in rc.local...
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo 10 > /sys/class/backlight/acpi_video0/brightness
exit 0
```

```
 ~ $ ls -l /etc/rc.local
-rwxr-xr-x 1 root root 360 Aug 31 11:46 /etc/rc.local
 ~ $ 

```

> Also, have a look in syslog for a possible error message:
```
cat /var/log/syslog | grep -i acpi_video0
```
That returned no output.

> _Another suggestion:_
You have 2 backlight interfaces. You might want to try the **acpi_backlight=vendor** kernel parameter. This parameter should remove the acpi_video0 interface leaving only the intel_backlight interface. It might solve the blank screen on boot issue for you rendering this fix unneccessary. See the "Kernel Boot Parameters" link in my signature for more information on how to test the parameter.
Before I do that, I feel I should let you know that whatever I do with the brightness, the value of intel_backlight/brightness never changes. (It's always 4882.)

---

### Post by Donny Bahama on 2013-09-06
> **matt_symes said:**
> Hi

Try all of Toz's suggestions first but if it is not fixed then move the brightness command into it's own file and call it from the lightdm configuration file.

You can copy and paste (and do copy and paste to eliminate errors) these commands into the terminal.

```
echo "echo 10 > /sys/class/backlight/acpi_video0/brightness" | sudo tee /usr/increase_brightness
```

```
sudo chmod 755 /usr/increase_brightness
```

```
sudo sed -i '/\[SeatDefaults\]/ a\display-setup-script=\/usr\/increase_brightness' /etc/lightdm/lightdm.conf
```

Hopefully that may fix it, if other fixes don't work.

EDIT:

If display-setup-script does not work then you can try session-setup-script but, IIRC, display-setup-script is the correct script to call.

Kind regards
***That worked!*** And it was display-setup-script. I hope this fix is permanent!

Thank you very much for the help, Matt & Toz!

---

