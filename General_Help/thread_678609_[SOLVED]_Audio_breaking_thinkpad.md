---
title: "[SOLVED] Audio breaking thinkpad"
date: 2008-01-26
forum: General Help
---

### Post by aliencam on 2008-01-26
I've had a thinkpad x61 tablet with ubuntu 7.10 gutsy on it. audio has worked "out of the box" perfectly for me (including the vol up/down buttons) however, all of the sudden I don't get any audio and I get these errors: 


```
cameron@camubuntux61tab:~$ aplay
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
aplay: main:545: audio open error: Device or resource busy

cameron@camubuntux61tab:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

and the error i get in system>preferences>sound>test
Autodetect:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Internal data flow error.
```


AD198x Analog:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.
```


and so far, I have tried reinstalling alsa with: 

```
sudo apt-get install --reinstall alsa-base
```




the last time this happened all i did was replug the laptop into the dock that i have for it, and it started working again, but that doesn't work this time.  



the really strange part though: 

my girlfriend has the exact same laptop, except for a different wifi card. she runs windows vista, and I run OSX and Ubuntu.

I took her and my hard drives and swapped them. both worked in the other computer.

that means my Ubuntu distro is not messed up since sound worked perfectly in her laptop

and it also means there is no problem with my hardware since windows vista played sound out of my speakers without any config at all. (the startup sound)

when I switched the hard drives back, my ubuntu sound fails to work again.



the worst part about this is that i left my radio at home because internet radio was working fine for me, and I just switched to banshee for music management, and banshee cant copy my podcasts to my iPod...

---

### Post by aliencam on 2008-01-26
I just tried changing everything in gnome-sound-properties to ASLA, but that didn't work.  some people who have gotten this problem before said that it worked for them... 

it says the device is busy... is there a *lock file i can delete anywhere??? 

```
Device 'default:0' is busy]

```

is what comes out of the terminal output...

---

### Post by aliencam on 2008-01-27
I called Lenovo support and the first guy didn't know how to fix my problem, but he was the most knowledgeable person i've ever spoken to regarding tech support.  he knew just about as much about linux as I do, and actually just talked to me about which distro I was using and how I got things set up...   I then found the solution to my problem, and called back in order to tell  lenovo in case they ever get a similar call.  the person I talked to during my second call was equally knowledgeable and while he did not know the solution immediately, when I told him the solution he knew why that was.    

the thinkpad models with this sound card/modem congifuration  (x60 and x61 and x61 tablets and some others)   require that the modem be enabled in BIOS for sound to work.  otherwise the intel drivers in linux right now cannot access it.  this is because they share a bus.  

so just enable the modem in BIOS and it should help.

---

