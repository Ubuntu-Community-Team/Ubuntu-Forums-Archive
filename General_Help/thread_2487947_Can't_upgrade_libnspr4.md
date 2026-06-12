---
title: "Can't upgrade libnspr4"
date: 2023-06-19
forum: General Help
---

### Post by Bucky Ball on 2023-06-19
Hi all,

Wife's computer has needed some TLC for awhile and I'm finally getting around to it. It's an MSI CX62 6QD. At least that's what it says on the box! It's running Xubuntu-core 20.04. The one clue I can give is that this didn't seem to be happening prior to upgrading to 20.04 (via the internet, not fresh install or upgrade from disk). Any further details required, just ask.

Problem is this. I have one package that keeps throwing an error when I try to upgrade it. libnspr4. I can update then upgrade and everything else updates/upgrades just fine, except libnspr4.  So, I do this after an update.

```
sudo apt full-upgrade
```

and I get this.

```
(Reading database ... 258747 files and directories currently installed.)
Preparing to unpack .../libnspr4_2%3a4.25-1_amd64.deb ...
dpkg: error processing archive /var/cache/apt/archives/libnspr4_2%3a4.25-1_amd64
.deb (--unpack):
 unable to open triggers ci file '/var/lib/dpkg/info/libnspr4:amd64.triggers': N
o such device or address
Errors were encountered while processing:
 /var/cache/apt/archives/libnspr4_2%3a4.25-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

When I look in Synaptic, libnspr4 is there and showing it wants to be upgraded, but when I try through Synaptic, it gives me this.

```
E: /var/cache/apt/archives/libnspr4_2%3a4.25-1_amd64.deb: unable to open triggers ci file '/var/lib/dpkg/info/libnspr4:amd64.triggers': No such device or address
```

Under details, it shows this.

```
(Reading database ... 258747 files and directories currently installed.)
Preparing to unpack .../libnspr4_2%3a4.25-1_amd64.deb ...
dpkg: error processing archive /var/cache/apt/archives/libnspr4_2%3a4.25-1_amd64.deb (--unpack):
 unable to open triggers ci file '/var/lib/dpkg/info/libnspr4:amd64.triggers': No such device or address
Errors were encountered while processing:
 /var/cache/apt/archives/libnspr4_2%3a4.25-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

I have hunted about for a fix, but so far, have come up with little. Anyone have any ideas? I will add that, apart from this glitch, the machine appears to be working faultlessly and has been for months. It 'just works' (which is just the way I like it as it means I am not in here every five minutes having to fix something!)

I have thought about uninstalling libnspr4, reinstalling and seeing if that fixes, but, seeing as this is my wife's workhorse and it is currently working fine, apart from this upgrading anomaly, I'd rather not risk breaking the system entirely and spending the next n amount of time trying to nut out a fix or workaround! If you follow me. ;)

Any clues/thoughts welcome and appreciated.

---

### Post by Bashing-om on 2023-06-19
Well Bucky ---

Looking at:
[https://packages.ubuntu.com/search?keywords=libnspr4&searchon=names&suite=focal&section=all](https://packages.ubuntu.com/search?keywords=libnspr4&searchon=names&suite=focal&section=all)
and the version shown is 2:4.25-1:

Makes one wonder where the installed version came from.
What shows
```

apt policy libnspr4

```

"apt show libnspr4" indicates the package as "optional" so here I would think perfectly safe to purge, and if needed to re-install from repo.

[INDENT]just my thought on the matter
[/INDENT]

---

### Post by Bucky Ball on 2023-06-19
Hi Bashing-om. Long time. And thanks for your input. :)

In that case, I will give a purge and reinstall a try and see what gives when I try to update/upgrade again.

As mentioned, this machine was upgraded from, from memory, 16.04 to 18.04 to 20.04 via the terminal and one after the other. I think! It was awhile ago. Maybe that's where things got mixed up. I sure didn't intentionally install the file manually. Don't even know what it is (or didn't until it started throwing this error after the OS upgrade). 

I'll post the output of your command and have a fiddle about when I'm back at that computer a bit later. Thanks again.
___

***Update***: The output was this.

```
~$ apt policy libnspr4
libnspr4:
  Installed: 2:4.18-1ubuntu1
  Candidate: 2:4.25-1
  Version table:
     2:4.25-1 500
        500 http://mirror.aarnet.edu.au/pub/ubuntu/archive focal/main amd64 Packages
 *** 2:4.18-1ubuntu1 100
        100 /var/lib/dpkg/status
```

So the newest is waiting. I checked my own machine and the output looks like yours. As for purging ...

```
~$ sudo apt purge libnspr4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  catdoc cups-ipp-utils evince-common firebird3.0-common firebird3.0-common-doc firebird3.0-server-core
  firebird3.0-utils fonts-crosextra-caladea fonts-crosextra-carlito fonts-dejavu fonts-dejavu-extra fonts-liberation2
  fonts-linuxlibertine fonts-sil-gentium fonts-sil-gentium-basic gimp-data gstreamer1.0-gtk3 java-common libabw-0.1-1
  libamd2 libapache-pom-java libatk-wrapper-java libatk-wrapper-java-jni libbabl-0.1-0 libblas3 libboost-date-time1.71.0
  libboost-iostreams1.71.0 libboost-locale1.71.0 libboost-thread1.71.0 libbsh-java libcamd2 libccolamd2 libcdr-0.1-1
  libcholmod3 libclucene-contribs1v5 libclucene-core1v5 libcmis-0.5-5v5 libcolamd2 libcommons-logging-java
  libcommons-parent-java libde265-0 libe-book-0.1-1 libel-api-java libeot0 libepub0 libepubgen-0.1-1 libetonyek-0.1-1
  libexiv2-27 libexttextcat-2.0-0 libexttextcat-data libfbclient2 libfreehand-0.1-1 libgegl-common libgexiv2-2
  libgfortran5 libgsl23 libgslcblas0 libgspell-1-2 libgspell-1-common libgtkmm-2.4-1v5 libgtkspell0 libgutenprint-common
  libgutenprint9 libgxps2 libheif1 libhsqldb1.8.0-java libib-util libimage-magick-perl libimage-magick-q16-perl
  libjsp-api-java libjuh-java libjurt-java libkpathsea6 liblangtag-common liblangtag1 liblapack3 libmetis5 libmhash2
  libmng2 libmspub-0.1-1 libmwaw-0.3-3 libmypaint-1.5-1 libmypaint-common libmythes-1.2-0 libneon27-gnutls
  libodfgen-0.1-1 liborcus-0.15-0 libpagemaker-0.0-0 libpotrace0 libpq5 libraptor2-0 librasqal3 libraw19 librdf0
  libreoffice-common libreoffice-java-common libreoffice-style-colibre libreoffice-style-elementary
  libreoffice-style-tango librevenge-0.0-0 libridl-java libservlet-api-java libservlet3.1-java libspectre1
  libsuitesparseconfig5 libsynctex2 libtommath1 libumfpack5 libuno-cppu3 libuno-cppuhelpergcc3-3
  libuno-purpenvhelpergcc3-3 libuno-sal3 libuno-salhelpergcc3-3 libunoil-java libunoloader-java libvisio-0.1-1
  libwebsocket-api-java libwpd-0.10-10 libwpg-0.3-3 libwps-0.4-4 libxmlsec1 libyajl2 libzip5 lp-solve musescore3-common
  python-backports.functools-lru-cache python-bs4 python-chardet python-html5lib python-lxml python-numpy
  python-pkg-resources python-scour python-setuptools python-six python-soupsieve python-webencodings python3-bs4
  python3-html5lib python3-lxml python3-pikepdf python3-scour python3-soupsieve python3-webencodings scour
  uno-libs-private ure
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  foomatic-filters libpaps0 paps
Recommended packages:
  poppler-utils
The following packages will be REMOVED:
  bluez-cups* ca-certificates-java* cups* cups-core-drivers* cups-filters* cups-filters-core-drivers* default-jre*
  default-jre-headless* evince* gimp* gir1.2-poppler-0.18* hplip* inkscape* libblockdev-crypto2* libevdocument3-4*
  libevview3-3* libgegl-0.4-0* libgimp2.0* libkf5filemetadata-bin* libnspr4* libnss3* libpoppler-cpp0v5*
  libpoppler-glib8* libpoppler-qt5-1* libpoppler97* libreoffice* libreoffice-base* libreoffice-base-core*
  libreoffice-base-drivers* libreoffice-calc* libreoffice-core* libreoffice-draw* libreoffice-gnome* libreoffice-gtk3*
  libreoffice-impress* libreoffice-librelogo* libreoffice-math* libreoffice-nlpsolver* libreoffice-report-builder*
  libreoffice-report-builder-bin* libreoffice-script-provider-bsh* libreoffice-script-provider-js*
  libreoffice-script-provider-python* libreoffice-sdbc-firebird* libreoffice-sdbc-hsqldb* libreoffice-sdbc-postgresql*
  libreoffice-wiki-publisher* libreoffice-writer* libvolume-key1* libxmlsec1-nss* musescore3* openjdk-11-jre*
  openjdk-11-jre-headless* openjdk-8-jre* openjdk-8-jre-headless* pdfarranger* pdfshuffler* poppler-utils*
  printer-driver-foo2zjs* printer-driver-gutenprint* printer-driver-hpcups* printer-driver-splix* python3-uno*
  signal-desktop* skypeforlinux* tumbler*
The following NEW packages will be installed:
  foomatic-filters libpaps0 paps
0 to upgrade, 3 to newly install, 66 to remove and 0 not to upgrade.
Need to get 109 kB of archives.
After this operation, 1,425 MB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.

```

It doesn't look safe to continue to me, but don't really know enough to know ... [s]What does the asterix signify next to the pakcages to be removed?[/s] Duh. Wildcards. Been awhile. 

Despite the 'purge' command telling me I have packages to 'sudo apt autoremove', when I try, the output is

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 1 not to upgrade.
```

... and the '1 not to upgrade' is, of course ...

---

### Post by Bashing-om on 2023-06-19
Bucky Ball; Hey 

I can understand that from an old 16.04 install there would be a *LOT* of cruft left behind. Were me I would trust the package manager and do that:
```

sudo apt --purge autoremove
sudo apt update
sudo apt upgrade

```
then see what we look like:
```

sudo apt -f install
sudo dpkg -C

```

[INDENT]me likes clean
[/INDENT]

---

### Post by Bucky Ball on 2023-06-20
Me likes clean too. Appears the only thing that's stopping this from upgrading to the new version is that the old one is locked in place. Somehow. Now, if only I knew how to unlock it, should upgrade a breeze! 

I'll try that purge, but I'm nervous. As I say, not my computer and can't really spend days fixing this if things go pear-shaped. Maybe I'll do a backup first.

Just thinking, though: wouldn't a purge remove ALL files of the package? Like configuration files? So when those packages are then reinstalled, they will be like fresh, brand newly installed packages/programs with none of the configuration they had previously? In other words, they will need to be set up again to be 'as they were' prior to the purge?

That will not be a good outcome if this is so. Could be a case of me running from the house with wife close behind wielding a sharp or blunt object ... or both! :|

Perhaps a remove rather than a purge? As I understand it, that would leave the config files and ... hang on; the config file might be why libnspr4 is locked in the first place. I wouldn't know. 

Just thinking out loud here. Do excuse ... :)

---

### Post by Bashing-om on 2023-06-20
Bucky Ball; Yeah ---

purge removes the config files --- but as the package manager considers sooo many files as obsolete - and we do want clean - and *IF* they are no longer required (autoremove) then removing also the config files will be a good thing. --- One can always do a dry run and check what the package manager will remove.

I refrain from speculating what my other half would inflict on me if I break her system !

edit - nother thought >>
we can look at what config files might be removed !
```

dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P

```
"While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package "

edit2 --- nawww - just tested and dpkg does not offer " are you sure" it just wipes away !
[INDENT]safety is no accident
[/INDENT]

---

### Post by Bucky Ball on 2023-06-20
I found this.

[https://installati.one/ubuntu/21.10/libnspr4/](https://installati.one/ubuntu/21.10/libnspr4/)

Specifically under this heading down the page.

> How To Uninstall libnspr4 on Ubuntu 21.10

The commands state nothing specific about 21.10, so figuring it would be same procedure for 20.04. 

Wish me luck. Going to start from the beginning and persevere until I can upgrade libnspr4. I's nervois!
___

Yep, and nervous I should have been. A dead set screw up that was. I ran ...

```
sudo apt-get remove libnspr4
```

... and just spent the last half an hour re-installing Skype, Signal, Libreoffice. And they're the ones I know got killed. No doubt my wife will be able to fill me in on what else is missing. A nightmare. So, I am stuck. 

In the process of running that command, it began removing things then got to the one - and only - thing I actually did want to remove, and threw this at me.

```
Removing libnspr4:amd64 (2:4.18-1ubuntu1) ...
dpkg: error processing package libnspr4:amd64 (--remove):
 unable to open triggers ci file '/var/lib/dpkg/info/libnspr4:amd64.triggers': No such device or address
dpkg: too many errors, stopping
Errors were encountered while processing:
 libnspr4:amd64
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Absolutely no idea how to resolve this without completely reinstalling and starting again. That is not an immediate option and definitely one I'd rather avoid, as you can imagine! Grim.

---

### Post by Bashing-om on 2023-06-20
Bucky Ball - Yukkie-Poo all over !

I would never have thunk such an outcome :(
It is an "optional" package !

Pardon me please !

Back to the situation at hand >>
My system:
> 
sysop@x2204mini:~$ apt show libnspr4
Package: libnspr4
Version: 2:4.32-3build1
Priority: optional
<snip>

sysop@x2204mini:~$ dpkg -l libnspr4
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWai>
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Architecture Description
+++-==============-==============-============-====================>
ii  libnspr4:amd64 2:4.32-3build1 amd64        NetScape Portable Ru>

sysop@x2204mini:~$ ls -al /var/lib/dpkg/info/libnspr4:amd64.triggers
-rw-r--r-- 1 root root 72 Mar 24  2022 /var/lib/dpkg/info/libnspr4:amd64.triggers
sysop@x2204mini:~$ 


Whereas in your case that .triggers file does not exist per the error report.

As we can not remove it --- can we re-install it ?
```

sudo apt install --reinstall libnspr4

```
What now does the package manager say ?

[INDENT]help to clean up the mess[/INDENT]

---

### Post by MAFoElffen on 2023-06-21
As I googled "problems with libnspr4" it comes up as a runtime library for Netscape... Which may jog some of our memories, but then confuse us asking, still, why would that get installed? Well, digging deeper, it used to be a depends for the Adobe Flash runtime / player. <-- That is why it is probably still there, on a system that has evolved over many do-release-upgrades. That is my best guess.

On '/var/lib/dpkg/info' this is what I found from here: [https://askubuntu.com/questions/805476/is-the-size-of-my-var-lib-dpkg-info-too-big](https://askubuntu.com/questions/805476/is-the-size-of-my-var-lib-dpkg-info-too-big)
> 
/var/lib/dpkg/info contains files that relate to packages - including the list of files (as full path names) provided by each package, the MD5sums of each of these files, and the executable scripts that would be run before and after installation or removal (preinst, postinst, prerm, postrm). Of course the system contains many, many packages and each one has multiple files here.

The more packages you install, the bigger this directory will get.

This directory is really important to the system. You should never delete anything from it, and if you do, you can expect bad bad bad things to occur.

So, if there were a problem with a file there, related to libnspr4, that is why it is having you are having a problem uninstalling it...

I think the safest bet is to first do install --reinstall, so that it replaces those files. Then it could probably be removed... If in question on something like that, I'll do a dry-run and see what it would have tried to do, beforehand. 

I don't see a current use for it. Strange that it uninstalled all that along with it.

EDIT: I am not immune. I have done that before and regretted it later.  Usuually when I'm in a hurry. That is why, now, if in question, I'll do
```

sudo apt remove -s <package-name>

```
I try to learn from my mistakes. Things do happen.

---

### Post by Bucky Ball on 2023-06-22
> **Bashing-om said:**
> Bucky Ball - Yukkie-Poo all over !

I would never have thunk such an outcome :(
It is an "optional" package !

Pardon me please !

Yuckie poo indeedy! All good. We can but try. Thankfully, after reinstalling those few things, wife has been working away feverishly on the machine and has nothing negative to report, so disaster averted.

> As we can not remove it --- can we re-install it ?
```

sudo apt install --reinstall libnspr4

```
What now does the package manager say ?

It says

```

~$ sudo apt install --reinstall libnspr4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libnspr4
1 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 0 B/107 kB of archives.
After this operation, 8,192 B disk space will be freed.
(Reading database ... 248379 files and directories currently installed.)
Preparing to unpack .../libnspr4_2%3a4.25-1_amd64.deb ...
dpkg: error processing archive /var/cache/apt/archives/libnspr4_2%3a4.25-1_amd64
.deb (--unpack):
 unable to open triggers ci file '/var/lib/dpkg/info/libnspr4:amd64.triggers': N
o such device or address
Errors were encountered while processing:
 /var/cache/apt/archives/libnspr4_2%3a4.25-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Not much diff.
___

> **MAFoElffen said:**
> As I googled "problems with libnspr4" it comes up as a runtime library for Netscape... Which may jog some of our memories, but then confuse us asking, still, why would that get installed? Well, digging deeper, it used to be a depends for the Adobe Flash runtime / player. <-- That is why it is probably still there, on a system that has evolved over many do-release-upgrades. That is my best guess.

Yep, I noticed somewhere a while ago it had something to do with Netscape and did scratch my head. And I'd say your best guess is close if not spot on as this has evolved through a few upgrades and, because of the version of libnspr4 that's being problematic, looks like it has been lurking for awhile. Wonder when the version suddenly changed from this one to the 20.04 version? This has not reared its head previously. 

> I think the safest bet is to first do install --reinstall, so that it replaces those files. Then it could probably be removed... If in question on something like that, I'll do a dry-run and see what it would have tried to do, beforehand. 

I don't see a current use for it. Strange that it uninstalled all that along with it.

Strange indeed. See above for result of attempting to install --reinstall. Anyhow, I tried to remove after running that and still wants to kill a bunch of apps.

> EDIT: I am not immune. I have done that before and regretted it later.  Usuually when I'm in a hurry. That is why, now, if in question, I'll do
```

sudo apt remove -s <package-name>

```

Thanks for the tip. Running that command for removing libnspr4, I see what it wants to remove 

```
The following packages will be REMOVED:
  ca-certificates-java default-jre default-jre-headless libnspr4 libnss3
  libpoppler97 libreoffice libreoffice-base libreoffice-base-core
  libreoffice-base-drivers libreoffice-calc libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk3 libreoffice-impress libreoffice-math
  libreoffice-nlpsolver libreoffice-report-builder
  libreoffice-report-builder-bin libreoffice-script-provider-bsh
  libreoffice-script-provider-js libreoffice-script-provider-python
  libreoffice-sdbc-firebird libreoffice-sdbc-hsqldb libreoffice-sdbc-mysql
  libreoffice-sdbc-postgresql libreoffice-wiki-publisher libreoffice-writer
  libxmlsec1-nss openjdk-11-jre openjdk-11-jre-headless python3-uno
  signal-desktop skypeforlinux
0 to upgrade, 0 to newly install, 35 to remove and 0 not to upgrade.
```

So, confirms it wants to kill similar to what it did last time I attempted to remove using 'sudo apt-get remove libnspr4'. Last time, during the process of removing libnspr4, it removed Signal, Skype and Libreoffice and fell over at the one thing I actually wanted to remove; libnspr4.
___

I may need to resign myself to the fact that I am going to have to reinstall at least Skype, Signal and Libreoffice at some point to get to the bottom of this. That's all fine, but my concern is that I'll drop the configuration files or some other vital data. When I reinstalled those apps last time this went pear-shaped, all came back exactly as they had been, all Skype contacts etc. present, same with Signal and conversations/contacts. Libreoffice recent documents populated, etc.

So I should be reassured this is going to be fine! I am confident it is not going to rip the heart out of 20.04 and leave me with a non-functional OS, so there's one positive ... ;) Appreciate your help.

---

### Post by MAFoElffen on 2023-06-22
Just a thought... If you do 'apt remove' without the --purge flag, then it should leave the configuration files... That might be easier on you when you go to reinstall applications. 

Another thought-- If you run the UbuntuForums 'system-info' script in my signature line, it has a section near the end for User Installed Packages. When I added that to the script, that came one of my scripts that I do for migrations... I take that list and use is as an array, then make a loop to install those applications again. Then I restore the config files for them.

LOL. Yes. I figure the heart of Ubuntu is 'Ubuntu Base'... If I can get the Kernel to boot to a Console, I have a chance do a lot of things to get things back together. I have nVidia. The nVidia graphics drivers have always been a risk during an update.

---

### Post by Bucky Ball on 2023-06-22
> **MAFoElffen said:**
> Just a thought... If you do 'apt remove' without the --purge flag, then it should leave the configuration files... That might be easier on you when you go to reinstall applications.

What I was hoping. The config files were there when I reinstalled the apps last time, thankfully. I'd just used the first instruction from here to uninstall the file, from memory.

[https://installati.one/ubuntu/21.10/libnspr4/](https://installati.one/ubuntu/21.10/libnspr4/) 

> Another thought-- If you run the UbuntuForums 'system-info' script in my signature line, it has a section near the end for User Installed Packages. When I added that to the script, that came one of my scripts that I do for migrations... I take that list and use is as an array, then make a loop to install those applications again. Then I restore the config files for them.


Will think further about this and experiment later.

> LOL. Yes. I figure the heart of Ubuntu is 'Ubuntu Base'... If I can get the Kernel to boot to a Console, I have a chance do a lot of things to get things back together. I have nVidia. The nVidia graphics drivers have always been a risk during an update.

Funny you should mention that, because whilst fiddling around trying to fix this on that machine, I noticed the nvidia driver was at about 450 or something and there was 530 available. I updated to that one in 'Software & Updates' and ... the machine stopped resuming when I opened the lid! Will reinstall the old one when back at that machine, among other things. Cheers.

---

### Post by Bucky Ball on 2023-07-02
Sorry about the delay. Had a few issues. Just an update to say that my wife's been flat out on that computer, so haven't had the chance to do much on it. When I have, I will bite the bullet and remove  libnspr4 and put the pieces back together from there.

She has noticed one other very strange anomaly that wasn't happening before trying to remove that file. In Libreoffice, when she tries to print multiple copies of a document, it won't. One copy and stops. Spent about an hour and a half trying to nut that out last night, but will remove libnspr4 and then post separate threads about any negative consequences that I can't get my head around. 

Will post back when I've had a good go at getting rid of that file again. ;)

---

