---
title: "Automatic power on/off"
date: 2007-11-22
forum: General Help
---

### Post by dragon_master_mokuba on 2007-11-22
Is it possible to have linux automatically (timed) power a computer on/off. i know you can on a mac, as im trying to get the graphic arts instructor at my school to switch the macs to linux because the macs are really crappy xD she loves having the macs turn themselves on/off so this would def be a plus =D thanks for your help in advance!

---

### Post by banewman on 2007-11-22
In a terminal type -
sudo shutdown -h 300
to turn the comp off in 5min
Read the man page for shutdown - in a terminal type - 
man shutdown
Hope that helps. :)

---

### Post by dragon_master_mokuba on 2007-11-22
yeah it did. thanks. is there any way for the computer to automatically turn itself on, lets say for the sake of example, at 6am every morning?

---

### Post by dj Kalma on 2007-11-22
> **dragon_master_mokuba said:**
> yeah it did. thanks. is there any way for the computer to automatically turn itself on, lets say for the sake of example, at 6am every morning?
You should be able to do that with an at/cron task. See examples: [http://www.cyberciti.biz/tips/howto-shutdown-linux-box-automatically.html]("http://www.cyberciti.biz/tips/howto-shutdown-linux-box-automatically.html")

---

### Post by Nebby on 2007-11-22
There's also normally a BIOS setting, which is what I've got waking mine every morning.
As your computer boots, you'll have a chance to hit a key (F2, Delete or Escape are popular) to enter BIOS, then have an explore in there.

---

### Post by dragon_master_mokuba on 2007-11-22
> **Nebby said:**
> There's also normally a BIOS setting, which is what I've got waking mine every morning.
As your computer boots, you'll have a chance to hit a key (F2, Delete or Escape are popular) to enter BIOS, then have an explore in there.

i didnt see any power settings. or anything related to that. any help? maybe i could put a new bios on it or something?

---

### Post by jespdj on 2007-11-22
> **dj Kalma said:**
> You should be able to do that with an at/cron task. See examples: [http://www.cyberciti.biz/tips/howto-shutdown-linux-box-automatically.html]("http://www.cyberciti.biz/tips/howto-shutdown-linux-box-automatically.html")
Ofcourse it is impossible to make a computer switch **ON** automatically with a cron script, because the computer has to be switched on already for the cron script to run... #-o

But as others have said, some computers have a setting in the BIOS settings to switch the computer on at a specified time. If your computer doesn't have this setting, you're out of luck. Look in the manual of your computer / motherboard or find the information on Internet.

---

### Post by AndrewRump on 2007-11-22
Some network cards also have the functionality of turning on the computer. Somebody must have implemented a hacking tool :) which would turn on all the computers (in a list) from one computer - which of course has to be up and running for the whole setup to work.
 
Please note - this will require power to all the computers 24/7.

---

