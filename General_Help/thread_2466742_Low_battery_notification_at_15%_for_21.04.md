---
title: "Low battery notification at 15% for 21.04"
date: 2021-09-04
forum: General Help
---

### Post by meetdilip on 2021-09-04
Hello, is it possible to set 2 notification popups one at 15% and 10% for the low battery in 21.04 ? Thanks.

---

### Post by steve234 on 2021-09-04
I've not had to do this (my 20.04 machine is a desktop) but there appears to be an [ask.ubuntu thread]("https://askubuntu.com/questions/1107397/no-low-battery-notification-on-ubuntu-18-04") from a year ago covering this. 

That thread suggests that you edit you edit ```
PercentageLow
```, and ```
PercentageCritical
``` in /etc/UPower/UPower.conf

---

### Post by TheFu on 2021-09-04
> **meetdilip said:**
> Hello, is it possible to set 2 notification popups one at 15% and 10% for the low battery in 21.04 ? Thanks.

Yes. A little script that you can modify for your needs.  Add the popups instead of using an alarm sound ... or do both.
```
#!/bin/bash

# Battery 0: Not charging, 100
BATT=$(acpi -i |grep -v capacity \
|sed -e 's/^.*[cC]harging, //g' -e 's/\%.*$//' \
|sed -e 's/^.*Discharging, //g' -e 's/\%.*$//')

# echo \"$BATT\"

if [ 50 -ge $BATT ] ; then
   wall "==INFO== Low battery: $BATT"
   mpv /usr/share/sounds/ubuntu/stereo/phone-incoming-call.ogg
else
   echo "==INFO== Battery Level: $BATT %"
fi
```

There are a few different menu popup commands with a simple "ok" button to make them go away.  They are usually based on dialog - xdialog, kdialog,  zenity, rofi, ... you get the idea.  Lots of easy popup menus.

---

### Post by meetdilip on 2021-09-04
Thanks @steve234

@TheFu

I tried the script and it is working great. How can I make sure that it is checking every 5 minutes ? Thanks.

---

### Post by TheFu on 2021-09-04
> **meetdilip said:**
> Thanks @steve234

@TheFu

I tried the script and it is working great. How can I make sure that it is checking every 5 minutes ? Thanks.

Run it in a loop with a 5m sleep?
or
Use cron.  And good beginner Unix/Linux book should have a section on cron and crontabs. I've written a few times about cron scripting pitfalls here.  In general, it isn't a good idea to use cron with things that interact with a desktop GUI, since cron runs even when people aren't logged in at all.  That might be something you want to add to the script - to tell if there is an active desktop and who the userid running it is.  Then send that user the announcement.  The "wall" command can be used, since that goes to all users with open terminals on the system, local and remote.

---

### Post by meetdilip on 2021-09-05
Do you think this one will not be intense ? I mean, will not check too often but will still work ? Thanks.

```
#!/bin/bash

while true

do

# Battery 0: Not charging, 100
BATT=$(acpi -i |grep -v capacity \
|sed -e 's/^.*[cC]harging, //g' -e 's/\%.*$//' \
|sed -e 's/^.*Discharging, //g' -e 's/\%.*$//')

# echo \"$BATT\"

if [ 18 -ge $BATT ] ; then
notify-send -i "$PWD/lowbatt.png" "Battery Low." "Level: ${BATT}% "
   wall "==INFO== Low battery: $BATT"
   mpv /home/njan/Music/lowbattery.mp3
else
   echo "==INFO== Battery Level: $BATT %"
   
fi

    sleep 300 # (5 minutes)
done

```

---

### Post by TheFu on 2021-09-05
Try it. See if it works.  You can change the 18 --> 95 temporarily, right?

I tried to use notify-send and it didn't work.
What you have isn't wrong, but I'd use **sleep 5m**.  Sleep has supported h/m/s  suffixes for a while now.  Fewer characters in a script should reduce the chance of bugs.

And I violated a number of "best practices" for scripting by not using the exact location for each program used.
mpv --> /usr/bin/mpv    for example.  Never trust that a PATH will be correct in any script.

---

### Post by meetdilip on 2021-09-05
Thanks. I installed mpv.

---

### Post by TheFu on 2021-09-05
> **meetdilip said:**
> Thanks. I installed mpv.

Perhaps I wasn't clear.
mpv in the script needs to be /usr/bin/mpv.
sed needs to be __________
acpi  needs to be __________
notify-send needs to be __________
wall needs to be __________

Fill in the blanks and update the script.

mpv is just an audio player.  Any can be used.  Also, the file to be played needs to work how you like WITH the volume you prefer.

Use the "which" command to find the locations for programs.
```
$ which mpv
/usr/bin/mpv
```

---

### Post by meetdilip on 2021-09-05
Ok. Thanks.

---

