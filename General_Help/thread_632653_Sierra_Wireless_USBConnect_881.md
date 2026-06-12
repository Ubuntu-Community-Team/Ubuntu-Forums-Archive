---
title: "Sierra Wireless USBConnect 881"
date: 2007-12-05
forum: General Help
---

### Post by a\v guru on 2007-12-05
First and foremost, thanks in advance for the help. I am new to Ubuntu and Linux.

I have an Intel based Mac Book (without PC card slots). I purchased a Sierra Wireless 881 card a couple of days ago. I got it running in OSX and Windows without a problem, however I have spent the last 5 hours trying to get it running on Ubuntu. I can not seem to find anyone else with this particular card and Linux. Any help would be great.

---

### Post by a\v guru on 2007-12-06
At least one of y'all know how to solve my problem I'm sure.

---

### Post by capsid on 2008-01-12
Hey buddy, I'm having problems as well.  

I found this guide here:
[http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=1076](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=1076)

When I do "modinfo sierra" the driver is located, but my problem is that the device doesn't seem to be located at /dev/ttyUSB0, or /dev/usb/ttyUSB0, or /dev/modem...How would I tell where it is located?

AT&T was worthless when it came to answering my questions.  They couldn't tell me what my username and password are, though I do know the phone number of the device.  I will keep experimenting and let you know what I find out, but if anybody has experience with this particular card and AT&T, I'd love to hear what you did to get it to work!

---

### Post by geraldm on 2008-01-13
When a driver finds its device, it should put a message into the log file.
Check in /var/log/syslog, /var/log/messages or /var/log/dmesg or use the command "dmesg"
No message usually would mean that the driver did not identify its device.

Gerald

---

### Post by capsid on 2008-01-13
Ok, thanks for the tip.  When I do "dmesg | grep sierra", I don't get anything.  I think that's because I need to apply the patch for TRU Install cards and recompile the kernel.  Supposedly the 6.23.xx kernel has this patch already applied.  Is there any easy way to do this (with apt, for example) or do I have to go off the beaten path?

I'll post the results...

---

### Post by traynor on 2008-06-20
Hi-

Were you able to get it to work? Is it possible to use an AT&T USBConnect 881 in Ubuntu 8.04???

Thanks!

---

### Post by quickwitt on 2008-06-22
I also have one of these devices. I would be grateful to know how to get it working under Ubuntu.

Thanks!

---

