---
title: "Save Screen Brightness Settings"
date: 2013-07-18
forum: General Help
---

### Post by cessanfrancisco on 2013-07-18
Hi,

I am running Ubuntu 13.04 32bit on an Asus UL80JT.

Is there a way to set Ubuntu to remember my screen brightness setting?

I managed to enable the controls so that the screen brightness can be increased and decreased.  I like to have the brightness set around 50-60%.  However, whenever I turn on my computer the screen brightness is back at 100%.  I'd like for the screen brightness be at the same level it was, from the previous session, when turning the computer on.

Thanks in advance.

---

### Post by fffree on 2013-07-31
This is possible, but you have to add your own scripts to the startup and shutdown sequences. Doing the following will save the current screen brightness when you shutdown or reboot your computer and restore to the same brightness setting when you start the computer.

**Step 1**
Save the following script in your home directory, as [FONT=fixedsys][FONT=courier new]~/brightness-reset.sh[/FONT][/FONT]
```
#!/bin/bash

DEFAULT_BRIGHTNESS=7
SAVEFILE="/var/brightness/last_brightness"

if [ -f $SAVEFILE ];
then
   echo $(cat $SAVEFILE) > /sys/class/backlight/acpi_video0/brightness
    #echo "Screen brightness reset to "$(cat $SAVEFILE)"."
else
   echo $DEFAULT_BRIGHTNESS > /sys/class/backlight/acpi_video0/brightness
    #echo "Screen brightness set to default ("$DEFAULT_BRIGHTNESS")."
fi

exit 0

```
And this script as [FONT=courier new]~/brightness-save.sh[/FONT]
```
#!/bin/bash

SAVEFILE="/var/brightness/last_brightness"

mkdir -p $(dirname $SAVEFILE)

cat /sys/class/backlight/acpi_video0/brightness > $SAVEFILE
#echo "Current screen brightness saved as "$(cat $SAVEFILE)"."

exit 0

```

**Step 2**
Open a terminal and go to your come directory ([FONT=courier new]cd ~/[/FONT]). Then run the following commands, one after another:
```
sudo bash
```
```
cp ./brightness-reset.sh /etc/init.d/
```
```
cp ./brightness-save.sh /etc/init.d/
```
```
chmod +x /etc/init.d/brightness-reset.sh
```
```
chmod +x /etc/init.d/brightness-save.sh
```
```
ln -s /etc/init.d/save-brightness.sh /etc/rc0.d/K10brightness-save
```
```
ln -s /etc/init.d/save-brightness.sh /etc/rc6.d/K10brightness-save
```
```
exit
```

**Step 4**
Open the file [FONT=courier new]/etc/rc.local[/FONT] with this command: ```
gksu gedit /etc/rc.local
```
The last line of this script should read [FONT=courier new]exit 0[/FONT].
Just before this, insert the following code:
```
#Reset screeen brightness
/etc/init.d/reset-brightness.sh

```
Make sure the last line of the script is still [FONT=courier new]exit 0[/FONT]!
Save and exit gedit.

**Step 5**
Delete the files [FONT=courier new]brightness-reset.sh[/FONT] and [FONT=courier new]brightness-save.sh[/FONT] from your home directory


That's all, adjust your screen brightness in the usual way and restart your computer. It should now start with the exact same brightness setting you had when you shut it down :)

---

### Post by hungrybelly on 2014-01-31
> **fffree said:**
> [solution]

I tried this in Xubuntu 12.04 on my Acer Aspire One 722 and it didn't work. I'd previously enabled the ATI/AMD proprietary FGLRX graphics driver to get my brightness controls to work -- do I maybe need to change the script to reflect this somehow?

---

### Post by Tornikee on 2014-09-21
I have exactly the same issue. I followed the instructions above, but the brightness level was back at 100% after restart.

Ubuntu 14.04 x64
Acer Aspire V3-772G

---

### Post by CantankRus on 2014-09-21
Test if xrandr will change your brightness.
Firstly find your active display...
```
xrandr -q | awk '/ connected/ {print $1}'
```
eg
```
@Trusty:~$ xrandr -q | awk '/ connected/ {print $1}'
[COLOR="#FF0000"]DVI-I-2[/COLOR]
```

Then to change brightness use...
xrandr --output [COLOR="#FF0000"]<displayName>[/COLOR] --brightness <value (0.00 to 1.0)>
eg for me
```
xrandr --output [COLOR="#FF0000"]DVI-I-2[/COLOR] --brightness 0.85
```

When using unity/compiz I can use this script to set the brightness after compiz has loaded.
Save as _brightness.sh_, make executable and use your [COLOR="#FF0000"]displayName[/COLOR].
```
#!/bin/bash

until (pidof compiz)
  do
    echo "waiting for compiz..."
    sleep 2
  done
sleep 1
xrandr --output [COLOR="#FF0000"]DVI-I-2[/COLOR] --brightness 0.85
exit 0
```

Add the full path to the script to Startup Applications.

---

### Post by Tornikee on 2014-09-22
Thanks for the instructions. The change brightness command changed the brightness to a different (cooler) colour tone though, compared to when I change it via keyboard hotkey. Is that normal?

---

### Post by CantankRus on 2014-09-22
> **Tornikee said:**
> Thanks for the instructions. The change brightness command changed the brightness to a different (cooler) colour tone though, compared to when I change it via keyboard hotkey. Is that normal?
Ignore what I wrote....this thread seems to be about laptop screen backlight.
Possibly look at xbacklight to use in the same manner, replacing the xrandr command.
[http://manpages.ubuntu.com/manpages/trusty/man1/xbacklight.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/xbacklight.1.html)

---

### Post by sophie5 on 2015-01-29
The scripts by fffree work, thank you fffree. But there are some mistakes in his procedure.

Here is the correct procedure:

[B]Step 1
[/B]Create two scripts in your home directory.

[FONT=courier new]~/brightness-save.sh[/FONT] contains:
```

[FONT=courier new]#!/bin/bash


SAVEFILE="/var/brightness/last_brightness"


mkdir -p $(dirname $SAVEFILE)


cat /sys/class/backlight/acpi_video0/brightness > $SAVEFILE
#echo "Current screen brightness saved as "$(cat $SAVEFILE)"."


exit 0[/FONT]

```

[FONT=courier new]~/brightness-reset.sh[/FONT] contains
```

[FONT=courier new]#!/bin/bash


DEFAULT_BRIGHTNESS=7
SAVEFILE="/var/brightness/last_brightness"


if [ -f $SAVEFILE ];
then
   echo $(cat $SAVEFILE) > /sys/class/backlight/acpi_video0/brightness
    #echo "Screen brightness reset to "$(cat $SAVEFILE)"."
else
   echo $DEFAULT_BRIGHTNESS > /sys/class/backlight/acpi_video0/brightness
    #echo "Screen brightness set to default ("$DEFAULT_BRIGHTNESS")."
fi


exit 0[/FONT]

```

**Step 2**
Open a terminal, go to your home directory ([FONT=courier new]cd ~/[/FONT]) and run the following commands, one after another:

```

[FONT=courier new]sudo bash
[/FONT][FONT=courier new]cp ./brightness-reset.sh /etc/init.d
[/FONT][FONT=courier new]cp ./brightness-save.sh /etc/init.d
[/FONT][FONT=courier new]chmod +x /etc/init.d/brightness-reset.sh
[/FONT][FONT=courier new]chmod +x /etc/init.d/brightness-save.sh
[/FONT][FONT=courier new]ln -s /etc/init.d/brightness-save.sh /etc/rc0.d/S10brightness-save
[/FONT][FONT=courier new]ln -s /etc/init.d/brightness-save.sh /etc/rc6.d/S10brightness-save
[/FONT][FONT=courier new]exit[/FONT]

```

**Step 3**
Open the file [FONT=courier new]/etc/rc.local[/FONT] as root:
```
[FONT=courier new]gksu gedit /etc/rc.local[/FONT]
```

Insert the following code just before line with [FONT=courier new]exit 0[/FONT].
```
[FONT=courier new]etc/init.d/brightness-reset.sh[/FONT]
```

**Step 4**
You can delete [FONT=courier new]bightness-save.sh[/FONT] and [FONT=courier new]bightness-reset.sh[/FONT] from your home directory.

---

