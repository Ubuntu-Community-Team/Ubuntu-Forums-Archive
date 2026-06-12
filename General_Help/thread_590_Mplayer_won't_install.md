---
title: "Mplayer won't install"
date: 2004-10-14
forum: General Help
---

### Post by williamroddy on 2004-10-14
I've tried to install mplayer, via ft-p nirum, after installing the new release candidate. Before, I was successful. Now, I get the following stop:


mplayer-586:
 Depends: libartsc0 but it is not going to be installed
 Depends: libggi2 but it is not going to be installed
  Depends: libungif4g but 4.1.0b1-6 is to be installed

You have a WONDERFUL distribution. I just love it. I'd appreciate help on the MPlayer issue. Thank you.

---

### Post by adbak on 2004-10-14
Will - 

I had this same problem last night, but thanks to my friend and Linux fairy, it's now thought to be because of an update scheduled sometime very recently.  I'm pretty much a newb when it comes to Linux, but because we caught the upgrade on the cusp, we aren't able to install it.  And because of all the patents it breaks, I doubt we'll be seeing an ubuntu version.

---

### Post by williamroddy on 2004-10-14
I finally figured out how to get it on. I didn't want to mess up Ubuntu with a lot of unnecessary Debian upgrades, so I put

# Primary

deb [ftp://ftp.us.debian.org/debian/](ftp://ftp.us.debian.org/debian/) testing main contrib non-free 
deb-src [ftp://ftp.us.debian.org/debian/](ftp://ftp.us.debian.org/debian/) testing main contrib non-free 
deb [ftp://ftp.us.debian.org/debian/](ftp://ftp.us.debian.org/debian/) unstable main contrib non-free 
deb-src [ftp://ftp.us.debian.org/debian/](ftp://ftp.us.debian.org/debian/) unstable main contrib non-free 

# non-us

deb [ftp://non-us.debian.org/debian-non-US/](ftp://non-us.debian.org/debian-non-US/) testing/non-US main contrib non-free 
deb-src [ftp://non-us.debian.org/debian-non-US/](ftp://non-us.debian.org/debian-non-US/) testing/non-US main contrib non-free 
deb [ftp://non-us.debian.org/debian-non-US/](ftp://non-us.debian.org/debian-non-US/) unstable/non-US main contrib non-free 
deb-src [ftp://non-us.debian.org/debian-non-US/](ftp://non-us.debian.org/debian-non-US/) unstable/non-US main contrib non-free 
deb [http://download.videolan.org/pub/videolan/debian/](http://download.videolan.org/pub/videolan/debian/) sid main 

# mplayer

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

into the sources list, did an update, did an apt-get on mplayer-586, and got the whole download of packages installled. Then I shut off the extra sources, so I wouldn't sully Ubuntu any more than that.

Hope you can use that, or you have some better way. Thanks for your comments. I appreciate them.

Wil

---

### Post by adbak on 2004-10-14
I tried your trick but wasn't able to download mplayer.  I should try again, this time shutting off all of the previous Ubuntu sources and using only the ones in your list.

Or is there any other way for this to work?

---

### Post by williamroddy on 2004-10-15
Sometimes, if you go into Synaptic and chose a setting, it works:
synaptic&gt;settings&gt;expert   and chance ignore to unstable. Then reload and update from synaptic.

You can also turn sources off and on in synaptic.

Turning the off and on there shuts them on or off in apt.

Making other adjustments sometimes only applies to synaptic.

But once you get what you want installed, shut the extra sources down again, because Unbuntu works pretty darn good without them.

Good luck,
Wil

---

### Post by Perfect Storm on 2004-10-15
Check here: [http://ubuntuforums.org/viewtopic.php?t=112](http://ubuntuforums.org/viewtopic.php?t=112)

---

### Post by jBilbo on 2004-10-20
[http://www.ubuntuforums.org/viewtopic.php?t=1379](http://www.ubuntuforums.org/viewtopic.php?t=1379)

---

