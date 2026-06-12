---
title: "No sound in vlc ?"
date: 2005-03-22
forum: General Help
---

### Post by PaTTeX on 2005-03-22
hi guys (sorry for my bad english)

when i launch a movie in vlc/mplayer i have the video but no sound ...

I chose in audio preferences ESD

but i have this error

```
/dev/dsp: Device or resource busy
[00000275] esd audio output error: cannot open esound socket (format 0x00001021 at 44100 Hz)
[00000275] oss audio output error: cannot open audio device (/dev/dsp)

```
any idea  ](*,) 

thx in advance

---

### Post by occy8 on 2005-03-22
Hello,
I'm having a similar problem. I can play Quicktime movies in Totem, but when it is started in Mozilla as plugin using **mozilla-plugin-vlc (0.8.1-1ubuntu1)**
I can see the movie but there is no sound.

---

### Post by garyng on 2005-03-22
you need a esound server on the machine running the vncviewer. But that is not enough, you also need to :

export ESPEAKER=<ip>:<port>

this much match your esound server. 

Unfortunately, I don't know an easy way to do this BEFORE the GNOME session start.

For quick fix, open a terminal and do the above then run applications that support esound(in that same terminal session).

---

### Post by bored2k on 2005-03-22
[QUOTE=occy8]Hello,
I'm having a similar problem. I can play Quicktime movies in Totem, but when it is started in Mozilla as plugin using **mozilla-plugin-vlc (0.8.1-1ubuntu1)**
I can see the movie but there is no sound.[/QUOTE]
 Use totem for streaming
[http://ubuntuforums.org/showthread.php?t=17727&highlight=mozplugger](http://ubuntuforums.org/showthread.php?t=17727&highlight=mozplugger)

---

### Post by occy8 on 2005-03-23
> Use totem for streaming
[http://ubuntuforums.org/showthread....ight=mozplugger](http://ubuntuforums.org/showthread....ight=mozplugger) 


Thanks that worked well.

---

### Post by irkab1rka on 2005-07-23
the codecs can be found in 'universe' or 'multiverse' section. Which means: :)

sudo vim /etc/apt/sources.list
# add this line to the end of the file:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
# exit from vim by: [esc]wq 
# if you can not save the file then you are not the root user. I wrote: 'sudo' above! :)
# now you are ready to update the list of available packages
apt-get update
# so why not download and install the xine package for totem movie player?
apt-get install totem-xine
# now you should be ready to play most of the movies with sound.

please let me know if i was not correct. I installed a lot of stuff before i got sound played by ubuntu 5.04 (xmms, mplayer, xine-lib,...) which was not working but you now: devil never sleeps

---

