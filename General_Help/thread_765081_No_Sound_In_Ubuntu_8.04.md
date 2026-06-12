---
title: "No Sound In Ubuntu 8.04"
date: 2008-04-24
forum: General Help
---

### Post by CheeseQueen452 on 2008-04-24
I just upgraded to Ubuntu 8.04, & I don't have any sound. What do I do? HELP!!!

---

### Post by tony2tone on 2008-04-24
what sound card do you have? did ur souncard worked with gutsy?

---

### Post by CheeseQueen452 on 2008-04-24
It's a SoundBlaster. Yes, it worked with Gutsy.

> **tony2tone said:**
> what sound card do you have? did ur souncard worked with gutsy?

---

### Post by CheeseQueen452 on 2008-04-24
Ok, it appears that ONLY my email notification, startup & shutdown sounds are not working. When I try to play an mp3 in movie player, I don't hear anything. Am I missing a plugin?

---

### Post by jocko on 2008-04-24
> **CheeseQueen452 said:**
> Ok, it appears that ONLY my email notification, startup & shutdown sounds [COLOR=Red]are not working[/COLOR]. When I try to play an mp3 in movie player, [COLOR=Red]I don't hear anything[/COLOR]. Am I missing a plugin?
Could you clearify what you mean? You first say that it's ONLY your system sounds that doesn't work, and then you say movie player (you mean totem?) also doesn't work.
Did you mean your system sounds work, but totem doesn't? The other way around? Or did you mean exactly what you wrote?

Either way:
First check that none of the sound channels on your sound cards are muted. Type "alsamixer" in a terminal and try changing volumes (Up/down arrows) and toggle between mute and unmute by pressing "m".

Then check which sound driver your system uses:
Type "gstreamer-properties" and "gnome-sound-properties" in a terminal (or find them in the menus). See what happens if you switch from alsa to pulseaudio or the other way around.

---

### Post by chrisccoulson on 2008-04-24
Note that the sound playback devices in gnome-sound-properties are set to 'Autodetect' on a default install, and sound should work properly with these settings. Some upgrades are breaking I think because people have changed these settings from 'Autodetect' to 'ESD' or 'ALSA' or whatever on Gutsy, combined with the fact that Hardy has migrated to Pulseaudio.

---

### Post by jocko on 2008-04-24
Sorry. double post. my firefox got stuck...

---

### Post by CheeseQueen452 on 2008-04-24
Sorry for the confusion.... I installed some Gstreamer plugins, & Totem now plays my music. But my email notification & startup/shutdown sounds still don't work. The sound channels are not muted. Pulseaudio doesn't work. Any other ideas?

> **jocko said:**
> Could you clearify what you mean? You first say that it's ONLY your system sounds that doesn't work, and then you say movie player (you mean totem?) also doesn't work.
Did you mean your system sounds work, but totem doesn't? The other way around? Or did you mean exactly what you wrote?

Either way:
First check that none of the sound channels on your sound cards are muted. Type "alsamixer" in a terminal and try changing volumes (Up/down arrows) and toggle between mute and unmute by pressing "m".

Then check which sound driver your system uses:
Type "gstreamer-properties" and "gnome-sound-properties" in a terminal (or find them in the menus). See what happens if you switch from alsa to pulseaudio or the other way around.

---

### Post by jocko on 2008-04-24
> **CheeseQueen452 said:**
> Sorry for the confusion.... I installed some Gstreamer plugins, & Totem now plays my music. But my email notification & startup/shutdown sounds still don't work. The sound channels are not muted. Pulseaudio doesn't work. Any other ideas?

System sounds (email notifications, startup/shutdown sounds and such) can only be played through pulseaudio. In the second tab of gnome-sound-properties, make sure both tick boxes are ticked.
When you say pulseaudio doesn't work, how do you mean? Is it running but not producing sounds? Or do you get any error message when you try to use it?
Do you see any error messages if you run:
```
pulseaudio -k
pulseaudio -C
```
in a terminal?
To change anything in pulseaudio you need the package padevchooser installed. You'll find it in synaptic.

---

### Post by CheeseQueen452 on 2008-04-24
I just don't hear anything. When I entered pulseaudio -C in the terminal, it said:
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib setup.c:96:(snd_sctl_install) Cannot lock ctl elem
ALSA lib conf.c:3952:(snd_config_expand) Unknown parameters 0
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM surround71:0

I'm attempting to install padevchooser right now, so we'll see what happens....

> **jocko said:**
> When you say pulseaudio doesn't work, how do you mean? Is it running but not producing sounds? Or do you get any error message when you try to use it?
Do you see any error messages if you run:
```
pulseaudio -k
pulseaudio -C
```
in a terminal?
To change anything in pulseaudio you need the package padevchooser installed. You'll find it in synaptic.

---

### Post by CheeseQueen452 on 2008-04-24
Still nothing....

---

### Post by jocko on 2008-04-24
> **CheeseQueen452 said:**
> I just don't hear anything. When I entered pulseaudio -C in the terminal, it said:
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib setup.c:96:(snd_sctl_install) Cannot lock ctl elem
ALSA lib conf.c:3952:(snd_config_expand) Unknown parameters 0
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM surround71:0

I'm attempting to install padevchooser right now, so we'll see what happens....

I don't think padevchooser will help with that problem.
I'm not sure if [this bug]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/189060") is what you experience, but if it is, this command would help: 
```
rm -rf ~/.pulse ~/.pulse-cookie
``` If it gives you a permission problem, put "sudo" in front of the command and try again.

---

### Post by jocko on 2008-04-24
Hmmm... I just realized I had exactly the same error messages when I tried to start pulseaudio on my laptop. In my case the problem was in alsa.
The reason I didn't think you had the same problem is because you said your sound channels were not muted, meaning you could actually start alsamixer?
I could not even start alsamixer, but that could be different for different drivers.

In any way, my problem was fixed with two simple commands:
```
sudo apt-get install module-assistant
sudo module-assistant auto-install alsa
```

The second command will compile and install the alsa drivers, which will take some time. When it's done, a reboot should bring everything to life.

---

### Post by CheeseQueen452 on 2008-04-25
Thanx, I'm trying it now....

> **jocko said:**
> In any way, my problem was fixed with two simple commands:
```
sudo apt-get install module-assistant
sudo module-assistant auto-install alsa
```

The second command will compile and install the alsa drivers, which will take some time. When it's done, a reboot should bring everything to life.

---

### Post by CheeseQueen452 on 2008-04-25
Still nothing.... What now?

---

### Post by CheeseQueen452 on 2008-04-25
Can anyone help?

---

### Post by CheeseQueen452 on 2008-04-28
Anyone?

---

### Post by cszikszoy on 2008-05-01
I'm having the same problem.  Well, I was anyways.  I could hear the system sounds (startup, login) just fine, and music was working perfectly in firefox (youtube, pandora).  I was even able to get music files to play ONCE (or maybe twice) with totem (and ONCE with rythmbox, too).  However, 95% of the time nothing would happen.  After checking the syslog, I found this:

```
May  1 17:28:43 chris-laptop pulseaudio[6056]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
May  1 17:43:05 chris-laptop pulseaudio[6056]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
May  1 17:44:12 chris-laptop last message repeated 2 times
May  1 17:44:38 chris-laptop last message repeated 2 times
```

Which lead me to believe it's a problem with pulseaudio.  I went to system > pref > sound and changed everything from 'autodetect' to ALSA (also worked perfectly [almost] for me in gutsy), and now everything works fine again.  I haven't tested yet, but I've also heard pulseaudio only causes problems for skype too.

What I'm wondering: why the switch to pulseaudio?  I didn't really have any problems with ALSA in gutsy, aside from my headphone jack on the front of my laptop not working, but I figured that was a problem with something else anyways, not really ALSA.

Try switching everything to ALSA on the sound dialog and see if that fixes it.

What I'd like is a more permanent solution though.  If hardy really has "switched" to pulseaudio, can we make this work for EVERYTHING, not just the system sounds??

---

### Post by CheeseQueen452 on 2008-05-02
My problem is the system sounds DON'T work.... at all.... I've been using ALSA all along, & after upgrading to Hardy, the sounds stopped working.

> **cszikszoy said:**
> I'm having the same problem.  Well, I was anyways.  I could hear the system sounds (startup, login) just fine, and music was working perfectly in firefox (youtube, pandora).  I was even able to get music files to play ONCE (or maybe twice) with totem (and ONCE with rythmbox, too).  However, 95% of the time nothing would happen.  After checking the syslog, I found this:

```
May  1 17:28:43 chris-laptop pulseaudio[6056]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
May  1 17:43:05 chris-laptop pulseaudio[6056]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
May  1 17:44:12 chris-laptop last message repeated 2 times
May  1 17:44:38 chris-laptop last message repeated 2 times
```

Which lead me to believe it's a problem with pulseaudio.  I went to system > pref > sound and changed everything from 'autodetect' to ALSA (also worked perfectly [almost] for me in gutsy), and now everything works fine again.  I haven't tested yet, but I've also heard pulseaudio only causes problems for skype too.

What I'm wondering: why the switch to pulseaudio?  I didn't really have any problems with ALSA in gutsy, aside from my headphone jack on the front of my laptop not working, but I figured that was a problem with something else anyways, not really ALSA.

Try switching everything to ALSA on the sound dialog and see if that fixes it.

What I'd like is a more permanent solution though.  If hardy really has "switched" to pulseaudio, can we make this work for EVERYTHING, not just the system sounds??

---

