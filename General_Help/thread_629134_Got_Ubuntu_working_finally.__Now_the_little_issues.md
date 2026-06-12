---
title: "Got Ubuntu working finally.  Now the little issues: Equaliser, Bluetooth dropout, HP"
date: 2007-12-02
forum: General Help
---

### Post by Mysticle31 on 2007-12-02
I've FINALLY got Ubuntu working well, so I would like to look into the other little issues now.

1) Bluetooth.  I have an MX5000 Keyboard and MX1000 mouse running the bluetooth receiver in HCI mode

When ever I try to connect my wireless mouse and keyboard I get "Couldn't display "obex://[MAC Address]""  How do I fix this?  I've installed gnome-vfs-obexftp.  It's not just my mouse and keyboard either, it's ALL my bluetooth devices.  I didn't have this problem in Kubuntu or any other distro I tried..  

I did get my keyboard and mouse working right, and running on system bootup by searching following these directions. 

[http://ubuntuforums.org/showthread.php?t=594624&highlight=HOWTO%3A+Logitech+Bluetooth+Mouse+Keyboard](http://ubuntuforums.org/showthread.php?t=594624&highlight=HOWTO%3A+Logitech+Bluetooth+Mouse+Keyboard)

It works well except for one thing.  Sometimes when booting and resuming from screensaver it "forgets", for lack of a better word, to activate the keyboard.  Then I have to go restart the computer and it may or may not work.

Also, is there a way to make the media buttons on my keyboard work?  

I've already gotten the back and forward buttons on my mouse working.  Is there a way to make the scroll left and right work?  How about the auto scroll (cruse)?  How about the task switcher button?

2) HP OfficeJet 7310. I've got HPLIP working well and it will print.  I don't yet know if the duplexer or scanner work, so I may ask about them later.  Anyhow, I have card readers on the printer.  HPLIP allows me to get pictures off of the card, however I would like to access the cards like a "real" card reader and mount it for file transfer.  Can this be done?

3)  I have a Creative Labs Audigy 2 Platinum ZS.  Is there any way to get it's features working?  It has THX and Dolby, and all sorts of them.  I would like to have them if I can.  However the two features that I need to use are these:
---------------Equalizer:  I miss having a system wide equalizer
---------------"What you hear": In windows the drivers came with a what you hear feature.  Where I could plug something into line in and hear it.  I plug my FM radio, XM, tape player, record player..etc though my sound card.

Bonus Question -

How do I do partioning in Ubuntu?  I want to change the mounting point of one of my hard drives that is not detected (a mybook)   I also can't find anything to manage my

---

### Post by Mysticle31 on 2007-12-02
2) getting HPLIP to allow mounting the cards was easy.  It's a USB connection only function and I was running my printer over the network.  Problem solved.  Too bad the "Select Computer" to scan to feature doesn't work on the printer itself.  It's not a big deal.

---

### Post by Mysticle31 on 2007-12-02
Any ideas?

I was thinking I could create a script that would run 

"hidd --search" to solve the bluetooth keyboard dropout problem

However when I create the file, I can't get it to run.

#!/bin/bash
sudo hidd --search

Any ideas to my other issues?

---

