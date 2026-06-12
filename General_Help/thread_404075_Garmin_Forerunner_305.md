---
title: "Garmin Forerunner 305"
date: 2007-04-07
forum: General Help
---

### Post by Xceptiona1 on 2007-04-07
I have a Garmin Forerunner 305 and it has software that downloads not only GPS data, but also heart rate data. It's the last application I need to move from Windows to Linux; Wine seems to load the setup just fine, until it hits the point where it wants to find the watch and then it sits there asking for it over and over. Obviously the watch, which connects via USB, is not being picked up during the installation. There is a windows driver I had to load in XP, but obviously that is not available for Linux from the Garmin website.

Does anyone have this or similar running watches working in Linux/Ubuntu. I am currently running Ubuntu 7 (beta). Thank you

---

### Post by laurens on 2007-12-14
I have exactly the same issue. I'm gonna try two programs:

[http://pytrainer.e-oss.net/](http://pytrainer.e-oss.net/) - this just might work, since it's written for linux.

[http://www.zonefivesoftware.com/SportTracks/index.html](http://www.zonefivesoftware.com/SportTracks/index.html) - This is written in C# for windows, and I'll give it a shot in the coming weeks, I hope.

---

### Post by Xceptiona1 on 2007-12-14
PyTrainer seems to find my Garmin 305, though it does not grab the heart rate. I see that there is a spot in which heart rate can be inputted, so I'm sure the plugin can be modified to grab that. I'm going to play with it some more; let me know how your tests come along. Thank you

---

### Post by laurens on 2007-12-16
I tried (under windows) SportTracks, and haven't yet checked PyTrainer, but I still intend to do so. SportTracks didn't seem to grab my heartrate either, but maybe I just couldn't find it yet.

---

### Post by laurens on 2007-12-16
I found another program, [http://code.google.com/p/garmintools/](http://code.google.com/p/garmintools/), which seems to support heartrate reading - I just browsed the source, haven't actually tried it. This is however, just a data-extraction tool, by the looks of it. Not a full GUI with lots of features.

---

### Post by butterman on 2008-01-25
Has anyone made any progress?  I have the same issue.

---

### Post by laurens on 2008-01-25
> **butterman said:**
> Has anyone made any progress?  I have the same issue.

Nope, not yet.

---

### Post by citybird on 2008-02-06
Any new info on this? I plan to pick up a new 305 today and just wanted to see if it would work under ubuntu native. 

If not no worries. I have VMware Server installed and I can run it under Windows 2000 native if needed.

---

### Post by laurens on 2008-02-07
No new info - it's just too easy to temp. boot windows, do my thing, and be done :)

---

### Post by brianborchers on 2008-02-09
gpsbabel can be used to extra heart rate data from the Garmin 305 using a couple of different formats.  
 
If you want a CSV file of time stamps, locations, and heart rates, use

gpsbabel -t -i garmin -f /dev/ttyUSB0 -o garmin301 -F outputfile

To get an XML file in Garmin's training center format, use
 
gpsbabel -t -i garmin -f /dev/ttyUSB0 -o gtrnctr -F outputfile

I see at least one occurence of "gtrnctr" in a recent update to the development version of pytrainer, so it looks like this is being added to pytrainer now but it isn't in the stable version yet.

---

### Post by brianborchers on 2008-02-09
[QUOTE=citybird;4280277]Any new info on this? I plan to pick up a new 305 today and just wanted to see if it would work under ubuntu native. 

So far, I've got the stable version of pytrainer working with my 305 for recording tracks and total mileage, but not the heart rate information.  I also have gpsbabel reading the heart rate information out in a couple of different formats, but pytrainer can't accept either of them yet.

---

### Post by the-kernelpanic on 2008-03-06
Thanks for posting your gpsbabel information above.  I was able to get my commute home ride extracted from my 305 and then manually trim it down and manually upload it as a .tcx file into Motionbased.  

It looks like even though I can't use my regular programs under Ubuntu, I can still get my information into Motionbased.  Now to automate the process a little bit...

Chris

---

### Post by ostehamster on 2008-03-12
> **citybird said:**
> If not no worries. I have VMware Server installed and I can run it under Windows 2000 native if needed.

Did you have any problem getting it to work in VMware/Windows? I have just got my Forerunne 305, and it works fine with pytrainer.  But, I still want to use GTC. Windows sees the Garmin device, but GTC can't see it :/

Regards
Christoffer

---

### Post by ahsoussan on 2008-03-15
Has anyone found a satisfying solution to installing the Garmin Training Center?

---

### Post by kommutator on 2008-03-16
Hi there, 

I've managed to get the tracks date from my Fr305 with gpsbabel by
      gpsbabel -t -r -w -i garmin -f usb: -o gpx -F outputfile
Tis works fine an can be imorted into PyTrainer. 
Unfortunately it does not include the heart rate data. 
This can be read by
      gpsbabel -t -r -w -i garmin -f usb: -o gtrnctr -F outputfile
but Pytrainer does not import this file (at least I couldn't do that). 

The PyTrainer plugin for Garmin devices with heart rate require setting the "device". 
Does anybody know what to fill in here?
I always get the error massage that the configuration is not correct.

Regards

kommutator

---

### Post by minophis on 2008-05-18
Hi

I have got Pytrainer working with the Forerunner 305 (including heart rate) on Ubuntu 8.04.

The correct device setting for Garmin Heart Rate is /dev/ttyUSB0

However to get the Forerunner to appear as ttyUSB0 you need to edit **/etc/modprobe.d/blacklist**. Comment out the line that says '**blacklist garmin_gps**' and then reboot.

After that Pytrainer should work with the Forerunner 305, it is a great piece of software.

I hope this helps.

Minophis

---

### Post by laurens on 2008-05-19
Thanks! Sounds great, I'll try it soon, tnx!

---

### Post by lrohr on 2008-07-15
You can also try the Software from [http://www.bikexperience.de/](http://www.bikexperience.de/)
it is written in Java and is available in English and German (of course free). It supports many different file types also you have to get the file first from the device (except the HAC devices I guess)

---

