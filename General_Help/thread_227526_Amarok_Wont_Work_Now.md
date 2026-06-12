---
title: "Amarok Wont Work Now"
date: 2006-08-01
forum: General Help
---

### Post by Roasted on 2006-08-01
Things just get better and better. I was using a site to find the proper repository settings and all of the commands to install certain programs. Now all of the sudden, my media players don't work. Amarok says "unable to load media (non playable)."

I had less trouble with Windows. What the hell is going on?!!??

---

### Post by croak77 on 2006-08-01
What are you trying to play? mp3, ogg, etc. What engine are you using? xine? Does any other player work?

---

### Post by Roasted on 2006-08-01
MP3 format. Just Amarok.

---

### Post by croak77 on 2006-08-01
With Xine right? Are all of these packages installed?

 libxine-extracodecs 
 w32codecs 
 libarts1-mpeglib 
 libarts1-xine 
 libakode2-mpeg

---

### Post by croak77 on 2006-08-01
BTW, what directions did you follow?

---

### Post by Roasted on 2006-08-01
I installed a few things from this site. Java, Adobe Reader, etc.

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28amaroK.29](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28amaroK.29)

How do I tell if I have those things installed?

---

### Post by croak77 on 2006-08-01
If you have Synaptic or Adept installed you can view all installed packages or search for each one and see if it is installed.

---

### Post by Roasted on 2006-08-01
> **croak77 said:**
> With Xine right? Are all of these packages installed?

 libxine-extracodecs 
 w32codecs 
 libarts1-mpeglib 
 libarts1-xine 
 libakode2-mpeg


I only have libxine-extracodecs and libarts1-xine

---

### Post by croak77 on 2006-08-01
> **Roasted said:**
> I only have libxine-extracodecs and libarts1-xine

Try installing the others and see if that helps. For the w32codecs, open a terminal;

```
wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb
sudo dpkg -i w32codecs_20060611-0.0_i386.deb
```

---

### Post by Roasted on 2006-08-01
It's not that they weren't installed. They're just flat out not listed. I don't know HOW to install them if they're not listed...

The two commands you posted above didn't help Amarok. Same problem.

---

### Post by croak77 on 2006-08-02
Go Here:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

If you don't know how to install software or manage repositories, follow the links in the 'Before You Start' section.

---

### Post by Roasted on 2006-08-02
On this one site with embedded movies, it used to run mplayer to play then. Now, this morning, when I go to that site it has a black screen over where the video is and says in white letters - gxine browser plugin.

Then another window opens. This window is gxine 0.5.1 or something, and plays the video.

Did I kick mplayer off the list?

---

