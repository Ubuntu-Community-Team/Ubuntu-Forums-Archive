---
title: "Ubuntu 7.4 DVD very Choppy"
date: 2007-05-13
forum: General Help
---

### Post by heather on 2007-05-13
Hi

i have a Geoforce 5500 agp 8x 256 ddr ram

i just today installed 7.4 of Ubuntu as i use to use 6.06 and OpenBSD
7.4 It seems stable so far,like  i mean like i did not have to 
install all the repositores to get my media playing  as in the 6.06 version
But did install the updates and a few extras to play with

But for some reason my Dvd Play extremely Choppy and audipo Skipping as well
in Mplayer and Vlc. What causes that?

Alll of my mpegs and avi files are fine and they are perfectly flawless and smooth

Also my Nvidia only seems to let me adjust the resolution to 1280 or 1024 rather and no higher?
i went to xserver-xorg and saved the settings from nvidia and Saved the changes

Then from there i installed Nvidia-glx-legacy
and did the sudo nvidia-glx-config enable

i saw the Nvidia logo at boot all went well except for the Dvd
any help please will be appreciated

Thank You

:confused:

---

### Post by sylva on 2007-05-13
Just the top of my head: Sometimes one's DVD player/recorder's standard laser beam may not decode other DVD/players' laser beam standard. Other times it's a software problem. For example, many times what I record via XP's DVD program won't be read, or it'd be choppy via Nero. This is because of the way software packages use recording/play standards of codec (code/decode). Because of that the decoding speed of your computer/processor may not be enough due to the degree of compression of the material on the DVD. 

Two questions: 

1. Where did you buy the DVD? I ordered one from Amazon but got the CD. 
2. Are Ubuntu's server packages on the DVD as Ubuntu states?

Thanks, John.

---

### Post by heather on 2007-05-13
Hi

First off possibly from what i read here the issue at hand  may have
more to do with Enabeling DMA Mode  for the Dvd Drive

The Movie  i bought it at a Store if thats what you meantor Ubuntu?
i Downloaded Ubuntu 7.04 and burned it to DVD with alcohol (my favorite)

What i am saying i guess is yes My computer is fast enough to play Dvd
i use it all the time on FreeBSD OpenBSD as well as Ubuntu 6.06 and it plays Beautifully

i only ran into this problem when i installed the new 7.04
Possibly its a sound codec that is causing the skipping?
 
Thanks for your reply :)

---

