---
title: "XFCE Help!"
date: 2015-04-20
forum: General Help
---

### Post by rcstck on 2015-04-20
Thanks to some helpful folks on another thread, I've gotten a bit better at compiling software!  I'm still trying to install xfce 4.12, and when I get to the make step in installing package "libxfce4ui-4.12.0" I encounter a fatal error:


"In file included from /usr/local/include/gtk-2.0/gdk/gdkscreen.h:32:0,
                 from /usr/local/include/gtk-2.0/gdk/gdkapplaunchcontext.h:31,
                 from /usr/local/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/local/include/gtk-2.0/gtk/gtk.h:32,
                 from ../libxfce4ui/xfce-dialogs.h:27,
                 from ../libxfce4ui/libxfce4ui.h:28,
                 from libxfce4ui-enum-types.c:4:
/usr/local/include/gtk-2.0/gdk/gdktypes.h:55:23: fatal error: gdkconfig.h: No such file or directory
 #include <gdkconfig.h>"

I've gone through apt-file search and found programs that include gdkconfig.h, installed them, reconfigured and tried make again to no avail.  Any suggestions?

---

### Post by Toz on 2015-04-20
If you go to the package's [launchpad page]("https://launchpad.net/libxfce4ui") and select your version, you'll see which build dependencies are required. For [libxfce4ui]("https://launchpad.net/ubuntu/vivid/+source/libxfce4ui"), those would be:
> 
    autotools-dev
    debhelper (>= 9)
    dpkg-dev (>= 1.16.1)
    intltool (>= 0.31)
    libglade2-dev
    libgtk-3-dev
    libgtk2.0-dev
    libstartup-notification0-dev
    libxfce4util-dev (>= 4.12)
    libxfconf-0-dev (>= 4.12)
    pkg-config


The important ones for this package are:
-    libglade2-dev
-    libgtk-3-dev
-    libgtk2.0-dev
-    libstartup-notification0-dev

(The first 4 and last 1 are either already included or not needed for manual building. The libxf* ones are created when you compiled the respective[ prerequisite build packages]("http://docs.xfce.org/xfce/building#package_specific_dependencies")).

In your case, the gdkconfig.h file is part of libgtk2.0-dev.

Edit: On closer inspection, it looks like its looking for the dev files in /usr/local. How did you install the dev files? What configure paramters are you using?

---

### Post by rcstck on 2015-04-20
Thank you for the heads-up on the Launchpad page, I didn't know of it before!  When you say configure parameters, what are you looking for?  To install packages, I either used synaptic, apt-get when I was told there was an error compiling, or downloaded the tar files as needed.  I created a directory /usr/local/src as per the instructions on the easy how to page for compiling on Ubuntu.  Also, I know I have libgtk2.0-dev.  I needed it earlier in the process.  If it's in a different location, how would I go about the make process and also include it?

---

### Post by steeldriver on 2015-04-20
Based on the path /usr/**local**/include/gtk-2.0/, it looks like you have installed gtk-2.0 from source instead of (or in addition to) the system package libgtk2.0-dev - presumably because xfce 4.12 requires a newer version (2.24.27) than that provided in the standard repository for your system version

If so, you may need to pass a parameter to the libxfce4ui-4.12.0 ./configure script to tell it where to look, or (depending on exactly how you installed / built gtk-2.0) adjust the PKG_CONFIG path(s) to pick it up - what does

```

pkg-config --modversion gtk+-2.0

```

say?

---

### Post by rcstck on 2015-04-20
It says 2.24.0

---

### Post by Toz on 2015-04-20
> **rcstck said:**
> When you say configure parameters, what are you looking for?
Prior to building a package, you generally configure it first by running "./configure" in the package's main directory. You can pass this configure command some parameters. With Xfce, you'll need to make sure you get the correct parameters if you want all of the functionality. For most packages you'll see a summary at the end of the configure process as to what functionality is being included. All of the packages should generally include "--prefix=/usr --disable-debug" plus an optional parameters. libxfce4ui, for example, should also be built with "--with-gtk3". What was your configure command?

---

### Post by rcstck on 2015-04-20
Ah, good to know.  All I did was use ./configure.  So I should go back in to that directory, and run "./configure --with-gtk3" ?

---

### Post by rcstck on 2015-04-22
Okay, I have been trying for days to compile xfce.  I'm frustrated, verging on getting pissed, because at every turn some new crap happens.

I try to install glib 2.40.0, as the xfce site says I need it.  I download it and run ./configure, but oh, I need the working zlib library and headers!  Where was that mentioned?  

So I get that, run it again, and another little piece is missing.  Imagine that.  Yes, I've downloaded build-essential, but clearly that doesn't cut it.

So here's the question, is there a package that contains all the little stuff so I can just install the pieces of xfce without all the "oops, this little piece no one mentioned is missing! Get that and then I'll tell you what piece is missing next.  So then you can go on the forum and all the people who know this  will just tell you to download Xubuntu.  Even though you want to learn it."

---

### Post by Toz on 2015-04-22
Building the Xfce environment from source is not an easy thing to do. This is complicated by the fact that I believe you are trying to build the latest version of Xfce on an earlier ubuntu version that doesn't have the minimum dependencies as part of the architecture. If you keep going, you'll end up rebuilding a good part of the distro.

_Suggestions:_
[LIST=1]
[*]If you want to build the latest 4.12 release, you'll need an up-to-date distro version. For Ubuntu, this would be 14.10, or even better, the soon to be released 15.04. It will have the required dependency versions of these packages already installed.
[*]
[*]As you are learning to do this, do it in a VM so that you don't affect your machine.
[*]
[*]Use the 15.04 mini iso to install a base system and build from there.
[/LIST]
_Compiling (there are basically two methods):_
[LIST=1]
[*]Using the debian-based method where all the work is pre-done for you. Basic instructions:
```
apt-get source package
cd package*
apt-get build-dep package
debuild -us -uc -b
cd ..
dpkg -i package*.deb
```
Note that system doesn't build the latest packages from the Xfce git tree, but rather the packages and package versions shipped (and pre-configured) with that specific version of Ubuntu. The newer the ubuntu version, the newer the Xfce packages. Plus, you'll also benefit from the custom patches that the Xubuntu team add to Xfce to make it work better in the ubuntu environment.
[*]Compile from source. As you can see, this is not easy. It takes patience, time and then more patience. I've personally never been able to build Xfce from source on an Ubuntu system. Its complicated. Props to the Xubuntu team for all the hard work they do. I've had much more luck building Xfce on Arch, but that build doesn't include any of the Ubuntu extra features.
[/LIST]

_Here are some basic instructions to get you started with method 1:_
[LIST=1]
[*]Grab the mini iso from: [http://archive.ubuntu.com/ubuntu/dists/vivid/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/vivid/main/installer-amd64/current/images/netboot/)
[*]Install it into a Virtualbox VM. During the install, at the Software selection screen, don't select anything.
[*]On reboot, prep your system:
```
apt-get update
apt-get dist-upgrade
apt-get install build-essential devscripts
```
[*]Follow the package build order at: [http://docs.xfce.org/xfce/building](http://docs.xfce.org/xfce/building). 
[/LIST]

_And, here are instructions for the first few packages:_
```
###################
# Create build directory
###################
mkdir /usr/src/xfce
cd /usr/src/xfce

###################
# xfce4-dev-tools
###################
apt-get source xfce4-dev-tools
cd xfce4-dev-tools*
apt-get build-dep xfce4-dev-tools
debuild -us -uc -b
cd ..
dpkg -i xfce4-dev-tools*.deb

###################
# libxfce4util
###################
apt-get source libxfce4util
cd libxfce4util*
apt-get build-dep libxfce4util
debuild -us -uc -b
cd ..
dpkg -i libxfce4util-*.deb
dpkg -i libxfce4util7_4*.deb
 
###################
# xfconf
###################
apt-get source xfconf
cd xfconf*
apt-get build-dep xfconf
debuild -us -uc -b
cd ..
dpkg -i xfconf*.deb
###you'll get an error about dbus-x11 not installed, so:
apt-get install dbus-x11
dpkg -i xfconf*.deb
dpkg -i libxfconf-0-dev*.deb
dpkg -i libxfconf-0-2_4*.deb


###################
# libxfce4ui
###################
apt-get source libxfce4ui
cd libxfce4ui*
apt-get build-dep libxfce4ui
debuild -us -uc -b
cd ..
dpkg -i libxfce4ui-common*.deb
dpkg -i libxfce4ui-utils_4*.deb
dpkg -i libxfce4ui-1-0_4*.deb
dpkg -i libxfce4ui-1-dev*.deb
dpkg -i libxfce4ui-2-0_4*.deb
dpkg -i libxfce4ui-2-dev*.deb

```

...and so on (make sure to see which actual deb files are created so that you can choose which ones to install - "ls -lt | grep deb | head" should help).

A list of the packages that I believe are installed in a default Xubuntu install are located here: [https://launchpad.net/xfce-project](https://launchpad.net/xfce-project). You can decide which ones to build.

EDIT: You'll also need to install the base X components so that you can start an X session when complete:
```
apt-get install xserver-xorg x11-xserver-utils x11-common xinit
```

---

### Post by rcstck on 2015-04-22
Thanks for this, this information will be invaluable going forward!

I've been having success so far today by using launchpad to ensure I have the correct packages installed before I install a new piece.  

I'm also glad to hear that someone else has had trouble and I'm not alone!

Whether I'm stubborn or dumb (draw your own conclusion), I'm committed to making this work.  Now it's a challenge and I won't let it go.

I encountered and error while installing exo-0.10.3 as follows:
"(Reading database ... 206148 files and directories currently installed.)
Preparing to unpack .../exo_0.10.3-1_amd64.deb ...
Unpacking exo (0.10.3-1) ...
dpkg: error processing archive /usr/local/src/exo-0.10.3/exo_0.10.3-1_amd64.deb (--install):
 trying to overwrite '/usr/local/share/icons/hicolor/icon-theme.cache', which is also in package libxfce4ui 4.12.0-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /usr/local/src/exo-0.10.3/exo_0.10.3-1_amd64.deb"

Side note: how do I put it one of those boffo boxes you use?

anyhow, how do overwrite that icons cache?

---

### Post by Mike_Walsh on 2015-04-22
Wouldn't it be easier simply to install the Xfce desktop?


Regards,

Mike.

---

### Post by rcstck on 2015-04-22
> **Mike_Walsh said:**
> Wouldn't it be easier simply to install the Xfce desktop?


Regards,

Mike.

See? this is what I'm talking about.

---

### Post by sammiev on 2015-04-22
> **rcstck said:**
> See? this is what I'm talking about.

This is likely what you are looking for. [XFCE 14.04]("http://xubuntu.org/")

---

### Post by QIII on 2015-04-22
The OP is talking about an exercise in actually compiling from source, not just having the DE.

---

### Post by rcstck on 2015-04-22
> **QIII said:**
> The OP is talking about an exercise in actually compiling from source, not just having the DE.


Thank you!

---

### Post by rcstck on 2015-04-22
I encountered and error while installing exo-0.10.3 as follows:
"(Reading database ... 206148 files and directories currently installed.)
Preparing to unpack .../exo_0.10.3-1_amd64.deb ...
Unpacking exo (0.10.3-1) ...
dpkg: error processing archive /usr/local/src/exo-0.10.3/exo_0.10.3-1_amd64.deb (--install):
 trying to overwrite '/usr/local/share/icons/hicolor/icon-theme.cache', which is also in package libxfce4ui 4.12.0-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /usr/local/src/exo-0.10.3/exo_0.10.3-1_amd64.deb"

Thoughts on how to overwrite that file?

---

### Post by Toz on 2015-04-22
> **rcstck said:**
> Thanks for this, this information will be invaluable going forward!

I've been having success so far today by using launchpad to ensure I have the correct packages installed before I install a new piece.  

I'm also glad to hear that someone else has had trouble and I'm not alone!

Whether I'm stubborn or dumb (draw your own conclusion), I'm committed to making this work.  Now it's a challenge and I won't let it go.

I encountered and error while installing exo-0.10.3 as follows:
"(Reading database ... 206148 files and directories currently installed.)
Preparing to unpack .../exo_0.10.3-1_amd64.deb ...
Unpacking exo (0.10.3-1) ...
dpkg: error processing archive /usr/local/src/exo-0.10.3/exo_0.10.3-1_amd64.deb (--install):
 trying to overwrite '/usr/local/share/icons/hicolor/icon-theme.cache', which is also in package libxfce4ui 4.12.0-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /usr/local/src/exo-0.10.3/exo_0.10.3-1_amd64.deb"
I'm not sure, I've never come across this issue. Which method are you using to compile this? Your first method of building from source, or the debian method I documented above?

> Side note: how do I put it one of those boffo boxes you use?
If you mean a virtualbox vm, have a look at [http://askubuntu.com/questions/142549/how-to-install-ubuntu-on-virtualbox]("http://askubuntu.com/questions/142549/how-to-install-ubuntu-on-virtualbox").

Perhaps the best thing is to start over, in a VM, using the 15.04 mini iso and the steps I documented above. I just completed the process for the base Xfce elements and it works.

---

### Post by rcstck on 2015-04-22
no, I meant those lighter colored deals you post code in.  I can't find the right button for that.

Also, my method at the moment is to extract the tar file to the directory I made, in my case /usr/local/src.  Then I run ./configure, then after that I run sudo checkinstall.  I also try the sudo checkinstall --fstrans=0 if I get errors, but --fstrans=0 won't beat that guy.

---

### Post by steeldriver on 2015-04-22
You posted [a previous thread](http://ubuntuforums.org/showthread.php?t=2274587&p=13269031#post13269031) in which you apparently got as far as installing libxfce4ui-4.12.0, so perhaps it's the files from that install attempt that the current one is complaining about?

I agree with Toz here - if you're just doing this as a learning exercise (not because you specifically need xfce 4.12 in Ubuntu 14.04) then you would do better to try building EITHER 4.10 on 14.04 OR 4.12 on 15.04 - if you're not sick of it after that you can always go back and try 4.12 on 14.04 (an all the associated dependencies) once you've got a few more builds under your belt

Also I'd suggest keeping all your questions about this in a single thread from now on, it will help you get consistent advice

---

### Post by rcstck on 2015-04-22
Alright, I suppose I'll have to compromise and build 4.10!  Also, total forum newbie still, so, sorry about posting all over.  Here's hoping it's easier next time around.

Interestingly, not only am I not sick of this, each set-back teaches me something interesting and I get more stubbornly determined.

---

### Post by Toz on 2015-04-23
> **rcstck said:**
> no, I meant those lighter colored deals you post code in.  I can't find the right button for that.
There are two ways:

1. Enclose the relevant parts of your post in **[noparse]```

```[/noparse]** tags.

2. Click on the "Preview Post" or "Go Advanced" button and you'll see more formatting options including a "#" button (which will add the code tags for you).

---

### Post by rcstck on 2015-04-23
Ah, you're the best! Thank you.

---

### Post by rcstck on 2015-04-23
Okay, tried to build 4.10, got the same error in the same place

---

### Post by rcstck on 2015-04-23
Just uninstalled that conflicting package in synaptic.  Seemed to work.  Let's see if it causes any bumps down the road.

---

### Post by oldos2er on 2015-04-23
Threads merged.

---

### Post by rcstck on 2015-04-29
Tried again and again to no avail.  Still Getting that same error.  Any ideas?

---

### Post by rcstck on 2015-05-01
I finally got everything installed, and I get the xfce session at the login screen.  When I log in, everything hangs at the desktop background, and only the mouse appears on screen.  I'm so close!  Where do I go from here?

---

### Post by rcstck on 2015-05-01
So I've seemingly installed xfce 4.10, but when I go to sign in, the screen hangs at the desktop background, but I still have mouse.

I install each package like this

```
 ./configure --prefix=/usr --sysconfdir=/etc && make && sudo make install 
```

before I try the install, I make sure to run this in terminal

```
 export PKG_CONFIG_PATH="/usr/lib/pkgconfig:$PKG_CONFIG_PATH" 
```

Using ```
 ./configure --prefix=/usr --sysconfdir=etc && make && sudo checkinstall 
```  always fails when installing exo-0.8.0 because it refuses to overwrite a hicolor icon theme file.

I have exhausted every possible resource I can think of to get this done.  When I use the forum to find an answer, it's always "try sudo apt-get install xfce4."  Yeah, that's how I know it will work on my 14.04 distro, but that's not how I want to install it.  Any ideas?  And please, don't merge this thread, the other one is clearly not helpful and mostly ignored.

---

### Post by ajgreeny on 2015-05-01
Why not just install Xubuntu?

---

### Post by QIII on 2015-05-01
Merged in any case (looks like the second merge here)

Please do not scatter multiple threads about the same subject around the forums.  It is confusing both to you and those who attempt to help.  And you have been getting help in this thread.

Please also allow the Staff to determine if threads need to be merged.

Thanks.

And again:  The OP is talking about an exercise in actually compiling from source, not just having the DE.

---

