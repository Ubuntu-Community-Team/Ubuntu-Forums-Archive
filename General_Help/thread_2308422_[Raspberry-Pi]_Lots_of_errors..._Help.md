---
title: "[Raspberry-Pi] Lots of errors... Help?"
date: 2016-01-02
forum: General Help
---

### Post by subway5411 on 2016-01-02
Hi, just today I got a Raspberry Pi 2 and I loaded Ubuntu Mate onto it. The first thing I did when I set it up was look around the OS a bit. It works quite well and I like the look. A few minutes later I got a warning stating that there was only 300 or so megabytes left on the SD card, It shocked me for a sec as the SD card is 32gb but then I remembered I needed to resize the file system. I did that following the exact instructions as on the site and I got all the memory back. After I did that I suddenly started getting all these errors, with the biggest one being that it cant check for updates. (There is a red circle with a line thru it). When I click show updates, It does nothing for about 30sec, then it says that the updater (or whatever program) has quit unexpectedly. There were also errors such as "Sorry, ubuntu 15.10 has experienced and internal error" and stuff like that. I checked the details and it said "ExecutablePath /usr/bin/apt-get". After a while, I left it for a while and came back. that red circle was still there but I wasn't getting spammed with messages. so I thought everything was good except for that. (Boy I was wrong). I went to restart the computer assuming that wound fix that but when it came back, i inputted my password and it literally just restarted. So great. Now I cant login. Anyone know whats up?

---

### Post by Bucky Ball on 2016-01-02
How did you create the SD and which version of Ubuntu Mate did you install? You are aware that a regular Ubuntu Mate will not install on a device with an ARM processor? You are going to need a spin for your RPi, not the desktop version downloaded in the regular way from the regular site. 

Have you had a look on the RPi site and seen what's on offer for download there? Did you download your [Mate from here]("https://ubuntu-mate.org/raspberry-pi/")? Have you seen the [other options here]("https://www.raspberrypi.org/downloads/")?

If you did download Mate from the RPi site, did you check the ISO for defects prior to creating the SD (did you use dd to create the SD?)?

---

