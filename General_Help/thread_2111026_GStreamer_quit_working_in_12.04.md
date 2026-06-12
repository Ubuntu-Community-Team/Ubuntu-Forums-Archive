---
title: "GStreamer quit working in 12.04"
date: 2013-01-31
forum: General Help
---

### Post by Weidbrewer on 2013-01-31
So, I noticed tonight that I can no longer play videos on my 12.04 install.  All players try to install gstreamer plugings (which are installed, I've verified this) and keep coming back to errors like this:

```
The following packages have unmet dependencies:
 gstreamer0.10-ffmpeg : Depends: libavcodec53 (>= 4:0.7.3-1) but it is not going to be installed or
                                 libavcodec-extra-53 (>= 4:0.7.3-1) but it is not going to be installed
                        Depends: libavformat53 (>= 4:0.7.3-1) but it is not going to be installed or
                                 libavformat-extra-53 (>= 4:0.7.3-1) but it is not going to be installed
                        Depends: libavcodec53 (< 5:0) but it is not going to be installed or
                                 libavcodec-extra-53 (< 5:0) but it is not going to be installed
 gstreamer0.10-plugins-bad-multiverse : Depends: libmjpegtools-1.9 (>= 1:1.9.0) but it is not going to be installed

```

Any ideas?

---

### Post by Frogs Hair on 2013-01-31
I received an update for libavcodec-extra-53  on the on 1-28 but it seems to have installed fine on 12.10 via the medibuntu repository which I have enabled. The other plug-in updates came from Ubuntu.  

I can only suggest checking for broken packages and fixing them via synaptic or the terminal.

---

### Post by Weidbrewer on 2013-01-31
> **Frogs Hair said:**
> I received an update for libavcodec-extra-53  on the on 1-28 but it seems to have installed fine on 12.10 via the medibuntu repository which I have enabled. The other plug-in updates came from Ubuntu.  

I can only suggest checking for broken packages and fixing them via synaptic or the terminal.

What I meant above about confirming the packages were installed was that I'd already uninstalled them and reinstalled.  I'm fairly confident that I don't have any broken packages.

---

### Post by Frogs Hair on 2013-02-01
The synaptic package manager will display all installed packages. It is no longer installed by default as on earlier versions and is in the software center.

You can generate a package list as a text document which will appear in the home folder with the following command .```
sudo dpkg --get-selections > installed-software
```

---

### Post by Weidbrewer on 2013-02-01
I'll give that a check when I get home, although I tried install/uninstall through package manager, command line and the software center.

---

### Post by Weidbrewer on 2013-02-07
Okay - I said I'd check when I got home.  I didn't say *which day.*  



Still stumped.  Again, Gstreamer is showing as installed, but doesn't work.  When I look for certain packages - like the one in your screen cap - they're not installed, but it won't let me install them with the error messages that I posted above.  The output of installed packages gives me things like this:

[CODE
gstreamer0.10-alsa				install
gstreamer0.10-fluendo-mp3			install
gstreamer0.10-gconf				install
gstreamer0.10-gnonlin				install
gstreamer0.10-nice				install
gstreamer0.10-plugins-bad			install
gstreamer0.10-plugins-base			install
gstreamer0.10-plugins-base-apps			install
gstreamer0.10-plugins-good			install
gstreamer0.10-plugins-ugly			install
gstreamer0.10-pulseaudio			install
gstreamer0.10-tools				install
gstreamer0.10-x					install

...

]libavcodec-extra-52				install
libavcodec-unstripped-52			install
libavcodec53					deinstall
libavdevice53					deinstall
libavfilter2					deinstall
libavformat53					deinstall
libavutil-extra-49				install
libavutil-extra-51				install[/CODE]

But I'm not sure what to do with that.  (man, I really, really hate when updates do this to a perfectly working systwem...)

---

### Post by Frogs Hair on 2013-02-07
Is the update manager giving you problems because I have already had another update for that package.

---

### Post by Weidbrewer on 2013-02-07
> **Frogs Hair said:**
> Is the update manager giving you problems because I have already had another update for that package.

We seem to be going in circles on the same issue, and I'm at a loss as to how I can explain things better.  I'm probably just not using the right term or label somewhere and I apologize. 

[LIST=1]
[*]Gstreamer was installed and working.  The world was happy.
[*]No distro upgrades or anything
[*]One day, after an update, GStreamer no longer worked.  The world was sad.
[*]The system seems to think it's installed and up to date, so the update manager doesn't have any problems
[*]Uninstalling GStreamer and reinstalling it doesn't help - I get back to the same spot.  This is true whether I do it from Synaptic, Software Center or command line
[*]It keeps telling me that I need a whole passel of dependencies, but won't let me install any of them.
[/LIST]

Does that clarify anything, or am I still saying it wrong?

Is there at least some way that I can nuke everything ever connected to GStreamer and reinstall from some place that has all the dependencies?  I mean, seriously - it's not like I was messing around with anything I shouldn't be...this is on my server for crying out loud.  I pretty much just install updates every now and again and move on with my life.  Occasionally, I'll have a browser open and try to watch a video.  So, whatever happened here is because of an official Ubuntu update, so I can't be the only one who's totally and irretrievably borked.

---

### Post by Frogs Hair on 2013-02-07
I was not sure you had run the update manager since or tried from the command line. Is there anything other than the default media player installed because that is the only thing I can think of that may break gstreamer dependencies. If you have tried to _purge_ the packages and can't I don't know what else to suggest. I would also try Ask Ubuntu.   [http://askubuntu.com/](http://askubuntu.com/)

The command on this page may help I have used it with a dependency problem.
[http://askubuntu.com/questions/179955/var-lib-apt-lists-huge-in-12-04](http://askubuntu.com/questions/179955/var-lib-apt-lists-huge-in-12-04)

---

### Post by mc4man on 2013-02-07
Your version of libavcodec-extra installed (libavcodec-extra-52) is not right for 12.04 which uses libavcodec-extra-**53**

Maybe open up software sources & make sure that under the 'updates' tab that 'security' & 'updates' are enabled. If using some obscure mirror then change to the Us or Main Server, update your sources & check what version of libavcodec-extra is installed.

Worst case just remove all ffmpeg (libav) shared libs, refresh your sources & re-install them, ect.
Ex. of current libavcodec-extra-53 in 12.04
[http://packages.ubuntu.com/precise-updates/libavcodec-extra-53](http://packages.ubuntu.com/precise-updates/libavcodec-extra-53)

---

### Post by Weidbrewer on 2013-02-07
> **mc4man said:**
> Your version of libavcodec-extra installed (libavcodec-extra-52) is not right for 12.04 which uses libavcodec-extra-**53**

Yep - that's exactly the problem we identified above...I just can't seem to get it to install.

---

### Post by mc4man on 2013-02-07
> **Weidbrewer said:**
> Yep - that's exactly the problem we identified above...I just can't seem to get it to install.
if installed I'd open up synaptic, search libav, scroll down a ways &  remove All the libav (ffmpeg) libraires like - 
libavcodec*, libavformat*, libavutil*, libswscale*
(I'd use synaptic because it tells you what's to happen & also keeps a nice history for you.
Then reload the sources, search libav, what  version of libavcodec is available to install? (if 53 then install it.

---

### Post by Weidbrewer on 2013-03-15
> **mc4man said:**
> if installed I'd open up synaptic, search libav, scroll down a ways &  remove All the libav (ffmpeg) libraires like - 
libavcodec*, libavformat*, libavutil*, libswscale*
(I'd use synaptic because it tells you what's to happen & also keeps a nice history for you.
Then reload the sources, search libav, what  version of libavcodec is available to install? (if 53 then install it.

I gotta be honest - his frustrated me so much that I walked away from it for a while.  Just tried your suggestions and they worked.  Thank you very much.

---

