---
title: "A sound oddity"
date: 2020-02-03
forum: General Help
---

### Post by WB0HYQ on 2020-02-03
For some reason, my sound notification icon keeps flashing on every so often. No sound comes from the speakers yet the icon keeps appearing at random intervals. Running Ubuntu 18.04LTS with XFCE desktop. I'm not sure what brand of sound chips are being used, but they're on the MOBO.

These "ghost" sounds will appear when I'm off doing something entirely different than requiring sound. It happens in the middle of an email composition (Thunderbird), while writing/editing my novels, or even when I'm on another desktop and using Remmina remote desktop. The remote computer is a Windows Server and has no sound card at all.

Any ideas?

Bill

---

### Post by CelticWarrior on 2020-02-03
Could be a symptom of some hardware problem.
Does it do the same in a live session?

---

### Post by WB0HYQ on 2020-02-04
Sorry. Failed to get a notification of your post in this thread. I get a lot of that for some reason. Absolutely NO notification emails for any of my posts/threads no matter how I have it set in Preferences.

Booted to a DVD and let the system sit for a while with no screensaver. The sound icon did the same thing--popped on for a brief moment (1 sec approximately) and back off. I've set it to Mute, yet it still does this. Only when I turn the sound to Off does it stop. Very strange.

Bill

---

### Post by CelticWarrior on 2020-02-04
So, if this is a new problem, i.e., if the system was working before without this nuisance, and now does that regardless of the OS, it points to a hardware problem.

---

### Post by WB0HYQ on 2020-02-04
Could be hardware, but I'm not sure of that. Also not sure when it actually started either. The pop-up only lasts for two seconds at the most, and there is nothing at all from the speakers or bass boombox, not even a pop. I'm wondering now if it might be coming from either Thunderbird or Chrome which I have running all the time in separate desktops. But the Thunderbird "you have mail" tones sounds just fine and so does Chrome when I'm on a noisy site like YouTube. Too many variables to try narrowing it down other than to simply shut down notifications from everything and turn them back on one-by-one. A tedious job to say the least. Plus, that would shut off visual notifications as well (I think).

I'll keep whacking away at it.

Bill

---

### Post by NM5TF on 2020-02-04
@WB0HYQ...can you post the output of

```
inxi -A
```

it will tell us what audio system & driver you are using...

it will look something like mine...

```
[tommy@tommy ~]$ inxi -A
Audio:
  Device-1: NVIDIA MCP61 High Definition Audio driver: snd_hda_intel 
  Sound Server: ALSA v: k5.5.1-arch1-1 
```

tommy

---

### Post by WB0HYQ on 2020-02-05
Sure. Here it is:

```

Audio:     Card-1 NVIDIA GK208 HDMI/DP Audio Controller driver: snd_hda_intel
              Card-2 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
              driver: snd_hda_intel
              Sound: Advanced Linux Sound Architecture v: k4.15.0-76-generic



```

Bill

---

### Post by CatKiller on 2020-02-05
I suspect cabling; a temporary blip in the connection that leads your computer to say, "good news! I've detected a **brand new** audio device! It's exactly the same as the old audio device! How exciting!"

---

### Post by NM5TF on 2020-02-05
if it is a cable problem, wiggling the cable should prove/disprove that easily enough.....

in all my searching I only found reference to 1 similar thing & a bug report filed, but
that was in 16.04 and supposedly fixed in 18.04.....

have you checked the logs for any error messages ???

/var/log/syslog
/var/log/debug

tommy

---

### Post by WB0HYQ on 2020-02-08
Sorry. Once again I wasn't notified of any posts in my thread. 

Since 1600 today, the sound icon has been flashing like a demented neon light. It will even change volume levels on its own.

From var/log:

```

Feb  8 16:05:13 bill-UBU systemd[1]: Started Run anacron jobs.Feb  8 16:05:13 bill-UBU anacron[32449]: Anacron 2.3 started on 2020-02-08
Feb  8 16:05:13 bill-UBU anacron[32449]: Normal exit (0 jobs run)
Feb  8 16:15:10 bill-UBU systemd-resolved[16176]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Feb  8 16:15:10 bill-UBU systemd-resolved[16176]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Feb  8 16:17:01 bill-UBU CRON[32610]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb  8 16:41:32 bill-UBU xfce4-notifyd[1703]: xfce_notify_window_expire_timeout: assertion 'XFCE_IS_NOTIFY_WINDOW(data)' failed
Feb  8 16:55:25 bill-UBU Thunar[2391]: gdk_window_set_icon_list: icons too large
Feb  8 16:55:25 bill-UBU gvfsd-metadata[3366]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
Feb  8 16:55:25 bill-UBU gvfsd-metadata[3366]: message repeated 7 times: [ g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed]
Feb  8 16:55:32 bill-UBU Thunar[2391]: gdk_window_set_icon_list: icons too large
Feb  8 16:55:35 bill-UBU gvfsd-metadata[3366]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
Feb  8 16:55:37 bill-UBU gvfsd-metadata[3366]: message repeated 33 times: [ g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed]
Feb  8 16:55:45 bill-UBU gedit[1952]: Theme parsing error: gtk.css:27:35: Junk at end of value for background-color
Feb  8 16:55:45 bill-UBU gedit[1952]: Theme parsing error: gtk.css:40:48: Junk at end of value for background-color
Feb  8 16:55:45 bill-UBU gedit[1952]: Theme parsing error: gtk.css:48:46: Junk at end of value for background-color
Feb  8 16:55:45 bill-UBU gedit[1952]: Theme parsing error: gtk.css:59:58: Junk at end of value for background-color
Feb  8 16:55:45 bill-UBU gedit[1952]: Theme parsing error: gtk.css:66:28: The :prelight pseudo-class is deprecated. Use :hover instead.
Feb  8 16:55:45 bill-UBU gedit[1952]: Theme parsing error: gtk.css:70:46: Junk at end of value for background-color
Feb  8 16:55:45 bill-UBU gedit[1952]: Theme parsing error: gtk.css:77:35: The :prelight pseudo-class is deprecated. Use :hover instead.
Feb  8 16:55:45 bill-UBU gedit[1952]: Theme parsing error: gtk.css:81:58: Junk at end of value for background-color
Feb  8 16:55:45 bill-UBU gedit[1952]: Theme parsing error: gtk.css:123:31: The :insensitive pseudo-class is deprecated. Use :disabled instead.
Feb  8 16:55:45 bill-UBU gedit[1952]: Theme parsing error: gtk.css:124:24: The :insensitive pseudo-class is deprecated. Use :disabled instead.
Feb  8 16:55:45 bill-UBU gedit[1952]: Theme parsing error: gtk.css:156:27: The :insensitive pseudo-class is deprecated. Use :disabled instead.
Feb  8 16:55:45 bill-UBU gedit[1952]: Theme parsing error: gtk.css:157:29: The :insensitive pseudo-class is deprecated. Use :disabled instead.
Feb  8 16:55:45 bill-UBU gedit[1952]: Theme parsing error: gtk.css:177:34: The :insensitive pseudo-class is deprecated. Use :disabled instead.
Feb  8 16:55:45 bill-UBU gedit[1952]: Theme parsing error: gtk.css:199:34: The :inconsistent pseudo-class is deprecated. Use :indeterminate instead.

```

While this is happening I am doing nothing at all except staring at the screen. There is no "debug" log.

Bill

---

### Post by WB0HYQ on 2020-02-08
The strange thing is my videos and MP3s play just fine. If I temporarily mute them, they stop, unmute and they take off again. This random notification thing is really distracting while I'm trying to write/edit my novel. Is there a way to simply cut off ALL notifications (or at least system sounds)? If so, I haven't fount it yet.

BTW, I get the "growling buzz" when I try to backspace past the beginning of an edit panel on any Chrome page OR in Open Office, so it doesn't appear to be a "normal" system sound. Even if I could make it give me some sound instead of nothing I might be able to identify where its coming from and what triggers it.

Bill

---

### Post by WB0HYQ on 2020-02-13
I can 't be certain, but I think this might be tied into my remote connection to my downstairs server. I seem to get a lot less soundless audio pop-ups when I'm not logged in. The server does not have a sound card, but there might still be some reason for it to try and get my attention. Why these seem to change the volume level is really mystifying.

Bill

---

### Post by WB0HYQ on 2020-02-20
Still at a loss as to why this is happening. Have now re-installed everything from the OS on up and still this is happening. Whatever it is has the capability of increasing or reducing the volume level to the extent of making it go to max or min without my noticing. Quite surprising to to go a Youtube video and be blasted out of my chair by the volume which has been set to max. Or, wondering why I can't hear anything in Facebook because the volume has gone to minimum. It doesn't seem to be hardware oriented as I've taken the audio card out of the system and put it back after the popups continued during that period the card was out.

I feel it is something in the OS that is producing a notification that is producing a short audio beep as a method of getting my attention. I've used a couple of methods to turn off every system noise I can find, yet these dang pop-ups still appear.

Bill

---

### Post by WB0HYQ on 2020-02-22
This has GOT to stop! Today, despite being explicitly turned ON, every ten minutes or so, it goes to MUTE or changes volume down to near-zero. It is now doing this in the middle of Youtube videos, playing MP3 music, and other listening sources such as Facebook.

I pulled the panels off the computer and dusted (something I usually do every 6 months), making sure the audio components were clean. Nothing untoward was found.

Is there a command I can give which will show me everything hardware-oriented toward sound? I think the sound chipset is NVIDIA but I'm not sure as it is based on the MOBO.

Bill

---

### Post by WB0HYQ on 2020-03-19
Still doing it, although not as much as before since the last Ubuntu Core update yesterday. I still think there is some event happening that tries to notify me, but gets killed before it can do so.

Bill

---

