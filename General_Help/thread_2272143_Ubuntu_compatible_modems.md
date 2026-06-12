---
title: "Ubuntu compatible modems"
date: 2015-04-04
forum: General Help
---

### Post by Siddhartha_Kashyap on 2015-04-04
I'm quite new to Lubuntu and I've been using Lubuntu 14.04.2 LTS right now. My problem is that I can't seem to make my LAPCARE 3G USB MODEM work with Lubuntu :( The only way to connect to internet is to tether my Android phone. I tried the Usbmodswitch and wvdial commands but I failed. I want to ask if there are ready made USB modems to work with Lubuntu ? Please recommend some good compatible USB modems.

---

### Post by egeezer on 2015-04-04
Try [http://www.hardware4linux.info/](http://www.hardware4linux.info/)

---

### Post by Siddhartha_Kashyap on 2015-04-04
It says "nothing found "

---

### Post by kunitoki2 on 2015-04-05
my isp is 1&1, a german company, they sent me a usb modem a couple years ago
the modem's manufacturer ist zte, it works great
lubuntu recognized it immediately, i didn't have to install or configure anything, 20 seconds and i was online
hope it helps you
maybe zte modems are a good choice
of course i don't know if the new ones also work as well as my old one
but of course i hope so

---

### Post by Siddhartha_Kashyap on 2015-04-07
THANKS. I must start looking for a ZTE modem

---

### Post by Topsiho on 2015-04-07
Hello,

If there's no special reason for using a USB modem, why don't you consider using an ethernet modem.
I had, a very long time ago (>10 years) a USB-modem, provided by my isp, that I had to jump through innumerable hoops to not succeed to get it working. But things may have changed by now,
After getting an ethernet modem, I never had any difficulties connecting to the internet. It was dead easy, not a problem at all. You may guess which modem I ditched ...

See also 

[https://help.ubuntu.com/community/InternetHowto](https://help.ubuntu.com/community/InternetHowto) 

It's a good idea to use google if you want some information :)

Topsiho

---

### Post by efflandt on 2015-04-07
Topsiho, the OP is discussing a mobile data dongle. I have not heard of an Ethernet mobile data modem other than using a mobile broadband router that the USB mobile data dongle could plug into.

Does Lubuntu have NetworkManager? Normally that would be used for connecting a mobile broadband device. I am not familiar with USBmodswitch (or is that used to switch between usb mass storage mode and modem mode for modems that have Windows drivers on them?), and probably have not used wvdial since dial up modem days, so I don't know if either of those would interfere with NetworkManager. The USB mobile data dongle I had a while ago (before I got a smart phone a couple of years ago) worked in NetworkManager without any problems.

---

### Post by Siddhartha_Kashyap on 2015-04-08
Well setting up broadband costs relatively higher than getting a 3G SIM card. So I'm specifically looking for a USB modem. Thanks

---

### Post by Siddhartha_Kashyap on 2015-04-08
Lubuntu does have a network manager. The USB tethering function in android works fine with it (without any setting and drivers). Lubuntu, Ubuntu and Elementary OS detect my modem as a storage device, not as a modem

---

### Post by Topsiho on 2015-04-08
> Topsiho, the OP is discussing a mobile data dongle. I have not heard of an Ethernet mobile data modem other than using a mobile broadband router that the USB mobile data dongle could plug into.

Oeps, I am sorry. The 3G part in LAPCARE 3G USB MODEM should have put me on my quivive, but did not. I only read the USB MODEM part.
To be sure, I never worked with such a dongle, so please forget it :(

Topsiho

---

### Post by kunitoki2 on 2015-04-08
my zte modem gets labeled as zte mmc storage in the left column of the disks app
but nevertheless it automatically works correctly and lubuntu automatically asks me to enter the sim pin
yes lubuntu has a network manager
there was a bug weeks ago where on some systems it didn't autostart
you could start it manually by running nm-applet
afaik the bug got fixed

---

### Post by kunitoki2 on 2015-04-08
i correct: it makes sense that the modem stick is also a storage stick since the (windows) dial up software is stored on it (which i guess isn't necessary anymore with the new windows versions)
lubuntu ignores it anyway and uses it out of the box

---

