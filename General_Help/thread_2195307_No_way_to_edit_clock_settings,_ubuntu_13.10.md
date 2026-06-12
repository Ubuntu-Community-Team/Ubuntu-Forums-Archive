---
title: "No way to edit clock settings, ubuntu 13.10"
date: 2013-12-23
forum: General Help
---

### Post by krafczyk-matthew on 2013-12-23
I can't edit my clock settings for some reason. The time displays, so it doesn't seem to be a duplicate of: [https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1228360](https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1228360)

I press the menu item 'Date & Time Settings' and it launches the system settings menu which lacks any kind of clock sub-menu.

---

### Post by bapoumba on 2013-12-23
Have you tried some of the fixes in that bug report ? Some users said they still had the clock showing but were not able to modify the settings.
```
killall unity-panel-service
```
Or also see post #18 and 29.
Are other users on your system affected ? Make a new one if you do not have any other user.

---

### Post by krafczyk-matthew on 2013-12-23
I did try. It didn't work.

Other users are affected.

Like I mentioned, The menu item to modify the date and time settings is there, but it links to the 'All Settings' window. This 'all settings' window does not have an entry for the clock. This makes my problem different from the linked bug. The linked bug claims that users cannot modify things in the clock tab, I do not have a clock tab in the 'all settings' window.

---

### Post by krafczyk-matthew on 2013-12-24
bump

---

### Post by hbuntuone on 2014-01-04
I am also having the identical issue. Any ideas?

---

### Post by bapoumba on 2014-01-04
Another bug : [https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1237361](https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1237361)

Are your systems up to date ?

Edit : [http://ubuntuforums.org/showthread.php?t=1742543](http://ubuntuforums.org/showthread.php?t=1742543)
[http://ubuntuforums.org/showthread.php?t=2183988](http://ubuntuforums.org/showthread.php?t=2183988)

---

### Post by hbuntuone on 2014-01-04
bapoumba:  None of those issues apply. The time and date shows in my panel without a problem. However, my System Settings contains no entry for Date & Time, and clicking on "Date & Time Settings" under the calendar/clock menu simply opens System Settings (which, again, doesn't have an entry for Date & Time).

My system is up to date.

---

### Post by coffeecat on 2014-01-04
@krafczyk-matthew and @hbuntuone, what desktop(s) are you running? This is what I see in a pure Unity 13.10 installation:

[ATTACH=CONFIG]249215[/ATTACH]    [ATTACH=CONFIG]249216[/ATTACH]

There was a thread a little while ago where the OP reported the same problem of no clock tab, but when they posted a screenshot it was clear they were not using Unity (possibly gnome shell) but never specified which.

---

### Post by hbuntuone on 2014-01-04
Running 13.10 with Unity. 

It's not that I'm missing the clock tab, it's that I'm missing that entire settings page (All Settings -> Time & Date).

---

### Post by mc4man on 2014-01-04
> **hbuntuone said:**
> Running 13.10 with Unity. 

It's not that I'm missing the clock tab, it's that I'm missing that entire settings page (All Settings -> Time & Date).
Is gnome-control-center-datetime installed?

---

### Post by hbuntuone on 2014-01-04
Weird. It wasn't installed. I wonder when/how it got removed.

Anyway, thanks a lot! That did it.

---

### Post by bapoumba on 2014-01-05
Glad to see you got it fixed. Please mark your thread as solved from the Thread Tools menu, thanks!

---

### Post by mc4man on 2014-01-05
> **bapoumba said:**
> Glad to see you got it fixed. Please mark your thread as solved from the Thread Tools menu, thanks!

That would be up to the Op you hasn't checked to see if the 'gnome-control-center-datetime' package is installed.
If it is & the panel still doesn't open then small possibility that attempting to open from cli would provide info. Unity & Gnome sessions use different launch commands to open the panel -  ( a -v could be added to commands

unity/ubuntu session - 
```
gnome-control-center indicator-datetime
```
gnome-shell/gnome session -
```
 gnome-control-center datetime
```

---

### Post by bapoumba on 2014-01-05
> **mc4man said:**
> That would be up to the Op you hasn't checked to see if the 'gnome-control-center-datetime' package is installed.

Argh, yes thanks, posted too quickly once again #-o

---

### Post by krafczyk-matthew on 2014-01-06
Awesome! This solution works for me as well! Will mark as solved.

---

### Post by bapoumba on 2014-01-06
Double thanks to mc4man :)

---

