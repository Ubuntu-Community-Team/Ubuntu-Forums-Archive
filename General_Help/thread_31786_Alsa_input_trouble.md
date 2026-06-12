---
title: "Alsa input trouble"
date: 2005-05-04
forum: General Help
---

### Post by forrestcupp on 2005-05-04
Please help me.  I have searched the forum and google for an answer to no avail.

I am using alsa on a Sound Blaster Audigy 2 with various software (ardour, audacity, etc.) to record music with my guitar, microphone, etc.  The Audigy has a mic input and a line input on the back of my computer.  On the front in a drive bay the audigy has a 1/4 " mic/line 2 input.  In the alsa mixer I have all of my playback volume sliders turned up and I can hear my guitar through the system when it is plugged in.  My problem is that whenever I record, it records everything that can be heard.  So I have drums playing on the first track, and when I record the second track, it rerecords the drums that are playing along with my guitar.  How can I tell alsa that I only want it to record from one certain input and not from everything that can be heard?  There has to be a way to do this. 

I hate Windows, but at least in Windows I could easily select my input method.  I love my Ubuntu, so if anyone can help me with this problem I will greatly appreciate it.

---

### Post by forrestcupp on 2005-05-07
I found out that alsamixer comes up with the playback volumes and I can press F4 to get to the capture volume sliders.  I turned the PCM capture slider all the way down, and now it doesn't record what I'm hearing from the other tracks.  I was thrown off because kmix and the gnome mixer doesn't show my record volumes.

---

### Post by c_dog on 2005-05-07
[QUOTE=forrestcupp]I found out that alsamixer comes up with the playback volumes and I can press F4 to get to the capture volume sliders.  I turned the PCM capture slider all the way down, and now it doesn't record what I'm hearing from the other tracks.  I was thrown off because kmix and the gnome mixer doesn't show my record volumes.[/QUOTE]

Kmix does show record volumes, but when enabled, the silly thing has it's input channel controls on the output mixer screen.

---

### Post by strat696 on 2006-04-09
Hello Forrestcupp...

I am new:-|  to Ubuntu and as yet do not have the new Linux OS so unfortunately I cannot help......and have not been able to add a seperate post as yet....Will read how to soon....I noticed you have SB Aud 2........I have SB X Fi....and am yet to record music with my guitar as I do not have any software....I have heard that Cakewalk and Qbass are the standards so far...do you know or anyone outhere of any other comparable software and the best place to dload or purchase   possibly in Australia.....


Thanks for your help and keep on strummin....


Regards



Jason Strat 696[8) 





QUOTE=forrestcupp]Please help me.  I have searched the forum and google for an answer to no avail.

I am using alsa on a Sound Blaster Audigy 2 with various software (ardour, audacity, etc.) to record music with my guitar, microphone, etc.  The Audigy has a mic input and a line input on the back of my computer.  On the front in a drive bay the audigy has a 1/4 " mic/line 2 input.  In the alsa mixer I have all of my playback volume sliders turned up and I can hear my guitar through the system when it is plugged in.  My problem is that whenever I record, it records everything that can be heard.  So I have drums playing on the first track, and when I record the second track, it rerecords the drums that are playing along with my guitar.  How can I tell alsa that I only want it to record from one certain input and not from everything that can be heard?  There has to be a way to do this. 

I hate Windows, but at least in Windows I could easily select my input method.  I love my Ubuntu, so if anyone can help me with this problem I will greatly appreciate it.[/QUOTE]

---

### Post by ogami1972 on 2006-04-10
if you are going to break into the world of linux recording, i must suggest statrting with the Agnula Demudi distribution. it comes pre-packed with just about every decent linux sound app out there, and my audigy card worked in jack without any configuration on my part.
On the other hand, and please don't take this the wrong way, you really should drop the audigy card. m-audio makes great cards in a lot of price ranges and they all work really well with ALL flavors of 'nux, in my experience. I have a Audiophile 2496 on this machine ( a windows/linux dual-boot that i use as a synth/daily computer) and a Delta 44 on my recording desktop. My recorder is running "ardour" a really powerful multi-track sequencer. (make sure you download all the LADSPA plugins!(cmt, swh, blop, etc.). I must confess that i use windows most often for synth work- there is still no Linux equivalent to Reason or FLStudio, although "hydrogen" is very good in it's own right, and "lmms" shows amazing promise. I also have a laptop i use a live sampler/effect bank (check out "freewheeling"!)
I say all this to let you know that there ARE other musicians out there using linux- stick with it- and if you decide to switch cards, remeber- you are not losing a card due to linux; you are choosing to support a company that supports open-source!

---

### Post by forrestcupp on 2006-06-20
Well, I asked this question over a year ago, and I have learned a lot since then.  From the way I see things now, there is no reason whatsoever for me to drop my Audigy 2.  I love it.  It works great for my recording purposes, and it has pretty good quality.  I know there are better cards out there, but when I spent a lot of money on this, and it works, there's no reason to just drop it and spend more money on another card.

By the way, strat696, if you're using linux now, Ardour is one of the better digital audio workstation applications out there.  There are some things about it that I don't like, but overall, it seems to be pretty quality.  Just like ogami1972 says, make sure you get the LADSPA plugins, too, or you won't be happy with Ardour.  If you're still a Windows user, n-Track Studio is a pretty good package.  You can find it at [www.fasoft.com](www.fasoft.com)  It's not free, it's $49 for the standard version and $75 for the version with 24-bit support, but that's a lot better than $1000 for something like Logic.  n-Track comes with a few effects, and there are lots of free vst and directx audio plugins available.  Or you could just come to Linux, and get Ardour for free.  Linux also has a good drum machine program called Hydrogen.

---

