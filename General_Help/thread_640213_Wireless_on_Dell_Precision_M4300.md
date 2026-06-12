---
title: "Wireless on Dell Precision M4300"
date: 2007-12-13
forum: General Help
---

### Post by tstorm007 on 2007-12-13
Hi,

I'm fairly  new to Ubuntu and just recently installed it on my new Dell M4300 laptop.  I've got nearly everything working as I would like (sound, dual monitors, etc) but I cannot get the wireless to work.  The little network thing on the top menu doesn't show any wireless networks (either here or at school, where there should be many).  When I go to the Network Settings GUI, it says the Wireless connection has Roaming Mode enabled.  

Do I need to install any special drivers for the wireless card?  How do I tell if it's installed correctly?

Thanks,
Todd

---

### Post by hrafninn on 2007-12-14
I have the same problem with my Precision M4300. First, check which Wireless card is on your machine.
You can use the command: lshw -C network.

I have a BCM4328 card.  Did some googling and found the following page: [http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes.html#4](http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes.html#4)

I followed the instructions described in section [COLOR="Red"]Fixing the WiFi for the BCM4328[/COLOR].
Unfortunately, it didn't solve the problem :-(
The writer used this method for his Dell Latitude D830, but I would think it should work for the Precision M4300 as well.  The same WiFi card is used in both cases.

When I run the Network Settings GUI, I only see "Wired connection" and "Modem connection".

Can anyone help here?

---

### Post by hrafninn on 2007-12-14
Got it to work!

Just follow the instructions in: [http://ubuntuforums.org/showthread.php?t=297092&highlight=Check+wireless+connection](http://ubuntuforums.org/showthread.php?t=297092&highlight=Check+wireless+connection)

---

### Post by tstorm007 on 2007-12-14
Awesome, that worked perfectly!

PS.  Wrote this message over my wireless connection :)

---

