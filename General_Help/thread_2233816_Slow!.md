---
title: "Slow!"
date: 2014-07-10
forum: General Help
---

### Post by william39 on 2014-07-10
Hello.  Excited to be using Ubuntu for the first time but am finding it really slow.  I am running the latest version.

It is installed on my Acer Laptop.  5.2GB of Ram, AMD A4-5000 APU with Radeon(TM) HD Graphics × 4......I assume it should be fast as my laptop is not an old one (less than a year old). 

Any help would be appreciated.  

Thanks.

---

### Post by mooreted on 2014-07-10
"Slow" can mean a lot of things. Slow loading webpages? Slow loading programs? Slow graphical animations?

Have you installed the driver for your video card? In the Dash menu you will find Additional Drivers. Look in there and see if there is a driver for your video card.

Ubuntu runs fast on my machine, but I have a pretty beefed up desktop.

---

### Post by william39 on 2014-07-10
Thanks for the reply.  The computer itself feels slow, opening up the additonal drivers, settings, even clicking on about this computer takes about 10sec for it to open up.

---

### Post by mooreted on 2014-07-11
That's not normal. Open a command prompt and enter the command "top". Look for any processes using a lot of CPU cycles.

Also run the command "free -m" and post the output.

Did you do manual partitioning or just use the defaults? If you did manual partitioning, did you create a swap partition?

What is the exact model of your video card?

Check the lists here and see if your card is on any of them:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by HermanAB on 2014-07-11
Run top or htop and see what is sapping the CPU and kill the culprit.  If the CPU is idle 99% of the time, then check your DNS performance with dig.

---

