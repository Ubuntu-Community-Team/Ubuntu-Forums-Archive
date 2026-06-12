---
title: "Mplayer DVD player with no sound (NEWBIE)"
date: 2005-09-13
forum: General Help
---

### Post by sorry_name_taken_already2 on 2005-09-13
I installed gMplayer by mucking about with the repository set up as instructed by 
[http://ubuntuforums.org/archive/index.php/t-21138.html](http://ubuntuforums.org/archive/index.php/t-21138.html)

I have successfully installed pre.1.06
Can you tell me how to patch or fix no sound prob when playing back DVD.

SYSTEM :
PIII 650eb
128MB ram
13 GB HDD
Pioneer (slot) DVD ROM
LG 16X10X40X
Generic MB with MSI 6163Pro chipset
savage AGP 

This is a desktop for clients to check their webmail and playing DVD demos in the office. I thought why not linux it never crashes and its FREE!  :roll: 

I was surprised with the easy installation and it picked up the windows network! I was scared that i had to install or muck around with scripts to get samba to work. I had bad experiences in the past from installing RH 7.0. I am still a newbie with linux.

I have managed to get Mplayer just to play DVD video without sound from changing the audio setting to OSS with decent video playback.

Previously, I was getting an error - crashed Mplayer with bad CPU/FPU etc etc NOW it is audio > not found

The sound card is ESS/SB128


BTW can you recommend a GUI CD burning software?!


Cheers 
-------------------------------------------
Seeking alternative to WIndoze

---

### Post by invisage01 on 2005-09-13
first off... have you got sound working elsewhere?

---

### Post by Emerzen on 2005-09-13
I had to change my audio settings to ESD, and then I got sound w/ my DVDs.  I'd also recommend checking out the Unofficial Guide at:  [www.ubuntuguide.org](http://www.ubuntuguide.org) 

Look at the section on installing DVD playback, then MPlayer specifically, then the section on how to get sound working properly.  I did this in Hoary and it worked fine.  I'm using Breezy Preview now, which has an updated MPlayer (installed via the 'add application' under preferences) then switched to ESD and it 'just worked' w/o all the extra stuff in the guide.

---

### Post by sorry_name_taken_already2 on 2005-09-13
[QUOTE=invisage01]first off... have you got sound working elsewhere?[/QUOTE]

I did apt-get install mplayer-codecs

YES - I forgot to add that sound works!
I can hear the sound theme and from playing CD-A and MP3s.

I am also in the process of figuring how to stream online media like RAM, Quicktime and WMA format. *HELP* ](*,) 

 :grin: My prority is getting Mplayer to play DVDs with SOUND   :grin:

---

### Post by codejunkie on 2005-09-13
[QUOTE=sorry_name_taken_already2]I did apt-get install mplayer-codecs

YES - I forgot to add that sound works!
I can hear the sound theme and from playing CD-A and MP3s.

I am also in the process of figuring how to stream online media like RAM, Quicktime and WMA format. *HELP* ](*,) 

 :grin: My prority is getting Mplayer to play DVDs with SOUND   :grin:[/QUOTE]
when you open mplayer right click on the display and go into the mplayer preferences  
click on the audio tab and choose esd click ok and restart mplayer and see if that fixes your audio problem.

---

### Post by sorry_name_taken_already2 on 2005-09-13
[QUOTE=codejunkie]when you open mplayer right click on the display and go into the mplayer preferences  
click on the audio tab and choose esd click ok and restart mplayer and see if that fixes your audio problem.[/QUOTE]

I get the following errors:
Mplayer interrupted by signal 11 in module: decode_audio
[OK]

Mplayer crashed by bad usage of CPU/FPU/RAM
Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and    disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
[OK]

MPlayer crashed. This shouldn't happen.
It can be a bug in the MPlayer code _or_ in your drivers _or_ in your gcc version. If you think it's MPlayer's fault, please read DOCS/HTML/en/bugreports.html and follow the instructions there
[OK]

We can't and won't help unless you provide this information when reporting a
possible bug.
[OK]

 ](*,) Q: How to install DVD playback capability?  ](*,) 

   1. Read General Notes
   2. Read How to add extra repositories?
   3. sudo apt-get install libdvdcss2

Q: How to install Multimedia Player (MPlayer) with Plug-in for Mozilla Firefox?

   1. Read General Notes
   2. Read How to add extra repositories?
   3. Read How to install Multimedia Codecs?
   4. Read How to install DVD playback capability?
   5. sudo apt-get install mplayer-386
       sudo apt-get install mplayer-fonts
       sudo apt-get install mozilla-mplayer
       sudo cp /etc/mplayer/mplayer.conf /etc/mplayer/mplayer.conf_backup
       sudo gedit /etc/mplayer/mplayer.conf
   6. Find this line
...
vo=x11,                  # To specify default video driver (see -vo help for
...
   7. Replace with the following line
vo=xv,                  # To specify default video driver (see -vo help for

[http://www.ubuntuguide.org/#dvdplayback](http://www.ubuntuguide.org/#dvdplayback)

[CENTER][COLOR=Sienna][SIZE=6]STILL NO SOUND![/SIZE][/COLOR][/CENTER]

---

### Post by Hairy_Palms on 2005-09-13
trying typing killall esd then running mplayer, and if you want a gui cd burner i recommend k3b coz it rocks.

---

### Post by Emerzen on 2005-09-13
This is a problem w/ the older version of MPlayer found in Hoary repo's.  I followed this thread[MPlayer source install how-to](http://www.ubuntuforums.org/showthread.php?t=31061&highlight=mplayer+install+source) and installed the latest MPlayer back when I was still w/ Hoary and it worked fine.  On the other hand, the latest version is included in the Breezy Repo's if you want to try that route, and that works out of the box.  Either way you still have to change the audio to ESD.  For me (a newbie) installing from source using this thread was a "Copy and Paste" into the command line and it all worked.  Hope that helps.

---

### Post by arnieboy on 2005-09-13
[QUOTE=sorry_name_taken_already2]I get the following errors:
Mplayer interrupted by signal 11 in module: decode_audio
[OK]

Mplayer crashed by bad usage of CPU/FPU/RAM
Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and    disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
[OK]

MPlayer crashed. This shouldn't happen.
It can be a bug in the MPlayer code _or_ in your drivers _or_ in your gcc version. If you think it's MPlayer's fault, please read DOCS/HTML/en/bugreports.html and follow the instructions there
[OK]

We can't and won't help unless you provide this information when reporting a
possible bug.
[OK]

 ](*,) Q: How to install DVD playback capability?  ](*,) 

   1. Read General Notes
   2. Read How to add extra repositories?
   3. sudo apt-get install libdvdcss2

Q: How to install Multimedia Player (MPlayer) with Plug-in for Mozilla Firefox?

   1. Read General Notes
   2. Read How to add extra repositories?
   3. Read How to install Multimedia Codecs?
   4. Read How to install DVD playback capability?
   5. sudo apt-get install mplayer-386
       sudo apt-get install mplayer-fonts
       sudo apt-get install mozilla-mplayer
       sudo cp /etc/mplayer/mplayer.conf /etc/mplayer/mplayer.conf_backup
       sudo gedit /etc/mplayer/mplayer.conf
   6. Find this line
...
vo=x11,                  # To specify default video driver (see -vo help for
...
   7. Replace with the following line
vo=xv,                  # To specify default video driver (see -vo help for

[http://www.ubuntuguide.org/#dvdplayback](http://www.ubuntuguide.org/#dvdplayback)

[CENTER][COLOR=Sienna][SIZE=6]STILL NO SOUND![/SIZE][/COLOR][/CENTER][/QUOTE]
Do the following:
```
sudo gedit /etc/mplayer/mplayer.conf
```
look for the line **ao**
and change it to:
**ao=esd,**
save and exit and run mplayer.

---

### Post by sorry_name_taken_already2 on 2005-09-14
I installed pre1.07 and now there is only mpegp, oss, alsa, null and pcm audio drivers? Where is this elusive ESD in 1.07 so i can play DVDs! :|

Checking audio filter chain for 48000Hz/2ch/s16be -> 48000Hz/2ch/s16be...
AF_pre: 48000Hz/2ch/s16be
[B][AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
Could not open/initialize audio device -> no sound.[/B]
Audio: no sound
Starting playback...

---

### Post by sorry_name_taken_already2 on 2005-09-14
[QUOTE=Hairy_Palms]trying typing killall esd then running mplayer, and if you want a gui cd burner i recommend k3b coz it rocks.[/QUOTE]

THANKS HAIRY PALMS... iwillgive it a ago! I hope its in the repository!

DO a apt-get on it?!

---

### Post by Emerzen on 2005-09-15
I'm not sure why the 1.07 isn't working for you out of the box.  Any problems w/ the install as listed in the thread I pointed you to?  

Try this:
Close MPlayer
at the command line type> sudo killall esd
Restart MPlayer and see if you get sound.

If that works, go to Ubuntuguide and find the section on "configuring sound to work properly" or something like that and follow the steps.

---

### Post by sorry_name_taken_already2 on 2005-09-15
[QUOTE=Emerzen]I'm not sure why the 1.07 isn't working for you out of the box.  Any problems w/ the install as listed in the thread I pointed you to?  

Try this:
Close MPlayer
at the command line type> sudo killall esd
Restart MPlayer and see if you get sound.

If that works, go to Ubuntuguide and find the section on "configuring sound to work properly" or something like that and follow the steps.[/QUOTE]

**# mplayer -ao help**
**MPlayer 1.0pre7-3.3.5 (C) 2000-2005 MPlayer Team**
CPU: Intel Celeron 2/Pentium III Coppermine,Geyserville (Family: 6, Stepping: 1)Detected cache-line size is 32 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE


[COLOR=Red]Available audio output drivers:
        mpegpes DVB audio output
        oss     OSS/ioctl audio output
        alsa    ALSA-0.9.x-1.x audio output
        null    Null audio output
        pcm     RAW PCM/WAVE file writer audio output[/COLOR]

[U]Please help - I have compiled and installed the lastest version of mplayer.
I also downloaded the essential codecs from mplayer's home page and apt-get install w32codecs ;) to be doubly sure![/U]

---

