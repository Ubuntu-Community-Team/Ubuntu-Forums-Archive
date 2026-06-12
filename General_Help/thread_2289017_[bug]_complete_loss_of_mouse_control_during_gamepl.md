---
title: "[bug] complete loss of mouse control during gameplay"
date: 2015-07-31
forum: General Help
---

### Post by tcll5850 on 2015-07-31
I've delt with this long enough to know it doesn't happen when I close and kill chromium
chromium: you don't want me to run in the background? screw you I'mma run anyways.
(I have a `killall chromium-browser` button specifically for this)

anyways, of the 3 tested games:

Minecraft
Nexuiz
Xonotic

I've had to run Wine versions of the last 2 because the linux versions would always fall behind a few seconds with audio, or the buffer rate would drastically drop with Xonotic (very slow and choppy audio).

anyways, if I run any one of them with chromium running, a few minutes into the game and my mouse will just randomly drop completely.
only fix I know of is to hard shut-down.

is there any sort of local fix that doesn't require a shut down??


@doubters thinking I'm a typical noob:
no, I'm not an idiot, my mouse is wired, and the USB cord does not have a short.
(like I said, the issue doesn't happen unless chromium is running)

---

### Post by pqwoerituytrueiwoq on 2015-07-31
what video card and driver are you using
i will try to reproduce this over the weekend
nvidia settings: 352.21-0ubuntu0~xedgers14.04.1
3.16.7-031607-generic
cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.2 LTS"

xfce 4.12

---

### Post by tcll5850 on 2015-07-31
[img]http://lh3.ggpht.com/-I1nNtIYsSf8/VbvV3VNCXtI/AAAAAAAAJfU/Lk7XujkYrPU/s868-Ic42/video_driver.png[/img]

my card:
[img]http://alienbabeltech.com/main/wp-content/uploads/2010/10/Galaxy_GT430_box_card.jpg[/img]

sorry if the image is too big, I'll reupload to picasa and size it to w800 if needed :)

---

### Post by pqwoerituytrueiwoq on 2015-07-31
i actually have that exact gpu in my moms pc, i am using a galaxy 650 ti boost (OCed) now

---

### Post by tcll5850 on 2015-07-31
lolol go figure, it's like you were meant for me XD

my CPU is an AMD Athlon x2 (dual core x64) 2.6GHz on this MBD:
[https://the620guy.com/wp-content/uploads/2014/03/20140212B-HP_CPQ_CQ5320Y_Pegatron_M2N68-LA_R6-01_A_II_X2_240_2-8GHz_N-3.jpg](https://the620guy.com/wp-content/uploads/2014/03/20140212B-HP_CPQ_CQ5320Y_Pegatron_M2N68-LA_R6-01_A_II_X2_240_2-8GHz_N-3.jpg)
^ peice of trash incompatible board causes issues with most programs.

sadly I can't afford anything, this was passed down to me.

EDIT:
just noticed, mine doesn't have the PS/2 (very corner) ports like that one does
(I REALLY wish it did though)

EDIT2:
found my EXACT board and updated the link

---

### Post by pqwoerituytrueiwoq on 2015-07-31
so far i have not been able to reproduce it, about how long does it take in xonotic
i have managed to loose keyboard control in xonotic lately, i think i may have lost mouse control before, though i usually don't have chromium open (mainly use firefox)
disconnecting and reconnected fixed it

---

### Post by tcll5850 on 2015-07-31
yea, Nexuiz seems to be the most active, now that I'm really looking at it, minecraft being 2nd-most.
I'm thinking it may have to do with the system RAM going into swap, but Nexuiz kinda breaks that as it never tops out...

and oh yea, I tried that before as well, including plugging in another mouse, they don't even turn on.

interesting how you lose KBd control >.>
I've never had an instance of that :/

EDIT:
btw, I use chromium because FF can't (doesn't give the option to) block as much web content.
just cause linux is safer when it comes to the web, that doesn't mean I want malicious ad-trackers and common web media trackers snooping around at everything I like to do.

tbh, Comodo Dragon is the next best thing to Tor, but I'm stuck to chromium until a linux build is out... heh.

---

### Post by pqwoerituytrueiwoq on 2015-07-31
i think it has something to do with window focus being stolen eg xscreensaver (had too many issues with litelocker)
for some reason i could not restore focus for the keyboard, ewll some keys worked, but not all in it, but if i cant spawn it may as well be 

this is off topic, but since you are using a AMD CPU from the same era as my mom's computer and the same video card have you had any issues with suspend and it not waking, it is almost like it gets stuck at the BIOS level of the wake up process

if it is ram related i am not going to be able to reproduce it on this system without taking ram sticks out (12gb ram, i5-4690K, OCed GTX 650 TI Boost)

---

### Post by tcll5850 on 2015-07-31
yea, I've removed litelocker and don't have any screensavers enabled...
played around with them as my desktop BG though... lol

also, the windows don't change focus, the mouse just dies in the middle of the game... I can still walk around and such.
it HAS happened a few times after closing chromium (making sure all chromium-browser processes are dead), but it usually never happens when I reboot and start a game (no chromium at all).


I've never had issues with suspend, though I have had issues with it refusing to go into hibernation.
(wifi just disconnects and then reconnects)
and I've also had it freeze after my screens went black while going into hibernation.
usually though an update (that doesn't require a restart) causes these.


and yea, I only got 4GB RAM and 4GB swap :P

---

### Post by pqwoerituytrueiwoq on 2015-07-31
try opening a large image in gimp to fill up some ram to force swap activity
see if that makes it happen

---

### Post by tcll5850 on 2015-07-31
ok, so I completely restarted my compy and I did ya one better :)
I wrote a python program to take up 1GB of memory for testing, but the thing backfired and threw a MemoryError at around 3.5GB so I left it... lol

from there I started Nexuiz and played a few levels choosing the most complex level (the one that has the most data) last. (which I do believe is Strength, but whatever if I'm wrong)

it took quite a few games before I finally lost my mouse control.

so I closed the game and the python program and am now at a blank desktop with no mouse control.


I think it has to do with a combination of swap usage and CPU overload.
(more likely CPU overload due to Nexuiz still causing it after freeing my RAM by killing chromium)
^ I have skype running normally which causes load every time a person comes online or goes offline


so before I restart, is there anything I can do through the terminal to regain my control??
all I gotz a KBd now... heh

also, I'm typing this msg off my laptop since I can't start chromium without my mouse to click the restore (tabs) button.

EDIT:
nvm... been wanting to work on my brute-force compressed NTFS recovery tool since I made this post...
2 hrs tops my patience when I have to go to bed in 1...
trying to recover some stuff for 2 other programs I'm having a hard time working on... heh
(I'm not mad, just overwhelmed beyond belief)
^ I don't have time for patience... lol

I'm sure you know my position :)
(hopefully you work on more than me)

---

### Post by pqwoerituytrueiwoq on 2015-08-04
1st sorry i did not notice this was on page 2.
try reconnecting the mouse, does it even slow up in lsusb?
also check dmesg, probably in the last few lines there may be a error message we can use

---

### Post by tcll5850 on 2015-08-04
this was on page 2 for you??
I've got my posts and threads display maxed out with the newest first (I hate newest last) :P

anyways I already know from experience the light doesn't even turn on again after plugging it back in.

I'll have to check dmesg next time I do it... heh

---

### Post by pqwoerituytrueiwoq on 2015-08-06
when you loose mouse control are you sure you don't have another window taking the window focus?
for example i loose mouse control if say my cat steps on my power button (he like to be annoying when he is hungry)
i set my power button to ask what i want to do (cause it annoys me when he turns my pc off)
so i click cancel and now i cant use my mouse in xonotic for some reason (aim/turn for example), relaunching it makes it work again

---

### Post by tcll5850 on 2015-08-07
not sure exactly what you mean... if you're saying you can still move your cursor to click cancel and what not, then that wouldn't be my problem.

Xonotic would actually pause the game if that happened, I think MC would as well.

no, my mouse just completely stopps, even to the point where I can actually see the default cursor, but can't move it around after closing the game window (Alt+F4) or changing focus using Alt+Tab.
all I can work is my KBd after the event.

it wouldn't be "complete loss" otherwize :P

---

### Post by pqwoerituytrueiwoq on 2015-08-07
different issue it seems
online play does not pause in xonotic, usually play instagib ctf

---

### Post by pqwoerituytrueiwoq on 2015-08-07
If you want to try to copy my configs here they are
CPU: i5-4690K
GPU: GTX 650 TI Boost (OCed)
Motherboard: AsRock Fatal1ty Z97 Killer
```
~$ lsb_release -a&&echo -e "Linux:\t\t$(uname -r)";apt-cache policy nvidia-355 xfce4-session xorg
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty
Linux:        3.19.0-25-generic
**nvidia-355**:
  Installed: 355.06-0ubuntu0~xedgers14.04.1
  Candidate: 355.06-0ubuntu0~xedgers14.04.1
  Version table:
 *** 355.06-0ubuntu0~xedgers14.04.1 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
**xfce4-session**:
  Installed: 4.12.1-1ubuntu1~14.04
  Candidate: 4.12.1-1ubuntu1~14.04
  Version table:
 *** 4.12.1-1ubuntu1~14.04 0
        500 http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     4.10.1-3ubuntu5 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
**xorg**:
  Installed: 1:7.7+1ubuntu8.1
  Candidate: 1:7.7+1ubuntu8.1
  Version table:
 *** 1:7.7+1ubuntu8.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1:7.7+1ubuntu8 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
```
in short im using the xorg edgers ppa and the xfce 4.12 ppa, the 3.19 kernel is from the repos

maybe you can reproduce my working system with yours

---

### Post by tcll5850 on 2015-08-07
+1 for instagib =D
I'll have to play you sometime :3

also, +1 for ASRock, I have an old (P4-era AMD Sempron) MBD that I hang on the wall (it died) which could prbly stomp my current MBD to this day if it could hold a dual-core.
[http://www.asrock.com/mb/photo/K7S41GX(L1).jpg](http://www.asrock.com/mb/photo/K7S41GX(L1).jpg) <3 <3

so anyways, I'm a noob, what am I supposed to do with these configs exactly??

---

### Post by pqwoerituytrueiwoq on 2015-08-14
i was basically telling you what versions i have installed
i am using these ppas:
[https://launchpad.net/~xubuntu-dev/+archive/ubuntu/xfce-4.12](https://launchpad.net/~xubuntu-dev/+archive/ubuntu/xfce-4.12)
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)

if you want to use them both

```
sudo apt-add-repository ppa:xubuntu-dev/xfce-4.12
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install nvidia-355 ppa-purge #ppa-purge can come in handy if say the driver does not work for you
```
if you want the 3.19 kernel
```
sudo apt-get install --install-recommends linux-generic-lts-vivid
```
if the system fails to boot right on next boot and you get stuck in low graphics mode or have to use recovery mode
```
sudo ppa-purge ppa:xorg-edgers/ppa
```

sorry forgot to check this thread all week, but i was busy with work also

---

### Post by tcll5850 on 2015-08-31
ok, I think I might be able to make the issue reproducable...

what's needed:
- a game that steals your mouse cursor in windowed mode
[s]- maxed RAM into swap (play Minecraft with something like an amplified world and wander around it for a bit, also have other RAM-hungry programs like chromium open with around 48 tabs or so, just to help)[/s]
- CPU usage of at least 70% (something that would cause minecraft to drop frames to something around 20FPS)
- Skype seems to play the part of the spark that ignites the fire, so try having a call going while people come online and go offline as you play.

I've only got 4GB on a 2.6GHz dual-core CPU, so I usually have hardly anything running (skype and minecraft alone is enough to kill my mouse)

anyways, the event is random, but max out the CPU to make it more likely...
once it happens, it's like the mouse driver just stops working.
(as stated earlier, reconnecting the mouse or even plugging in a new mouse has no effect)

any ideas as to what might be coughing??
hopefully it'll be a simple fix I can do with the keyboard via a shell script:
Ctrl+Alt+T > $ mouse > *mouse control restored*

hopefully there will be an update to automate that process when the event happens (if it can be done)

---

### Post by efflandt on 2015-09-01
I had a Galaxy GT 430 maybe 4-5 years ago that began failing shortly after its 1 year warranty expired. Initial symptom in Win7 was a pause and then something like "Video driver stopped responding, recovered" regardless of trying various nvidia drivers. Initial symptom in Linux (64-bit Ubuntu 11.10 at the time) was that randomly the keyboard and mouse buttons would stop responding entirely (could not even Ctrl+Alt+F1, etc.), but mouse cursor could usually still move. I actually don't remember that happening in minecraft even if playing for hours, but it might randomly happen after returning to desktop or sometimes immediately after booting. At first it did not seem to happen at all in 64-bit Ubuntu 10.04 which was also on the computer, so I thought it was something 11.10 specific, but maybe graphics in 10.04 was just simpler.

Eventually I would sometimes get weird color patterns on the screen while booting and/or boot errors (dmesg) from nvidia that the hardware was not responding. And eventually it started also happening in Ubuntu 10.04. I replaced the Galaxy GT 430 with an EVGA GTX 550 Ti (3 yr warranty) and never had those issues again in 11.10 or 12.04. Since January I have been running an MSI Twin Frozr Gaming GTX 750 Ti and then installed 64-bit Ubuntu 14.04. Other than initial issues with the GTX 750 Ti with new Maxwell chip not supported by nouveau nor nvidia-current and needing a newer video driver (nvidia-331-updates worked, now using nvidia-352), I have not had any such problems with this video card either with the same exact PC and other hardware that gave me troubles with the Galaxy GT 430.

So it is possible that your issue has nothing to do with Linux. It might just be that Galaxy video cards are not that reliable (unless there is some issue specific to the GT 430).

PS: This is with the PC in my sig which has no swap at all since I do not hibernate and last time I tried suspend it took about as long to wake from that as cold booting. I don't normally even shut down because my PC only uses 50 watts idling.

PPS: Didn't realize that there was a 2nd page of replies and that this only affected your mouse. I have had 1 similar issue lately which I thought might have been from not rebooting after doing certain updates. If I am using Google Chrome to watch Netflix (which I have set to stop after a show or movie ends) and I happen to doze off. When I wake the screen in the morning and close Chrome sometimes my system gets very sluggish (even though uptime shows low load ave.) and sometimes when I open something else it seems to end up transparent in the background and I cannot click on anything to shutdown or anything. But the keyboard still works, so I can Ctrl+Alt+F1, login, sudo reboot, and everything is back to normal.

---

### Post by tcll5850 on 2015-09-01
eh... idk... this is actually my 3rd Galaxy card (in general), which I'd given my 2nd to my brother.
I'd like to believe Galaxy is quite reliable as my first 2 are still kicking after 3 years, even after my abuse to them. XD
this GT430 isn't even a year old yet, so yea I'm inclined to disbelieve it's the card itself... >.>

buuut, just because it's new doesn't mean an issue like that couldn't happen, which I hope that's not the case... <_<
I mean, I did get 2 $75 Sparkle GT cards:
- first BSoD'd on installation
- replacement displayed patterns only after 7 months

but I know Galaxy is much better than Sparkle, so again, hopefully that's not the case... heh

reason I have this card is because I'm against a wasted slot in my PC for the heatsink...
this would render one of my PCIe x1 slots unusable.

I'd like to believe the issue is more with my cruddy MBd which has compatibility issues up it's A

---

### Post by tcll5850 on 2015-09-24
ok, so much for full RAM...

just happened to me again, twice, with RedEclipse.
(I'd thought the first time was a spoof)
RAM usage was about 50%, but the CPU was topped.

so it looks like a busy CPU causes my USB mouse driver to kill itself...
(and I'm running skype every time)

still no idea what could be going on here??
could have something to do with SDL I think (which somewhat makes sense) >_>

really wish more developers would use GLFW >3<

---

### Post by pqwoerituytrueiwoq on 2015-09-24
can you make it happen again and press ctrl+alt+f2
that should get you to a tty login
login and run dmesg -T > Desktop/dmesg.txt
you can then run 
sudo restart lightdm
i think that should get your mouse working again without a full reboot
post the last 15 lines or so here (see new file on desktop)
if you cant use your keyboard for this try using ssh (you will need to install openssh-server on your desktop and know its local ip address and have a second system to loginto it with)

try updating to the 3.19 kernel, i think that fixed my moms issue with suspend
[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes#LTS_Hardware_Enablement_Stack](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes#LTS_Hardware_Enablement_Stack)

---

### Post by tcll5850 on 2015-09-24
well, after losing everything I typed (there's a thing called drafts, this forum should use them), I'm just gonna say this:

Ctrl+Alt+F2 froze me, but the game still played music (the game was not the active window)
not sure if this was my video driver, lightdm, or a complete soft-freeze (like my wii with a bad hack)...

I wrote a small script to use ~50% of my CPU before starting my game, and I lost control within minutes of starting the match, so confirmed.

next time it happens, I'm just going to open a terminal and:
$ dmesg -T > Desktop/dmesg.txt
$ sudo restart lightdm


btw, that's what happened to cause me to lose everything... heh
($ sudo restart lightdm)
^wanted to see what exactly it did (kills all my programs, which I was kinda hoping to avoid)

EDIT:
welp, restarted lightdm, and it froze at my desktop BG...
but I did manage to get the report (can't attach) :)
[https://copy.com/Sj3YbOKI0N6mZJY9](https://copy.com/Sj3YbOKI0N6mZJY9)

---

