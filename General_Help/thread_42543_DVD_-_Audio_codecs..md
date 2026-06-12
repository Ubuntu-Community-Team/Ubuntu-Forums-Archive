---
title: "DVD - Audio codecs."
date: 2005-06-18
forum: General Help
---

### Post by peter07 on 2005-06-18
I try to play DVD movies, but i can't here any sound. Mplayer crashed when use it to open DVDs: Fatall Error: audio codecs. Other players play movies without sound. Which audio codecs i should install???

---

### Post by diebels on 2005-06-18
w32codecs?

---

### Post by peter07 on 2005-06-18
I had installed w32codecs before installing mplayer and other players.  They don't work properly - I can't hear any sound in DVD movies :(.

 I use w32codecs from standard ubuntu package database.

---

### Post by gil-galad on 2005-06-18
Do you have liba52-0.7.4 installed?

---

### Post by afonic on 2005-06-18
[QUOTE=peter07]I try to play DVD movies, but i can't here any sound. Mplayer crashed when use it to open DVDs: Fatall Error: audio codecs. Other players play movies without sound. Which audio codecs i should install???[/QUOTE]
 Make sure you install everything mentioned here:

[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

---

### Post by peter07 on 2005-06-18
I've just installed:

sudo apt-get install w32codecs

sudo apt-get install gstreamer0.8-plugins

sudo apt-get install lame

sudo apt-get install sox

sudo apt-get install ffmpeg

sudo apt-get install mjpegtools

sudo apt-get install vorbis-tools

(everything from [http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs) without sudo apt-get install gstreamer0.8-lame)

I have also liba52-0.7.4 installed.

Sorry, but I still can't hear any sound in DVD movies. I have got more problems: Totem ( movie player) crashes every time I try to play DVD's. I have mplayer and even Vlc but Totem is set as default player and it automatically starts when I put new disk into the player.

---

### Post by peter07 on 2005-06-19
Any new ideas ???

---

### Post by gil-galad on 2005-06-19
Try totem-xine.  I just tried mplayer myself and I noticed the same problem.  The build must just be bugged.  I am going to recompile it myself and see if it works.

---

### Post by peter07 on 2005-06-19
I try totem-xine - it doesn't crash - but i still can't hear any sound  ](*,)

---

### Post by heart_reaver on 2005-06-19
try kplayer but for that you need to install kde libraries

---

### Post by afonic on 2005-06-19
[QUOTE=peter07]Any new ideas ???[/QUOTE]
 Try to enable DMA for your DVD-ROM, this may fix it.

If you don't know how, ubuntuguide is your friend:
[http://www.ubuntuguide.org/#speedupcddvdrom](http://www.ubuntuguide.org/#speedupcddvdrom)

---

### Post by gil-galad on 2005-06-19
Do music files and stuff work when you play them with totem-xine?  Maybe your audio is muted?

---

### Post by steven_ellis on 2005-06-19
There is an issue with AC3 audio and the builds of mplayer.

Download xine and try that. Works fine for me.

I've even tried a custom build of mplayer and I still hit the AC3 issues.

Now the question is does this only happen on K7 cpus or does it affect everyone else.

Steve

---

### Post by gil-galad on 2005-06-19
Thats a good question, as I have a k7 cpu.  I also remember having no problems with mplayer in warty.  I am compiling mplayer as I type this, so we will see what happens.

Edit:  I compiled the latest version myself and it works fine.

---

### Post by peter07 on 2005-06-20
Thanks for your help. 

 I look myself for some information and i find something about ESD. [https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29)

I' ve made some changes in /etc/esound/esd.conf and it started to work. Now i can hear sound in DVD movies when I use Totem. Mplayer and Vlc still don't work.

---

### Post by ptigga on 2005-06-26
[QUOTE=gil-galad]Thats a good question, as I have a k7 cpu.  I also remember having no problems with mplayer in warty.  I am compiling mplayer as I type this, so we will see what happens.

Edit:  I compiled the latest version myself and it works fine.[/QUOTE]

I've been having the same problems with mplayer and audio where mplayer crashes with the error "MPlayer interrupted by signal 11 in module: decode_audio".
Bug report: ([https://launchpad.ubuntu.com/malone/bugs/1150](https://launchpad.ubuntu.com/malone/bugs/1150))

Please can you tell me what you did to compile mplayer to fix this bug?  Is it easy to make a .deb out of a package that you have compiled yourself?

---

### Post by ptigga on 2005-06-29
[QUOTE=ptigga]I've been having the same problems with mplayer and audio where mplayer crashes with the error "MPlayer interrupted by signal 11 in module: decode_audio".
Bug report: ([https://launchpad.ubuntu.com/malone/bugs/1150](https://launchpad.ubuntu.com/malone/bugs/1150))

Please can you tell me what you did to compile mplayer to fix this bug?  Is it easy to make a .deb out of a package that you have compiled yourself?[/QUOTE]

Addeneum to this problem - I've found some links for discussions by people who have had the same problem.  I haven't solved it yet, but these links may help you to solve it and if they do then please post your solution here.

Bug report: [https://launchpad.ubuntu.com/malone/bugs/508](https://launchpad.ubuntu.com/malone/bugs/508)

Discussion on ubuntu mailing list: [http://ubuntuforums.org/archive/index.php/t-29132.html](http://ubuntuforums.org/archive/index.php/t-29132.html)

---

### Post by peter07 on 2005-06-30
[QUOTE=ptigga]Addeneum to this problem - I've found some links for discussions by people who have had the same problem.  I haven't solved it yet, but these links may help you to solve it and if they do then please post your solution here.

Bug report: [https://launchpad.ubuntu.com/malone/bugs/508](https://launchpad.ubuntu.com/malone/bugs/508)

Discussion on ubuntu mailing list: [http://ubuntuforums.org/archive/index.php/t-29132.html](http://ubuntuforums.org/archive/index.php/t-29132.html)[/QUOTE]

They give te solutions:

> I don't really think that this is a mplayer bug, as I never had any
problem with mplayer compiling it myself. This time I'm using the ubuntu
deb package and I run into those problems.

I have big problems with compilations: [http://ubuntuforums.org/showthread.php?t=43742](http://ubuntuforums.org/showthread.php?t=43742)

I use totem - only this player works.

---

### Post by Sky-Net on 2005-07-06
Hi all.

  I have exactly the same AC3 problem using MPlayer in Ubuntu (Amd64 generic) version

---

### Post by chevyou on 2005-07-06
I might be of some help.  I noticed that even after installing the proper codecs etc, I was unable to get anything from a CD/DVD in terms of audio until I went into KMix -> Mixer and then clicked the input tab then enabled and turned up the Aux bar.

Hope this helps.

---

### Post by tread on 2005-07-06
Have you tried wxvlc?

---

### Post by Sky-Net on 2005-07-09
Thanks,
  It seems to be a Mplayer bug... with other programs ac3 dvd playback runs perfectly.  Anyway... Has anyone found a fix for Mplayer?

---

### Post by madverb on 2005-08-06
I can only watch DVD's with mplayer if I use 'mplayer -ao oss' but then I get no sounds until I 'killall esd'. It's obvious that the problem is caused because of ESD. mplayer seems to have a problem with it.

---

### Post by confused on 2005-08-19
I must thank all those who suggested the following and finally my dvd is playing in totem movie player.

1. I installed all the reqd codecs etc by sudo apt-get for multimedia for xine etc. Then enabled the DMA and finally when i saw the movie but cld nto hear the sound, i went to the volume control and found that they were at the minimum. A week's effort has been finally successful.

2.Good forum which has helped me in the follg too: monitor screen resolution change:

Mine is a Hansol monitor and so i went to the etc/X11/xorg.cong and edited the monitor and the screen devices to Hansol model and added the horizsync and vertical info and lo my monitor which had been showing huge screens displayed beautifully.

---

