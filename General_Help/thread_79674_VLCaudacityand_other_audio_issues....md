---
title: "VLC/audacity/and other audio issues..."
date: 2005-10-20
forum: General Help
---

### Post by ymmotrojam on 2005-10-20
I have been noticing that when I am playing music in VLC, at first nothing comes out of the speakers at all. I have to stop the music and hit play to get it going. If that doesn't work, I have to disable the audio in VLC through the Audio menu, and re-enable it, and that usually fixes it. On top of that, when I try to run a visualization, vlc freezes up, and then I have to kill vlc and reboot because vlc brought down all audio in ubuntu (there's probably an easier way than rebooting to get it back, but I'm a newbie :)).

In audacity, it says something to the effect that I haven't selected a device for capturing and a device for output... When I go into the audacity preferences, and into the part to select those devices, it doesn't even allow me to choose anything (there's literally nothing to choose).

I have also had problems in other applications as well such as "Sound Recorder"... Sound Recorder doesn't appear to be getting any input from my microphone. I have checked and re-checked my audio configuration, and I'm pretty sure that all the settings that I can see are appropriate for what I want, and that this is just a hardware compatibility issue.

any help would be appreciated!:)

EDIT: more info on my current settings are here...
[http://www.ubuntuforums.org/showthread.php?t=79674&page=2#top]("http://www.ubuntuforums.org/showthread.php?t=79674&page=2#top")

---

### Post by Kyral on 2005-10-20
For VLC have you tried installing the vlc-plugin-alsa and vlc-plugin-esd packages?

---

### Post by ymmotrojam on 2005-10-20
[QUOTE=Kyral]For VLC have you tried installing the vlc-plugin-alsa and vlc-plugin-esd packages?[/QUOTE]
I haven't, but will tonight when I return home from school. The only thing is that the sound is messing up in multiple applications, so I don't think it's just vlc...

---

### Post by arunsub on 2005-10-20
Did you try this?
[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)

---

### Post by ymmotrojam on 2005-10-20
[QUOTE=arunsub]Did you try this?
[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)[/QUOTE]
thanks for the link. won't be able to try it until later tonight, but it definitely explains why a lot of the sound issues may be occurring...

---

### Post by arunsub on 2005-10-20
After following those steps, go to sound & video - volume control and make sure you select the right device from the menu and after selecting the right device, make sure the microphone and speakers are not muted.

---

### Post by ymmotrojam on 2005-10-21
hurray... got it working. thanks for the help guys!

PS: if anyone gets it working and notices it's really quiet, enable Mic Boost +20db in the preferences of the Volume Control:)

**Nevermind. I logged out and back in and it went back to the way it was... How do I get it to stick?**

---

### Post by arunsub on 2005-10-21
[QUOTE=ymmotrojam]hurray... got it working. thanks for the help guys!

PS: if anyone gets it working and notices it's really quiet, enable Mic Boost +20db in the preferences of the Volume Control:)

**Nevermind. I logged out and back in and it went back to the way it was... How do I get it to stick?**[/QUOTE]
Did you mean the entire stuff or just the mic boost part?

---

### Post by ymmotrojam on 2005-10-21
[quote=arunsub]Did you mean the entire stuff or just the mic boost part?[/quote] The entire thing... The only thing I changed was the /etc/esound/esd.conf...

I checked that file, and it has the changes I made, but I'm still having the same roblems. But it did do something temporarily because I was able to record...:???:

---

### Post by arunsub on 2005-10-21
[QUOTE=ymmotrojam]The entire thing... The only thing I changed was the /etc/esound/esd.conf...

I checked that file, and it has the changes I made, but I'm still having the same roblems. But it did do something temporarily because I was able to record...:???:[/QUOTE]

Can you check in the volume manager and make sure you have the right device selected (i forgot the menu option since i'm not in front of Ubuntu).  Also try the following part from that link.
Howto go further: listening many sounds at the same time, without ESD !

---

### Post by ymmotrojam on 2005-10-21
**Volume Control** is set to:
[COLOR=DarkGreen]0: Intel ICH5 (Alsa Mixer)
[COLOR=Black]there is also...
1: Analog Devices AD1888 (OSS Mixer)

The Mic is not muted, and is turned all the way up. I also have enabled the Mic Boost +20db.

**Multimedia Systems Selector** is set to:
...within the audio tab
Default Sink:
[COLOR=DarkGreen]ALSA
[COLOR=Black]Default Source:
[COLOR=DarkGreen]ALSA

**[COLOR=Black]This is what my /etc/esound/esd.conf file looks like...[/COLOR]**[COLOR=Black]
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by arunsub on 2005-10-21
I'm out of ideas now. Also, I'm not in front of Ubuntu. I'll go home, check and see if mine is anything different from yours.

---

### Post by ymmotrojam on 2005-10-21
I somehow got it to work, but only half-way... I typed "alsamixer" into the terminal and turned everything up, then made sure the mic was selected for recording. I can hear my voice out of the speakers, but still applications like audacity and Sound Recorder are not getting anything and do not recognize my sound card.

---

