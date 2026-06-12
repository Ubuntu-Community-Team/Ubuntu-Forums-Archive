---
title: "How do I save screen brightness after logging out from a session ?"
date: 2013-05-06
forum: General Help
---

### Post by Veren on 2013-05-06
Hello,
I am currently using 13.04 on an Asus laptop and I have this issue that anytime I start the system, or even wake it up, the screen and keyboard backlights are all the way up. Is there a way to 'save' the setting in a session so that the system will remember them ? I am using nouveau drivers. Thanks

---

### Post by Toz on 2013-05-06
What is the model number of the Asus laptop?

Are you currently using any kernel boot parameters? To check, open a terminal window, enter the following command:
```
cat /proc/cmdline
```
...and post back the results.

---

### Post by Linuxisfast on 2013-05-06
create a start up entry with xgamma -gamma xx where xx represents your value of gamma, next time you reboot, it will stick.

---

### Post by Nick8 on 2013-05-07
The brightness setting should be stored  in the file /sys/class/backlight/acpi_video0/brightness or  /sys/class/backlight/intel_backlight/brightness

Changing the number in one of these files should change the brightness.

To set the default brightness, add an entry to /etc/rc.local so that the bottom of the file looks like:

```

echo [x] > /sys/class/backlight/acpi_video0/brightness
exit 0

```

or

```

echo [x] > /sys/class/backlight/intel_backlight/brightness
exit 0

```

depending on which file is on your system.

[x] is a number usually from 0 to 10, but it varies between systems.

---

### Post by Veren on 2013-05-08
> **Toz said:**
> What is the model number of the Asus laptop?

Are you currently using any kernel boot parameters? To check, open a terminal window, enter the following command:
```
cat /proc/cmdline
```
...and post back the results.

It is a G73sw, the output is 

```
 BOOT_IMAGE=/vmlinuz-3.8.0-19-generic root=UUID=3368c59f-189a-482d-b7b9-355a92b08255 ro quiet splash vt.handoff=7 
```

I didn't change anything in that line.

---

### Post by Veren on 2013-05-08
> **Nick8 said:**
> The brightness setting should be stored  in the file /sys/class/backlight/acpi_video0/brightness or  /sys/class/backlight/intel_backlight/brightness

Changing the number in one of these files should change the brightness.

To set the default brightness, add an entry to /etc/rc.local so that the bottom of the file looks like:

```

echo [x] > /sys/class/backlight/acpi_video0/brightness
exit 0

```

or

```

echo [x] > /sys/class/backlight/intel_backlight/brightness
exit 0

```

depending on which file is on your system.

[x] is a number usually from 0 to 10, but it varies between systems.


Thank you, the first one worked (with acpi_video0). Marking this as SOLVED. I believe the keyboard backlight could be set similarly ?

---

### Post by Nick8 on 2013-05-08
I think keyboard backlight brightness can be set by editing the file /sys/class/leds/keyboard-backlight/brightness

But I'm not sure about this, since I don't have a keyboard backlight.

If there's no such file on your system, you could try looking around in /sys/class for an appropriate file to edit. Different systems have different files and folders in /sys/class depending on their hardware.

---

