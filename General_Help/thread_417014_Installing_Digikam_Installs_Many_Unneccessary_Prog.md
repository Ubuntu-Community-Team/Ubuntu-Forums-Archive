---
title: "Installing Digikam Installs Many Unneccessary Programs"
date: 2007-04-21
forum: General Help
---

### Post by nrwilk on 2007-04-21
I have found a strange bug in the Digikam package in the repositories.

When I try to install digikam, it tries to install a bunch of other stuff which is NOT required by digikam.

I finally gave up and installed it all, and then I was able to delete all the unneccessary software, but this is still annoying.

Just thought I'd verify that other users are experiencing this before I make a bug report.

Thanks! :)

---

### Post by ajgreeny on 2007-04-21
What were these files that you say are not dependencies of digikam.  Are you sure they are not kde lib packages which are needed.  Don't forget digikam is a kde package rather than gnome, and therefor needs many packages not in ubuntu by default.

When I installed digikam it also installed:-

[I]dcraw (7.94-1ubuntu1)
digikamimageplugins (0.8.0-1-1ubuntu1)
kipi-plugins (0.1+rc1-1ubuntu2)
libimlib2 (1.2.1-2)
libkexif1 (0.2.2-2ubuntu2),[/I]
and of course
[I]digikam (0.8.2~rc1-0ubuntu3)
[/I]
OK, I don't have to have the plugins, though they are very useful, nor the dcraw if I don't use raw data for my photos (which I don't) but this hardly means a great load of packages that are not needed.

---

### Post by nrwilk on 2007-04-21
Yes, I know the required dependencies.  Also, I run KDE, and it was not trying to install KDE libs (these are all already installed).

It was trying to install kooka, postfix, kmail, ocrad, procmail, ssl-cert, and the dependencies for these programs.

None of those are anywhere close to being digikam dependencies.

Thanks for the try, though. :)

[COLOR="Red"]**EDIT:**[/COLOR]

Here is the complete output from aptitude:
```
user@domain:~$ sudo aptitude install digikam
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  digikamimageplugins exiv2 kdepim-kio-plugins kipi-plugins kmail kooka
  libexiv2-0.12 libid3tag0 libimlib2 libkexiv2-0 libkipi0 libkmime2
  libkpimidentities1 libksieve0 libmimelib1c2a libungif4g ocrad postfix
  procmail ssl-cert
The following NEW packages will be installed:
  digikam digikamimageplugins exiv2 kdepim-kio-plugins kipi-plugins kmail
  kooka libexiv2-0.12 libid3tag0 libimlib2 libkexiv2-0 libkipi0 libkmime2
  libkpimidentities1 libksieve0 libmimelib1c2a libungif4g ocrad postfix
  procmail ssl-cert
0 packages upgraded, 21 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/17.4MB of archives. After unpacking 59.9MB will be used.
Do you want to continue? [Y/n/?]
```

Now I will hit y and it will install all this stuff.  After that, I can remove the packages I don't want, but this is still not what should be happening.

---

### Post by ajgreeny on 2007-04-22
Agreed!  Totally baffling why this should happen.  It certainly didn't to me, so there must be something else involved here.

---

### Post by theseeker on 2007-05-18
Same problem here:

```

$ sudo aptitude install digikam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  digikamimageplugins enscript k3b kaddressbook kcontrol kdebase-data 
  kdepim-kio-plugins kdeprint kfind kicker kipi-plugins kmail konqueror 
  kooka libgpgme11 libimlib2 libkcal2b libkdepim1a libkexiv2-0 libkipi0 
  libkleopatra1 libkmime2 libkpimidentities1 libkscan1 libksieve0 libktnef1 
  libmimelib1c2a poster postfix procmail psutils sane-utils 
The following NEW packages will be installed:
  digikam digikamimageplugins enscript k3b kaddressbook kcontrol 
  kdebase-data kdepim-kio-plugins kdeprint kfind kicker kipi-plugins kmail 
  konqueror kooka libgpgme11 libimlib2 libkcal2b libkdepim1a libkexiv2-0 
  libkipi0 libkleopatra1 libkmime2 libkpimidentities1 libkscan1 libksieve0 
  libktnef1 libmimelib1c2a poster postfix procmail psutils sane-utils 
0 packages upgraded, 33 newly installed, 0 to remove and 0 not upgraded.
Need to get 44.1MB of archives. After unpacking 124MB will be used.
Do you want to continue? [Y/n/?] n
Abort.

```

I'm not aware of what all those lib packages are for, but certainly k3b, kmail etc. are not required dependencies for digikam to install!

What's wrong?

---

### Post by carlosqueso on 2007-05-18
Aptitude installs suggested packages too....try using apt-get instead: ```
sudo apt-get install digikam
``` and it should just install the dependencies.

---

### Post by Sweet Spot on 2007-07-27
I am about to install DK, but noticed TWICE *(restarted terminal to make sure) that sudo aptitude install digikam is not only adding things which dk doesn't need, but it's doing it TWICE in one shot ! Exact: > Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  digikamimageplugins enscript exiv2 graphicsmagick 
  graphicsmagick-imagemagick-compat k3b kaddressbook kamera kcontrol 
  kdebase-bin kdebase-data kdebase-kio-plugins kdelibs-data kdelibs4c2a 
  kdemultimedia-kio-plugins kdepim-kio-plugins kdeprint kdesktop kfind 
  kicker kipi-plugins kmail konqueror kooka libakode2 libarts1-akode 
  libarts1c2a libavahi-qt3-1 libdbus-qt-1-1c2 libexiv2-0.12 libflac++5c2 
  libgpgme11 libgraphicsmagick1 libimlib2 libiso9660-4 libk3b2 libkcal2b 
  libkcddb1 libkdepim1a libkexiv2-0 libkipi0 libkleopatra1 libkmime2 
  libkonq4 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblua50 
  liblualib50 libmimelib1c2a libopenexr2c2a libpcre3 libqt3-mt 
  libsamplerate0 libvcdinfo0 ocrad perl-suid pmount poster postfix procmail 
  psutils sane-utils vcdimager 
The following NEW packages will be installed:
  digikam digikamimageplugins enscript exiv2 graphicsmagick 
  graphicsmagick-imagemagick-compat k3b kaddressbook kamera kcontrol 
  kdebase-bin kdebase-data kdebase-kio-plugins kdelibs-data kdelibs4c2a 
  kdemultimedia-kio-plugins kdepim-kio-plugins kdeprint kdesktop kfind 
  kicker kipi-plugins kmail konqueror kooka libakode2 libarts1-akode 
  libarts1c2a libavahi-qt3-1 libdbus-qt-1-1c2 libexiv2-0.12 libflac++5c2 
  libgpgme11 libgraphicsmagick1 libimlib2 libiso9660-4 libk3b2 libkcal2b 
  libkcddb1 libkdepim1a libkexiv2-0 libkipi0 libkleopatra1 libkmime2 
  libkonq4 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblua50 
  liblualib50 libmimelib1c2a libopenexr2c2a libpcre3 libqt3-mt 
  libsamplerate0 libvcdinfo0 ocrad perl-suid pmount poster postfix procmail 
  psutils sane-utils vcdimager 
0 packages upgraded, 66 newly installed, 0 to remove and 0 not upgraded.
Need to get 75.2MB of archives. After unpacking 222MB will be used.
Does sudo aptitude do this with ALL programs you try and install ? If so, I'll NEVER use it ! Synaptic seems a better way to go at this point if that's the case. 

Second question in regards to DK, is photo show needed, or is it also just suggested. I want to use DK to edit/touch up pics and also use it as a pic/album viewer. I'm asking because in Synaptic, it's listed amongst the items that came up with I did a search for DK. 

Doug

---

### Post by yabbadabbadont on 2007-07-27
As was stated in a previous post, aptitude will, by default, install all recommended packages in addition to those that are required.  Use apt-get or synaptic and you won't see this behavior.  Or you can just run the interactive aptitude, go to the settings menu, then dependency handling, then uncheck the "consider recommended packages as requirements".

---

### Post by Sweet Spot on 2007-07-27
Sure, I got that but... why in my case is it installing the same dependencies (needed and not needed ones) twice ?  That seems like a bigger bug than originally seen. 

Doug

BWT, installed via Synaptic. Digikam is a brilliant program ! Definitely worth going against my not wanting to install anything non Gnome native....   But, is Showfoto necessary, or is it just based off of digicam and pretty much redundant ?

---

### Post by yabbadabbadont on 2007-07-28
> **Sweet Spot said:**
> Sure, I got that but... why in my case is it installing the same dependencies (needed and not needed ones) twice ?  That seems like a bigger bug than originally seen. 

You need to read the output a little more closely.  :D

```
The following NEW packages will be automatically installed:
```
and
```
The following NEW packages will be installed:
```
These are two **different** bits of information that, in this case, happen to show the same thing.  It is *not* telling you that the packages will be installed twice.  ;)

---

### Post by Sweet Spot on 2007-07-28
Gotcha. So it's just reiterating the initial statement basically...  Still, AFAIC, this is a really bad bug. If we're expected to use aptitude, it shouldn't  just have free reign over what it THINKS it should install for you. It should just install the things that the program(s) are dependent on. That's why they're called dependencies, not 'thinkyoushouldusethistooencies' ! :)

Thanks.

---

### Post by yabbadabbadont on 2007-07-28
> **Sweet Spot said:**
> Gotcha. So it's just reiterating the initial statement basically...  Still, AFAIC, this is a really bad bug. If we're expected to use aptitude, it shouldn't  just have free reign over what it THINKS it should install for you. It should just install the things that the program(s) are dependent on. That's why they're called dependencies, not 'thinkyoushouldusethistooencies' ! :)

Thanks.
No, it isn't reiterating the initial statement.  The first section tells you which packages are needed **in addition** to those that you specified to be installed.  The second section tells you **all** the packages that are going to be installed.  For example, if you had listed twenty packages to be installed on the command line and there was only one extra package that was needed, that you hadn't listed, then only that one package would be listed in the first section.  :)

Who says that you are supposed to use aptitude?  Just about every guide I've seen (for feisty) tells you to stick with apt-get on the command line or use either Synaptic (in gnome) or Adept (in KDE).  Aptitude's behavior can easily be changed, (I told you how), using its preferences menu.  Just because you don't happen to like the default setting does not mean that it is a "bug".  ;)

---

