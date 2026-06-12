---
title: "OpenSCAM - yes,really !"
date: 2014-08-29
forum: General Help
---

### Post by grey1beard on 2014-08-29
I'm running 12.04, and Linuxcnc for my cnc machine.
I've been recomended OpenSCAM(bizarre name) as a 3d graphical visualiser of the machine cutting.
Having run into a problem with getting the installed program to run, I posted onto the linuxcnc first, but the op there is running windows.
A search of the forum here for openscam produces no results, which surprises me.

If anyone is using it, I'd be grateful for some help.

I'll add more details of my attempt so far, if anyone is willing to take on the challenge !

John

---

### Post by dragonfly41 on 2014-08-29
I've no experience with OpenSCAM .. but I see from the OpenSCAM manual (installation) that it installs via gdebi.

One thought. Did you use the GUI version of Gdebi (from Ubuntu Software Centre) instead of command line .. since the GUI usually shows up any dependencies required for *.deb packages.

---

### Post by grey1beard on 2014-08-29
Hi Dragonfly.
Details of what I've done so far - 
From the OpenSCAM page, I downloaded the version for my 32 bit system - openscam_0.2.5_i386.deb
[I]To install any of the Linux .deb packages open a terminal and go to the directory where you downloaded the package and run the following commands:
[/I] [B]sudo apt-get install gdebi
sudo gdebi openscam_*.deb[/B]
[I]In Linux, if you've installed a package, you should find OpenSCAM in system menu under Other. Alternatively, you can open a terminal and run openscam.
[/I]
It was listed, and it appeared to start loading, but failed, so I tried 'openscam' in a Terminal. However this didn't work either, so I googled for help, and I found an answer on the askubuntu.com page, where the same problem is asked, by someone else running 12.04.
This involved using the following code in terminal - 
**sudo apt-get install libgtkglext1 libc6 bzip2 zlib1g libexpat1 openssl libgtk2.0-0 libglade2-0 freeglut3 sqlite3**
which I did.
During that install, I noted several files were the 'newest version', but one oddity I spotted -
[I]libglade2-0 is already the newest version.
libglade2-0 set to manually installed.[/I]
Not sure if that is relevant as I don't know what it means.

Then running openscam in terminal gave the following error -
[I]openscam: error while loading shared libraries: libboost_regex.so.1.40.0: cannot open shared object file: No such file or directory
[/I]
The next suggestion from the original linuxcnc user was to run *sudo apt-get install libboost-regex, or possibly libboost-regex-dev*, and admitted then that he was running it on windows.
I have tried the first, but this threw up another error 'couldn't find libboost-regex' ,and so far have not tried the second suggestion, as I then decided to open another thread here.

Regards
John

---

### Post by dragonfly41 on 2014-08-29
Following up those latter clues ..

Launch Applications > Ubuntu Software Centre

search "libboost_regex"

Select for installation:-

Regular expression library for C++
libboost-regex1.49.0
and
libboost-regex1.49-dev

Try again.

**[later edit]**

I've just noticed that your OpenScam is looking for libboost-regex**1.40.0** ..and not libboost-regex**1.49.0** as I have suggested.

So check that you have at least version installed (I don't see libboost-regex1.40.0 in my Ubuntu 12.04 Software Centre). 
My default version is 1.46.1.

Also try this ...

sudo updatedb .. you will have to wait quite a while while your files are indexed.
then when you see your command prompt again

**sudo locate libboost-regex**

to see what is installed.

Here is my output ...

```
/usr/share/doc/libboost-regex1.46.1
/usr/share/doc/libboost-regex1.46.1/NEWS.Debian.gz
/usr/share/doc/libboost-regex1.46.1/README.Debian.gz
/usr/share/doc/libboost-regex1.46.1/changelog.Debian.gz
/usr/share/doc/libboost-regex1.46.1/copyright
/usr/share/lintian/overrides/libboost-regex1.46.1
/var/lib/dpkg/info/libboost-regex1.46.1.list
/var/lib/dpkg/info/libboost-regex1.46.1.md5sums
/var/lib/dpkg/info/libboost-regex1.46.1.postinst
/var/lib/dpkg/info/libboost-regex1.46.1.postrm
/var/lib/dpkg/info/libboost-regex1.46.1.shlibs
```


Also tried **sudo locate libboost_regex.so** .. (note underscore instead of hyphen in earlier search)

returned ... /usr/lib/libboost_regex.so.1.46.1

---

### Post by grey1beard on 2014-08-29
Followed your suggestion, and I get exactly the same terminal output as you have posted.
When I searched the Software Centre, I was offered 1.48.0 and 1.48-dev as the highest version.
Also noted that while I have 1.46.1 installed, I don't have 1.46-dev, so I wonder if that might be the problem ?
John

---

### Post by dragonfly41 on 2014-08-29
add 46.dev .. and try .. you can always uninstall via Ubuntu Software Centre.

---

### Post by grey1beard on 2014-08-29
It's still looking for 1.40.1, so I'll check for the latest version of openscam next.
John

---

### Post by grey1beard on 2014-08-29
It's a big thumbs down fom the author himself.
I've found a page on Github where the author quotes that 'OpenSCAM does not work on Ubuntu 12.04'.
Although the question was originally aimed at the 64-bit version, I take it to be more general, so I'm prepared to abandon further efforts.
Thanks for your help dragonfly.
PS if you're into dragons as well, you could find me at the end of a Dragon Hedge ;)

John

---

### Post by dragonfly41 on 2014-08-29
I found that out myself ...

To save time I just downloaded openscam_0.2.5_i386.deb to try installing on my Ubuntu 12.04.

I launched GDebi from Applications > System Tools > GDebi Package Installer.

File > Open > openscam_0.2.5_i386.deb

Package: openscam
**Status: All dependencies are satisfied**

Clicked on install package.

In the terminal window in GDebi ...

Selecting previously unselected package openscam.
(Reading database ... 487014 files and directories currently installed.)
Unpacking openscam (from .../openscam_0.2.5_i386.deb) ...
Setting up openscam (0.2.5) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...


Package 'openscam_0.2.5_i386.deb' was installed.

Close



...

went to Applications > Other > OpenSCAM

but no GUI launched

tried in command terminal:

openscam
openscam: error while loading shared libraries: libv8.so.3.14.5: cannot open shared object file: No such file or directory.


searched .. found this ...

[https://launchpad.net/ubuntu/trusty/+package/libv8-3.14.5](https://launchpad.net/ubuntu/trusty/+package/libv8-3.14.5)

But for **Ubuntu Trusty**.

So this points to it being Ubuntu **14.04** compatible.

Perhaps now is the time to email the Maintainer: Joseph Coffland <joseph@cauldrondevelopment.com>

---

### Post by grey1beard on 2014-08-29
Getting out of my depth(again), so I think I'll just stick to cutting the hedge !

John

---

### Post by grey1beard on 2014-08-30
Have now removed OpenSCAM from my system, so if anyone reading this can suggest an alternative, providing that it is known to work in 12.04, please post.

Regards all,
John

---

### Post by dragonfly41 on 2014-08-30
I'm also closing down my testing of OpenSCAM (which was installed on 12.04 for curiosity only) .. but some closing thoughts .. anything here ... [www.linuxcnc.org?](www.linuxcnc.org?)

[http://www.linuxcnc.org/index.php/italian/forum/49-basic-configuration/27846-cartesian-g-code-to-cylindrical-machine-coordinate?start=10](http://www.linuxcnc.org/index.php/italian/forum/49-basic-configuration/27846-cartesian-g-code-to-cylindrical-machine-coordinate?start=10)

[http://article.gmane.org/gmane.linux.distributions.emc.user/52401](http://article.gmane.org/gmane.linux.distributions.emc.user/52401)

[http://www.shapeoko.com/wiki/index.php/Previewing_G-Code](http://www.shapeoko.com/wiki/index.php/Previewing_G-Code)

Good luck with your project.

---

### Post by markdashabout on 2014-10-21
I was using openscam on my 12.04 system (32 bit) until yesterday. Its a great program and works well and reliably, at least it did. Then I updated a bunch of stuff including qt libraries and now it just segfaults on startup. 
This is so frustrating - update hell is one of the reasons that I first started using Linux back in 2000, and here we are 14 years later with the same old problems. I have emailed Cauldren Development, see if they respond, but another post states its the broken qt libraries on 12.04. 

Its been broken a while, but this is a good program that works well, if you can get it to work at all.

---

### Post by stalkingwolf on 2014-10-21
try running recovery mode then fix broken packages.   also check that updates are current.

---

### Post by markdashabout on 2014-10-21
I tried that - or something quite similar that resulted in an update of all packages to the latest 12.04. I hate that, initram, kernel everything got updated. I rebooted with bated breath, expecting a cryptic message about X ... and 
everything worked flawlessly. 

I tried openscam, and that works too!. 

Really happy that you made me do this!!

---

### Post by johnnycatt on 2015-09-09
> **dragonfly41 said:**
> 


tried in command terminal:

openscam
openscam: error while loading shared libraries: libv8.so.3.14.5: cannot open shared object file: No such file or directory.

>

NOT FOR NOTHING, but I got this error, too... I went to the Ubuntu software center and searched for "libv8.so.3.14.5"

I installed that and then just clicked the icon to run openSCAM... it opened right up and functioned normally...

good luck!

---

