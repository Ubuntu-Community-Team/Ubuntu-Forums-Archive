---
title: "No MP3's ???"
date: 2005-10-17
forum: General Help
---

### Post by shane2peru on 2005-10-17
Hey, I'm a newbie to Ubuntu, and still a newbie to Linux.  I have installed amarok, and tried the other probrams that were already installed.  I'm unable to play MP3 files??? Any ideas?  What am I missing?  Thanks.

---

### Post by aysiu on 2005-10-17
You're missing codecs:

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)
[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

Install all the codecs that have the word *lame* in them.

---

### Post by Dr. Nick on 2005-10-17
enable universe repository from synaptic or by editing /etc/apt/sources.list. the "run apt-get update" and download the gstreamer packages, espicially gstreamer0.8-mad. Search the forum as I know several people have posted more detailed descriptions


EDIT
Hehe took me to long to reply, the above works to.

---

### Post by shane2peru on 2005-10-17
aysiu,

Ok, I updated my sources list.  And then tried the next step.  I cut and pasted these,
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install w32codecs
sudo apt-get install libdivx4linux
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
gst-register-0.8

and everytime it comes to install Y/n  I tried Y and y and n and everytime it aborts??? I don't know why Help!  Thanks.

Shane

---

### Post by ecobuntu on 2005-10-17
[QUOTE=shane2peru]aysiu,

Ok, I updated my sources list.  And then tried the next step.  I cut and pasted these,
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install w32codecs
sudo apt-get install libdivx4linux
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
gst-register-0.8

and everytime it comes to install Y/n  I tried Y and y and n and everytime it aborts??? I don't know why Help!  Thanks.

Shane[/QUOTE]



sudo apt-get install akode-mpeg

As well!
Strange that it should abort.  Try it again using Synaptic

---

### Post by aysiu on 2005-10-17
Well, first of all, for MP3s, I think you just need these: ```
sudo apt-get install gstreamer0.8-lame
sudo apt-get install lame
``` Can you cut and paste what the abort looks like?

---

### Post by bluck on 2005-10-17
[QUOTE=shane2peru]aysiu,

Ok, I updated my sources list.  And then tried the next step.  I cut and pasted these,
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install w32codecs
sudo apt-get install libdivx4linux
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
gst-register-0.8

and everytime it comes to install Y/n  I tried Y and y and n and everytime it aborts??? I don't know why Help!  Thanks.

Shane[/QUOTE]

as a side note, you dont need to install each package with a separate command,  you can install them like `sudo apt-get install pkg1  pkg2  pkg3 ...`

i know it doesnt help your problem, but at least you'll type less :)

---

### Post by ecobuntu on 2005-10-17
[QUOTE=aysiu]Well, first of all, for MP3s, I think you just need these: ```
sudo apt-get install gstreamer0.8-lame
sudo apt-get install lame
``` Can you cut and paste what the abort looks like?[/QUOTE]

Are you sure?  I couldn't use mp3 then I installed akode-mpeg and it worked for me.

---

### Post by Stormy Eyes on 2005-10-17
[QUOTE=aysiu]Well, first of all, for MP3s, I think you just need these: ```
sudo apt-get install gstreamer0.8-lame
sudo apt-get install lame
``` Can you cut and paste what the abort looks like?[/QUOTE]

You got this one, aysiu? Or should I pounce if I notice him posting further details before you do?

---

### Post by shane2peru on 2005-10-17
Synaptic?  I'm not sure how to use that.  Is that a GUI or cli?  I like GUI, but can use cli a little too.  Thanks for the help.

Shane

---

### Post by shane2peru on 2005-10-17
shane@ubuntu:~$ sudo apt-get install gstreamer0.8-lame
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  liblame0
The following NEW packages will be installed:
  gstreamer0.8-lame liblame0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 187kB of archives.
After unpacking 504kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.

I have tried Y and I have tried y.  Any idea?  Thanks.

Shane

---

### Post by aysiu on 2005-10-17
It's GUI. See the second link in my sig for a tutorial.

---

### Post by shane2peru on 2005-10-17
Ok, I tried the synaptic thing.  That was pretty easy.  I installed all of them, do I need to restart the computer because it still doesn't work.  One more thing, there was one that didn't install right or something.  I don't remember, and just continued.  I don't know exactly what it was.  Thanks for the help.

Shane

---

### Post by Qrk on 2005-10-17
Don't press y. Just hit enter. 

I know you've finished, but for future reference. I can't use y either. I have no idea why (y?)

---

### Post by ecobuntu on 2005-10-17
[QUOTE=shane2peru]Synaptic?  I'm not sure how to use that.  Is that a GUI or cli?  I like GUI, but can use cli a little too.  Thanks for the help.

Shane[/QUOTE]

Synaptic is a GUI and should be under System -> Administration -> Synaptic Package Manager

Just search for the files that you've been instructed to install under Synaptics Search button.  

It's possible the repositories you're trying to get the files from are not working...check out this thread if it happens to you.

[http://ubuntuforums.org/showthread.php?t=78010](http://ubuntuforums.org/showthread.php?t=78010)

---

### Post by ecobuntu on 2005-10-17
You shouldn't need to reboot.  

at terminal:  killall-artsd
that should do the trick!

---

### Post by raublekick on 2005-10-18
click on System -> Preferences -> Multimedia Systems Selector

For me it was set on OSS and ESD by default. Setting both options to ALSA got sound working in all programs.

---

### Post by shane2peru on 2005-12-06
Ok, all this seemed to fix it.  I have had to re-install Ubuntu, and found this thread that I left open and never finished.  I re-read through it and got my MP3's to play.  The only thing that didn't work was the killall-artsd  It didn't find this command.  Oh well, it works.  Thanks for the input guys.  Sorry for such a long delay!

Shane

---

