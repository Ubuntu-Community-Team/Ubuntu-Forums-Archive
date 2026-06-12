---
title: "Pilot syncing"
date: 2008-07-09
forum: General Help
---

### Post by greybeard95a on 2008-07-09
I don't know what forum category this goes under, so I assume somebody will refile it.

I'm getting really annoyed with the issue of syncing Palm Pilots.  As near as I can tell, the procedure is profoundly broken on every operating system I've tried it on.  But I'd really like it to work under Ubuntu.  And what would be really cool is if were reliable.

I'm using jpilot--not that this seems to make any difference--because I got tired of having to force evolution to shutdown because it keeps hanging on issues unrelated to this.  I thought I was successful in configuring the Palm Pilot through gnomecc, but when I try to actually sync, it fails to recognize the device, saying it needs to be configured through gnomecc.

As near as I can tell, the problem is that gnomecc failed to accept the ID from the device.  It thinks it knows about a Palm Pilot with ID zero; the error message says the Pilot (actually a Treo 700p) identifies with a several digit number that is less than zero.  When I tried telling gnomecc to get the number from the device, it came back with zero.  When I tried inputting the number reported in the error message, it refused to accept the dash needed to signify a negative number.  Lastly, when I tried telling gnomecc to set the ID to a positive number (with fewer digits), it simply failed.  I also tried finding where on the Pilot to change its ID manually, but didn't see anything.

I looked around and found an old HOWTO that starts off by referring to devices that do not exist in my /dev directory: ttyUSB0 and ttyUSB1.  So that's obviously wrong.

Come on, guys.  You can't claim this is working when it is this difficult.  And you can't imagine how fed up I am with this nonsense.

How do I get this broken garbage working?

---

### Post by arm-c on 2008-07-09
I had problems... but I use Palm Treo 650 and Evolution.  I also do not use XUBUNTU.

I remember that there is a config file with device ID information in it.  I found this through google search for something like:  Ubuntu hardy "Treo 650" synch howto

Adding the correct device ID information to the file improved my synch efforts.

If that doesn't turn up something, try variations.  I haven't tried a Treo 7xx yet, so don't have that experience.  

Try this thread -  but it might be too old: 
[http://ubuntuforums.org/showthread.php?t=77387&page=9](http://ubuntuforums.org/showthread.php?t=77387&page=9)

I didn't have too difficult a time getting it going though.  Wish I remembered the details.  Don't give up! :)

---

### Post by greybeard95a on 2008-07-11
I'm not sure what worked.  Here is my .gnome2/gnome-pilot.d/gpilotd :


[General]
sync_PC_Id=1773583092
progress_stepping=5
num_devices=1
num_pilots=2

[Device0]
type=1
name=Cradle
device=usb:
speed=57600
timeout=2

[Pilot0]
name=MyPDA
pilotid=-1010058756
creation=1176750091
romversion=88682785
pilotusername=benfell
basedir=/home/benfell/MyPDA

[Pilot1]
name=MyPDA1
pilotid=1010058756
creation=1176750091
romversion=88682785
pilotusername=benfell
basedir=/home/benfell/MyPDA1

I edited pilotid in both cases.  It still failed to recognize the device with the negative number but failed to complain when I created a second entry [Pilot1] using gnomecc and edited it to the absolute value of the number.

It may be that none of this is relevant to jpilot.  jpilot has its own preferences, under File>Preferences, which must be set.  The device must be changed from /dev/pilot (the default) to usb: and the ID--for which it supplies a random number--must be corrected under File>Install User.

Unfortunately, jpilot doesn't seem to deal with the photos I had taken on the device.  It copied down all my ring tones and all my programs, but I never saw my pictures.  I don't see any option for dealing with anything on the memory card.

---

### Post by greybeard95a on 2008-07-11
It turns out there is a plugin for jpilot to deal with photos and the SD card.  Information is at [http://kaybyrd.com/?p=58]("http://kaybyrd.com/?p=58") and the plugin itself can be downloaded from [http://sourceforge.net/projects/picsnvideos]("http://sourceforge.net/projects/picsnvideos").

---

