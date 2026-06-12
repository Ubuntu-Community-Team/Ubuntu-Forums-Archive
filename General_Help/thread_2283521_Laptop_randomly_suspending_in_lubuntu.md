---
title: "Laptop randomly suspending in lubuntu"
date: 2015-06-22
forum: General Help
---

### Post by henry47 on 2015-06-22
Hi,

I have just installed lubuntu on and old acer aspire one laptop, it's mostly running fine but I'm struggling to stop the laptop going to sleep randomly. I have all the settings set to not go to sleep (AC and battery) but even when playing music it seems to want to doze off after 3-5 mins! Does anyone know why this might be? Also, the preference settings about what happens when you shut the lid don't really seem to work properly as if I put it to do nothing, it sleeps, if I put it to lock screen it does nothing.

I hope somebody could please help me, if any more info is needed, let me know!

Thanks very much, all the best

---

### Post by QDR06VV9 on 2015-06-22
Hi henry47 have you tried with this before
Try installing :
```
sudo apt-get install xfce4-power-manager
```

Then configure it in:
> xfce4-power-manager-settings
Kind Regards

---

### Post by henry47 on 2015-06-22
Hi, thanks for replying, yes I have that installed and that's where I had originally configured it, just it doesn't seem to be working!

---

### Post by QDR06VV9 on 2015-06-22
> **henry47 said:**
> Hi, thanks for replying, yes I have that installed and that's where I had originally configured it, just it doesn't seem to be working!
Aahh! for temp fix (at first anyway)
Type In terminal
```
xset s 0 0
```
 this command disables the blanking only for current session
See if that meets your needs.
I you are then satisfied with the results you can make it permanent by, insert a line with the same command at the start of the /home/username/.profile file.
Let us know how it works out.
Cheers

---

### Post by henry47 on 2015-06-22
Thanks, I'll see how that goes. I've just noticed actually, had another play around with the settings, turns out the monitor was going to sleep, and when that goes to sleep it takes the computer to sleep with it. So it could be that, I'll see how this turns out for the next couple of days and if it doesn't work I'll try your fix. Thanks very much for your time!

Also, I have another thing so that when I press the power button it should suspend, but it still just seems to ask me, any ideas on how to solve that?

---

### Post by QDR06VV9 on 2015-06-22
> **henry47 said:**
> Thanks, I'll see how that goes. I've just noticed actually, had another play around with the settings, turns out the monitor was going to sleep, and when that goes to sleep it takes the computer to sleep with it. So it could be that, I'll see how this turns out for the next couple of days and if it doesn't work I'll try your fix. Thanks very much for your time!

Also, I have another thing so that when I press the power button it should suspend, but it still just seems to ask me, any ideas on how to solve that?
Your Welcome.
For suspend and power button never worked for me I just close the lid on the laptop.
But the code below will manually put it in suspend at will.
```
pm-suspend
```

---

### Post by ajgreeny on 2015-06-22
This may or may not solve all your problems but have a look at light-locker which you can open with command ```
light-locker-settings
```
Set it to "Off" and you may then be able to set any power-manager or screensaver settings (does Lubuntu come with xscreensaver by default?; I can't remember) and avoid any conflicts between the applications

---

