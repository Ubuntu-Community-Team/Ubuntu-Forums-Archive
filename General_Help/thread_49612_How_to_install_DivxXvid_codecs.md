---
title: "How to install Divx/Xvid codecs?"
date: 2005-07-17
forum: General Help
---

### Post by Noah0504 on 2005-07-17
I need to install the Divx and Xvid codecs.  It would be nice if the codecs would allow me to play videos in Totem or Real Player,

Can anyone help me?

---

### Post by Kuolio on 2005-07-17
Make sure you have enabled universe, multiverse and restricted repositories. Install multimedia codecs:

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


After that, you should have no worries about multimedia codecs of any sort o/

---

### Post by Noah0504 on 2005-07-17
I've enabled all of the repositories, yet the w32codecs package can't be found.

---

### Post by adeen on 2005-07-17
Hey,
Where can't the w32codecs be found - in the repositories? If that is the problem, you need to enable the backports repositories, which are listed at the end of the sources.list example given in the Unofficial Ubuntu Starter Guide here: [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/). Check out the "How to Install Multimedia Codecs" section, and either apt-get or use Synaptic.
Good luck.

---

### Post by telcy on 2005-09-30
How can i fix this:
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
I tried apt-get update and it tish is what hapens...
...
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
404 Not Found
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
404 Not Found
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
404 Not Found
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
404 Not Found
...
PLS HELP!:rolleyes:

P.S Sorry for my bad eanglish!

I manage to fix it and it's working now! Sorry for the post!

---

### Post by greywolf73 on 2005-09-30
Right now you can not install the real player using backports it and the w32codec moved due to legal reasons.  If you want real player you have the to use the instructions on the realplayer site.

BTW, those backports that you are using are out of date. Please remove them and add this:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

---

### Post by azteech on 2005-10-11
[quote=Kuolio]Make sure you have enabled universe, multiverse and restricted repositories. Install multimedia codecs:

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

After that, you should have no worries about multimedia codecs of any sort o/[/quote] 


Anyone know where the libdivx4linux codec for breezy is located?

---

### Post by Perfect Storm on 2005-10-11
Try avifile-divx-plugin and see if it helps

and for dvd playback (libdvdcss2):   [http://www.dtek.chalmers.se/groups/dvd/deb/](http://www.dtek.chalmers.se/groups/dvd/deb/)

---

### Post by tats on 2005-10-13
[QUOTE=azteech]Anyone know where the libdivx4linux codec for breezy is located?[/QUOTE]

try this repositry

deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-extras main universe multiverse restricted

---

