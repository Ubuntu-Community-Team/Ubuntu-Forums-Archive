---
title: "lost sound after adding user"
date: 2017-09-11
forum: General Help
---

### Post by Buntu Bunny on 2017-09-11
I had no problem with sound until my husband's computer died and I added him to mine as a second user. Since then, I can't get any sound on my desktop, even though he can get it on his. The volume indicator on my system notification area looks fine until I hit "play," then it changes to the mute symbol. When I click the icon to take a look at sound settings, sound is not muted. If I hit sound pause or stop, the notification icon changes back to normal. 

The only things I knew to check were these:

```
sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC662 rev3 Analog [ALC662 rev3 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
cat /var/log/syslog* | grep -i pulse
Sep 11 05:34:34 leigh-Inspiron-3650 pulseaudio[2050]: [pulseaudio] pid.c: Daemon already running.
leigh@leigh-Inspiron-3650:~$ cat /var/log/syslog* | grep -i pulse
Sep 11 16:52:15 leigh-Inspiron-3650 pulseaudio[7307]: [pulseaudio] pid.c: Daemon already running.
Sep 10 12:34:05 leigh-Inspiron-3650 pulseaudio[6626]: [pulseaudio] pid.c: Daemon already running.
Sep 10 21:45:35 leigh-Inspiron-3650 pulseaudio[6613]: [pulseaudio] module-x11-publish.c: PulseAudio information vanished from X11!
Binary file (standard input) matches
```

None of this is helping me.

This is on 16.04, but I had this problem with 12.04 as well, i.e. second user had sound, admin user did not. 

Suggestions?

---

### Post by Buntu Bunny on 2017-09-17
Well, I've tried messing with user settings to no avail.

```

sudo aplay /usr/share/sounds/alsa/Front_Center.wav
```

No sound if I log into a guest session, no sound even as root. But I can get sound if I log in as my husband. His user account in the only one that doesn't mute the sound automatically!

---

### Post by holiday2 on 2017-09-17
Just for whatever try 
# sudo groups <yourlogin>
# sudo groups <husbandslogin>

Just a wild bic-flick in a great dark, but there could be a permissions issue somewhere about groups. You should be in the same groups right?

---

### Post by Buntu Bunny on 2017-09-17
Hmm, well, that did nothing, but I did read on the [SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") page that it might be a configuration problem, but this

```
sudo addgroup <leigh> audio
```

returned

```
bash: leigh: No such file or directory
```

????

As far as groups, I simply added my husband through Settings > Users and groups. 

I've run across one more thing I can try, so we'll see!

---

### Post by holiday2 on 2017-09-17
addgroup adds a group to the system. That's my understanding anyway. 
When I want to add a user to a group, I go

# usermod -aG groupname username

so 

sudo usermod -aG audio leigh

Assuming that your husband is in the audio group and you are not. Is that the case?

It's a weird one for sure.

---

### Post by Buntu Bunny on 2017-09-18
> **holiday2 said:**
> addgroup adds a group to the system. That's my understanding anyway. 

Assuming that your husband is in the audio group and you are not. Is that the case?


Well, I *used* to be! So somehow the groups or permissions have changed, because sound passes the hardware and driver tests.

> It's a weird one for sure. 

Indeed.

---

### Post by holiday2 on 2017-09-18
And after you have rejoined the audio group using the usermod command, the next stop along this road is you must log out of your gui session and log back in. 
That may have changed but I don't know that it has.

---

### Post by Yellow Pasque on 2017-09-18
Neither user should be in the audio group: [http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/](http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/)

---

### Post by holiday2 on 2017-09-18
> **Temüjin said:**
> Neither user should be in the audio group: [http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/](http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/)


So... might it be helpful for BB to remove her husband from the audio group?

---

### Post by Buntu Bunny on 2017-09-18
I'm not sure how or why, but it's fixed. Of the various things I tried, none gave me immediate results, but this evening my sound is back.

Thank you holiday2 and Temüjin for taking the time to reply and add your thoughts.

I take that back (about what might have corrected the problem, not the thank-you). I read on the Ubuntu help audio troubleshooting page that sometimes ALSA doesn't wake up if the computer goes into hibernation mode. I changed that but didn't see an immediate result. It must have kicked in after reboot. Not positive this fixed it, but that's the last thing I did before the correction.

---

