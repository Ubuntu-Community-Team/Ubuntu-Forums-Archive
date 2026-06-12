---
title: "System Freezing"
date: 2008-07-05
forum: General Help
---

### Post by Aphelion02 on 2008-07-05
I just installed Ubuntu yesterday (dual boot w/ Vista), and I have to say I've never loved an OS more in my life. However, there's been two hang ups where the system just completely, suddenly froze with no warning whatsoever. The screen would simply freeze in position, and no commands would be taken and I have to reboot via the reset button.

I have the exactly system time for the second time this happened, but beyond that I can't really tell anything. Can anyone help me with this issue?

---

### Post by Sam Lars on 2008-07-05
What were you doing before the crash?  You should check /var/log/syslog to see if anything was logged before the crash that would indicate what went wrong.
Can you get to a terminal with Ctrl+Alt+F1, or restart X with Ctrl+Alt+Backspace?

---

### Post by Aphelion02 on 2008-07-05
I was running firefox and accessing my school server via ssh. It just happened another 10 minutes ago, and that was me literally just starting up. I didn't even have time to open the applications yet

This time it happened it was 21:54. I included the syslog file from then since I don't really understand it.

---

### Post by Aphelion02 on 2008-07-05
Just crashed again, making it the second time in 10 min. Now I'm pretty scared. Crash time was 22:10. Syslog is below, interesting they both show the wlan entry right before restart. For now I'm making sure I'm wired, but I'm just guessing here. Any gurus please help?

I'd just like to add that the system would not respond to ctrl-alt-F1 or ctrl-alt-backspace

---

### Post by Aphelion02 on 2008-07-06
Bump, this problem is very serious for me, please spare some time to help!

Thanks!

---

### Post by Sam Lars on 2008-07-06
Since the second one has that entry a while before your crash, I don't think it's directly related.  But it could definitely be related to wi-fi, I've had some hard freezes with Ndiswrapper.  Does it seem to go away when you're on a wired connection?

---

### Post by Aphelion02 on 2008-07-07
I can't really tell, but I suspected the same thing and put myself on a wired connection - it hasn't crashed for those 12 hours or so. Afterwards I had to switch to wireless and it crashed within an hour or so.

I attached the screenshot below: notice its the exact same line w/ wlan0 complaining about there being no IPv6 routers present. The late restart time was because I booted up windows after that. Its been the same thing the last 3 times - can we conclude a correlation? What should I go about doing to fix this? I want to be able to use my wireless card eventually, is there a workaround?

Please help - I simply can't go back to Vista at this point everything about it annoys me now.

---

### Post by Sam Lars on 2008-07-07
Well how is your wireless set up?  Did it work out of the box, or are you using some other driver?  And what kind of card is it?

You could try disabling this IPv6:
```
/etc/modprobe.d/aliases
```
Change from:
```
alias net-pf-10 ipv6
```
to
```
alias net-pf-10 off 
```

---

### Post by Aphelion02 on 2008-07-07
I have a linksys wireless-g pci adapter which worked out of the box with ubuntu. 

I'll try the changes you described and let you know, thanks!

---

### Post by Aphelion02 on 2008-07-07
This was quick, system prompted froze again after I tried wireless. I'm going to touch wireless now - 5 hard reboots in 3 days way too much, I don't want to lose my harddrive.

This time the system had a weird --MARK-- line in syslog at time of reboot, and before that was the all two familiar complaint about IPv6 routers. I did the changes you suggested but they didn't seem to work.
Ironically this all happened was I was reading through the Hardy Freezing thread. Was there anyone with this problem? Is there a way to get the powers-to-be to understand this, this feels like a pretty severe problem in an LTS release.

---

### Post by Sam Lars on 2008-07-07
You should try using Ndiswrapper to set up your wireless card.
Could you post the output of
```
lspci
```
in a terminal?  That will help to get the right driver (and help) for your card.

---

### Post by Aphelion02 on 2008-07-07
Here's the output for lspci. I heard of this Ndiswrapper -what does it do? And also, reading through some similar threads, I've heard of people crashing with ndiswrapper - will it help my situation?

---

### Post by Sam Lars on 2008-07-07
Yes, it's frozen on one card I've had, but with another one I have, it's been going for a couple months with no problems.  If you're having issues with the default Ubuntu driver, you should at least try it.
Here's a guide for Ralink cards:
[http://ubuntuforums.org/showthread.php?t=563547&highlight=ralink+rt2561](http://ubuntuforums.org/showthread.php?t=563547&highlight=ralink+rt2561)
Basically you need to
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
```
while you're connected to internet, of course.
Then:
```
echo 'blacklist rt61' | sudo tee -a /etc/modprobe.d/blacklist
```
You'll need the driver that came with the card.  If you don't have the CD, you can try the manufacturer's website.  That chipset is used in a lot of different cards, so I don't know which one you have.
Otherwise, you can try these:
[http://www.drivershq.com/Drivers/Devices/Ralink-RT2561-RT2661-series-Wireless-LAN-Driver/4689/36/Drivers.aspx](http://www.drivershq.com/Drivers/Devices/Ralink-RT2561-RT2661-series-Wireless-LAN-Driver/4689/36/Drivers.aspx)
[http://www.opendrivers.com/freedownload/237047/ralink-rt61-rt2500-wireless-pci-driver-1.2.0.0-whql-windows-9x-2000-xp-xp-x64-download.html](http://www.opendrivers.com/freedownload/237047/ralink-rt61-rt2500-wireless-pci-driver-1.2.0.0-whql-windows-9x-2000-xp-xp-x64-download.html)
[http://wiki.zenwalk.org/index.php?title=RaLink_RT2561/RT61](http://wiki.zenwalk.org/index.php?title=RaLink_RT2561/RT61)
You'll want the .exe file:
```
unzip <driver_archive>.exe
```
Then go to System > Administration > Windows Wireless Drivers, and Install New Driver.  Navigate to the folder that the previous command created, and find the .inf file.  Make sure it says the hardware is present.  If it says it isn't, then try a different driver.
Check /etc/modules to see if there's an "ndiswrapper" line.  If it's not there, you can add it.
You can try a reboot then to see if it works.

---

### Post by Aphelion02 on 2008-07-07
Thanks! I was looking around and apparently Ralink released fairly recent native linux drivers for my chipset. Is this driver different from what Ubuntu provides by default? 

[http://www.ralinktech.com/ralink/Home/Support/Linux.html]("http://www.ralinktech.com/ralink/Home/Support/Linux.html")

If I go ahead and use these drivers rather than windows ones, do I need to install ndiswrapper even after that? From what I understand, ndiswrapper simply implements the windows api?

---

### Post by Sam Lars on 2008-07-07
I'm pretty sure those are the drivers that Ubuntu is using.  They may be a little newer, but I think they're the same.
I would suggest trying Ndiswrapper first, it's much more simple and easy to undo if it doesn't work.
If Ndiswrapper doesn't work, you can try to set up the driver from that site.  There's a README file in the Module folder, and a guide [here]("http://ubuntuforums.org/showthread.php?t=132980").
If you have any questions just post back here.

---

