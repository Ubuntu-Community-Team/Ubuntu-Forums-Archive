---
title: "how can i make the computer turn itself on?"
date: 2006-12-13
forum: General Help
---

### Post by delfick on 2006-12-13
hello :D

is there a way i can make my computer turn itself on at a particular time ??

i've searched for an answer for a while now, and i'm starting to think that it isn't possible....but before i give up, i want to know if anyone here would know of a way to do this ??

thnx :D

---

### Post by engineer on 2006-12-13
there's no easy way.

if your mainboard has a wakeonlan feature, you could send a command from another computer, that is running all the time.

otherwise you could connect the power button of your case to an alarm clock. this would need some experience with electric circuits.

---

### Post by Titus A Duxass on 2006-12-13
Have a look in the BIOS, some times there is an option to wake up there.

---

### Post by v8YKxgHe on 2006-12-13
Yes you can set it in the BIOS ( sometimes ), press DEL or F1 when your computer starts up, somewhere in there you will be able to set what time it turns on.

---

### Post by scrooge_74 on 2006-12-13
I used to make my computer boot up by itseld  at work to start at 7 am so it could receive faxes. I only had to make a change in the BIOS, most BIOS have that support from at least 5 years back

---

### Post by d3v1ant_0n3 on 2006-12-13
Well this kept me more amused than reading Digg with my morning coffee.

See trademark dev1ant_0n3 shoddy mockup:D 

Basically- take a regular old style alarm clock, remove the 'bells' at the top but leave the hammer. Add an extension to the hammer and a catch on one side of the hammer arm. Position next to computer so the hammer falls on the power button. At a given time, the alarm will ring, swing the arm, hit the power button, turn on the computer, the arm will return and hit the catch- this will stop it from repeatedly hitting the power button. :D 


Might want to see if there's a bios option first tho', it's less insane.


I sketched the idea out in 3 seconds on paper, then tried for 10 minutes trying to draw said idea in inkscape. I really need a tablet or something. Or tablets, one or the other.

---

### Post by v8YKxgHe on 2006-12-13
haha great idea! :p

---

### Post by technodigifreak on 2006-12-13
> **d3v1ant_0n3 said:**
> Well this kept me more amused than reading Digg with my morning coffee.

See trademark dev1ant_0n3 shoddy mockup:D 

Basically- take a regular old style alarm clock, remove the 'bells' at the top but leave the hammer. Add an extension to the hammer and a catch on one side of the hammer arm. Position next to computer so the hammer falls on the power button. At a given time, the alarm will ring, swing the arm, hit the power button, turn on the computer, the arm will return and hit the catch- this will stop it from repeatedly hitting the power button. :D 


Might want to see if there's a bios option first tho', it's less insane.


I sketched the idea out in 3 seconds on paper, then tried for 10 minutes trying to draw said idea in inkscape. I really need a tablet or something. Or tablets, one or the other.

I thought I saw something like this on instructables :D anyway, most modern BIOS's support boot at a specific time.

---

### Post by delfick on 2006-12-13
thnx for the replies people :D

......i probably should have mentioned this in the first post, sry :D, but

i have an Abit AN8-V

and i've already looked at bios....

in the manual here i have

||Wakeup by PME# of PCI
--When set to enabled any event related to PCI cards (PME) will power on the system...
(what does that mean ??)

||Wake-up by OnChip LAN:
--when set to enabled, you can remotely wake up a PC in soft-off condition via a ALN card that support the wake up function.
(i only have one computer.....)

||Wake up by Alarm
--When set to enabled you can see the date and time at which the RTC alarm awkens the system from suspend mode
(when i first looked at the bios, i saw this, and i thought YAY! but when i look at the manual it says, from suspend mode.....unfortunately suspend refuses to work for me :'( i just can't get it to go into suspend mode and then come out of it to my desktop........(desktop pc) ......

and that's it...


(one other thing, unrelated to this, as i don't really seeing it going far (i'm such an optimist :D) there is a function here to define how you turn on the computer, i.e. the normal big button, mouse keys, password as in you type in a password and it turns on 
how does anything other than the power button turn on the computer ??

and thankyou  d3v1ant_0n3, you are of truly legendary status :D:D
you should seriously think about becoming an inventor, you'll become very rich with your fantastic "ideas" :D:D (lol)

---

### Post by scrooge_74 on 2006-12-13
Wake up by alarm is what you are looking for, set a time and it will start the PC, some bios have options for days of the week.

You can have any of those options wake up your pc, if you pay attention closely to your Pc, even when off you will see that your lancard is on.  If you have a router you will see that the light for the PC conection is on.

---

### Post by delfick on 2006-12-13
> **scrooge_74 said:**
> Wake up by alarm is what you are looking for, set a time and it will start the PC, some bios have options for days of the week


i set it to wake at a certain time, then turned off the pc.....

that time came along and passed and the pc didn't turn itself on :(

...



EDIT :: excuse me while i kick myself ! :D

i just looked at the bios and realised that the time in the bios was different to the time on my watch (by several hours) which explains why the time always changed everytime i booted into windows....

anywho, i changed it to the proper time, and reset the wakeup on alarm to another time (to go off a few minues after a changed it) then i turned off the computer........and FINALLY !!! it worked, the computer magically turned itself on :D:D:D


now i need to know, how do i make it so that when my computer boots, it logs itself in ??

edit :: figured it out...

thnx all for your help :D:D

---

### Post by delfick on 2006-12-16
everytime i set the time in bios to the correct time, i log into ubuntu and the the time is out by a matter of hours.... :D (like 8, 15, or something like that...)

so that means everytime i set the computer to wake itself up, i also have to reset the time in bios....

why?? and how can i stop that?? 

thnx :D

also, is it possible to edit the bios from within ubuntu??

so i can set the wake-up alarm from within ubuntu ??

that would be awsome...!

---

### Post by delfick on 2006-12-18
so that's a no ??

---

### Post by RaZer0r on 2006-12-18
it is indeed a no, I never have seen any application that makes it possible to edit the alarm times without going into the bios itself.

some motherboards can update the bios from within windows, but i have never seen anything for any linux distro...

---

### Post by flyingbrass on 2006-12-18
> so that means everytime i set the computer to wake itself up, i also have to reset the time in bios....

why?? and how can i stop that??
Sounds like the system is using UTC/GMT when you don't want it to.  Ubuntu syncs with a time server each time it boots, and it resets your system clock per your settings.

Right click on the clock, select preferences.  If UTC is checked, uncheck it.  Also, make sure your time zone is set correctly in System -> Administration -> Time and Date.

If your settings in the dialog boxes don't stick, see [this thread](http://ubuntuforums.org/showthread.php?t=135214).

---

### Post by delfick on 2006-12-18
ye, both your suggestions are already like that......

---

### Post by delfick on 2006-12-18
> **RaZer0r said:**
> it is indeed a no, I never have seen any application that makes it possible to edit the alarm times without going into the bios itself.

some motherboards can update the bios from within windows, but i have never seen anything for any linux distro...

ye, just found this thread, doesn't look promising :(
[http://www.ubuntuforums.org/showthread.php?t=318878&highlight=edit+bios](http://www.ubuntuforums.org/showthread.php?t=318878&highlight=edit+bios)

---

### Post by flyingbrass on 2006-12-18
Are you booting another OS in between?

---

### Post by delfick on 2006-12-18
> **flyingbrass said:**
> Are you booting another OS in between?

nope

though i sometimes boot into windows...

but i change the time in bios back to what it's supposed to be, then boot straight back into linux and the time on my gnome-panel is wrong....

---

### Post by flyingbrass on 2006-12-18
Check /etc/default/rcS and look for the line UTC.  It should be set to "no" since you're dual booting Windows.

Set your correct local time in Ubuntu.  Then pull up a terminal and type:

sudo hwclock --systohc --localtime

That will set your hardware clock to the time showing in Ubuntu.  Note that people whose system clock is set to UTC would use --utc instead of --localtime in that command.

Then, if you like, install ntpd to keep your clock from wandering too far out of whack.  System -> Administration -> Time and Date, then check the box "Periodically synchronize clock with Internet servers."  You'll be prompted to install ntpd.

---

### Post by delfick on 2006-12-18
> **flyingbrass said:**
> Check /etc/default/rcS and look for the line UTC.  It should be set to "no" since you're dual booting Windows.

Set your correct local time in Ubuntu.  Then pull up a terminal and type:

sudo hwclock --systohc --localtime

That will set your hardware clock to the time showing in Ubuntu.  Note that people whose system clock is set to UTC would use --utc instead of --localtime in that command.

Then, if you like, install ntpd to keep your clock from wandering too far out of whack.  System -> Administration -> Time and Date, then check the box "Periodically synchronize clock with Internet servers."  You'll be prompted to install ntpd.

THANKYOU!!!! :D :D

that fixed that problem :D...


now i just need to be able to set the alarm from within ubuntu :D

thnx :D

---

### Post by PurplePenguin on 2006-12-18
> **d3v1ant_0n3 said:**
> 

Basically- take a regular old style alarm clock, remove the 'bells' at the top but leave the hammer. Add an extension to the hammer and a catch on one side of the hammer arm. Position next to computer so the hammer falls on the power button. At a given time, the alarm will ring, swing the arm, hit the power button, turn on the computer, the arm will return and hit the catch- this will stop it from repeatedly hitting the power button. :D 

Might want to see if there's a bios option first tho', it's less insane.


You've definitely got my vote for most entertaining UF post ever. :D

---

### Post by thelinuxguy on 2007-04-27
> **delfick said:**
> 
now i just need to be able to set the alarm from within ubuntu 


You could try nvram-wakeup from the repositories.

---

### Post by Aetherius on 2007-04-27
I just recently found the "Power On after Power Fail" option in my BIOS.

Its never down :D

---

### Post by JoseArmandoJeronymo on 2007-07-21
I set the wake-up time directly on the bios. It works fine. However it is not supported by nvram-wakeup:(:confused:

I have elaborated on the idea of turning the computer on by using a 5V outlet from the power source to energize a relay which turns on an external audio amplifier, the printer, the ADSL modem and a LAN router.

Also, I am experimenting with BASH and espeak. The computer already greets the family as it wakes up, telling the current time, playing a musical selection and then "tuning" on a webradio (fyi, French Canada music station, Éspace Musique, that has a great classical program weekdays mornings).

Next I plan to make the box read some verses of the Gospels and will put loudspeakers on my bedroom and kitchen so that I have the sound all over the place (if, of course, my wife grants me permission for so).

It is amazing what one can do with Ubuntu.

---

