---
title: "Screen stuck at max brightness"
date: 2013-08-05
forum: General Help
---

### Post by ka2012 on 2013-08-05
I installed ubuntu 12.04 on my hp pavilion dm1 laptop about a month ago. It was working fine. The other day, the screen brightness controls stopped working. I can go into the window and move the screen brightness slider, and when I press the brightness control buttons, the bar displaying the brightness level changes, but the actual screen brightness doesn't...it started doing this about the time I was installing one of the propriety drivers , and I don't know if that could have caused it or was just a coincidence...still usable, but the brightness being always at maximum is starting to get annoying. Anybody know or have an suggestions as to how to fix this?

---

### Post by Toz on 2013-08-05
Which video card?

Are you using any kernel parameters? Open a terminal window, type in the following command and post back the results:
```
cat /proc/cmdline
```
What backlight interfaces do you have? Run this command in a terminal window and post bac the results:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/max_brightness; cat $i/brightness; done
```
And finally, can you post back the contents of your dmesg log file? Run this command:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

---

### Post by ka2012 on 2013-08-05
Graphics card:
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6310]

Kernel parameters:
BOOT_IMAGE=/boot/vmlinuz-3.5.0-37-generic root=UUID=7bcb268f-6dfe-4f5c-8187-26f9a9517fe7 ro quiet splash vt.handoff=7

Backlight interfaces:
/sys/class/backlight/acpi_video0
10
10

And here's the link to the log file:
[http://paste.ubuntu.com/5952437/](http://paste.ubuntu.com/5952437/)

Thanks for any help you can give!

---

### Post by Toz on 2013-08-05
Interesting.

Does the following command:
```
echo 5 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
...change the screen brightness?

Can you also post back your Xorg log file:
```
pastebinit /var/log/Xorg.0.log
```

How did you install the proprietary drivers? Was it through the Additional Drivers app?

---

### Post by ka2012 on 2013-08-05
The first command didnt change the screen brightness, it just returned "5"

Heres the link to the Xorg log file:
[http://paste.ubuntu.com/5952563/](http://paste.ubuntu.com/5952563/)

And yeah, I installed them through the additional drivers app

Edit: I have my computer dual booting windows 7 and ubuntu, forgot to mention that before (I don't know if that would be affecting anything, but just in case it helps) And the windows 7 brightness controls are working, so its just ubuntu

---

### Post by Toz on 2013-08-05
It must be something with the proprietary drivers as it should be working. Can you look in the catalyst control center to see whether there is a setting there related to screen backlight (unfortunately I don't have an ATI card to check myself).

Also, can you try this script to see if it changes the brightness:
```
i=0; while [ "$i" -ne "20" ]; do echo 5 | sudo tee /sys/class/backlight/acpi_video0/brightness; i=$(($i+1)); echo $i; done
```

---

### Post by ka2012 on 2013-08-05
I opened catalyst control center, and the brightness control center there is working...the normal brightness tools and my brightness keys are still not working, but at least I have some way to change it, even if I do have to do it a different way...

Do you think, if I uninstalled the proprietary driver, would it return it to normal?

Edit: Actually, I just restarted my computer and the brightness stayed where I had it, at 50%, effectively solving a problem I've had since I installed ubuntu where the brightness returns to maximum every time I turned on the computer...so thats good...I think Im fine with doing it this way for now (its really not that inconvenient, although it is rather annoying I cant use my brightness buttons) I may try uninstalling the proprietary driver and seeing if that returns it to normal though...Thanks for all of the help!

---

