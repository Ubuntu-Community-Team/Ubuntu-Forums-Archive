---
title: "How to increase brightness sensitivity range?"
date: 2012-11-09
forum: General Help
---

### Post by donalgodon on 2012-11-09
Is there any way to increase the sensitivity of the brightness settings on my laptop? I have a Dell Vostro V131.

I'd like to have more than just **FIVE** levels of brightness. I have **SEVENTEEN** levels of volume.

This seems sort of silly. I'd love to have 17 levels with which to adjust brightness also, because 5 doesn't give me the best settings for my environment typically. Five isn't sensitive enough. I'm sure there's a way and I just don't know how, or at least that's why I hope.

Any help would be greatly appreciated. I hope this can be addressed by default in future updates, because when I boot from the live USB, it is more sensitive but lacks the on screen controls. Somehow, the updates after installation breaks the sensitivity and gives me only five levels.

---

### Post by pqwoerituytrueiwoq on 2012-11-09
what does this give you
```
cat /sys/class/backlight/acpi_video0/max_brightness
```

---

### Post by donalgodon on 2012-11-09
It gives me an output of 15

---

### Post by pqwoerituytrueiwoq on 2012-11-09
then you have 16 settings
try using this script to adjust your backlight
[https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/1064117/+attachment/3388158/+files/backlightx.tar.bz2](https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/1064117/+attachment/3388158/+files/backlightx.tar.bz2)

---

### Post by donalgodon on 2012-11-09
> **pqwoerituytrueiwoq said:**
> then you have 16 settings
try using this script to adjust your backlight
[https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/1064117/+attachment/3388158/+files/backlightx.tar.bz2](https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/1064117/+attachment/3388158/+files/backlightx.tar.bz2)

Well, if I have 16 settings, why are there only five levels available?

At the lowest setting, 0, I can push the button four more times to reach 15.

I'll try the script and report back.

Edit:

Still have only five levels of brightness in the range.

---

### Post by pqwoerituytrueiwoq on 2012-11-09
are you running the script?
backlightx --set +1
backlightx --set -1
backlightx --set 0
backlightx --set 16

---

### Post by donalgodon on 2012-11-09
> **pqwoerituytrueiwoq said:**
> are you running the script?
backlightx --set +1
backlightx --set -1
backlightx --set 0
backlightx --set 16

Sorry, but do you mean did I run it?

I ran it via terminal, but nothing happened. 


Was I supposed to do something else with it?

Maybe I missed something.

---

### Post by pqwoerituytrueiwoq on 2012-11-10
[http://pastebin.com/HzzHrS2g](http://pastebin.com/HzzHrS2g)
save it to [FONT=Courier New]/usr/local/bin/backlightx[/FONT]
then ```
chmox +x /usr/local/bin/backlightx
```
then
```
sudo chmod 777 /sys/class/backlight/acpi_video0/brightness
```
then run some of these
```
backlightx --set +1 # increase brightness
backlightx --set -1 # decrease brightness
backlightx --set 0 # set back light to minimum
backlightx --set 16 # set back light to maximum
```

---

