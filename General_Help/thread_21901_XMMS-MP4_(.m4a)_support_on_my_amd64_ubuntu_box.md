---
title: "XMMS-MP4 (*.m4a) support on my amd64 ubuntu box?"
date: 2005-03-24
forum: General Help
---

### Post by zaubara on 2005-03-24
Hey there :)

Yesterday, I installed ubuntu 5.04 on my amd64 machine and I like it a lot so far. But I want to be able to play my .m4a files, imported from my Ipod, which work fine on my mac!

I installed the XMMS plugin, but starting XMMS returns this:

libmp4v2.so.0: cannot open shared object file: No such file or directory

After hours of googling, I found MPEG4IP to be missing, which is not on any ubuntu source. I had to compile it for myself. I installed everything needed and it stops making with some strange error at the server module, so I made it again without the server; in the libs folder, I found a libmp4v2.so.0.0.0 which i copied to /lib/libmp4v2.so.0.

Starting XMMS now returns this error:
/usr/lib/xmms/Input/libmp4.so: undefined symbol: MP4GetTrackAudioType

Playing *.m4a's still doesnt work. :(
Is anyone of you already able to play such files??

Thanks for all of your support! ;)
zaubara

---

### Post by zaubara on 2005-03-25
Wellwell ...
I reinstalled ubuntu, added this repository:

[http://cyberspace.ucla.edu/marillat](http://cyberspace.ucla.edu/marillat) unstable main

reinstalled a few programmes and now it works flawlessly. :)
Just in case you wanted to know.

---

### Post by ChaperonNoir on 2005-03-25
Hey dude 

Im trying like you to get AAC support. I have an ipod so i have countless AAC files.

Im using rhythmbox.

Your repository works fine , installed gstreamer0.8-faad perfect but after this, it tells me to run gs-register ?

But i dont have this command ?

At the moment, i lost all my plugins :S

EDIT

Thanx google, i got all my plugins back using gst-register0.8 :)

But i still cant play the AAC files :9

Could not decode stream blablablalbal

---

### Post by zaubara on 2005-03-25
[QUOTE=ChaperonNoir]Hey dude 

Im trying like you to get AAC support. I have an ipod so i have countless AAC files.

Im using rhythmbox.

Your repository works fine , installed gstreamer0.8-faad perfect but after this, it tells me to run gs-register ?

But i dont have this command ?

At the moment, i lost all my plugins :S

EDIT

Thanx google, i got all my plugins back using gst-register0.8 :)

But i still cant play the AAC files :9

Could not decode stream blablablalbal[/QUOTE]
 Well, I was cheering too fast i guess... :/

Rhytmbox is for me a no-go, too :(

Thats what XMMS tells me:

2-MPEG-4 AAC Low Complexity profile
MP4 - 2 channels @ 44100 Hz
MP4: Pulse coding not allowed in short blocks

Dunno what that means, someone I found on google stated that this was a bug in faad2 fixed a long time ago ...


// edit:

What I now did was installing BMP (apt-get install beep-media-player beep-media-player-dev), compiling the plugin for BMP from this page: [http://fondriest.frederic.free.fr/realisations/](http://fondriest.frederic.free.fr/realisations/) and I am now listening to a m4a file. ;)

No clue why it doesnt work with XMMS tho ... whatever, BMP looks great too :)

---

### Post by atf487 on 2005-03-25
[QUOTE=zaubara]Well, I was cheering too fast i guess... :/

Rhytmbox is for me a no-go, too :(

Thats what XMMS tells me:

2-MPEG-4 AAC Low Complexity profile
MP4 - 2 channels @ 44100 Hz
MP4: Pulse coding not allowed in short blocks

Dunno what that means, someone I found on google stated that this was a bug in faad2 fixed a long time ago ...


// edit:

What I now did was installing BMP (apt-get install beep-media-player beep-media-player-dev), compiling the plugin for BMP from this page: [http://fondriest.frederic.free.fr/realisations/](http://fondriest.frederic.free.fr/realisations/) and I am now listening to a m4a file. ;)

No clue why it doesnt work with XMMS tho ... whatever, BMP looks great too :)[/QUOTE]

Could you tell me how you compiled that plugin? I'm lost.

---

### Post by ChaperonNoir on 2005-03-25
Me too please  :mrgreen: 

my ./configure works. But my make command fails.


This command fails to autoreconf -vifs

I get lost when he talks about FLAGS and PKG_CONFIG_PATH.

Why does ./configure && make && make install never works =/

---

### Post by zaubara on 2005-03-25
What I did was installing automake1.8 instead of the shipped 1.4 or newest 1.9 (the easiest way to do this is by synaptic)

I then did

ACLOCAL=aclocal-1.8 AUTOMAKE=automake-1.8 autoreconf -vifs
./configure
make
sudo make install

... AFAIR.
Make double sure you have all tools required for compiling (like automake 1.8, autoconf, libtool), aswell aus "beep-media-player-dev"!

If you still fail, post the last lines of your bailing make :)

Good luck!

---

### Post by atf487 on 2005-03-25
[QUOTE=zaubara]What I did was installing automake1.8 instead of the shipped 1.4 or newest 1.9 (the easiest way to do this is by synaptic)

I then did

ACLOCAL=aclocal-1.8 AUTOMAKE=automake-1.8 autoreconf -vifs
./configure
make
sudo make install

... AFAIR.
Make double sure you have all tools required for compiling (like automake 1.8, autoconf, libtool), aswell aus "beep-media-player-dev"!

If you still fail, post the last lines of your bailing make :)

Good luck![/QUOTE]


!

THANK YOU SO MUCH!

I had no idea the ac local thing was a command  :oops:

---

### Post by ChaperonNoir on 2005-03-25
:(


```
root@amd64:/home/edmond/bmp-mp4_20041215 # autoreconf -vifs
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
autoreconf: `aclocal.m4' is unchanged
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --force
autoreconf: running: /usr/bin/autoconf --force
autoreconf: running: /usr/bin/autoheader --force
autoreconf: running: automake --add-missing
automake: libfaad2/Makefile.am: not supported: source file `codebook/hcb.h' is in subdirectory
automake: libfaad2/Makefile.am: not supported: source file `codebook/hcb_1.h' is in subdirectory
automake: libfaad2/Makefile.am: not supported: source file `codebook/hcb_2.h' is in subdirectory
automake: libfaad2/Makefile.am: not supported: source file `codebook/hcb_3.h' is in subdirectory
automake: libfaad2/Makefile.am: not supported: source file `codebook/hcb_4.h' is in subdirectory
automake: libfaad2/Makefile.am: not supported: source file `codebook/hcb_5.h' is in subdirectory
automake: libfaad2/Makefile.am: not supported: source file `codebook/hcb_6.h' is in subdirectory
automake: libfaad2/Makefile.am: not supported: source file `codebook/hcb_7.h' is in subdirectory
automake: libfaad2/Makefile.am: not supported: source file `codebook/hcb_8.h' is in subdirectory
automake: libfaad2/Makefile.am: not supported: source file `codebook/hcb_9.h' is in subdirectory
automake: libfaad2/Makefile.am: not supported: source file `codebook/hcb_10.h' is in subdirectory
automake: libfaad2/Makefile.am: not supported: source file `codebook/hcb_11.h' is in subdirectory
automake: libfaad2/Makefile.am: not supported: source file `codebook/hcb_sf.h' is in subdirectory
autoreconf: automake failed with exit status: 1
root@amd64:/home/edmond/bmp-mp4_20041215 #
``` 

./configure works fine.

But make fails. probably because this command fails.

I have libtool, i have autoconf18, i have everything.

---

### Post by pfrrp on 2005-03-29
when i use autoreconf it doesnt recognize the command -vifs
im new to this...
thanks for any help.
R

---

### Post by Reb on 2005-04-20
Okay, so .m4a's work for me in beep-media-player (compiled a plugin) and vlc (just worked), but still not in Rhythmbox. I have all the libraries, it just doesn't happen.

---

### Post by antidrugue on 2005-10-05
I had those errors as well, when starting xmms:
[I]libmp4v2.so.0: cannot open shared object file: No such file or directory
libmikmod.so.2: cannot open shared object file: No such file or directory[/I]

So... I found those repositories...

[B]deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main
deb-src [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main[/B]

Add those repositories to /etc/apt/sources.list

From there of course:

[I]sudo apt-get update
sudo apt-get install libmp4-0 libmp4-dev
sudo apt-get install libmikmod2 libmikmod2-dev
[/I]
That's it! Now xmms is good to go!

---

### Post by antidrugue on 2005-10-05
And of course you had to at some point do that... (if not done already)

*sudo apt-get install xmms-mp4*

---

