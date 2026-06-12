---
title: "Picture/Sound synchronization problem"
date: 2005-07-07
forum: General Help
---

### Post by Athropos on 2005-07-07
Hi,

I'm pretty new to Ubuntu, I'm trying to switch from Windows since a week. Until now I had no problem, but I'm now facing a problem with videos: the sound is not kept synchronized with the picture. It's OK at the begining, but it's getting worst and worst after a few minutes. I tried with totem-xine and vlc (with ESD plugin, for gnome), but got the same problem with both. I have no problem playing videos with Windows on the same computer, picture and sound are OK. With Ubuntu, this happens with any video I'm trying to play (mpg, avi...). If someone has a solution to this problem, I would be grateful to hear it...

---

### Post by remin8 on 2005-07-07
I have had similar problems involving slower machines. I think if you upgrade your kernel and get the correct version of mplayer it will help. I know totem is not the smoothest or fastest video player out there. Only problem with this is you will have to play local files. Mplayer doesn't support gnome's virtual file system... that means no playing over a windows share. :( Check out the site  [http://ubuntuguide.org/](http://ubuntuguide.org/) for help.

---

### Post by Athropos on 2005-07-07
What I don't understand, is that I'm using also VLC to read videos (the same ones) with Windows, so I expected it to perform the same with Linux...
My computer is an Athlon 2600+, so I don't think it is too slow (considering I don't see this problem with Windows). I don't really know the Linux world, so I'm unable to determine what could causes this...

---

### Post by polo_step on 2005-07-07
[QUOTE=Athropos] With Ubuntu, this happens with any video I'm trying to play (mpg, avi...). If someone has a solution to this problem, I would be grateful to hear it...[/QUOTE]
Click "Pause" on and off every five or ten minutes.

Not the solution I'm looking for, but it's a stopgap measure that works.

---

### Post by Athropos on 2005-07-08
[QUOTE=polo_step]Click "Pause" on and off every five or ten minutes.

Not the solution I'm looking for, but it's a stopgap measure that works.[/QUOTE]

Moving the slider to a new position works, the synchronization is good again, but that's not an interesting solution :)

---

### Post by cobelloy on 2005-07-08
I also have sound out of sync, with any player and I tried the starter guide, tried setting the sound driver and turning off esd, but still no luck, and for me it doesn't sync up after pausing, it just stays out of sync.

---

### Post by dancnpete on 2005-07-08
arg I was hoping to find an answer here but at least I have found I am not alone here

---

### Post by Athropos on 2005-07-08
I found a (hardware) solution: I changed my soundcard.

I tried with mplayer, but had the same problem. However, I found this in its documentation:

> 
Linux sound card drivers have compatibility problems. This is because MPlayer relies on an in-built feature of properly coded sound drivers that enable them to maintain correct audio/video sync. Regrettably, some driver authors don't take the care to code this feature since it is not needed for playing MP3s or sound effects.


As I was unable to get A/V sync with mplayer even with -autosync whatever, I tried to use a sound blaster left in my old PC and now it works like a charm. It seems like the Linux nforce2 driver (I was using the on-board chipset) is not perfect. I didn't try to compile and install the driver on nvidia website, for now I keep using the sb driver...

---

### Post by polo_step on 2005-07-09
[QUOTE=Athropos]I found a (hardware) solution: I changed my soundcard..[/QUOTE]
Anyone know what soundcards/drivers will work properly with Linux in synched MultiMedia?

---

### Post by dancnpete on 2005-07-09
I may have found a solution I'm not exactly sure which one of these did the trick but I followed the directions in this forum:
[http://www.ubuntuforums.org/showthread.php?t=27186](http://www.ubuntuforums.org/showthread.php?t=27186)
and then poking around in xine I changed the method to audio to video control under the settings for audio and changed it from metronome to resample and enabled resampling

now I don't seem to have any more sync problems \\:D/

---

### Post by polo_step on 2005-07-09
[QUOTE=dancnpete]I may have found a solution I'm not exactly sure which one of these did the trick but I followed the directions in this forum:
[http://www.ubuntuforums.org/showthread.php?t=27186](http://www.ubuntuforums.org/showthread.php?t=27186)[/quote]
This seems to be about dual soundcards.
> poking around in xine I changed the method to audio to video control under the settings for audio and changed it from metronome to resample and enabled resampling
I don't see this in gXine audio menu anywhere for some reason. Odd. I'll doink around with resample and see what happens.

If I do get synch squared away, then I have to find a way to keep gXine from crashing my system when I go to fullscreen mode.  I wonder what *that's* about!

---

### Post by dancnpete on 2005-07-09
[QUOTE=polo_step]This seems to be about dual soundcards.

I don't see this in gXine audio menu anywhere for some reason. Odd. I'll doink around with resample and see what happens.

If I do get synch squared away, then I have to find a way to keep gXine from crashing my system when I go to fullscreen mode.  I wonder what *that's* about![/QUOTE]

yes but they are the same instructions I found here:
[http://www.ubuntuforums.org/showthread.php?t=32063&highlight=multiple+sounds+alsa](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=multiple+sounds+alsa)

the sync option only showed up when I changed then xine configuration experience level to "master of the known universe"

---

### Post by WamBamBoozle on 2006-02-07
Enabling "resample" was all I needed. This means you must change ~/.xine/aaxine_config file to

[INDENT]```
# method to sync audio and video
# { metronom feedback  resample }, default: 0
#audio.synchronization.av_sync_method:metronom feedback

audio.synchronization.av_sync_method:resample feedback
```[/INDENT]

I'm running AMD 64 & NForce chipset

---

