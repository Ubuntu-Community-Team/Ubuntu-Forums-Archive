---
title: "Repositories To Install W32Codecs"
date: 2006-12-11
forum: General Help
---

### Post by MeltdownMX on 2006-12-11
Hi All,

This is my first post.  I wanted to start off by thanking everyone involved with Ubuntu from creating it, developing it further, and all those who support it.  I have been using it for the last 2 weeks and while it has been challenging to get things to work, it has also been fun learning and the experience is 100000 times better than when I played around with RedHat 6.0 six or seven years ago.

Anyway, to make a long story short while trying to get all my media files working from WindozeXP I wound up doing something to my system that causes some MPEGS in totem to display video and no sound.  It also has disabled my sound while viewing movies on YouTube.

What I did was Install XINE.  This wouldnt run on my XGL session, so I then installed MPlayer.  Some AVI files wouldnt run right, so I then Installed the VLC media player.  This works perfect.  It runs EVERYTHING I needs, AVIs, MPEGs, MP3s this is great, but its still not the default player and I cant just launch MP3s by clicking on them etc.  When I do, Totem runs and then will throw up any of the following errors.

> Audio codec 'MPEG 1 Layer 3 VBR' is not handled.
> Audio codec 'MPEG 1 Layer 3 CBR' is not handled.
> Video codec 'Microsoft MPEG-4 v3' is not handled.

I think when I removed some packages when I was installing xine, MPlayer, and VLC, that I removed the w32codecs :confused:   To make sure that I had the codecs, I tried installing them again.  But they are no where to be found (not even present in the Synaptic Package Manager), which brings me to the title of this Thread.

From what I have found so far, the repository which has the w32codec is the [Penguin Liberation Front]("http://plf.zarb.org/") and according to that page the Ubuntu repositories arent being mainatined and are down.

I have seen this thread, but it isnt any help.  [http://ubuntuforums.org/showthread.php?p=1686584]("http://ubuntuforums.org/showthread.php?p=1686584")

There is still a 404 error, no matter what repository or mirror you put in for the PLF.

Does anyone know a different repository where I can get the w32codecs for Ubuntu Edgy Eft?  Thanks in advance.

---

### Post by hikaricore on 2006-12-11
They have only been down since like Friday and they've already got a new maintainer who will be solving this issue soon.

You could try debian multimedia (or one of the many mirrors)

## Debian Multimedia
deb [http://mirror.home-dn.net/debian-multimedia](http://mirror.home-dn.net/debian-multimedia) stable main
deb-src [http://mirror.home-dn.net/debian-multimedia](http://mirror.home-dn.net/debian-multimedia) stable main

deb [http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia](http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia) stable main
deb-src [http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia](http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia) stable main

deb [http://floating3.ucd.ie/debian](http://floating3.ucd.ie/debian) stable main
deb-src [http://floating3.ucd.ie/debian](http://floating3.ucd.ie/debian) stable main

deb [http://debian-multimedia.dfoell.org/](http://debian-multimedia.dfoell.org/) stable main

deb [http://debian-multimedia.gnali.org](http://debian-multimedia.gnali.org) stable main
deb-src [http://debian-multimedia.gnali.org](http://debian-multimedia.gnali.org) stable main

deb [http://debian.dc-uoit.net/debian-multimedia/](http://debian.dc-uoit.net/debian-multimedia/) stable main

deb [http://mirrors.ecology.uni-kiel.de/debian/debian-multimedia](http://mirrors.ecology.uni-kiel.de/debian/debian-multimedia) stable main
deb-src [http://mirrors.ecology.uni-kiel.de/debian/debian-multimedia](http://mirrors.ecology.uni-kiel.de/debian/debian-multimedia) stable main

deb [http://ftp.mgts.by/debian-multimedia/](http://ftp.mgts.by/debian-multimedia/) stable main
deb-src [http://ftp.mgts.by/debian-multimedia/](http://ftp.mgts.by/debian-multimedia/) stable main

deb [http://debian.netcologne.de/debian-multimedia.org](http://debian.netcologne.de/debian-multimedia.org) stable main
deb-src [http://debian.netcologne.de/debian-multimedia.org](http://debian.netcologne.de/debian-multimedia.org) stable main

deb [http://debian.three-dimensional.net/debian-multimedia](http://debian.three-dimensional.net/debian-multimedia) stable main
deb-src [http://debian.three-dimensional.net/debian-multimedia](http://debian.three-dimensional.net/debian-multimedia) stable main


But like I said I can't promise they're there, just might be one place to try.

---

### Post by xabbott on 2006-12-11
From [this]("https://help.ubuntu.com/community/RestrictedFormats#w32codecs") page:

wget -c [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb)
sudo dpkg -i w32codecs_20061022-0.0_i386.deb

---

### Post by MeltdownMX on 2006-12-11
Cool, Thanks xabbott & hikaricore.

Figures.  It must be just me!  The same thing happened when I first installed Ubuntu and was trying to install Beryl and those were also down due to a server crash.  Here I am trying to read all these tutorials and they werent working thinking I was doing something wrong.  Its good though.  Learn more that way!

Well I did as xabbott suggested, and it worked!  w32codecs installed, but I am still getting the same error messages in Totem when launching an MP3 and still no sound with Flash movies (YouTube)

Guess it wasnt the codecs?

---

### Post by az on 2006-12-11
> **MeltdownMX said:**
> 
Well I did as xabbott suggested, and it worked!  w32codecs installed, but I am still getting the same error messages in Totem when launching an MP3 and still no sound with Flash movies (YouTube)

Guess it wasnt the codecs?

Totem, by deafult, uses the gstreamer backed.  You can install totem-xine to make totem use the w32codecs.  Read the RestrictedFormats page as mentioned.

As for Flash, what version of the flash player are you using?  The second Beta for the flash 9 plugin seems to have solved some sound issues.

---

### Post by MeltdownMX on 2006-12-11
> Totem, by deafult, uses the gstreamer backed. You can install totem-xine to make totem use the w32codecs. Read the RestrictedFormats page as mentioned.

I believe as part of my installing xine that the totem-gstreamer was removed?  (It all happened so fast!) :) 

> As for Flash, what version of the flash player are you using? The second Beta for the flash 9 plugin seems to have solved some sound is

You know, come to think of it, I have installed Ubuntu so many times over the last few weeks (mostly due to getting my ATI drivers right. I have killed X server so many times!!)  I think I followed a tutorial on installing it one time, but I think the last time I installed it, I did it through firefox.

Can you recommend instructions on installing the 2nd Beta?  Also, how do you change file associations so that VLC media, is the default player instead of Totem?  Maybe that will help?

---

### Post by MeltdownMX on 2006-12-11
Found the answer to my Flash Beta 2 Question

[How_to_update_to_Flash_Player_9_Beta_2]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_update_to_Flash_Player_9_Beta_2_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox")

Okay, This fixed my problem with sound in Flash !!!  Sweet, except now I still have these errors with Totem.  Any ideas?  Ive googled them with not much success.

> 
Audio codec 'MPEG 1 Layer 3 VBR' is not handled.
Audio codec 'MPEG 1 Layer 3 CBR' is not handled.
Video codec 'Microsoft MPEG-4 v3' is not handled.

---

### Post by MeltdownMX on 2006-12-12
Okay, update to last nights posts.

Everything is working!!!!   I dont know what the hell I did?!?!?!?!

I do know this.  I went to the [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats") page and was going to kind of "start over" from there.

I went into synaptic and installed ALL of the gstreamer0.08 packages, then all of the gstreamer0.10 packages.  Nothing was working.  Then I removed all of the ones that wouldnt remove the ubuntu-desktop, totem, and all of the other default players that come standard.  I left the w32codecs alone at this point.  Still NOTHING was working.  I was getting some CRAZY results too.  I got the error messages to go away in Totem and it would show visualizations no problem like it was playing the file, but the time would also go really fast like in double time and sometimes it would skip a few numbers and go from 1:23 to 1:25, then 1:26 in the matter of 1/2 a second. :evil:  It was getting late and I said screw it, ill mess with it after work tomorrow.

So here I am.  I come home getting ready to go through the Restricted Formats page step by step and I have no idea why, but I clicked on an MP3.  Totem opened it fine!  It played with NO PROBLEMS.  After that i decided to open up all my other media in its various formats AVI, MPG, MPEG, and THEY ALL RAN FINE!!!   I didnt do anything and it fixed itself!  :-k 

No idea what happened, just thought I would share in case anyone else has the same problem.  Thanks!

---

