---
title: "Yet another microphone doesn't work at Ubuntu Feisty"
date: 2007-08-09
forum: General Help
---

### Post by dmee on 2007-08-09
Hey guys,

I got the pretty common issue w/ my gateway M285-E laptop: the built-in microphone doesn't work neither in Skype nor in any other application. The sound card is sort of popular one: hda-intel.

I've read the whole bunch of similar threads here and at launchpad and tried many different ways of solving the problem (I have updated my alsa drivers and many other stuff).

And it still doesn't work.

Any idea?

P.S. The microphone was working on Vista before.

---

### Post by 5-HT on 2007-08-10
Are you sure your using the proper, unmuted channel (whether it's mic or front mic or other) in alsamixer and that the chipset is getting recognized properly? A lot of the times the inputs are muted by default.

---

### Post by dmee on 2007-08-10
Here is the screenshot of the alsamixer. Pressing "M" on "Input Source" doesn't change anything.

---

### Post by 5-HT on 2007-08-11
> **dmee said:**
> Here is the screenshot of the alsamixer. Pressing "M" on "Input Source" doesn't change anything.
On that capture channel you have highlighted there, does pressing the spacebar give you a red-coloured 'capture' where those white dashes are now?
BTW, I have a STAC9200 and hda-intel and had to do the above.

---

### Post by dmee on 2007-08-11
Here you go. What now?

---

### Post by 5-HT on 2007-08-11
> **dmee said:**
> Here you go. What now?
Still nothing? It *should* just be a matter of finding the right capture channel and input source. If you play around with some some combinations of those that should do the trick. You can also play around with Gnome's volume controls (sometimes channels are not displayed and you need to go into the prefs to select em).

Another thing to try:  Prior to Edgy, I believe, I had to append ```

options snd-hda-intel model=ref
```to /etc/modprobe.d/alsa-base to get the mic to work. Might be worth a shot (would have to reload the module and restart alsa or just reboot for it to take effect). I'm not sure if I either made a config change to eliminate the need for that, or whether it was done upstream.

---

### Post by dmee on 2007-08-11
Still doesn't work. Feisty.

---

### Post by 5-HT on 2007-08-11
I just came across this: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/111145](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/111145)
Could be a similar issue. Apart from going into Gnome's Volume Control applet and making sure all the capture and recording switches are fully on for both HDA Intel and the Sigmatel Devices, I'm outta ideas apart from some new options the STAC9250 may need in /etc/modprobe.d/alsa-base (could google around to see if anyone else is having luck with em). It is a rather new chip isn't it?

---

### Post by BoogieKnight on 2007-08-11
I had similar issues with my mic not working... turned out I needed to change my mic to mic2 instead of mic1 and all is working.

right-click on volume icon > open volume control > edit / preferences > check mic select
then under the option s tab change to mic2 or whatever.

not sure if you've tried this yet or if it will even work for your problem but this is what solved mine.

---

