---
title: "No sound Ubuntu 7.10"
date: 2008-02-26
forum: General Help
---

### Post by gsingh144 on 2008-02-26
Hi, 
 I have just installed Ubuntu on my laptop HP dv9640us, I am not able to get any sound on my laptop. Following is the aplay-l of certain commands:

$ aplay -l [I]
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/I]

I think this means that my sound card is being detected. I also cannot hear sound using a headphone or as root. This rules out some of the suggestions that i found on the net (turning of external amplifiers and chmod 666 /dev/dsp).  I also tried out alsamixer. The setting there looks fine to me. I have attached a screenshot of the alsamixer. 

Please let me know what other places should I look into. Any help would be greatly appreciated.

regards,
gaurav

---

### Post by carlos_listas on 2008-03-15
:confused:
Hi!
What ubuntu image did you use to install your notebook? I'm trying with the live cd amd64 but the note don't boot.

---

### Post by superprash2003 on 2008-03-16
hope this helps [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by Luinfana on 2008-03-21
I have the same machine, and had the exact same problem after installing 7.10 for the first time. A friend directed me to Method E on [this page]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller"), which seemed to solve my problems (all I did was add "options snd-hda-intel model=acer" to /etc/modprobe.d/alsa-base and restart). I then used alsamixer to manage my sound for a long while.

After a recent reinstall of several key packages (libc6, etc...it's a long story), my sound is now completely gone again, and most of my channels disappeared from alsamixer.

Alsamixer on my system now looks exactly like the screenshot you posted. When it worked before, it had ALOT more channels (Front, Headphone, CD, Mic, Line In, etc etc). Tried reinstalling alsamixer, alsa-base, etc. but that didn't help, either. And my added line is still in /etc/modprobe.d/alsa-base.

I'm really confused now. Help, someone?!

---

### Post by n7bek on 2008-03-22
Ok I suffered for along time with my laptop not being able to have sound or effects

i have intel HDA and sigmatel any way i think this solution will probably help every one cause now guess what i have sound & i swear its higher, better and even more clearer than xp or vista

I missed up alsa in upgreading it & recompiling so I suggest u reinstall gusty

then go to "System" menu and -> "Administration" -> "Software Sources"

then in there select the "Updates" you will have to select all the first 4 options

generally u will have only the first 2 selected

you have to select the options "Unsupported updates" & "Pre-released updates" and then close it restart & when prompted to update do the update restart & voalaaaaaa it works.

I have searched all over the net 4 a way to fix it yet this is the only one that worked 4 me 

Let me know if it works out 4 you
good luck

---

### Post by n7bek on 2008-03-22
ohh yeah & in 

then go to "System" menu and -> "Preferences" -> "Sound"

I set the first 3 choice boxes to "auto detect "
the 4th to ALSA
and the last one to intel HDA

:guitar: rock on Ubuntu

---

### Post by Luinfana on 2008-03-26
Just thought I'd comment on how I ended up solving my problems...

For reference, my machine is a HP Pavilion dv9640us (Realtec ALC268 card/HDA Intel).

I just upgraded to Hardy Beta. That upgrade completely disabled sound - gstreamer couldn't see my soundcard at all, and alsamixer showed only two nonfunctional channels - "Master" and "PCM."

The solution turned out to be very, very simple. My machine was booting the 2.6.24-12-386 kernel by default...apparently HDA Intel doesn't work at all in this kernel, or it has major problems (at any rate, it refused to work for me). All I needed to do was to boot 2.6.24-12-generic, and voilà, sound works - all channels assigned and working perfectly in alsamixer.

---

