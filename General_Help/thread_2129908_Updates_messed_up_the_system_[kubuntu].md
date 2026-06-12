---
title: "Updates messed up the system [kubuntu]"
date: 2013-03-27
forum: General Help
---

### Post by mastablasta on 2013-03-27
So i was doing regular updates.

Could not update Chromium via Moun. It needed a newer kernel?! i tried to update with terminal that also couldn't do it. 

So i restarted the computer. It get's into KDE, and the desktop is  responding it seems (various messages popping up, i could switch windows via alt+tab if i had any open). But mouse is frozen in the middle of the screen,  keyboard is changed to another setting (probably US keyboard or  similar). hard to say. the correct keyboard is in console though.

went to console to perform update again it said chromium could not update and suggested me to use 
```
sudo apt-get install -f
```

something wicked happened during that one.


however it seem to me something wicked happened before that command as well.

how do i get my desktop back? how do i get the mouse to work normally again? and keyboard?

i can get into console. i can't get to grub usually. only managed to get into it once and tried to boot from older kernel. mouse is still frozen. i can use keyboard but it is a bit difficult since the letters on screen don't correspond my keys. 

how do i open K?

mouse and keyboard are almost the cheapest logitech generic stuff that worked well so far.


another update well done #-o

---

### Post by Bashing-om on 2013-03-27
mastablasta;

Maybe of no help, but as display, keyboard and mouse are all controlled through Xserver, do you use the /etc/X11/Xorg.conf file on your system ? Maybe it got corrupted, or maybe Xserver it's self is fouled.[INDENT=3]
just a thought

[/INDENT]

---

### Post by schragge on 2013-03-27
> **mastablasta said:**
> something wicked happened during that one.
...
however it seem to me something wicked happened before that command as well.This sounds pretty vague. Could you please be a bit more specific?

---

### Post by mastablasta on 2013-03-28
i do not use xorg.conf

i can't be any more specific, since i did not remember the error. but form what i read is that is couldn't performs the chromium update saying i do not have the right ubuntu - my guess is that was the kernel number. as the required number was higher than i have/had installed.

it ended with somehtign wicked happened. i though well ok you can't install chromium update, so what. it shouldn't affect the mouse or keyboard at all.

the only thing that affects them is kernel - or possibly xserver.

like i said everyhitng looks normal onyl the mouse doens't move and the keyboard seems to be off (wrong type) in the KDE. it is correct keyboard if i switch to console.

something definatelly went wrong with updates but aside from chromium, muon didn't report any problems when updating.

---

### Post by mastablasta on 2013-03-28
update
we tried to get at least some work done on LAMP server. so since console worked we droped into it and then initialised apache server and mysql. both turn on ok and don't report any issues.

however upon trying to connect from the other computer via LAN it said connection timed out. it seem plenty of things are messed up not just mouse and keybaord.

if anyone knows a solution i would really appreaciate a speedy reply as there is work waiting to be done on this maschine. and i hope there is a simpler solution before i do a reformat and reinstall the whole thing.

adidtional question - is it possible that if i reinstall without formatting to keep my programmes and settings? or will things like sources list and such get overwriten anyway?

i plan to report this as i have a feeling a graphics driver bug caused it all. it is not normal for fans to go full spin after monitor turns off....

---

### Post by Bashing-om on 2013-03-28
mastablasta;

I do not know of a "quick fix". I'll offer this up. Under stressful situations, it is tough to see the forest for the trees. Have you done the obvious;
As remote log-in is also under Xserver's control:Check the Xorg.log file (/var/log/Xorg.0.log).
And have you tried booting up with an older kernel ?[INDENT=3]
we be look'n
[/INDENT]

---

### Post by mastablasta on 2013-03-28
so i took your advice and stepped back from the forest.

problem was as i was unable to get to grub. i managed to do it only once in all reboots.

finally i got in again and used a much older kernel. turns out same things happened. i prepared my self this time. i checked the log. no errors.

i then used keyboard shortcuts to get to input devices settings. mouse was recognised but not working. keyboard working but not correct one.


so first i plugged the mouse into netbook and sure enough mouse worked. then i figured that the output is wrong. you see i am using a USB mouse and to save a usb port for other things i have it plugged in ps/2 via interface. so i removed interface and plugged it directly into USB port. and the mouse worked. i then set up the keyboard to my langauge and it seems mouse and keyboard are working now. i started apache and can access the work i've done so far.

BUT - sound is not working AGAIN!!!!!!!! stupid updates will make me go crazy. sound was working on 12.04 in beginnign after one months it stopped and i found a workarround and now it's not working again. which means they broke it fully again.

it still puzzles me as to why this happened in the first place as well as why i still can't update chromium browser to version 25.0.1364.160

i installed it via muon (kubuntu's software center). install -f doesn't work.

---

### Post by Bashing-om on 2013-03-28
mastablasta;

Not much one can say - updates are a necessary evil (in some respects) !

You are making progress !

I do not make claim to being a sharp tack in a box of sharp tacks, nor to tell gramps how to suck eggs; to me:
sound problem -> module ? what module is loaded into the kernel in a working environment and which when not working ? Black list the offending one, modprobe the working one ? -back to the logs -

chromium; how 'bout this as a suggestion:
```
sudo apt-get install --reinstall chromium.<whatever_version>
```
Then see if "apt-get" will update/upgrade to the current version ?[INDENT=3]
I hope to be of some small help

[/INDENT]

---

### Post by mastablasta on 2013-03-28
Now it's solved. thanks to IRC and helpfull community member.

i tried cleaning cache with apt get but same thing.

i then checked the apt archives and found many files in it. i deleted them all and ran the update upgrade command. a new chromium patch was downloaded and this one installed well.

in the mean time trying to troubleshoot the sound i've instaleld alsamixer. during the install package manager picked up kernel that seems to have not been installe dbefore. anyway a few more additioanl packages were downloaded and installed. alsamixer was showing the card and volumes were up. which was a known thing for me. so reloading the modules got the sound back. (i already made a short script for that since it happened too often before and i am not always arround to help).

it still puzzles me that updates  appart from chromium were shown to be done and installed. yet for soem reason it seems they were only half done. i will need to dig into logs and report a bug in kubuntu launchpad. but i do not have time at the moment for that. need to continue with the work. maybe over weekend...

---

