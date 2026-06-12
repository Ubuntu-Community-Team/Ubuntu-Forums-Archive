---
title: "monitor brightness not saved on shutdown"
date: 2015-11-25
forum: General Help
---

### Post by daobra_daloosh on 2015-11-25
Hello all,

I recently installed ubuntu 14.04 LTS on my Vaio laptop and am really happy with it. I do have two issues of which I will list one here.

The brightness level in system preferences is not saved on shutdown. So each time I startup the screen is at full brightness. Anyone any ideas on how to troubleshoot this?

---

### Post by Melnik_Hoogland on 2015-11-25
There's already been a topic on this, but I had to modify it some to make it work. Based on sophie5's post at [http://ubuntuforums.org/showthread.php?t=2163556&p=13217954](http://ubuntuforums.org/showthread.php?t=2163556&p=13217954):[B]

Step 1[/B]
Create two scripts in your home directory.

[FONT=courier new]Put the following in ~/brightness-save.sh[/FONT]:
```

[FONT=courier new]#!/bin/bash


SAVEFILE="/var/brightness/last_brightness"


mkdir -p $(dirname $SAVEFILE)


cat /sys/class/backlight/acpi_video0/brightness > $SAVEFILE
#echo "Current screen brightness saved as "$(cat $SAVEFILE)"."


exit 0[/FONT]

```

[FONT=courier new]And put this in ~/brightness-reset.sh[/FONT]:
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
[FONT=courier new]gksudo gedit /etc/rc.local[/FONT]
```
If gksudo isn't installed, install it:
```
[FONT=courier new]sudo apt-get install gksu[/FONT]
```

Insert the following code just before line with [FONT=courier new]exit 0[/FONT]. (be sure to save it afterwards)
```
[FONT=courier new]etc/init.d/brightness-reset.sh[/FONT]
```

**Step 4**
You can delete [FONT=courier new]brightness-save.sh[/FONT] and [FONT=courier new]brightness-reset.sh[/FONT] from your home directory.

Tested and working on my Acer Aspire E11 with 14.04.

---

### Post by daobra_daloosh on 2015-11-25
OK I tried this, unfortunately it didn't work. I am however  not used to using terminal so at first I have executed the commands in [FONT=courier new]brightness-save.sh[/FONT] in terminal. That went until the last line 
[FONT=courier new]cat /sys/class/backlight/acpi_video0/brightness > $SAVEFILE

Not sure if that messed things up but unfortunately no fix just yet. Anything I can check or try?[/FONT]

Thanks for your help!

---

### Post by Melnik_Hoogland on 2015-11-25
Make sure you've rebooted at least once since you set the brightness scripts up (to make sure there is (or at least should be) a brightness save file) then execute these commands and post the output (in code tags please):
```
cat /var/brightness/last_brightness
cat /sys/class/backlight/acpi_video0/brightness
cat /etc/init.d/brightness-save.sh
cat /etc/init.d/brightness-reset.sh
ls -l /etc/rc0.d/S10brightness-save /etc/rc6.d/S10brightness-save
cat /etc/rc.local
```
This will help us debug what is going on.

Also, what do you mean by "that went until the last line"? Did the last line give an error? If it did, please post the error, again in code tags please.

EDIT: Just looked at some posts about controlling brightness levels on Vaios; I'm going to wait for you to post the output of those commands but if I'm right I think I know what's going on and how to fix it.

---

### Post by daobra_daloosh on 2015-11-26
Hi Melnik,

Last night it din't work out but this morning it did! Don't know why but it does so I'm a happy camper now!

Thanks a lot!

Daobra

---

### Post by Melnik_Hoogland on 2015-11-26
No problem. Please mark the thread as solved from the "Thread Tools" menu right above the first post in this thread.

---

