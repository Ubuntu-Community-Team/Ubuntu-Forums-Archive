---
title: "GIMP (and Ubuntu in general) has become unbearably slow..."
date: 2014-05-13
forum: General Help
---

### Post by luis_valdivieso2 on 2014-05-13
And I do mean unbearably  slow. For instance: if I undo or zoom, it can sometimes take 2-3 seconds  or more to apply the changes. And when I change the transparency of a  layer, I can't see the immediate result, I have to click on the work  space first, then the changes will apply. This alone makes it incredibly  annoying to work but on top of all that it also generally lags a lot even  if I restart the program. And no, it's not because of the image  size/number of layers. It does the same thing with small files.

What I have done to try and fix this:

-Disabled colour management
-Cleared all undo history
-Changed the tile cache to 4-5GB as recommended by other Gimp users

None  of the above seem to have corrected my issues. Therefore, I believe the  problem is Ubuntu related and not Gimp related. Or rather, some  installations/changes/deletions that I've made recently to optimize  Ubuntu but that are now causing Gimp to run this slow.

What I've done recently that might've caused this:

I tried to install a bunch of stuff because I was hoping to use ffmpeg:

```

sudo apt-get update
sudo apt-get -y install autoconf automake build-essential libass-dev libfreetype6-dev libgpac-dev \
  libsdl1.2-dev libtheora-dev libtool libva-dev libvdpau-dev libvorbis-dev libx11-dev \
  libxext-dev libxfixes-dev pkg-config texi2html zlib1g-dev
mkdir ~/ffmpeg_sources
```
I installed Yasm, libx264, libfdk-aac, libmp3lame, libopus and ffmpeg. Basically a bunch of video and audio encoders.

Since  my ffmepg adventure resulted in a bunch of errors and I later learned  that most of what I installed was obsolete, I wanted to uninstall most  of the stuff that was now considered useless. So I followed some guide  to keep Ubuntu clean. I did the following:

Cleaning up of partial package: sudo apt-get autoclean

Cleaning up of the apt cache: sudo apt-get clean

Cleaning up of any unused dependencies: sudo apt-get autoremove

And finally, I installed gtkorphan to remove ALL orphaned packages.


That's  about it for the recent changes I made. I also uninstalled a bunch of  programs I didn't need anymore like Avidemux, RythmBox, Banshee,  Solitaire games, etc. But nothing important. 

So what is it that  is now causing GIMP to run this slow? And what can I do to fix this?  Please help. It's so bad that I'm almost considering going back to  Windows lol.

---

### Post by luis_valdivieso2 on 2014-05-13
Actually Ubuntu seems much slower as well. It's not just Gimp. I noticed it in Gimp first but now basic tasks like opening up the home folder or minimizing the firefox window are now laggy.

I've also noticed strange things like having 2x firefox icons and 2x gimp icons in the Launcher. Those duplicate icons don't do anything and I can't seem to unlock them.

I'll try to provide additional information:

Ubuntu 12.04 (precise) 64-bit

System Monitor says that the memory I'm using is: 2.6GB of 5.8GB. And I'm using 75% of sda3 but I still have 70-90+GB left of unused space in sda3. (and 306+GB of free space in another sda)

Currently scanning with Disk Usage Analyzer..

EDIT: Well, I installed some updates and restarted my CPU and now everything seems to run smooth. So problem solved I guess...

---

