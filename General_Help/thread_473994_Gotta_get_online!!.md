---
title: "Gotta get online!!"
date: 2007-06-14
forum: General Help
---

### Post by John CCC on 2007-06-14
Hi, I'm new to Linux and Ubuntu. However eager I am to learn with forums and countless sites, I need to get my pc connected to the internet with a speedtouch adsl modem.  I am currently using a separate machine that I will only have access to for the night.  From what I've read, it's more complicated that I thought it would be.  Can anyone point me in the right direction?
Please help...
THanks!

---

### Post by jwh400 on 2007-06-14
I'm not familiar with that modem but here's a link to setting it up.

[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

---

### Post by RedSquirrel on 2007-06-14
I don't have that modem, but here are a couple of links:

General internet connection information:

[https://help.ubuntu.com/7.04/internet/C/index.html](https://help.ubuntu.com/7.04/internet/C/index.html)

SpeedTouch:

[https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch)

---

### Post by John CCC on 2007-06-16
Thanks for the links... unfortunately, I'm getting stuck on the early steps.. ie: which version of speedtouch adsl modem am I using.  Plugging the usb modem into the linux machine and then trying this:
awk '/4061/ { print $5 }' /proc/bus/usb/devices
in the terminal is supposed to tell me which version it is.  However, it yields, "directory not found"  
I still have access to a windows machine and the internet, is there another way to figure out which version I am using? and then, I am afraid, I am not altogether confident that I am using the terminal correctly.  Ideally, it would be nice if I could get that together before attempting any thing complicated (as it seems that this process is) however, So...
I found this link [http://linux-usb.sourceforge.net/SpeedTouch/docs/howto.html](http://linux-usb.sourceforge.net/SpeedTouch/docs/howto.html)  The speedbundle referred to here looks like it would be a simple solution.  However, I am having a hard time knowing where to find the right firmware (version??), and then where to put it once I do find it... (directions simply state "on the box")

---

### Post by RedSquirrel on 2007-06-16
Hmm... at the top of the page of the second link I mentioned, they suggest using this command to determine the firmware version:

```
grep -B 1 "THOMSON" /proc/bus/usb/devices
```

---

### Post by John CCC on 2007-06-16
haaaaaaaaaa lay lu yah
ha lay lu yah
ha lay lu yah
ha laaaaay luuuu yaaaah

haaaaaaaaaa lay lu yah
ha lay lu yah
ha lay lu yah
ha laaaaay luuuu yaaaah

haaaaaaaaaa lay lu yah
ha lay lu yah
ha lay lu yah
ha laaaaay luuuu yaaaah

I would just like to take this opportunity to thank all those who stood by me throughout this difficult ordeal.... redwinder, I may not know you... but through all this you've been like a brother to me! I love ya man...

Red Squirrel you gave it your all... and I won't soon forget that!

Rui Pais, (pause for dramatic effect) bottom line... you came through for me man... (through tears) You tha man!

And to all you other homeys and hommettes out there usin Ubuntu... keep on keepin on!

Peace out!

P.S. I got the modem to work! I used: USB ADSL Modem Manager for Gnome? referred by Rui Pais. It's absolutely brilliant and hastle free!

---

