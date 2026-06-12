---
title: "xdtv &amp; Breezy Badger"
date: 2005-10-14
forum: General Help
---

### Post by M4l3k on 2005-10-14
Hi all,

Any ideas on how one could install xdtv without having to dkpg the deb? 
I am thinking about backports but I don't know where to find them.

I actually tried the .deb thing but it requires other libraries and I am a little bit reluctant in messing around with libraries myself. I am on for the nice and esay solution through synaptic if possible!

Cheers and long life to Ubuntu!

M4l3k

---

### Post by M4l3k on 2005-10-17
Hi to myself and others!

I came to realize that I mixed it all up.

I figured out how to install xdtv and want to share the procedure within this helpful community. Here it goes.

Install xdtv

1/ Add repositories in /etc/apt/sources.list:
## XdTV
deb [http://xawdecode.sourceforge.net/debian/](http://xawdecode.sourceforge.net/debian/) binary/
deb-src [http://xawdecode.sourceforge.net/debian/](http://xawdecode.sourceforge.net/debian/) source/
deb-src [http://perso.wanadoo.fr/debian/](http://perso.wanadoo.fr/debian/) unstable main

2/ Install codec libavcodec2:
download: 
[http://search.belnet.be/packages/ubuntu/ubuntu/pool/multiverse/f/ffmpeg/](http://search.belnet.be/packages/ubuntu/ubuntu/pool/multiverse/f/ffmpeg/)
install: 
sudo dpkg -i libavcodec2_0.4.9-pre1-0.2_i386.deb

This happens:
user@server:~$ sudo dpkg -i xdtv_setup/libavcodec2_0.4.9-pre1-0.2_i386.deb
Selecting previously deselected package libavcodec2.
(Reading database ... 56661 files and directories currently installed.)
Unpacking libavcodec2 (from .../libavcodec2_0.4.9-pre1-0.2_i386.deb) ...
dpkg: dependency problems prevent configuration of libavcodec2:
 libavcodec2 depends on libfaad2-0 (>= 2.0.0-0.1); however:
  Package libfaad2-0 is not installed.
 libavcodec2 depends on libimlib2; however:
  Package libimlib2 is not installed.
 libavcodec2 depends on liblame0 (>= 3.96.1-1); however:
  Package liblame0 is not installed.
dpkg: error processing libavcodec2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libavcodec2

But then, synaptic kicks in and updates the missing codecs!
install: sudo dpkg -i libavcodec2_0.4.9-pre1-0.2_i386.d

3/ Install xdtv
sudo apt-get install xdtv

4/ Configure xdtv
xdtv_wizard

Done! :-)

Feels good. XDTV rocks though I have the impression that tvtime gives a better picture.

Cheers

M4l3k

---

