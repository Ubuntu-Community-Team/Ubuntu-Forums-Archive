---
title: "Unetbootin not working in Ubuntu 12.04"
date: 2014-04-16
forum: General Help
---

### Post by Vannyi on 2014-04-16
I have an iso Ubuntu image that I would like to burn to a USB stick.  I have always used Unetbootin to do this, but today, when I put the dot in DiskImage and then click on the three dots to select the location of the iso image, Unetbootin freezes.

I have tried uninstalling/rebooting/reinstalling the application, but the problem remains.

I had two questions:

1.  Is there any way to fix this that anyone knows?
2.  If not, is there an alternative to Unetbootin that I can use?

Thank you

---

### Post by sudodus on 2014-04-16
I just checked in my 12.04.4 system, and Unetbootin works. If your system is updated/upgraded, there must be something wrong. I would have suggested, that you reinstall it, but you have already done that. Maybe it will work if you update/upgrade and then reboot your computer.

Otherwise there are several alternatives. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I like [mkusb]("http://ubuntuforums.org/showthread.php?t=1958073") (but I'm prejudiced, because I made it).

You can also try Ubuntu's own usb-creator (Startup Disk Creator). Wiping a drive might not work, but otherwise it should work for you.

---

### Post by coldraven on 2014-04-16
Strange, it works fine for me on 12.04. Have you moved an iso file from where Unetbootin thinks it was the last time you used it?
I just looked but could not find a configuration file associated with the program.

---

### Post by sammiev on 2014-04-16
Every once in a while I need to use GParted to delete and format my USB stick to get Unetbootin to work.

---

### Post by Vannyi on 2014-04-16
Thanks everyone for your suggestions and tips.  I've used the same format I always have....make a drive image of my pc using remastersys and then make a live USB stick.  Remastersys always puts the file in the same spot.

@sudodus I did not know that Ubuntu had this feature built into their OS.  I just tried it and it worked perfectly.  Thank you, problem solved.

---

### Post by sudodus on 2014-04-17
I glad it worked for you :-)

Please click on Thread Tools at the top of the page and mark this thread as SOLVED

---

