---
title: "Skype issue (USB? Connection?)"
date: 2007-08-29
forum: General Help
---

### Post by zzelinski on 2007-08-29
When I had Skype for Linux 1.4.0.74 I could use Skype with no problems. Since upgrading to 1.4.0.99, I can still hear through the earpiece fine, but my audio sent to the other person is completely screwed up. They hear messed up bits and pieces; not even entire words are getting through, just little sounds. I tested this out with another feisty computer I had not updated to the latest version yet, and found that yes, the .74 version works fine, but when I upgraded it to .99 the mic audio was terrible.

I noticed I can display technical call info, so I looked at it while calling the Skype Test Call. My SessionIn UDP is about 60 packets updated every time the info refreshes (I can only assume something like 60 packets a second? Whatever) compared to, even when I'm recording my test message, around 4 packets for SessionOut UDP every time the info updates. In other words, by the time my UDP IN packets reach over 1000, my UDP out packets are only just over 150.

I also tested it with a different USB mic (connected to a camera) and it does the same thing, and I tested it with the other devices listed in the options. I'm not sure what device name goes with which actual port on my sound card, but one of them (not the USB devices but a sound card) during the test call just sends static--but it is fully recorded and played back, no problem. I also noticed that the UDP out packets went up to about 60 a second or whatever when sending the static. So maybe it's a problem with USB devices?

***I just tested my usb mics with another program and they work fine through that program...but don't in skype.

Please help! Everything worked fine in 1.4.0.74...if someone has a .deb of that, let me know-- I just want Skype to work, and I can't find any download for the old .74 version anywhere.

---

### Post by zzelinski on 2007-09-04
What is going on? Will anybody help me out? I have no idea what is happening, but it seems like somehow my mic output is either being recorded at a low rate or is being transferred at a low rate. HELP!!

---

