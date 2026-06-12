---
title: "Pinnacle PCTV HD Ultimate stick TV tuner"
date: 2007-10-22
forum: General Help
---

### Post by MichaelSwengel on 2007-10-22
Has anyone found a way to get the Pinnacle PCTV HD Ultimate stick USB TV tuner working with Gutsy?

---

### Post by karhulitos on 2007-10-24
I have Pinnacle PCTV DVB-T Usb stick. I got it running with Feisty but now that Gutsy came I lost my TV. Haven't found instructions, v4l-dvb didn't help me. All dmesg says is (after doing sudo modprobe em28xx)
```

[ 5361.736000] usb 3-1: new high speed USB device using ehci_hcd and address 3
[ 5361.868000] usb 3-1: configuration #1 chosen from 1 choice
[ 5384.688000] Linux video capture interface: v2.00
[ 5384.732000] em28xx v4l2 driver version 0.0.1 loaded
[ 5384.732000] usbcore: registered new interface driver em28xx

```

Too bad..

---

### Post by karhulitos on 2007-10-24
Darn I was stupid.. had a bookmark to [http://mcentral.de/wiki/index.php/Em2880]("http://mcentral.de/wiki/index.php/Em2880")
but didn't remember it.
Started to work immediately. I used the v4l-dvb-experimental.

---

### Post by asdf46 on 2007-10-27
karhulitos where did you download the expermental from? When I try to do the hg clone it tells me  > abort: 'http://mcentral.de/hg/~mrec/v4l-dvb-kernel' does not appear to be an hg repository!
Any idea what I am missing?

Thank you,
asdf46

---

### Post by quick_nick on 2007-10-27
your going to have to use
```
 hg clone http://mcentral.de/hg/~mrec/v4l-dvb-experimental
```

that should work for you as of now.  I still dont have mine working but i was able to get that stage.  I'm stuck not able to scan for channels yet.

---

### Post by asdf46 on 2007-10-28
Thanks for that, it is working now. I'm not sure what you are using for DVB Tuning, but MythTV is the only thing that I could ever get to work.

asdf46

---

### Post by karhulitos on 2007-10-30
Oh, slow lazy sucker I am. Fortunately someone already answered to use that experimental one.
I've been using Kaffeine for watching TV as MythTV crashed too many times.

So far it's been perfect for my needs, except I haven't found a way to set finnish subtitles as default, i.e. whenever I watch a substitled show I need to play with the mouse. Bugger.

---

### Post by fearpi on 2008-01-07
Are any of you actually using the Pinnacle PCTV HD **Ultimate** stick? I had the Pro stick (800e) which worked fine with em28xx, but now that I am using the Ultimate stick, I get nothing. No device /dev/video0 is even created anymore.

---

### Post by MichaelSwengel on 2008-01-22
I am...that's what this thread was created for. But apparently the topic got changed. :mad:

Now. Does anyone have a clue about the PCTV HD **ULTIMATE** stick??

---

### Post by fearpi on 2008-03-16
Just a bump as it's been a couple of months. Can anyone share any knowledge about this device?

---

### Post by harty83 on 2008-05-29
Just bought the ultimate stick and of course can't get it to work in gusty or hardy.  It has again been a couple months so any new insight on getting this to work with Ubuntu?

---

### Post by fearpi on 2008-05-29
I have exchanged e-mails in the past few weeks with Markus Rechberger, a developer affiliated with the video4linux and em28xx projects. He has obtained specs for the device (from Pinnacle, I guess) under a non-disclosure agreement. I don't know anything beyond that. You may want to sign up for the [video4linux mailing list](http://www.redhat.com/mailman/listinfo/video4linux-list), or contact Markus (mrechberger at empiatech dot com).

---

