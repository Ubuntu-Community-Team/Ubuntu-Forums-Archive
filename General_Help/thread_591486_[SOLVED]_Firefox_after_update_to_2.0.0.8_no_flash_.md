---
title: "[SOLVED] Firefox after update to 2.0.0.8 no flash sound"
date: 2007-10-25
forum: General Help
---

### Post by squirage on 2007-10-25
Hi All,

  I am having issues with no flash audio in Firefox 2.0.0.8. I do have flash 9 installed and I tied one fix that said something about removing the .so and .xpt files, but that didn't work. I also tried the pulse audio installation, as well as the alsa-oss installation and reconfigured the DSP setting in firefoxrc, but none of that worked.

I have removed all of the aforementioned stuff and may try to go through it again. Just wondering if anyone had a fix that worked for them that I did not see.

Thanks

---

### Post by squirage on 2007-10-26
Anyone?

I've done a lot of searching, finding things more than a year old and nothing has worked so far. I'm just surprised that this has re-surfaced.

Would switching to Gutsy help?

---

### Post by Ubuntoob on 2007-10-26
I am using 7.10 and FF 2.0.0.8 and flash sound is fine.

However, I wouldn't recommend anyone switch to 7.10 until the graphics drivers (for especially ATI cards) are sorted out. The forums are full of people who cannot get 3D acceleration working for their ATI cards (like me) and therefore can't use desktop effects.
Desktop effects or 3d support and high frames per second might not be high on the list compared to flash sound - that's your call.

Maybe you could reinstall your system and not update Firefox?

Good Luck. (I'm a linux noob and loving Ubuntu but looking forward to this graphic card driver issue being sorted).

(While you are testing - my sig url is a flash site with rollover sounds and videos/audio etc.)

---

### Post by carlos1992 on 2007-10-26
Hey that's weird, i updated and did it just perfect the sound, video etc. i had a problem actually with the last version of FF for example i couldn't see the pictures when you try to buy a dell computer, but i reinstall the flash and reinstall FF (Synaptics. otherwhise you won't be able) and that worked just fine.<br>
Good luck

---

### Post by squirage on 2007-10-26
Hi,

Thanks carlos1992 and Ubuntoob. As usual the solution was there it was just muddling through all the "solutions" to find the right one or combination of ones.

What ended up working was a combination of installing pulseaudio and asla-oss.

There were several places that had the procedure but I used this:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_PulseAudio_Sound_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_PulseAudio_Sound_Server)

So we install this:
```
sudo apt-get install "pulseaudio-*" paman padevchooser paprefs pavucontrol
```

Then get the libflashsupport_1.0-2219-1_i386.deb from the mirror because the other link is dead.

[http://www.divshare.com/download/454409-e7c](http://www.divshare.com/download/454409-e7c)

Then edit the configuration file but instead of /etc/asound.conf do 

```
gksudo gedit ~/.asoundsrc
```

and paste this into it:

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

I guess you could follow the next step and set pulse prefs by typing
```
paprefs
```

but it seemed like it was already set correctly.

Typing ```
pulseaudio
``` gave me a big error message.

You can also probably skip the sound preferences manage group step as those were already checked for me too.

So I rebooted and some immediate progress, I have the drum sounds when I log on for the first time in a month. Further "progress" youtube now crashes firefox everytime I open a video.

So then I ran ```
firefox -V
``` and it showed me that FIREFOX_DSP=  and there was nothing there. Well I know that I needed to have something there so I tried another step that i had seen somewhere.

It was originally posted at htttp://www.macewan.org/2006/06/01/howt-firefox-flash-video-sound-on-ubuntu-linux-dapper/

```
sudo apt-get install alsa-oss
```
then
```
sudo nano /etc/firefox/firefoxrc
```

Change whatever FIREFOX_DSP=" " says to 
FIREFOX_DSP="aoss"

And then you have sound on youtube. Perhaps it was the Knob Creek Bourbon that really facilitated this fix\\:D/

On to the next fix.

---

### Post by Ubuntoob on 2007-10-27
Nice one!

Glad you sorted it out!

One down - always more to go..

Keep soldiering on..

:)

---

