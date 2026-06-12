---
title: "Set Backlight on Resume Script"
date: 2012-12-06
forum: General Help
---

### Post by AgentOrange96 on 2012-12-06
Hello, I have an Acer 5734Z (running Bodhi, technically, but based on Ubuntu.) And there is a problem where the backlight doesn't automatically turn on. In order to turn it on, I must hit the screen brightness keys on my laptop. I can also resume the backlight by typing into terminal:
```
xbacklight -set 0
```
(It is good to note that the backlight values are backwards on my computer, so 0 is brightest and 100 is the most dim.)

So, I have the following in /etc/pm/sleep.d:
```
#! /bin/bash
#This makes the backlight set to 0 when the computer resumes.
case $1 in
suspend)
#echo "Suspeding ..."
;;
resume)
COMMAND="xbacklight -set 0"
;;
hibernate)
#echo "Hibernating ..."
;;
thaw)
COMMAND="xbacklight -set 0"
;;
esac
exit 0
```

When I first added this script, it ran beautifully. However, since I have restarted my computer, it hasn't worked. (I turn my computer off every night.) It doesn't seem that the script is even running. Does anyone know why? Any help would be much appreciated. Thanks!

---

### Post by Toz on 2012-12-06
Hello and welcome to the forums.

I'm not sure why the script isn't running, there may be some information in the /var/log/pm-suspend.log file to indicate why its failing.

As an alternative, you could directly echo brightness values into the backlight interface files. To do so, you would echo a value between 0 and the contents of the file **max_brightness** to the **brightness** file. The backlight interface files are located at /sys/class/backlight and there may be more than one, so you'll need to go into each of the directories and test it out.

For example, if you have an acpi_video0 interface (/sys/class/backlight/acpi_video0) you would have a number of files in that directory. Check the contents of max_brightness and echo a value between 0 and max_brightness to the brightness file:
```

echo 5 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

Once you find the correct interface and correct value to set the brightness, change the line:
> COMMAND="xbacklight -set 0"
...to read:
```
echo X > /sys/class/backlight/INTERFACE/brightness
```
...where X is the value and INTERFACE is the name of the interface (directory). 

As an example:
```
echo 5 > /sys/class/backlight/acpi_video0/brightness
```

---

### Post by AgentOrange96 on 2012-12-06
Thanks for your help! Unfortunately, that did the exact same thing. When I first made the script, it worked perfectly, however, once I restarted my computer, it stops working.

EDIT: Now however it came up with an error message (that I could not read) and made it take longer before my brightness up and down keys were able to turn the backlight back on. Also, they didn't work when the error message was up and I wasn't able to get enough light to read it, nor do I know how to take a screenshot in e17.
EDIT: Okay, set a key to execute a screenshot command successfully, I'll do that if I get the error again.
EDIT: [IMG]http://i1093.photobucket.com/albums/i428/agentorange96/Internet/screenshot.png[/IMG]

---

### Post by Toz on 2012-12-06
Can you post back the contents of your /var/log/pm-suspend.log file:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

And also a copy of that script in /etc/pm/sleep.d.

---

### Post by AgentOrange96 on 2012-12-06
Sure. The [log is here.]("http://paste.ubuntu.com/1415717/") What's interesting is that it says that the execution of the script was successful. If you are looking, the script is called "0000_screenbrightness" and is as follows:
```
#! /bin/bash
#This makes the backlight set to 0 when the computer resumes.
case $1 in
suspend)
#echo "Suspeding ..."
;;
resume)
echo 15 > /sys/class/backlight/acer-wmi/brightness
echo 736950 > /sys/class/backlight/intel_backlight/brightness
;;
hibernate)
#echo "Hibernating ..."
;;
thaw)
echo 15 > /sys/class/backlight/acer-wmi/brightness
echo 736950 > /sys/class/backlight/intel_backlight/brightness
;;
esac
exit 0
```

For the record, I had it so that it only did acer-wmi, but I then added intel_backlight after that one didn't do it. Again, my original code was in my first post.

---

### Post by Toz on 2012-12-06
> echo 15 > /sys/class/backlight/acer-wmi/brightness
echo 736950 > /sys/class/backlight/intel_backlight/brightness

Only one of those should actually work to change the brightness. Can you manually find out which one:
```
echo 15 | sudo tee /sys/class/backlight/acer-wmi/brightness
echo 7 | sudo tee /sys/class/backlight/acer-wmi/brightness

echo 736950 | sudo tee /sys/class/backlight/intel_backlight/brightness
echo 350000 | sudo tee /sys/class/backlight/intel_backlight/brightness
```
...and only keep the one that works in the file.

According to your logs, this script is executed and there are no errors. Funny that it doesn't work after reboot. 

Can you try inserting a delay in the file to see if maybe you need to wait before changing the brightness? (its a bit of a long shot). Before the "case $1" line, insert:
```
sleep 5s
```

Try playing with 5s (5 seconds) value to see if a delay helps at all.

EDIT: can you also add, before the "case $1" line the following line:
```
cat /sys/class/backlight/acer-wmi/brightness
```
...to see if the interface exists as this script runs.

EDIT2: And one more thought. Is it possible that Enlightenment is running a command/script that affects the brightness when the DE returns? I've never used it so I don't know.

---

### Post by AgentOrange96 on 2012-12-07
Solved!
I set the number after "echo" to 0 rather than 736950, (remember, my computer is backwards.) commented out acer-wmi, and then later commented out the delay. (I was wondering why it was taking for ever to suspend, then I remembered.) I restarted my computer and... it still works! Thank you so much. This makes life easier.
...now if only I can make my computer resume when I open the lid*...

My final code is below:
```
#! /bin/bash
#This makes the backlight set to 0 when the computer resumes.
#sleep 15s
cat /sys/class/backlight/intel_backlight/brightness
case $1 in
suspend)
#echo "Suspeding ..."
;;
resume)
#echo 15 > /sys/class/backlight/acer-wmi/brightness
echo 0 > /sys/class/backlight/intel_backlight/brightness
;;
hibernate)
#echo "Hibernating ..."
;;
thaw)
#echo 15 > /sys/class/backlight/acer-wmi/brightness
echo 0 > /sys/class/backlight/intel_backlight/brightness
;;
esac
exit 0
```
I didn't bother to delete everything I don't need, mainly for reference for myself.
I shall now do your favorite thing and mark this as solved!


*I don't think this is possible as it doesn't do this in Windows...

---

### Post by Toz on 2012-12-07
> I shall now do your favorite thing and mark this as solved!

:)

> ...now if only I can make my computer resume when I open the lid*...
Probably best to create a new thread for this issue.

---

### Post by AgentOrange96 on 2012-12-07
> **Toz said:**
> :)


Probably best to create a new thread for this issue.

Don't worry, I don't think the BIOS even supports this. Besides, I've had this computer long enough to be in the habit of hitting the spacebar before I have the screen all the way up anyway.
Thanks again!

---

