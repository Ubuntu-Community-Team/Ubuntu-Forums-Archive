---
title: "PulseAudio related issues"
date: 2008-06-15
forum: General Help
---

### Post by das letzte einhorn on 2008-06-15
Prior to this I had sound working in Ubuntu, but not with Timidity or Wine. Therefore I followed the instructions in this HOWTO: [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup) , in order to get sound with the two latter applications. However, after rebooting, I had the wonderful surprise of not having any sound at all anymore. When I load the PulseAudio device chooser, I get the connection refused message, which apparently the reason for it is that PulseAudio is not running.

Ironically however, I cannot load the deamon, as you can see here:

xavier@Xavier:~$ pulseaudio -D
E: main.c: daemon startup failed.

I tried reinstalling the package, and it does not work either. Is there a potential solution for this?

Thanks!

EDIT: Finally, it seems that there is sound in PlayonLinux and MIDI, but not Ubuntu. What a mess.. Haha. I guess the question now is : is there a way to make all of them work together?

---

### Post by iaculallad on 2008-06-15
Had you tried reading this [page]("http://ubuntuforums.org/showthread.php?p=4451132") already?

---

### Post by das letzte einhorn on 2008-06-15
I just did. Here is what I get for the final steps

xavier@Xavier:~$ pulseaudio -k
xavier@Xavier:~$ pulseaudio -C
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL surround51:0
ALSA lib setup.c:96:(snd_sctl_install) Cannot lock ctl elem
W: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
W: alsa-util.c: Device hw:2 doesn't support 6 channels, changed to 1.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL surround51:1
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:1
Welcome to PulseAudio! Use "help" for usage information.

I rebooted afterwards, I get the same thing. I do not get however the connection refused message, therefore it seems that PulseAudio is loading. The sound is not muted however, hence I do not know why nothing comes out.

Edit: I have added two screenshots from the PulseAudio device chooser. For some odd reason, output devices are recognized, playbacks are recognized, both of them are not muted, but still, no sound comes out...

---

### Post by iaculallad on 2008-06-15
Backup your /etc/pulse/default.pa file:

```
sudo cp /etc/pulse/default.pa /etc/pulse/default.pa.original
```

Try to open /etc/pulse/default.pa file for editing:

```
gksudo gedit /etc/pulse/default.pa
```

and change:

> load-module module-esound-protocol-unix

to:

> load-module module-esound-protocol-unix socket=/tmp/.esd/socket

---

### Post by das letzte einhorn on 2008-06-15
Just did, unfortunately it hasn't solved the problem. In fact now there is no sound at all produced from anything, else than from GTick metronome! Interesting mess so far :P

---

### Post by iaculallad on 2008-06-16
Try to open your mpd.conf file.

```
gksudo gedit /etc/mpd.conf
```

and try adding the lines of text below:

> audio_output {
type “pulse”
name “My MPD PulseAudio Output”
}

Save changes and close gedit. Restart mpd

```
sudo /etc/init.d/mpd restart
```

---

### Post by das letzte einhorn on 2008-06-16
The file did not exist at first. Afterwards..

xavier@Xavier:~$ sudo /etc/init.d/mpd restart
sudo: /etc/init.d/mpd: command not found

I made some further testing, all the components (Ubuntu sound, timidity and wine) go now through pulse audio, and when I run them the volume meter detects sound flow. However there is no sound coming out of my speakers. Therefore we are on the good path. Nothing is set to mute.

---

### Post by das letzte einhorn on 2008-06-16
Bump. Is there anybody else with such an issue?

---

### Post by das letzte einhorn on 2008-06-16
New update

I have tried to kill Pulseaudio for the session, it failed to do so, but for some odd reason sound in Wine has been restored. It's at least that, but it would be good to have some extra indications on how to restore sound in the rest of the system, without hopefully to have to kill the process in order for Wine and Timidity to work as well.

---

