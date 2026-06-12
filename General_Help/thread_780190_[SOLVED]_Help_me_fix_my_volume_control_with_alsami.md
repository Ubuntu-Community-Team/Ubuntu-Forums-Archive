---
title: "[SOLVED] Help me fix my volume control with alsamixer in Hardy Heron!"
date: 2008-05-03
forum: General Help
---

### Post by linuxvacuum on 2008-05-03
After a hard time upgrading from 7.10 to 8.04, I find that I cannot change my volume with alsamixer !
> alsamixer: function snd_mixer_load failed: No such file or directory
If I type > sudo /etc/init.d/alsa-utils restart then I get > * Shutting down ALSA...                                                                                                                                                                                     * warning: 'alsactl store' failed with error message 'alsactl: get_control:209: Cannot read control info '2,0,0,Master Playback Volume,0': No such file or directory'...                                   amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
                                                                                                                                                                                                     [fail]
 * Setting up ALSA...                                                                                                                                                                                        * warning: 'alsactl restore' failed with error message 'alsactl: set_control:98 * Shutting down ALSA...                                                                                                                                                                                      * warning: 'alsactl store' failed with error message 'alsactl: get_control:209: Cannot read control info '2,0,0,Master Playback Volume,0': No such file or directory'...                                   amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
                                                                                                                                                                                                     [fail]
 * Setting up ALSA...                                                                                                                                                                                        * warning: 'alsactl restore' failed with error message 'alsactl: set_control:981: warning: numid mismatch (17/19) for control #17
alsactl: set_control:983: warning: iface mismatch (2/2) for control #17
alsactl: set_control:985: warning: device mismatch (0/0) for control #17
alsactl: set_control:987: warning: subdevice mismatch (0/0) for control #17
alsactl: set_control:989: warning: name mismatch (PCM Playback Volume/PCM Playback Volume) for control #17
alsactl: set_control:991: warning: index mismatch (0/0) for control #17
alsactl: set_control:989: warning: name mismatch (Digital Capture Volume/Master Playback Switch) for control #18
alsactl: set_control:991: warning: index mismatch (0/0) for control #18
alsactl: set_control:993: failed to obtain info for control #18 (Operation not permitted)'...1: warning: numid mismatch (17/19) for control #17
alsactl: set_control:983: warning: iface mismatch (2/2) for control #17
alsactl: set_control:985: warning: device mismatch (0/0) for control #17
alsactl: set_control:987: warning: subdevice mismatch (0/0) for control #17
alsactl: set_control:989: warning: name mismatch (PCM Playback Volume/PCM Playback Volume) for control #17
alsactl: set_control:991: warning: index mismatch (0/0) for control #17
alsactl: set_control:989: warning: name mismatch (Digital Capture Volume/Master Playback Switch) for control #18
alsactl: set_control:991: warning: index mismatchamixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
amixer: Mixer hw:0 load error: No such file or directory
                                                                         [ OK ] (0/0) for control #18
alsactl: set_control:993: failed to obtain info for control #18 (Operation not permitted)'...

Is this related to the HAL failed to initialize error?
How can volume control be buggy in a brand new shiny release? This bug is unnaceptable...

---

### Post by linuxvacuum on 2008-05-05
Hello ?

---

### Post by linuxvacuum on 2008-05-07
:confused:

---

### Post by dondad on 2008-05-07
> **linuxvacuum said:**
> After a hard time upgrading from 7.10 to 8.04, I find that I cannot change my volume with alsamixer !

If I type  then I get 

Is this related to the HAL failed to initialize error?
How can volume control be buggy in a brand new shiny release? This bug is unnaceptable...

Hardy uses pulseaudio by default. If you want alsa mixer, you probably would have to install it.

---

### Post by Tom--d on 2008-05-07
Type in Terminal:

```
lspci
```

and post the outcome.

---

### Post by linuxvacuum on 2008-05-07
What is the pulseaudio equivalent of alsamixer? What is the command from the terminal?

> 04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

---

### Post by Butthead on 2008-05-07
> **linuxvacuum said:**
> Hello ?

Don't know if this will work, but type "alsamixer -c0" (without quote marks) in terminal. :confused:

---

### Post by linuxvacuum on 2008-05-07
I get> alsamixer: function snd_mixer_load failed: No such file or directory

---

### Post by orawax on 2008-05-08
> **linuxvacuum said:**
> After a hard time upgrading from 7.10 to 8.04, I find that I cannot change my volume with alsamixer !

I was struggling with the exact same issue. The answer lies not in fixing ALSA but in properly setting up PulseAudio, which is the standard sound server in Hardy.

I just followed these simple steps from [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
and then changed all devices to PulseAudio in System > Preferences > Sound.
Now there are other options for default mixer than just OSS, and everything seems to work perfectly.

So what you need to do is install some extra packages for PulseAudio: (I wonder why these aren't there by default...)
```
sudo aptitude install libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter
```

Generate asound.conf -file:
```
sudo gedit /etc/asound.conf
```

And paste in the following:
```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

```

Save the file, reboot and change the sound devices and mixer.

---

### Post by jocko on 2008-05-08
> **orawax said:**
> I was struggling with the exact same issue. The answer lies not in fixing ALSA but in properly setting up PulseAudio, which is the standard sound server in Hardy.

That's wrong. There's a [bug in hardy]("https://bugs.edge.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/192382") that they just don't seem to care about fixing. ALSA with the snd-intel-hda module (I don't know if it affects other modules as well) is not working properly, which leads to OSS becoming the only available sound system.
Pulseaudio is still just a sound server, which means it's dependent on ALSA or OSS for it's function.
By setting ALSA to OUTPUT to pulseaudio (as you do if you add those lines in /etc/asound.conf) you just accept that ALSA doesn't work and use OSS instead.
If you set it like that with working ALSA, you would create a loop where ALSA sends it's output to pulseaudio, which in turn would send it back to ALSA and so on...
I don't know what would happen, but I'm sure it would NOT produce any sound, and probably crash ALSA or pulseaudio.
[To fix alsa, look at this post]("http://ubuntuforums.org/showpost.php?p=4675505&postcount=8"). And why not add to the bug report to get the attention of whoever is supposed to fix it properly...

---

### Post by linuxvacuum on 2008-05-11
Thanks Jocko! You are a :KS

> sudo module-assistant auto-install alsa
sudo /sbin/alsa reload

PROBLEM SOLVED!

---

### Post by ChemistDB on 2008-10-18
Hi all, I ran the commands listed above and changed my sound preferences to ALSA, but still I have no sound.  I'm using an Emachines W3502 machine running hardy heron and here's the output from my  cat /proc/asound/cards 
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0x80200000 irq 18

Any help would be appreciated.

---

