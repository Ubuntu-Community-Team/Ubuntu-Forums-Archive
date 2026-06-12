---
title: "Musicbrainz Picard and dependency hell"
date: 2006-11-12
forum: General Help
---

### Post by theholycow on 2006-11-12
Ubuntu may be for humans, but apparently only lawyers are supposed to have forum accounts. The agreement is 28 pages (in it's medium-sized text box, anyway; wc reports 108 lines, 3194 words, 19028 chars) long. Egads, man!

Anyway...

I'd like to install Musicbrainz Picard ( [http://musicbrainz.org/](http://musicbrainz.org/) ). I run Breezy Badger.

Synaptic says picard: Depends: python-tunepimp but it is not going to be installed

Synaptic says python-tunepimp:
 Depends: libtunepimp4 but it is not going to be installed
 Depends: python2.4-tunepimp but it is not going to be installed
 Depends: python2.3-tunepimp but it is not going to be installed or
 	python2.4-tunepimp but it is not going to be installed

Synaptic says python2.4-tunepimp:
 Depends: libtunepimp4 but it is not going to be installed

Synaptic says python2.3-tunepimp:
 Depends: libtunepimp4 but it is not going to be installed

Synaptic says libtunepimp4:
  Depends: libcurl3 (>=7.15.0-1) but 7.14.0-2ubuntu1.2 is to be installed
  Depends: libgcc1 (>=1:4.0.2) but 1:4.0.1-4ubuntu9 is to be installed
  Depends: libidn11 (>=0.5.18 ) but 0.5.13-1.0 is to be installed
  Depends: libkrb53 (>=1.4.2) but 1.3.6-4 is to be installed
 Depends: libmusicbrainz4c2a but it is not going to be installed
 Depends: libofa0 but it is not going to be installed
  Depends: libogg0 (>=1.1.3) but 1.1.2-1 is to be installed
 Depends: libssl0.9.8 (>=0.9.8a-1) but it is not installable
  Depends: libstdc++6 (>=4.0.2-4) but 4.0.1-4ubuntu9 is to be installed
 Depends: libtag1c2a (>=1.4) but it is not installable
  Depends: libvorbis0a (>=1.1.2) but 1.1.0-1ubuntu1 is to be installed
  Depends: libvorbisfile3 (>=1.1.2) but 1.1.0-1ubuntu1 is to be installed

](*,)

Up until a year or two ago, I used Slackware and I compiled and installed every program from source. I thought that if I use a modern distribution with a real package manager, it would take care of dependencies for me. Bah! It seems I get dependency hell wherever I go.

I suspect that if I upgrade to Dapper Drake, I can get it working. I'm rather afraid to do it, though. What will I have to backup if I want to roll back my system? I've already backed up everything except /home (and /proc and /dev, both of which shouldn't need backing up). If I do upgrade, will it mess with anything in my home directory (config/settings files)?

Still, I'd like to _avoid_ upgrading just to get the program to run. How do I get out of dependency hell?

---

### Post by christhemonkey on 2006-11-12
Are you online on this ubuntu box?
If so, do you have all the repositories enabled?

(in synaptic if you go settings and then repositories, then make sure you have universe, restricted and multiverse enabled)


As for upgrading to dapper, id say the one place that you would need to back up would be your /home as this is where your important data (file etc) is most likely to be kept.

---

### Post by theholycow on 2006-11-12
It is online, and all the repositories are enabled. Additionally, I've even done Edit -> Reload Package Information just in case my info was out of date.

Yeah, I figured I'd have to backup my home directory, but that's going to be a real mess. I've got a heck of a lot of data there...

---

### Post by christhemonkey on 2006-11-12
libmusicbrainz4c2 is in the security.ubuntu.com repository for security updates. Is this enabled?

I would recommend backing up your home directory an upgrading to dapper, then you can install picard from their dapper repository!
[http://musicbrainz.org/doc/PicardLinuxInstall#head-5f60c040c32c67c304b335181b88678ad34149c2](http://musicbrainz.org/doc/PicardLinuxInstall#head-5f60c040c32c67c304b335181b88678ad34149c2)

---

### Post by theholycow on 2006-11-13
I've got that repository and I've even got libmusicbrainz4c2 installed.

However, somewhere down the line (and I no longer remember where), something asks for libmusicbrainz4c2a. If I try to install libmusicbrainz4c2a, I get these messages:

To Be Removed:
[list of nearly all media player programs on my system, and ubuntu-desktop (say, isn't that one important?)]

libmusicbrainz4c2a:
  Depends: libgcc1 (>=1:4.0.2) but 1:4.0.1-4ubuntu9 is to be installed
  Depends: libstdc++6 (>=4.0.2-4) but 4.0.1-4ubuntu9 is to be installed

---

### Post by christhemonkey on 2006-11-13
Hmm yeah, that sounds like you have mixed repostories or something, as libmusicbrainz4c2**a** is not in the official breezy ubuntu repositories.

So yeah, i would really reccomend the upgrade to dapper!

Also ubuntu-desktop is just a meta-package, so removing it does not actually harm your install, the one time it might is when your upgrading distro, like breezy to dapper, then you should have it installed.

---

### Post by theholycow on 2006-11-13
I thought a meta-package installed/uninstalled a bunch of other packages.

Oh well, I guess I gotta do the upgrade. Quite scary, actually... I have a relatively stable system, and I hate to mess with success, but I'd like to run this program.

I tried running the windows version in Wine, but besides being terribly slow, it crashes when it tries to write anything to disk.

Hey, wait a minute...maybe I could run it in a chrooted install of something else. Or maybe I can get the source and compile/install like I used to, years ago. I'm going to work on that...a live, in-place upgrade is scary to me.

---

### Post by theholycow on 2006-11-13
Well, I fearlessly tread into my old territory of compiling from source and installing with "make install". Actually, picard itself is a python script, but depends on libtunepimp and whatever else. Yes, I know that I've now entirely defeated the purpose of the packaging system, and it will never be the same. Maybe it will convince me to upgrade, which ought to clean up th mess.

So, I downloaded the source for libtunepimp, chased down a million dependencies that came up each time I tried to run "./configure", and had to hack up configure for two libraries that it failed to recognize as installed and up-to-date. Finally, I got it installed and tried to run picard, but it's still no good. ](*,) 

Silly me. It just occured to me that I ought to see if there's a support mailing list or forum for picard. If so, I bet they've dealt with these problems repeatedly...heh.

---

### Post by theholycow on 2006-11-13
Got it!

While searching through archives of mailing lists and forums, it occured to me that I should be looking for info specific to Breezy Badger. I found this, and after going through the steps, picard is running!

[http://musicbrainz.org/doc/PicardSourceInstall?highlight=(CategoryProducts](http://musicbrainz.org/doc/PicardSourceInstall?highlight=(CategoryProducts))

I'll post yet again if it fails...

---

### Post by theholycow on 2006-11-13
It failed. It would load and run, but when I actually tried to feed it some files, it wouldn't take mp3s, and wavs crashed it. Googling tells me that other folks have problems with wav files; no problem, I don't have many (most of which are just decoded mp3s for testing a program).

A little more digging tells me that /usr/local/lib/tunepimp/plugins/ is missing everything except the wav plugin. I fsck around until I get the plugins in there, and now it seems to work.

...a few minutes later...

Sweet! It actually works, all the way through tagging and saving files!

---

