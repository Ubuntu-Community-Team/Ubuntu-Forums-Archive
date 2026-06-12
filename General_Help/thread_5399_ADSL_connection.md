---
title: "ADSL connection"
date: 2004-11-18
forum: General Help
---

### Post by viorel on 2004-11-18
[FONT=Verdana][SIZE=1]Well, ubuntu is the first distro that JUST recognizes my ADSL modem (alcatel speedtouch usb). And after plugging it i was looking in the device manager and couldn't believe my eyes. Is it really just going to work? Well, not quite. I might not have taken the right steps, but here's what I did next:

1. Computer --> System Configuration --> Networking
2. Add, wizzard automatically launches (too good to be true I thought)
3. Connection type: Modem(PPP)
4. Phone number (just typed in something, don't need it to connect)
5. Typed in my username and password
6. I chose Apply and activate connection
7. The new connection was added in my Network Settings window
8. I decided to take a look at the Properties of my new connection, and saw that the Modem port is /dev/modem. Just to make sure I clicked autodetect, and this is what I got:

```
**Could not autodetect modem device**
Check that the device is not busy and that is correctly
attached to the computer
```

Well, the device is not busy and it is correctly attached to the computer (how could you do it wrong, it's an USB port). More than that, as I said, the modem is recognized by the system, so nothing wrong there.
If I try to activate the connection, it deactivates after 1 second (probably because it can't communicate with the modem). What am I doing wrong?[/FONT][/SIZE]

---

### Post by puzzledm on 2004-11-18
Take a look at this page on the Ubuntu Wiki site:

[http://www.ubuntulinux.org/wiki/UKSpeedtouchDSLHowTo](http://www.ubuntulinux.org/wiki/UKSpeedtouchDSLHowTo)

It should help.

---

### Post by viorel on 2004-11-18
That one is for a different modem, I have the one from Alcatel. Do I still have to download the same thing from the  universe repository?

---

### Post by puzzledm on 2004-11-22
[QUOTE=viorel]That one is for a different modem, I have the one from Alcatel. Do I still have to download the same thing from the  universe repository?[/QUOTE]
 Thomson and Alcatel are the same company - so the above link is for the exact same modem as you have.  Follow that and it should work.

---

### Post by thoms on 2004-11-22
I had quite a lot of hassle setting up that modem with Red Hat, got it working evetually but I've got a new router now anyway which Ubuntu recognised straight away  :grin:

---

