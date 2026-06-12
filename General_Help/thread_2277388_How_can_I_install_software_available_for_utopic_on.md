---
title: "How can I install software available for utopic on vivid?"
date: 2015-05-08
forum: General Help
---

### Post by TriforceOfKirby on 2015-05-08
So I want to install MakerBot Desktop on Ubuntu 15.04; however, according to [http://www.makerbot.com/support/new/Desktop/Using_MakerBot_Desktop/01-Getting_Started/How_to_Install_MakerBot_Desktop_for_Linux](http://www.makerbot.com/support/new/Desktop/Using_MakerBot_Desktop/01-Getting_Started/How_to_Install_MakerBot_Desktop_for_Linux), it only supports up to 14.10 at the moment. Can I install the 14.10 version on 15.04?

---

### Post by ian-weisser on 2015-05-09
That's a great question for the MakerBot forums, since _they_ support that non-Ubuntu software.

You can certainly try installing the older version, but recognize that it may not work.

---

### Post by TriforceOfKirby on 2015-05-11
I don't think Makerbot has an official forum, their support page just has online guides, FAQs, videos, and troubleshooting tips.

---

### Post by Geoffrey_Arndt on 2015-05-12
Or, you could install 14.04 LTS ..and have a functional system for about 4 years.

---

### Post by TriforceOfKirby on 2015-05-12
So is there a way to install software for an older version or not? The installation for this particular software is pretty typical:
```

sudo apt-add-repository http://downloads.makerbot.com/makerware/ubuntu
sudo apt-get update
sudo apt-get install makerware

```
So are there any parameters that will install the software from the older distro?

Otherwise I'm willing to use any other way to create a print file for Replicator 2 printer.

---

### Post by Bucky Ball on 2015-05-12
*Thread moved to **General Help**.*
[I][B]
Installation & Upgrades[/B][/I] is for problems installing and upgrading the OS itself. ;)

---

### Post by grahammechanical on 2015-05-12
I advise that after adding the repository you check you check repository url in Software & Updates to see if it has any reference to vivid. If it does then edit the url to read utopic instead of vivid. I suspect that will not be the case. If that repository is active you should not get any error messages when you update. But you may be dependency issues.

Regards.

---

### Post by TriforceOfKirby on 2015-05-12
Ok so I changed the url from vivid to utopic for both main and source code, no error messages were given after update. Here is my output from the terminal when trying to install the software:
```

sudo apt-get install makerware
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 makerware : Depends: conveyor (= 3.6.0-14.10)
             Depends: conveyor-ui (= 3.6.0-14.10) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```
So what steps should I take from here to correct dependencies?

---

### Post by ian-weisser on 2015-05-12
Well, I would have simply downloaded the deb and installed it using dpkg.
Changing your sources can cause all kinds of problems. I would undo that.

Conveyor is not in the Ubuntu repositories. You got it from someplace else. The error means that the version you have is simply incompatible with your current setup.
That's a risk risk of using version-dependent software, when you decide to mix versions.
If you undo the changes to your sources, the problem should probably go away.

Do remember that after changing your sources, you must run 'apt-get update' to update your package database to the new sources.

---

### Post by Geoffrey_Arndt on 2015-05-12
Why not install "Trusty Tahr" 14.04.2 LTS?   Supported through April 2019, and the software you want (PPA) is tested and supported.

   Should be the same basic steps as used to install 15.04 . . . problem solved . . .

---

### Post by Bucky Ball on 2015-05-12
> **Geoffrey_Arndt said:**
> Why not install "Trusty Tahr" 14.04.2 LTS?   Supported through April 2019, and the software you want (PPA) is tested and supported.

   Should be the same basic steps as used to install 15.04 . . . problem solved . . .

+1. Unless there's a specific reason you're running 15.04 ...

---

### Post by TriforceOfKirby on 2015-05-13
Alright, how can I download the deb directly?

I'm using 15.04 for various reasons, primarily for the change to systemd.

Ok I figured out how to download the deb using aptitude, so here's what I did:
```

cd ~/Downloads; aptitude download makerware; sudo dpkg -i *.deb; sudo apt-get -fy --force-yes install; rm *.deb

```
And here's the output:
```

Get: 1 http://downloads.makerbot.com/makerware/ubuntu/ utopic/main makerware amd64 3.6.0-14.10 [165 MB]
Fetched 165 MB in 34s (4,725 kB/s)
Selecting previously unselected package makerware.
(Reading database ... 204874 files and directories currently installed.)
Preparing to unpack makerware_3.6.0-14.10_amd64.deb ...
Unpacking makerware (3.6.0-14.10) ...
dpkg: dependency problems prevent configuration of makerware:
 makerware depends on libjsoncpp0 (>= 0.6.0~rc2); however:
  Package libjsoncpp0:amd64 is not installed.
 makerware depends on libopenmesh-3.2; however:
  Package libopenmesh-3.2 is not installed.
 makerware depends on libqt5multimediawidgets5 (>= 5.0.2) | libqt5multimediawidgets5-gles (>= 5.0.2); however:
  Package libqt5multimediawidgets5:amd64 is not installed.
  Package libqt5multimediawidgets5-gles is not installed.
 makerware depends on gksu; however:
  Package gksu is not installed.
 makerware depends on conveyor (= 3.6.0-14.10); however:
  Package conveyor is not installed.
 makerware depends on conveyor-ui (= 3.6.0-14.10); however:
  Package conveyor-ui is not installed.
 makerware depends on libthing (= 3.6.0-14.10); however:
  Package libthing is not installed.
 makerware depends on libmbqtutils (= 3.6.0-14.10); however:
  Package libmbqtutils is not installed.
 makerware depends on mb-libstdc++6; however:
  Package mb-libstdc++6 is not insta
dpkg: error processing package makerware (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info (1.3-1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu5) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for bamfdaemon (0.5.1+15.04.20150202-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.58ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.14-0ubuntu1) ...
Errors were encountered while processing:
 makerware
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  avrdude gksu libboost-program-options1.55.0 libboost-serialization1.55.0 libboost-thread1.55.0 libftdi1 libgksu2-0 libgtkglext1 libjsoncpp0 libmbqtutils
  libopencv-calib3d2.4 libopencv-features2d2.4 libopencv-flann2.4 libopencv-highgui2.4 libopenmesh-3.2 libqt5multimediawidgets5 libthing libtinything
  libtoolpathviz makerbot-driver mb-libjsonrpc mb-libopencv2.4 mb-libstdc++6 mb-pyserial miracle-grue
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gksu libgksu2-0 libjsoncpp0 libmbqtutils libopenmesh-3.2 libqt5multimediawidgets5 libthing libtinything mb-libstdc++6
The following packages will be REMOVED:
  makerware
The following NEW packages will be installed:
  gksu libgksu2-0 libjsoncpp0 libmbqtutils libopenmesh-3.2 libqt5multimediawidgets5 libthing libtinything mb-libstdc++6
0 upgraded, 9 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 830 kB of archives.
After this operation, 179 MB disk space will be freed.
WARNING: The following packages cannot be authenticated!
  libopenmesh-3.2 libthing mb-libstdc++6 libtinything libmbqtutils
Get:1 http://us.archive.ubuntu.com/ubuntu/ vivid/main libqt5multimediawidgets5 amd64 5.4.1-1ubuntu1 [36.5 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ vivid/universe libjsoncpp0 amd64 0.6.0~rc2-3.1ubuntu1 [59.0 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ vivid/universe libgksu2-0 amd64 2.0.13~pre1-6ubuntu7 [72.1 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ vivid/universe gksu amd64 2.0.2-9ubuntu1 [51.5 kB]
Get:5 http://downloads.makerbot.com/makerware/ubuntu/ utopic/main libopenmesh-3.2 amd64 3.2-14.10 [135 kB]
Get:6 http://downloads.makerbot.com/makerware/ubuntu/ utopic/main libthing amd64 3.6.0-14.10 [357 kB]
Get:7 http://downloads.makerbot.com/makerware/ubuntu/ utopic/main mb-libstdc++6 amd64 3.6.0-14.10 [1,880 B]
Get:8 http://downloads.makerbot.com/makerware/ubuntu/ utopic/main libtinything amd64 3.6.0-14.10 [53.4 kB]
Get:9 http://downloads.makerbot.com/makerware/ubuntu/ utopic/main libmbqtutils amd64 3.6.0-14.10 [63.3 kB]                                                    
Fetched 830 kB in 6s (134 kB/s)                                                                                                                               
(Reading database ... 204928 files and directories currently installed.)
Removing makerware (3.6.0-14.10) ...
Processing triggers for hicolor-icon-theme (0.14-0ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu5) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for bamfdaemon (0.5.1+15.04.20150202-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.58ubuntu1) ...
Processing triggers for shared-mime-info (1.3-1) ...
Selecting previously unselected package libqt5multimediawidgets5:amd64.
(Reading database ... 204874 files and directories currently installed.)
Preparing to unpack .../libqt5multimediawidgets5_5.4.1-1ubuntu1_amd64.deb ...
Unpacking libqt5multimediawidgets5:amd64 (5.4.1-1ubuntu1) ...
Selecting previously unselected package libjsoncpp0:amd64.
Preparing to unpack .../libjsoncpp0_0.6.0~rc2-3.1ubuntu1_amd64.deb ...
Unpacking libjsoncpp0:amd64 (0.6.0~rc2-3.1ubuntu1) ...
Selecting previously unselected package libgksu2-0.
Preparing to unpack .../libgksu2-0_2.0.13~pre1-6ubuntu7_amd64.deb ...
Unpacking libgksu2-0 (2.0.13~pre1-6ubuntu7) ...
Selecting previously unselected package gksu.
Preparing to unpack .../gksu_2.0.2-9ubuntu1_amd64.deb ...
Unpacking gksu (2.0.2-9ubuntu1) ...
Selecting previously unselected package libopenmesh-3.2.
Preparing to unpack .../libopenmesh-3.2_3.2-14.10_amd64.deb ...
Unpacking libopenmesh-3.2 (3.2-14.10) ...
Selecting previously unselected package libthing.
Preparing to unpack .../libthing_3.6.0-14.10_amd64.deb ...
Unpacking libthing (3.6.0-14.10) ...
Selecting previously unselected package mb-libstdc++6.
Preparing to unpack .../mb-libstdc++6_3.6.0-14.10_amd64.deb ...
Unpacking mb-libstdc++6 (3.6.0-14.10) ...
Selecting previously unselected package libtinything.
Preparing to unpack .../libtinything_3.6.0-14.10_amd64.deb ...
Unpacking libtinything (3.6.0-14.10) ...
Selecting previously unselected package libmbqtutils.
Preparing to unpack .../libmbqtutils_3.6.0-14.10_amd64.deb ...
Unpacking libmbqtutils (3.6.0-14.10) ...
Processing triggers for man-db (2.7.0.2-5) ...
Processing triggers for gconf2 (3.2.6-3ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu5) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for bamfdaemon (0.5.1+15.04.20150202-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.58ubuntu1) ...
Setting up libqt5multimediawidgets5:amd64 (5.4.1-1ubuntu1) ...
Setting up libjsoncpp0:amd64 (0.6.0~rc2-3.1ubuntu1) ...
Setting up libgksu2-0 (2.0.13~pre1-6ubuntu7) ...
update-alternatives: using /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo to provide /usr/share/gconf/defaults/10_libgksu (libgksu-gconf-defaults) in auto mode
Setting up libopenmesh-3.2 (3.2-14.10) ...
Setting up libthing (3.6.0-14.10) ...
Setting up mb-libstdc++6 (3.6.0-14.10) ...
Setting up libtinything (3.6.0-14.10) ...
Setting up libmbqtutils (3.6.0-14.10) ...
Processing triggers for gconf2 (3.2.6-3ubuntu1) ...
Setting up gksu (2.0.2-9ubuntu1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...

```
So that didn't quite work, afterwards I ran this:
```

sudo apt-get update; sudo apt-get upgrade; sudo apt-get autoremove; sudo apt-get clean

```
And it removed these packages:
```

gksu libgksu2-0 libjsoncpp0 libmbqtutils libopenmesh-3.2 libqt5multimediawidgets5 libthing libtinything mb-libstdc++6

```

---

### Post by ian-weisser on 2015-05-13
Wow.

I think you are making this rather more complicated than it needs to be.

For example, I would have used simple old wget (or a web browser) to download the deb. You SHOULD NOT have 14.10 sources mixed with 15.04 sources. That way lies great frustration.

Also, don't randomly run apt-get autoremove and apt-get clean and apt-get upgrade. It's important to understand what each one does - they are not magic incantations. Many are the people I have seen who have deleted a deb they desperately needed by thoughtlessly running 'clean'.

And *really* don't run 'dpkg -i *.deb' nor 'apt-get -fy' without doing a --simulate run first! Nor should you script those powerful, dangerous commandz. Randomly forcing apt-get to do things that it thinks are a bad idea (and ignoring it's warnings) is an easy way to damage your system quite horribly.

>  makerware depends on conveyor (= 3.6.0-14.10); however:
  Package conveyor is not installed.
 makerware depends on conveyor-ui (= 3.6.0-14.10); however:
  Package conveyor-ui is not installed.
 makerware depends on libthing (= 3.6.0-14.10); however:
  Package libthing is not installed.
 makerware depends on libmbqtutils (= 3.6.0-14.10); however:
  Package libmbqtutils is not installed.

Those are version-specific dependencies. I don't see any of them in the Ubuntu repositories, so I suspect makerware expects you to also download and install those debs from it's site. When using dpkg to install them, be sure to install all those dependencies first, so the later install of the makerware deb will run smoothly.

Your experience would be much better if the Makerware developers, having done all the hard work of packaging the deb, would take the easy final step and upload the software to Debian. You would have had an unremarkably trivial install days ago.

---

### Post by TriforceOfKirby on 2015-05-13
I don't think Makerbot offers a direct download to the deb, is using aptitude to download it incorrect? Also, I do understand what the various apt-get commands do, I regularly run clean to free up disk space. I did run a --simulate first, sorry probably should of noted that. *.deb was only used as it's faster to type and I was aware of the contents of the directory.

So, how do I go about installing these dependencies? I'm not quite sure where their sites would be, conveyor seems to have a GitHub repository, but I can't seem to find a deb file.
Also how should I get the correct deb file for makerware through wget/web browser?

---

### Post by ian-weisser on 2015-05-13
> **TriforceOfKirby said:**
> So, how do I go about installing these dependencies? I'm not quite sure where their sites would be, conveyor seems to have a GitHub repository, but I can't seem to find a deb file.

Excellent questions for the Makerware developers or support community. It is, after all, *their* software that is incompatible with your release of Ubuntu.
I don't happen to use makerware. I can tell you a *lot* about Ubuntu software and Debian packaging and what install errors mean and how to fix them. But I cannot tell you why makerware decided to use deb packaging and repositories without matching Debian/Ubuntu releases. Perhaps they are simply shorthanded.
One assumes that the dependencies are available in the Makerware repository, since they seem not in Debian nor Ubuntu.


> **TriforceOfKirby said:**
>  Also how should I get the correct deb file for makerware through wget/web browser?

Good question.
You already have the correct deb file. Apt already downloaded it for you. You told it to do that. The problem is mixing 14.10 and 15.04 sources.
If you didn't have the deb, then usually you find a .deb that's posted on their website.
Alternately, all Debian/Ubuntu repositories are simply URLs, and the file tree is browsable in any web browser.
Example source from my own /etc/apt/sources.list file: [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)

---

### Post by TriforceOfKirby on 2015-05-13
> **ian-weisser said:**
> Excellent questions for the Makerware developers or support community. It is, after all, their software that is incompatible with your release of Ubuntu.
I don't happen to use makerware. I can tell you a *lot* about Ubuntu software and Debian packaging and what install errors mean and how to fix them. But I cannot tell you why makerware decided to use deb packaging and repositories without matching Debian/Ubuntu releases. Perhaps they are simply shorthanded.
One assumes that the dependencies are available in the Makerware repository, since they seem not in Debian nor Ubuntu.

Alright, I'll see if I can contact them.

> **ian-weisser said:**
> Good question.
You already have the correct deb file. Apt already downloaded it for you. You told it to do that. The problem is mixing 14.10 and 15.04 sources.
If you didn't have the deb, then usually you find a .deb that's posted on their website.
Alternately, all Debian/Ubuntu repositories are simply URLs, and the file tree is browsable in any web browser.
Example source from my own /etc/apt/sources.list file: [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)
I suppose makerware is an exception to this: [http://downloads.makerbot.com/makerware/ubuntu/](http://downloads.makerbot.com/makerware/ubuntu/) I'm not able to browse the contents of their repository.

---

### Post by ian-weisser on 2015-05-14
> **TriforceOfKirby said:**
> I suppose makerware is an exception to this: [http://downloads.makerbot.com/makerware/ubuntu/](http://downloads.makerbot.com/makerware/ubuntu/) I'm not able to browse the contents of their repository.

That's a setting on makerbot.com's server. Nothing you or I can do about it.

I am sorry, wish I had a better solution for you.

---

### Post by Shideneyu on 2016-01-27
Found a way:

> 
sudo apt-get download makerware --allow-unauthenticated
sudo dpkg -i makerware_3.7.0-12.04_amd64.deb
sudo apt-get -f install
sudo dpkg -i makerware_3.7.0-12.04_amd64.deb
 


But my beautiful qt51webkit is still missing. I can launch makerware but got this issue:

>  makerware : Depends: qt51webkit but it is not going to be installed
>  /usr/share/makerbot/makerware: symbol lookup error: /usr/lib/x86_64-linux-gnu/libQt5WebKit.so.5: undefined symbol: _ZN7QString23toLatin1_helper_inplaceERS_ 

---

