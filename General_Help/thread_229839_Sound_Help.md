---
title: "Sound Help"
date: 2006-08-05
forum: General Help
---

### Post by MuteMathSSR on 2006-08-05
Uh thank you vereh much.  Well like I said this is finally my first time using Linux.  I'm a very good windows user but on linux i'm newb. Honestly I was a little scared earlier this morning when I started this whole crazy venture. 

I have dapper drake running<br>

I seem to have one major problem and that is that I can't get any sound<br>

<a href="http://reviews.cnet.com/Gateway_7330GZ_Mobile_Pentium_4_532_3_06_GHz_15_4_TFT/4505-3121_7-31477979.html">This</a> is my computer.  I believe that the sound card is recognized b/c when I go to <br>

system>preferences>sound<br>

it says

at soundcard it says intel 82801DB-ICH4<br>

it also gives me a choice of using conexant (OSS MIXER) and
Intel (Alsa Mixer)

Yes,  the volume is turned up all the way and not on mute.  There is no manual mute key on the laptop.  I tried ALSAMIXER and turned everything on and up and still nothing.  I'm wondering if there is some sort of "Driver" that i need to install.  And if so how/where would I do such a thing?

---

### Post by Skia_42 on 2006-08-05
You should be able to find an application that handles volume on your computer such as "vumeter", when you find it check the settings and ajust appropriatly. I doubt you have to install any drivers in ubuntu to get the sound working.

---

### Post by MuteMathSSR on 2006-08-05
For anyone who is interested I found the problem.  Here is some quoted text that solved the problem

[I]You'll want to use the Intel (ALSA) option.

Try the following, it seems to work for a number of people.

Open Alsamixersudo alsamixer

You'll want to mute the "IEC958 Capture Monitor"

Quit alsamixer and run the following in the terminal:sudo alsactl store

That should fix you up. If not, you'll also want to follow blaq's instructions for providing appropriate information about your system. That will tell us what hardware you have, what drivers you're using, what's getting recognized at boot, and stuff like that. In additions to the commands blaq requested, also provide the output of the following:
$ cat /proc/asound/cards
$ sudo cat /etc/modprobe.d/alsa-base

Also, click on the speaker icon, open volume control, and make sure the speakers are unchecked. This seems obvious, but sometimes that's the easiest way to fix the problem :p[/I]

---

