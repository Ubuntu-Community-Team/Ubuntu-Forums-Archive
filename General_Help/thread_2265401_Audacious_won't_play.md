---
title: "Audacious won't play"
date: 2015-02-14
forum: General Help
---

### Post by cicada2 on 2015-02-14
Hi there! 
I am running Lubuntu 14.04 and... I cannot get Audacity 3.4.3 to play flac files. I add flac files and select "play". But nothing happening. Any ideas are greatly appreciated.


Compaq Presario-R3000 
Pentium(R)4 - 2.40 GHz

---

### Post by tgalati4 on 2015-02-14
Try using *mplayer* first.  Open a terminal:

```
sudo apt-get install mplayer
mplayer music_file.flac
```

---

### Post by cicada2 on 2015-02-14
I ran the sudo to install, but I don't see Mplayer anywhere (obvious). It may be that I'm just a newbee or maybe something went sideways? For sure it looks like the flac command was a fail. Here's the printout from my terminal...

```
cicada@cicada-Presario-R3000-DS514U-ABL:~$ sudo apt-get install mplayer
[sudo] password for cicada: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  esound-common libaudiofile1 libesd0 libmpeg2-4 libsvga1 libx86-1
Suggested packages:
  pulseaudio-esound-compat mplayer-doc netselect fping
The following packages will be REMOVED:
  mplayer2
The following NEW packages will be installed:
  esound-common libaudiofile1 libesd0 libmpeg2-4 libsvga1 libx86-1 mplayer
0 upgraded, 7 newly installed, 1 to remove and 0 not upgraded.
Need to get 2,896 kB/2,951 kB of archives.
After this operation, 4,180 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ trusty/main libaudiofile1 i386 0.3.6-2 [115 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ trusty/main esound-common all 0.2.41-11 [9,558 B]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ trusty/main libesd0 i386 0.2.41-11 [16.3 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu/ trusty/main libx86-1 i386 1.1+ds1-10 [81.7 kB]
Get:5 http://ca.archive.ubuntu.com/ubuntu/ trusty/universe libsvga1 i386 1:1.4.3-33 [289 kB]
Get:6 http://ca.archive.ubuntu.com/ubuntu/ trusty/universe mplayer i386 2:1.1+dfsg1-0ubuntu3 [2,385 kB]
Fetched 2,896 kB in 6s (420 kB/s)                                              
Selecting previously unselected package libaudiofile1:i386.
(Reading database ... 142702 files and directories currently installed.)
Preparing to unpack .../libaudiofile1_0.3.6-2_i386.deb ...
Unpacking libaudiofile1:i386 (0.3.6-2) ...
Selecting previously unselected package esound-common.
Preparing to unpack .../esound-common_0.2.41-11_all.deb ...
Unpacking esound-common (0.2.41-11) ...
Selecting previously unselected package libesd0:i386.
Preparing to unpack .../libesd0_0.2.41-11_i386.deb ...
Unpacking libesd0:i386 (0.2.41-11) ...
Selecting previously unselected package libmpeg2-4:i386.
Preparing to unpack .../libmpeg2-4_0.5.1-5ubuntu1_i386.deb ...
Unpacking libmpeg2-4:i386 (0.5.1-5ubuntu1) ...
Selecting previously unselected package libx86-1:i386.
Preparing to unpack .../libx86-1_1.1+ds1-10_i386.deb ...
Unpacking libx86-1:i386 (1.1+ds1-10) ...
Selecting previously unselected package libsvga1:i386.
Preparing to unpack .../libsvga1_1%3a1.4.3-33_i386.deb ...
Unpacking libsvga1:i386 (1:1.4.3-33) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
dpkg: mplayer2: dependency problems, but removing anyway as you requested:
 gnome-mplayer depends on mplayer2 | mplayer; however:
  Package mplayer2 is to be removed.
  Package mplayer is not installed.
  Package mplayer2 which provides mplayer is to be removed.
 gnome-mplayer depends on mplayer2 | mplayer; however:
  Package mplayer2 is to be removed.
  Package mplayer is not installed.
  Package mplayer2 which provides mplayer is to be removed.

(Reading database ... 142767 files and directories currently installed.)
Removing mplayer2 (2.0-701-gd4c5b7f-2ubuntu2) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Selecting previously unselected package mplayer.
(Reading database ... 142761 files and directories currently installed.)
Preparing to unpack .../mplayer_2%3a1.1+dfsg1-0ubuntu3_i386.deb ...
Unpacking mplayer (2:1.1+dfsg1-0ubuntu3) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up libaudiofile1:i386 (0.3.6-2) ...
Setting up esound-common (0.2.41-11) ...
Setting up libesd0:i386 (0.2.41-11) ...
Setting up libmpeg2-4:i386 (0.5.1-5ubuntu1) ...
Setting up libx86-1:i386 (1.1+ds1-10) ...
Setting up libsvga1:i386 (1:1.4.3-33) ...
Setting up mplayer (2:1.1+dfsg1-0ubuntu3) ...
Processing triggers for libc-bin (2.19-0ubuntu6.5) ...
cicada@cicada-Presario-R3000-DS514U-ABL:~$ mplayer music_file.flac
Creating config file: /home/cicada/.mplayer/config
MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing music_file.flac.
File not found: 'music_file.flac'
Failed to open music_file.flac.


Exiting... (End of file)


```

---

### Post by tgalati4 on 2015-02-15
Try using a real music file.  music_file.flac is a suggestion.  Let's assume your music is in /Music:

```
cd
cd Music
ls -la
mplayer try_a_real_music_file.flac
```

---

### Post by Dennis N on 2015-02-15
You are using Audacious, not Audacity. (The version number you give is for Audacious) 

Audacity is an audio tool for recording and editing - it's not intended to be used as a general music player. 

Audacious uses its default plugins (automatically installed) to support these formats:

 * Audio CD reading
  * MPEG support (mp3)
  * Ogg Vorbis support
  * Windows Media support (WMA)
  * AAC support
  * FLAC support
  * ALAC support
  * WAVE support

FLAC support is by default, so you don't need to install anything else. Is there evidence that the file is playing, such as the time counter advances, the progress bar is moving, and activity in the info bar? If so, sound could be muted or set extremely low. Check all volume levels. Check the settings in alsamixer to be sure sound is not muted in master or PCM. Run alsamixer from the terminal to check this. Do other types of files, such as mp3, play? It could also be that a particular file is unplayable - unreadable or corrupted content.

Also, when  you installed mplayer, the package manager removed mplayer2, which may not have been a good idea - time will tell.

---

### Post by tgalati4 on 2015-02-15
Either mplayer or mplayer2 should work.  At least you get some diagnostic information in the terminal:

Let's fix it:

```
sudo apt-get install mplayer2
cd
cd Music
ls *.flac
mplayer *.flac
```

Yes, I presumed *audacious* as well; I don't know how to get messages from *audacious*.

Try playing your file in *audacious* and hit Control-I to get information.  What does format, quality, and bitrate show?

---

### Post by cicada2 on 2015-02-15
Hello and thanks for the feedback. I am trying to play files in ***Audacious*** (not Audacity). My apologies to all. 

DennisN -The time counter doesn't move/ no activity in the progress bar. This is not a volume issue. I can't recall any other format like mp3 for music I have in my archives, except shn or some ripped WAV's. I'll poke around and see if I can find something else in my archives to use.

Thanks to Tgalati4... I did try running a real flac file in the terminal. The terminal is running and endless loop with this result

```
Trying to reset soundcard.
Write error: brioken pipe
```

Regarding mplayer... how to start the program? Is it only run in the terminal? I haven't been able to try it outside of the terminal.

---

### Post by oldos2er on 2015-02-15
Changed thread title to "Audacious...."

---

### Post by mc4man on 2015-02-15
I don't use Lubuntu but do remember a couple of times when testing  that the sound settings were wrong by default. So maybe check in audacious > File > Settings > Audio or in lubuntu's sound settings

---

### Post by Dennis N on 2015-02-15
> DennisN -The time counter doesn't move/ no activity in the progress bar. This is not a volume issue. I can't recall any other format like mp3 for music I have in my archives, except shn or some ripped WAV's. I'll poke around and see if I can find something else in my archives to use.


I get the impression you have never played any audio on this system, since all you have are the (unplayable) flac files?? 

To test the general playability of one of those files, just double click on the file name and it will open the default player for that file type. On my Lubuntu 14.04, double clicking on a flac file opens and starts playing it in GNOME-MPlayer, which is the default player for flac (and for mp3 and ogg as well) in Lubuntu. What happens for you?

If you need to, download an mp3 file or two from the internet and use those for a test in Audacious. Inform us of the results. Millions of those files around.

---

### Post by cicada2 on 2015-02-15
I converted a set of these flacs to WAV and mp3, then I opened in audacious. They played fine. So, I tried them in Gnome Mplayer. And, they played fine. 
So, I tried playing flacs in both players andpresto chango... they are now playing fine. Seems strange, so strange. However, I am up and running. Thanks for the support!!

---

### Post by cicada2 on 2015-02-15
Periodically, audacious "hangs". It just stalls for 30 seconds or more. After a bit, it starts where it left off. I checked preferences and the buffer sizewas set for 500 ms. Should I tweak this or maybe something else? 

I will experiment with Mplayer to see if the same problem arises. Could be this this old laptop (maybe my chipset or the radeon card - sigh).

---

### Post by cicada2 on 2015-02-15
Now it's not restarting. The system hangs and the only way out is to force a shutdown and reboot. Mplayer hangs worse than Audacious.

I recently converted this old laptop over from XP to Lubuntu 14.04. I was not having issues until I started playing music. I know it's an old model laptop, but I want to see if I can keep it working.

---

### Post by tgalati4 on 2015-02-16
If your hard disk is failing then playing back flac could be a problem because the disk can't keep up with the speed needed send the data for decoding.  Using mp3 is easier on the disk because the file size is smaller but uses more CPU power.  It's possible that your disk drive is just not fast enough to feed a flac file.

---

### Post by cicada2 on 2015-02-17
This computer played FLAC fine for years. But, it started stuttering a  while back. I figured it was just bogged down due to the XP madness.  That is one of the main reasons I went to Ubuntu - I wanted to see if I  could listen to music while working on this computer (once again). So far, I can go  for weeks with no system "hang" as long as I don't play music. But, once  I started playing music files, the system just locks up. I don't have  any interest in converting all my music to mp3, so I hope I can find  some other way to resolve this issue.

---

### Post by tgalati4 on 2015-02-17
Play a flac file then open a terminal and examine the output of:

```
dmesg | tail -50
```

Only post errors, not the whole output.

---

### Post by cicada2 on 2015-02-17
I think this is the error I'm looking to find. It wasn't there until Audacious got hung up.

[HTML][  756.088821] usb 1-3.1.2: reset high-speed USB device number 10 using ehci-pci
[ 1205.096366] usb 1-3.1.2: reset high-speed USB device number 10 using ehci-pci
[ 1248.104381] usb 1-3.1.2: reset high-speed USB device number 10 using ehci-pci
[ 1279.144919] usb 1-3.1.2: reset high-speed USB device number 10 using ehci-pci
[ 1310.120483] usb 1-3.1.2: reset high-speed USB device number 10 using ehci-pci
[ 1341.097053] usb 1-3.1.2: reset high-speed USB device number 10 using ehci-pci
[ 1372.136586] usb 1-3.1.2: reset high-speed USB device number 10 using ehci-pci[/HTML]

---

### Post by Holger_Gehrke on 2015-02-18
The next step is obvious: find out what USB device is having trouble. Do the same thing again and check the output of 'lsusb' for the device with the number in the error message. It could be a failing device or it could be something trivial like a bad cable or bad mechanical connection.

---

### Post by tgalati4 on 2015-02-18
It could be your USB controller chipset is failing.  Every 30 seconds or so, it gets hot and needs to be reset.  Try disconnecting all of your USB devices and see if your music-playing performance improves.

---

