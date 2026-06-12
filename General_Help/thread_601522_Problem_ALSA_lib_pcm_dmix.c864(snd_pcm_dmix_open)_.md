---
title: "Problem: ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave"
date: 2007-11-03
forum: General Help
---

### Post by BlackSergie on 2007-11-03
No sound in all programms with support SDL.
Terminal error:  ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
OS: Ubuntu 7.10 & ALSA  v1.0.15

Why?

---

### Post by hikaricore on 2007-11-08
I believe this is a conflict with ALSA and PulseAudio.

I've been looking into this issue personally for awhile now, it was not present in Feisty but is in Gutsy.
Hopefully a fix will come to light sooner or later.  :/

---

### Post by scarolan on 2007-11-09
Same problem here.  I also am hoping for a fix.

---

### Post by TaTaE on 2007-11-10
You could install this package: 
```
libsdl1.2debian-all
```
and REMOVE any line containing SDL_AUDIODRIVER from your .bashrc with:
```
gedit $HOME/.bashrc
```



[[IMG]http://brainstorm.ubuntu.com/idea/129/image/2/[/IMG]](http://brainstorm.ubuntu.com/idea/129/)

---

### Post by mrashley on 2007-11-12
I've just done this. What is the effect this will have on the rest of my applications?

Anyone? ;)

---

### Post by Sophont on 2007-11-20
I have the same error message.

Sound works when playing music with Rhythmbox or sytem sound effectds.

But no sound anymore through wine.

It's working partly when playing DVDs - i.e. I get sound on menu and musical soundtrack and part of the voices during movie - but most of the voices are gone.

libsdl1.2debian-all is installed. No SDL_AUDIODRIVER wasn't there to begin with).

All sound (DVD, system, wine, etc....) worked fine before I upgraded to Gutsy.

My Machine:
Dell Inspiron 9400 Laptop, 2 GHz Duo Core 2, 2 GB RAM
NVidia Geforce Go 7900 GS (compiz enabled)
HDA Intel

dmesg | grep -i error
[   16.564032] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    4.304000] usb 1-1: device not accepting address 2, error -71

dmesg | grep -i fail
[    0.508000] Marking TSC unstable due to: check_tsc_sync_source failed.
[    2.992000] Failure registering capabilities with primary security module.
[  158.108000] Failure registering capabilities with primary security module.

None of the error/fail messages seem to be related to my audio problems. The "usb 1-1" has always been there - even when sound used to worked everywhere (pre Gutsy/Pulseaudio?).

---

### Post by Holmen on 2007-12-10
Installed libsdl1.2debian-all package worked for me.

---

### Post by TaTaE on 2007-12-13
Maybe those who get this error mesage have pulseaudio installed. Pulseaudio is really great , BUT is not implemented on some games and other programs. So, if you are in games, you better get rid of pulseaudio, by searching "pulse" in synpatic and purging it all. Than, you will have ALSA audio left, which is default in Gutsy. For complete uninstalling , you must do "sudo aptitude purge libpulse" and install libesd-alsa.
     Some report that "asoundconf reset-default-card" did the trick for them.
:guitar:


Or you could switch to Hardy Heron.

---

### Post by JunCTionS on 2008-03-16
neither solutions worked for my girlfriend's Toshiba A105-S4344 with Kubuntu Gutsy.
and as you may have seen on other posts of mine,  my Toshiba A105-S4677 didn't have any sound at all with Gutsy so I had to switch from ALSA to OSS which mostly worked (except for some KDE apps like Kopete and the system sounds).

---

### Post by Sophont on 2008-03-18
All my sound problems went away with a fresh install to Hardy alpha.

Wait for final release (next month) though - there's been quite a bit of breakage during the alpha (that's what alphas are for :-) ).

YMMV

---

### Post by meisterelrond on 2008-07-04
Hi there!
Though I use Hardy (8.04) I get the same error message for my alsa audio-player. So no real fix I fear ...
Greetings,
meisterelrond

---

