---
title: "Amarok: audio output unavailable; the device is busy"
date: 2008-06-11
forum: General Help
---

### Post by yuv656 on 2008-06-11
This error is driving me mad.

I googled and asked on IRC and tried several fixes to no avail, e.g.:

- reboot and try again = problem persists
- grep for /dev/snd or esd or whatever and kill it = found nothing
- switch amarok to pulseaudio = same problem
- install flash 10 which supposedly fixes the bug where flash hogs the sound = same problem
- use aoss to wrap amarok or firefox = problem persists

Please help!

---

### Post by Tom--d on 2008-06-11
I noticed when I was using Flash 10 that (watching a video) it hogged my sound and after, no sound in other applications worked. So I had to use Flash 9 :(

And now thinking of going to gnash

---

### Post by yuv656 on 2008-06-11
> **Tom--d said:**
>  So I had to use Flash 9 :(

I had flash 9, it gave me this problem, then i installed a flash 10 package from a person on irc, in which he supposedly fixed the bug, but the problem persists.

The other error that Amarok gives when I try to play something is this: 
"The script Default exited with error code: 127"
Details: /usr/share/apps/amarok/scripts/score_default/score_default.spec : 1: name: not found

---

### Post by yuv656 on 2008-06-11
Please help me.

I  have no sound, so basically something is hogging my sound device, and even rebooting has no effect.

---

### Post by jkhh07 on 2008-08-01
Hey everyone, I don't know why someone didn't post earlier but the _**fix to this is this:**_

1. open amarok
2. settings - configure amarok
3. engine - set _output_ plugin to **"alsa"**

---

### Post by ranjithkumarshetty on 2008-09-21
> **jkhh07 said:**
> Hey everyone, I don't know why someone didn't post earlier but the _**fix to this is this:**_

1. open amarok
2. settings - configure amarok
3. engine - set _output_ plugin to **"alsa"**



Wonderful... it worked!! thanks a ton :)

---

### Post by atarisan on 2008-10-14
:lolflag::lolflag::lolflag::lolflag::lolflag::lolflag::lolflag:
been searching up and low,,,,,,
finally, now I can forget about WinXp for mp3. :)

---

### Post by Marcin/Enialis on 2008-11-23
> **jkhh07 said:**
> Hey everyone, I don't know why someone didn't post earlier but the _**fix to this is this:**_

1. open amarok
2. settings - configure amarok
3. engine - set _output_ plugin to **"alsa"**



I have the same error, but setting to alsa is no use:( There are any other systems to fix it?

---

### Post by vittoriov on 2008-12-01
> **Marcin/Enialis said:**
> I have the same error, but setting to alsa is no use:( There are any other systems to fix it?

look at the pulseaudio process. Go to System / Administration / System Monitor and look for it. Kill the process and restart Amarok.

If it works now, consider to remove pulseaudio. This is a good guide: [http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/](http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/)

Vittorio

---

### Post by Marcin/Enialis on 2008-12-03
On System monitor I don't have any process named pulseaudio or anything similar :-(

---

### Post by barley342 on 2009-01-01
Stopping pulse audio fixed the problem for me. I had the same symptoms. I was very perplexed until I found your post here. My next step is to remove the pulse audio. 

Using 
Ubuntu 8.10- the Intrepid Ibex - released in October 2008
Amarok
Postgresql 8.3

Thank you so much!:KS

~Barley342~

---

### Post by JordanMcSwifty on 2009-01-15
I killed pulseaudio and restarted amarok and now it says:

xine was unable to initialize any audio drivers

The audio driver isnt the problem though because my speakers work fine on pandora and such.

---

### Post by wmtmanjula on 2009-04-03
> **jkhh07 said:**
> Hey everyone, I don't know why someone didn't post earlier but the _**fix to this is this:**_

1. open amarok
2. settings - configure amarok
3. engine - set _output_ plugin to **"alsa"**


This worked for me
Many Thanks!):P

---

