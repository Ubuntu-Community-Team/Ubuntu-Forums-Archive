---
title: "Volume of AC3 video audio is very very low"
date: 2006-08-06
forum: General Help
---

### Post by glotz on 2006-08-06
Hi there! All my videos with AC3 format sounds are very quiet. I had this issue on windows too but then I found some AC3 decoder setting to fix it. (I'm maxing out my normal volume settings and the audio is still a bit quiet. Also maxed out my speaker volume..!)

There's an older locked thread with same issue right here [http://www.ubuntuforums.org/showthread.php?t=157941](http://www.ubuntuforums.org/showthread.php?t=157941)

I'd be very grateful if you could come up with a solution or even suggestions.

---

### Post by glotz on 2006-08-07
teh bump

---

### Post by hopstah on 2006-08-07
what media player are you using right now?

---

### Post by hanzomon4 on 2006-08-08
What is AC3 audio? I ask because my dvd's volume is really low.

---

### Post by glotz on 2006-08-08
Using Totem player that comes with Ubuntu. I downloaded extra codecs, can't remember if those included AC3.

AC3 is a way to compress audio, just like MP3. I think this might be your problem too then. [http://en.wikipedia.org/wiki/Ac3](http://en.wikipedia.org/wiki/Ac3)

---

### Post by glotz on 2006-08-10
bump

(I know it's lame to bump your thread, so it must be double-lame to double-bump...)

---

### Post by glotz on 2006-09-08
bump

---

### Post by glotz on 2006-10-19
Bunmpxor!!11

---

### Post by glotz on 2006-10-28
bump

Isn't anybody else seeing this issue?

---

### Post by smalleraperture on 2006-11-06
I am having this issue as well...

---

### Post by Atomic Dog on 2006-11-07
Good job emdlessly bumping this thread up without even looking at the bug reports to see this problem was recently solved.  The patch/fix was accepted into Edgy just a short time ago.

Solution:  [https://launchpad.net/distros/ubuntu/+source/gxine/+bug/39275](https://launchpad.net/distros/ubuntu/+source/gxine/+bug/39275)

Edgy fix acceptance info: [http://www.mail-archive.com/edgy-changes@lists.ubuntu.com/msg07674.html](http://www.mail-archive.com/edgy-changes@lists.ubuntu.com/msg07674.html)

---

### Post by glotz on 2006-11-07
Good job bashing a clueless newbie. Where's the Ubuntu bug reports tutorial? I did a thorough search on this forum for a solution before posting this thread, believe me. :)

Thanks for the info though. Now, I'm still on Dapper. Can I somehow apply that patch?

---

### Post by glotz on 2006-11-15
Anybody?

---

### Post by glotz on 2006-11-22
bump

---

### Post by bazz on 2006-11-24
Yeah I have it too. Cant hear much of anything with the volume all the way up. So how does this get fixed? Seems like a silly bug.

---

### Post by glotz on 2006-12-01
bump

bazz, you bump next. in a week or so, k?

---

### Post by TheMaxxus on 2006-12-04
That patch has already been applied to the gstreamer0.10-plugins-ugly package in the Synaptic Package Manager.  Try installing that package; if it still doesnt work Id say its something else.

---

### Post by glotz on 2006-12-05
I have the package. Just removed and reinstalled it. No change. AC-3 audio volume is considerably lower than mp3 or wma.

Solution suggestions welcomed.

---

### Post by 454redhawk on 2006-12-16
I also have this problem and canot seem to get it fixed.

---

### Post by glotz on 2006-12-25
ppl in need of lil help here!

---

### Post by digTro on 2006-12-26
You, sir, have a lot of patience. This is what I do while playing AC3 encoded files. Type alsamixer at the console. Jack up the master volume and PCM volume to the max. Even then I have to turn up my speaker volume to about 70% of the max level to hear the dialog properly. And remember to jack down the PCM volume while playing mp3s. For me when PCM level is at its max, mp3s sound distorted. (In alsamixer, the levels have some color coding. If the level is at red, I guess it means distortion)

---

### Post by glotz on 2006-12-26
That's the drill. Except I've got alsamixer on my panel.

Let's hope somebody will help us all with this racket...

---

### Post by glotz on 2007-01-08
Here we are again, at the one week outer marker beacon. Commence ze routine BUMPastique!

If I forgot to wind my watch, I could still keep track of time just by watching myself bump this thread at constant intervals...

---

### Post by glotz on 2007-01-23
dahcahwdtvdawavdwth

---

### Post by mikl on 2007-01-31
Bleh, I have this problem as well. Sigh.

---

### Post by mikl on 2007-01-31
...and now, after trying almost everything, I removed gstreamer0.10-ffmpeg and now everything is bliss. Apparently, the bug mentioned earlier is fixed in the "ugly" plugins, but if you have ffmpeg installed, it uses that - and the bug persists. Or something.

Now, I have movies to see...

---

### Post by mcduck on 2007-01-31
AC3 generally sounds like the volume was low, as movie soundtracks are generally using very high dynamic range (meaning big difference between low and hight volume sounds). This doesn't work very well on home use, but many movie players (xine for example) can do audio compression (which makes silent sounds louder and loud sounds more silent.)

In gXine go to file/configure/preferences and under audio/A52 there is a checkbox to enable compression as well as a slider you can use to preamplify the sound.

Also in Audio/Settings there's sliders for both compression and pream.

And make sure you are using correct speaker settings.. If you don't have a surround system you should set your speaker arrangement to 'stereo' or '2.1', and enable 'surround downmix'.

---

### Post by bsmith1051 on 2007-06-21
> **mcduck said:**
> make sure you are using correct speaker settings.. If you don't have a surround system you should set your speaker arrangement to 'stereo' or '2.1', and enable 'surround downmix'.
Where do you set that?  I know where such a setting is in Windows but not in Gnome.

Also, someone said that the problem is related to the ffmpeg package -- but if you remove that then what decodes the MPEG2 video etc?

---

