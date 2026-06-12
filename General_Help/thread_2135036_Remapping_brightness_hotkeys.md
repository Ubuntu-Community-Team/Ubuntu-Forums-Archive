---
title: "Remapping brightness hotkeys"
date: 2013-04-13
forum: General Help
---

### Post by cuptos on 2013-04-13
I have just installed Ubuntu 12.10 on my netbook Packard Bell dot s with Intel GMA3600 graphics and everything works pretty well but the hotkeys on the keyboard to regulate the screen brightness, which don't work at all, either on Ubuntu or Xubuntu desktop.

I have been browsing and Ubuntu and my netbook doesn't seem to get along with this issue ([http://ubuntuforums.org/showthread.php?t=2127253&highlight=packard+bell+dot+brightness](http://ubuntuforums.org/showthread.php?t=2127253&highlight=packard+bell+dot+brightness))
However, I can vary the brightness level from the terminal with
```
echo X | sudo tee /sys/class/backlight/psb-bl/brightness
```
where X is the brightness level, so the problem is not that serious,

I am wondering if there is any way to assign a command to this keys so that when pressed, brightness increases or decreases 10 percent, or  to a fixed amount at least, which would fix my problem quite fast.

Thank you. O:)

---

### Post by Toz on 2013-04-13
Hello and welcome to the forums.

If you open a terminal window, execute this command (enter your password when prompted):
```
sudo acpi_listen
```
...then press the function+brightness-up and function+brightness_down keys, do any events register (does anything display on the terminal window)?

If so, we can use a modified version of [this procedure]("http://ubuntuforums.org/showthread.php?t=2084054&p=12357584&viewfull=1#post12357584") to create new acpi events specific for your device.

If not, we'll need to create a script to do it.

Either way, we'll need the results of this command to proceed:
```
grep . /sys/class/backlight/psb-bl/*
```

---

### Post by cuptos on 2013-04-14
Thank you for answering

```
pikachu@White:~$ sudo acpi_listen
video DD02 00000086 00000000
±video DD02 00000087 00000000
```

That's what appears when I press brightness up and brightness down keys (in that order). Once I have run  acpi_listen, both keys work correctly changing the brightness level (a brightness icon with a level bar show up on the display), even after closing the terminal. 

I have noticed that when I press the brightness up key, it actually changes the brightness, but also a "±" is printed (as you can see in the acpi_listen report).

```
pikachu@White:~$ grep . /sys/class/backlight/psb-bl/*
/sys/class/backlight/psb-bl/actual_brightness:100
/sys/class/backlight/psb-bl/bl_power:0
/sys/class/backlight/psb-bl/brightness:100
/sys/class/backlight/psb-bl/max_brightness:100
grep: /sys/class/backlight/psb-bl/power: Es un directorio
grep: /sys/class/backlight/psb-bl/subsystem: Es un directorio
/sys/class/backlight/psb-bl/type:platform
```

Thank you

---

### Post by cuptos on 2013-04-14
I want to add that I have modified my GRUB (before starting this post) like this
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **acpi_backlight=vendo**r"
```
without this, I cannot change brightness anyway (checked).

---

### Post by Toz on 2013-04-14
So, do the function keys now work?

---

### Post by cuptos on 2013-04-14
Excuse me, I totally forgot to mention that when I reboot, I have to run again acpi_listen to make these function keys work.

---

### Post by Toz on 2013-04-14
> **cuptos said:**
> Excuse me, I totally forgot to mention that when I reboot, I have to run again acpi_listen to make these function keys work.

?! That is really weird!
Lets move ahead with creating a special set of acpi listeners for those codes and see if it works after reboot.

Create the following files with the following content (you will need root privileges to do this, so something like "gksu gedit <file>" where <file> is: )

1. /etc/acpi/events/brightness-up
```

event=video DD02 00000086 00000000
action=/etc/acpi/brightup.sh

```

2. /etc/acpi/events/brightness-down
```

event=video DD02 00000087 00000000
action=/etc/acpi/brightdown.sh
```

3. /etc/acpi/brightdown.sh
```

#!/bin/bash
curr=`cat /sys/class/backlight/psb-bl/actual_brightness`
if [ $curr -gt 11 ]; then
   curr=$((curr-12));
   echo $curr  > /sys/class/backlight/psb-bl/brightness;
fi
```

4. /etc/acpi/brightup.sh
```

#!/bin/bash
curr=`cat /sys/class/backlight/psb-bl/actual_brightness`
if [ $curr -lt 89 ]; then
   curr=$((curr+12));
   echo $curr  > /sys/class/backlight/psb-bl/brightness;
fi
```

Make all 4 of those scripts executable via:
```

sudo chmod +x /etc/acpi/events/brightness-up
sudo chmod +x /etc/acpi/events/brightness-down
sudo chmod +x /etc/acpi/brightdown.sh
sudo chmod +x /etc/acpi/brightup.sh
```

Reboot and test.

---

### Post by cuptos on 2013-04-14
Thank you very much! It works flawlessly!
Finishing, may I ask how to stop that ± from coming up when brightness up key is pressed?
Thank you once more

---

### Post by Toz on 2013-04-14
> **cuptos said:**
> Finishing, may I ask how to stop that ± from coming up when brightness up key is pressed?

I think that its just an errant display - it doesn't seem to affect the system so its probably safe to just ignore it.

If you don't mind, can you make this thread as solved so others may benefit? 
_Mark as solved Procedure:_
Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.

Thanks

---

