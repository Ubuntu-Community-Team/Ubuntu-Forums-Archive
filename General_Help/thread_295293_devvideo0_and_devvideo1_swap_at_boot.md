---
title: "/dev/video0 and /dev/video1 swap at boot"
date: 2006-11-07
forum: General Help
---

### Post by fragos on 2006-11-07
I have two video devices.  The 1st is a TV card supported by the bttv driver and the 2nd is a webcam.  I only seen this with Edgy.  The TV card usually comes up as /dev/video0 and the webcam as /dev/video1.  Some times these mount points are swapped and the configuration files of video applications like tvtime must be edited to work.  Is there a way to see that these devices have consistently assigned mount points.

---

### Post by fabertawe on 2006-11-16
I have the same problem... can anyone shed some light on this?

Cheers ... Paul

---

### Post by Psykotik on 2006-12-07
Has any of you find a solution ? I have same issue...

---

### Post by fabertawe on 2006-12-10
Psykotik, I've not found a solution but I was having a similar problem with sound, the onboard sound (disabled in BIOS) kept getting selected as the default in VLC instead of my sound card. After disabling the module for onboard sound I've not had the video switch problem. This could of course be purely coincidental!

Paul

---

### Post by fragos on 2006-12-10
I don't think your problem was coincidental.  To me it further illustrates some randomness in device recognition.  Pehaps this relates to the improvements made in boot time.  Mind you I'm not complaining about the faster boot and shutdown that Ubuntu 6.10 has brought to the party.  For me the problem is more of an annoyance than a show stopper.  This is a problem that a newbie might not be able to understand and I'd hate to see some go back to the evil empire because of it.

---

### Post by fabertawe on 2006-12-11
I've read loads of posts regarding Edgy's faster boot but it's exactly the same as Dapper for me (43-45 seconds) even though I've disabled lots of services etc. Shutdown is faster though.

Unfortunately these kinds of little problems can be very annoying for new users, like you say. We could also look at it another way... after the first month or two, if you've stuck with it, then you're actually learning how to manage your system and it's a good feeling to resolve issues and feel in control. It's got to be a good thing if (ex)Windows users can realise that they run their computer and not "big brother". WGA was the breaking point for me (I never enjoyed the "Windows experience" anyway). I'm getting way OT now, sorry!

I'm using 64bit so I've had a few extra issues to resolve ;) Definitely worth it though, I love Ubuntu.

Paul

---

### Post by fragos on 2006-12-11
Just got an updated udev.  Perhaps that will fix things.  I've been all Linux for 5 years.  I was a SuSE user but switched to Ubuntu with a Dapper RC.  Loveing Edgy and looking forward to Fiesty.

---

### Post by Psykotik on 2006-12-28
Bios "muting" is definitely not a good solution : I'm using the integrated soundcard !

Definitly not Edgy-and-his-new-boot related : I've been annoyed by this bug since dapper.

Definitly not a good bug for newbies : it takes time to identify the bug, and a newbie will spend much time searching why his TVcard works sometimes, and sometimes no. Why his webcam works the full moondays, and doesn't the others.

And as GNU/Linux is well known to have many problems with peripherals (due to the hardware constructors policy), many newbies are going to blame Ubuntu more than what it deserve it 8)

I've opened [a bug]("https://bugs.launchpad.net/distros/ubuntu/+bug/77332") in launchpad.

---

### Post by Stemp on 2006-12-28
Same problem here.
To handle it i've created 2 devices : /dev/webcam and /dev/tv

[http://ubuntufr.free.fr/?p=27]("http://ubuntufr.free.fr/?p=27") it's in French sorry.

In fact you just have to create a /etc/udev/rules.d/95-perso.rules file for your personal udev rules.

---

### Post by Psykotik on 2006-12-28
I speak french, so you've helped me very much ! Merci Stemp.

---

### Post by fragos on 2006-12-28
> **Stemp said:**
> Same problem here.
To handle it i've created 2 devices : /dev/webcam and /dev/tv

[http://ubuntufr.free.fr/?p=27]("http://ubuntufr.free.fr/?p=27") it's in French sorry.

In fact you just have to create a /etc/udev/rules.d/95-perso.rules file for your personal udev rules.

I don't speak French but the command lines don't need translation and with a little care I could follow the directions.  My TV card has a separate sound jack which gets externally cabled back into my box.  lspci gives me two lines for that card:

00:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

Is there something additional I need to do for the audio portion of the card?

I'll be glad to post the HowTo in English for those less adventuresome than I.

---

### Post by Psykotik on 2006-12-28
In my (humble) opinion, since it is related to a video conflict, you'll have to avoid a video conflict only. Investigate "00:0a.0" only, using the following how-to :

```

*look after your TV card :*

stemp@caderousse:~/documentation$ lspci
.....
00:0a.0 Multimedia controller: Philips Semiconductors SAA7134 Video Broadcast Decoder (rev 01)
…..

*use info related to your TV card to get still more info :*

stemp@caderousse:~$ cat /sys/devices/pci0000\:00/0000\:00\:0a.0/vendor
0×1131
stemp@caderousse:~$ cat /sys/devices/pci0000\:00/0000\:00\:0a.0/device
0×7134

*According this, add an fill up /etc/udev/rules.d/95-perso.rules :*

KERNEL=="video*", SYSFS{vendor}=="0×1131“, SYSFS{device}==”0×7134“, SYMLINK+=”tv”
```

I've not be able to use that second part related to TV card device, never got the symlink. Maybe because it is not recognized at all (no vendor or device id). But I've discovered a symlink which can perfectly substite the "tv" one : it's named "vbi" (target : vbi0), and works like a charm.

---

### Post by kf_man on 2007-04-08
In order to solve this issue for my Hauppauge PVR-250 and my FusionHDTV5 Lite, I had to use some slightly different commands.

To get the device info for my cards, I used the following udevinfo commands:
```
udevinfo -a -p $(udevinfo -q path -n /dev/video0)
udevinfo -a -p $(udevinfo -q path -n /dev/video1)
```

Since the Hauppauge includes multiple devices, video0, video24, and video32, I had to use the name of the proper device to get the proper mapping.

My final /etc/udev/rules.d/95-perso.rules file is:
```
KERNEL=="video*", SYSFS{vendor}=="0x4444", SYSFS{device}=="0x0016", SYSFS{name}=="ivtv0 encoder MPEG", SYMLINK+="video/pvr250"
KERNEL=="video*", SYSFS{vendor}=="0x109e", SYSFS{device}=="0x036e", SYMLINK+="video/fusionhdtv5"
```

This results in the following symlinks:
```
/dev/video/pvr250
/dev/video/fusionhdtv5
```

Hopefully this helps someone since I had a hard time getting it all to work together.

---

### Post by fragos on 2007-04-08
Thanks.  I'lll give this a try.

---

