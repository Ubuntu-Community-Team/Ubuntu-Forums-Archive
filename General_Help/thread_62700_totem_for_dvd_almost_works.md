---
title: "totem for dvd almost works"
date: 2005-09-05
forum: General Help
---

### Post by randlieb on 2005-09-05
i've had ubuntu installed (dual booted with windows xp) for about 2 weeks now. i wanted to switch to linux/open source and ubuntu looked like a good choice (i don't remember HOW i found the site but i love their philosophy!!!)

the base installation is great, but i wanted more. i didn't realize how complicated it could get! ](*,)

my first problem was my cd played then didn't play then i found a post that got it playing again.

then i went to the 'unofficial starter guide' and found how (after a bit of trial and error) to do all sorts of stuff that allowed me to get plugins for firefox and install some non-standard (for ubuntu) apps (nvu, realplayer, mozilla thunerbird etc.). i at first thought i'd have to download and install them all from their respective web sites!

FINALLY found the right post for setting up my lexmark printer. \\:D/ 

now i'm just about all set to rid myself of my dependence on windows except for one thing.....i want to play dvd's! i don't have (and don't plan on getting) a dvd player/stereo system. this computer IS my home entertainment center.

SOOOOO......
i've searched the forums high and low to get dvd's to play. 

at the start, inserting a dvd opened up totem and it just froze. got totem to start the dvd but after all the intro scenes and with no sound! then i got sound but a herky-jerky playback/soundtrack. the last thread i saw showed me a fix to correct that problem, but alas, it was not to be. i'm starting this new thread in hopes of getting the last bit of help to finish things up.

i wish now i had been saving the thread links for what worked so i could show them here....sorry. i was just happy to get something fixed and then move on to the next problem. :roll: 

so here i am, a VERY wordy post to (i hope!) a simple solution! any and all help is GREATLY appreciated. the ubuntu community has been great, giving me hands on training, so to speak, with linux/ubuntu. i just hope to be able to give something in return at some future time. :grin:

thanks from this linux newbie/wannabe

---

### Post by banjobacon on 2005-09-05
Install totem-xine (via Synaptic). I find it works better than gstreamer, which is used by default. That solved my jerky DVD issues.

---

### Post by randlieb on 2005-09-05
been there - done that......

i've been trying to think of some of the other work-arounds i've already tried.

- something to do with changing dma
- have installed all the multi media codecs
- installed xine in addition to totem-xine

i also have installed mplayer, realplayer and VLC for gtk+ as i was trying to see if SOMETHING would play my dvd! would any of those interfere with totem?

if i remember any more i'll post here.

thanks for your input!

---

### Post by randlieb on 2005-09-05
i kept looking through search for more info and found it! in the 'unofficial starter guide' there is a 'how to' for speeding up dvd playback. thought i'd give that a try and IT WORKED!!! hallelujah....goodbye windows....welcome ubuntu/linux!!!!

---

### Post by Samuli on 2005-10-26
I had problems with totem playing any video (as well as some other players) and this is what I did:

1. Install all the media codecs (including libdvdcss2) according to [www.ubuntuguide.org](www.ubuntuguide.org)

2. get rid of all those players you've tried with no luck and get totem-xine. It seems that gs-streamer really does suck ;)

3. Enable dma for dvd-drive if the playback is slobby (mine wasn't even though my computer certainly isn't up-to-date and dma was not used. Go figure). For instructions: [www.ubuntuguide.org](www.ubuntuguide.org) -> speeding up cd/dvd

---

