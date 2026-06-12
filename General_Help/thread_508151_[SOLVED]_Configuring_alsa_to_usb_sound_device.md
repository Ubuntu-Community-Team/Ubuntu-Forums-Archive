---
title: "[SOLVED] Configuring alsa to usb sound device?"
date: 2007-07-23
forum: General Help
---

### Post by rouge568 on 2007-07-23
I have [this]("http://http://www.siig.com/product.asp?catid=83&pid=871") USB sound device hooked up to my surround sound speaker system. Only problem is, I can't get it to work. When testing the usb sound device though sound preferences, I get a tone, but it doesn't work for regular playback. Any help? Thanks in advance.

---

### Post by geraldm on 2007-07-23
Please post the device information found in /proc/bus/usb/devices for just this device.

It appears to use the usb audio class, so there is a possibility that alsa could drive it.

Gerald

---

### Post by LDRoamer on 2007-07-23
I had similar problems with a usb sound card (turtle beach card).  I found that I had to force the usb sound card to be the default device. I followed this from another message on the forum to get it working:

had the same problem with my USB speakers, and after much searching found this solution:
Code:

asoundconf list

your USB headset/speakers should be in there (mine were just called "Audio"), now:
Code:

asoundconf set-default-card Audio

replace "Audio" with whatever your device is called. Now reboot and you're done.

Once I did this my usb sound card was working perfectly.  Good luck.

---

### Post by rouge568 on 2007-07-24
There was nothing in /proc/bus/usb/devices, neither the sound device or the wireless mouse that I use. hmmm...

edit: Thank you Roamer! Your solution worked! Hildago never sounded so good.

---

