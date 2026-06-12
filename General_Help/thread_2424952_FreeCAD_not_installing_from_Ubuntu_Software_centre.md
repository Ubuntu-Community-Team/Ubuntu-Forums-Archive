---
title: "FreeCAD not installing from Ubuntu Software centre"
date: 2019-08-18
forum: General Help
---

### Post by gawardnz on 2019-08-18
Hi,
I have used FreeCAD 0.17 for about a year now, and it used to install without issue. In recent times FreeCAD has been upgraded to version 0.18. It appears that now Ubuntu (I am not sure whether any other Linux falvours have an issue though) is no longer able to install it. I have tried via the command line as well as using the Ubuntu Software centre.

I get no errors during the install using the command line as instructed here:
[http://ubuntuhandbook.org/index.php/2019/04/install-freecad-0-18-ubuntu-18-04-16-04/](http://ubuntuhandbook.org/index.php/2019/04/install-freecad-0-18-ubuntu-18-04-16-04/)

However when the application starts, most of the menu options are simply not there. It's as if half the application has disappeared, and you cannot even load or save documents etc. I found this thread that implies there may be dependencies missing, but I have not been successful in getting FreeCAD up and running again.
[https://forum.freecadweb.org/viewtopic.php?t=34629](https://forum.freecadweb.org/viewtopic.php?t=34629)

If I try to use Ubuntu Software Centre to do the install, it progresses to about 15% and then states "Unable to install FreeCAD: Cannot perform the following tasks:" No tasks are listed, so I have no idea why the Software Centre is not working.

I appreciate that this is more a FreeCAD Forum issue as opposed to an Ubuntu issue (I think...) but given the problem appears to be prevailing with Ubuntu, and I haven't had much luck with the suggestions on their forum, I'm hoping somebody here is a bit more of an Ubuntu/FreeCAD guru than I am.

Thanks guys.

---

### Post by Autodave on 2019-08-18
What version of 'buntu are you using?  Did you clean install this version or update from a previous version?

---

### Post by rwe061 on 2019-08-18
I had a similar problem with freecad, it acted like it was loading but just just exited after a short time, but I am using Ubuntu 19.04, which may not be relevant.

I can't remember exactly what I did, but I did some general upgrade or update and that action installed some upgraded or new libraries.  After that my freecad installation worked.

Good luck.

---

### Post by dragonfly41 on 2019-08-18
What does this command show .. missing dependencies ..
```
apt-cache depends freecad
```
although I understand that this only works for installed packages.

There is [another utility here]("https://www.techrepublic.com/article/how-to-check-package-dependencies-with-apt-rdepends/").

---

### Post by gawardnz on 2019-08-19
Thanks for the support guys. Sorry, I neglected to mention I am running Ubuntu 18.04 (all kept up to date too). I was running FreeCAD 0.17 just fine, and have in fact installed that a couple of times before without issue. When you say a "clean install", I presume you are referring to FreeCAD (not Ubuntu, though for the record, Ubuntu 18.04 is a software migration/upgrade from 16.04 that I previously used). With regard to FreeCAD, first I simply installed new over old, then deleted the whole lot, and did a clean install of new (0.18). I got the same result both times.

To clarify, I installed first the standard Ubuntu install (after making sure all versions of FreeCAD had been removed from my machine) using the command line as prescribed here:
[https://www.freecadweb.org/wiki/Install_on_Unix](https://www.freecadweb.org/wiki/Install_on_Unix)

Next I installed the PPA option to keep it up to date, following all instructions as listed in the aforementioned website (for the stable release of FreeCAD).

I noticed that after doing this, I get the following:
[ATTACH=CONFIG]283826[/ATTACH]

It certainly does appear to be complaining about missing dependencies, though whether they are critical or not, I wouldn't know (if for example they are just part of the help files, then not vital to program execution, but Murpy's law dictates I'm almost certainly wrong!)

Running 
apt-cache depends freecad
[FONT=arial]
I got the following:

[/FONT][ATTACH=CONFIG]283827[/ATTACH]

Cheers!

---

### Post by m-j-malone on 2020-03-23
I am using Ubuntu 18.04.04 (/etc/issue).  I run the metacity classic gnome desktop, not the unity-dasher tricycle interface with intrusive bars taking up valuable screen real-estate on all sides of my screen that is the red headed stepchild of some windows mistake.   Gosh I find it worse than Macs. 

I read up on the free 3D cad programs for Ubuntu.   FreeCad seemed to be the logical choice.   I apt-cache search freecad, it was listed to I sudo apt-get install freecad

The install process went without error.   When I started freecad off of the automatically installed menu item in my classic Gnome desktop applications tab under Graphics, it gave me an error I did not write down, something about WebGui or something not installed.  There was a grey bar at the top with no menu items, nothing I could click, drag, open, all I could do was close the app.   Is it far inferior to the apt-get install behaviour I am used to.   

So I googled.  There was a PPA to add to get freecad from the original host site, and naturally they said it would be better to get it from them.   The install went without error.   The freecad menu item in Graphics had disappeared, but the instructions on installing freecad off the PPA indicated that I should use the command line to invoke as "freecad".  I got very specific errors, which I took to be a good thing.  It was telling me exactly what it was missing.   So I methodically hunted for every lib?????.so file it was complaining it was missing.  I found all of them using:

cd /
find . -print 2>&1 | grep lib?????.so

(to help the new) in the /snaps/vlc (the video player) directory.  I found similarly named files in the  /usr/lib/x86_64-linux-gnu/ so I figured, if things were properly installed, that is the directory they should have gone into.   Looking into that directory, I found broken links.  Links to files that did not exist.   I found files and links just missing.   I did my best to get the libraries from the /snaps/vlc/1049/usr/lib/x86_64-linux-gnu/ directory and put them into the /usr/lib/x86_64-linux-gnu/ directory.  In total, the following files needed to be copied, relinked or something (basically in the reverse order to what freecad complained about in sequential invokations):

libQt5Core.so.5
libicudata.so.55.1
libicudata.so.55
libpcre2-16.so.0
libicuuc.so.55
libicuuc.so.55.1
libicui18n.so.55
libicui18n.so.55.1
libQt5Core.so.5.11.1
libdouble-conversion.so.1
libdouble-conversion.so
libdouble-conversion.so.1.0
libQt5Svg.so.5.11
libQt5Svg.so.5
libQt5Svg.so
libQt5Svg.so.5.11.1

I was never able to make it work.   I just sudo apt-get remove freecad

So, Am I right that:

- the dependencies of freecad do not properly list a number of libraries for Ubuntu 18.04 ?
- that possibly vlc uninstalled some important components ? 
- that the classic metacity Gnome desktop causes some of these broken links ?
- that the update from 18.04 to 18,04.04 caused some of these broken links ?
- or that, out of the box, 18.04 is missing some libraries and has broken links ?

May I ask that someone look at sudo apt-get install freecad on 18.04 and check to make sure all of its dependencies are right and it works in some version (I don't care about the latest version) out of the box ?

Thank you

---

### Post by m-j-malone on 2020-03-24
I found the solution.  Short answer is, my Ubuntu 18.04.04 was missing the files that a number of links pointed to in the /usr/lib/x86_64-linux-gnu/ directory.   

The first part of the solution was, install FreeCad from the PPA, then try running it from the command line.   On each time I tried it, it complained it could not find a particular shared library file.  For each file it thought I was missing, I checked to see what package it should have come in, and tried installing them -- I got answers that these packages were already installed.  So I did a --reinstall.

```
apt-cache search {file}
sudo apt-get install --reinstall {package}

```

That fixed the broken links by putting the missing file in just install without --reinstall was not enough, it just said the package was up to date.   Checking the /usr/lib/x86_64-linux-gnu/ directory for all broken links and reinstalling all appropriate packages to fill in the missing files might be another way to arrive at a state no broken links to needed shared libraries.


The second part of the solution came after recognizing that, my Ubuntu 18.04.04 had libQt_5.9.5 libraries, and all sudo apt-get install freecad binaries (from the PPA) required libQt_5.11 libraries.   No pre-compiled version was going to work.  Compiling from source was the only way to make it work on my machine.

[https://wiki.freecadweb.org/Compile_on_Linux](https://wiki.freecadweb.org/Compile_on_Linux)

Was the answer, specifically:

```

cd
mkdir freecad 
cd freecad mkdir freecad-source
sudo apt-get install git
git clone https://github.com/FreeCAD/FreeCAD.git freecad-source
```

That gets the source distribution.   Now one has to make sure they have all the utilities needed to compile:

```

sudo apt install cmake cmake-gui libboost-date-time-dev libboost-dev libboost-filesystem-dev libboost-graph-dev libboost-iostreams-dev libboost-program-options-dev libboost-python-dev libboost-regex-dev libboost-serialization-dev libboost-signals-dev libboost-thread-dev libcoin-dev libeigen3-dev libgts-bin libgts-dev libkdtree++-dev libmedc-dev libocct-data-exchange-dev libocct-ocaf-dev libocct-visualization-dev libopencv-dev libproj-dev libpyside2-dev libqt5opengl5-dev libqt5svg5-dev libqt5webkit5-dev libqt5x11extras5-dev libqt5xmlpatterns5-dev libshiboken2-dev libspnav-dev libvtk7-dev libx11-dev libxerces-c-dev libzipios++-dev occt-draw pyside2-tools python3-dev python3-matplotlib python3-pivy python3-ply python3-pyside2.qtcore python3-pyside2.qtgui python3-pyside2.qtsvg python3-pyside2.qtwidgets python3-pyside2uic qtbase5-dev qttools5-dev swig
```

This just gets the computer to think it has freecad installed, so that it will update properly.

```

sudo add-apt-repository --enable-source ppa:freecad-maintainers/freecad-daily
sudo apt-get update
sudo apt-get build-dep freecad-daily
sudo apt-get install freecad-daily
```

Now build the binary:

```

mkdir freecad-build
cd freecad-build
cmake -DBUILD_QT5=ON -DPYTHON_EXECUTABLE=/usr/bin/python3 ../freecad-source
make -j$(nproc --ignore=2)
```

Then run it in the build/bin directory to test it out:

```

cd bin
./FreeCAD
```

I have not played with FreeCAD extensively, I have only gotten it to open, that is all.   

I tried 7 different ways to get FreeCAD working before I got to here.  I hope this saves people some problems with getting FreeCAD working.  It would be really nice if Canonical would recompile their 18.04LTS binary of FreeCAD with Qt_5.9.5 shared libraries and also make sure it has whatever the WebGUI error is missing, so, a simple sudo apt-get install freecad works, out of the box.

---

### Post by Impavidus on 2020-03-25
It's slightly worrying that some files belonging to installed packages were missing. It suggests that either your system was somehow damaged or you had a wrong version (you write you have Qt 5.9, but the PPA depends on Qt 5.11) – but that's something a reinstall of the package shouldn't solve.

Version conflicts, like with a PPA depending on Qt 5.11 while you have Qt 5.9, often happen with PPAs. One approach you could consider is using Ubuntu 19.10. It has Qt 5.12.

---

### Post by rsteinmetz70112 on 2020-03-25
I understand freecad is available from the official Ubuntu repositories. Why isn't that version acceptable? I understand it may be a little older but the official repositories are generally more reliable.

---

