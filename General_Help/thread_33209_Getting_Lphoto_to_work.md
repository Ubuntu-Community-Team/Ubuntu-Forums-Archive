---
title: "Getting Lphoto to work"
date: 2005-05-09
forum: General Help
---

### Post by greenwom on 2005-05-09
Ok (newbee)
Lphoto is a linspire supported piece of software that I want.

I grabbed the source code [Lphoto pool](http://software.linspire.com/pool-src/l/lphoto/) 

I extracted the tar file in gnome.

in the terminal I ran 'make'
[COLOR=Navy]mike1@mikesubuntu:~/marlin_build_lphoto-1.0$ make
python2.3 install.py
Sorry, please install PyQt.
make: *** [install] Error 1[/COLOR]

So I ran 'apt-get install pyqt-tools'  - that installed fine but I get the same error above.

So I downloaded a different PYQT file that need a SIP file none of these worked.

Am I chasing a dream here as a newbee, maybe someones done it already
Let me know :)

---

### Post by lt_kije on 2005-05-09
When you compile programs, you generally need to install Ubuntu packages that end with "-dev." In this case, I suggest (although I haven't tried compiling Lphoto) installing python-qt-dev. Also, have you tried the f-spot program included with the Ubuntu repositories? I just downloaded it today, and it runs great. I quite like it. See if it meets your needs: [http://www.gnome.org/projects/f-spot/](http://www.gnome.org/projects/f-spot/).

Good luck,
lt_kije

---

### Post by DutchLau on 2005-05-09
In order to use the "make" command, you need a C++ compiler (I believe)

Open up a terminal and do this:

> sudo apt-get install build-essential 

Now try doing that again, hopefully it should work  :razz: 

DutchLau

---

### Post by greenwom on 2005-05-10
Fspot is just a mangement program to organize your pics (from what I've read)

I also have 'build-essentials' installed, I've already complied my kernal once and rane 'make' on different software so I know (think) I've got all the apps installed.....  Right now it looks like I need a certian version of PyQt



Lphoto has the ability to take your pics and edit them on a timeline and put music in the background.  you can then burn it to VCD (I hope a DVD format will be added)

Anyway I still haven't figured this out.

---

### Post by lt_kije on 2005-05-10
[QUOTE=greenwom]Fspot is just a mangement program to organize your pics (from what I've read)[/QUOTE]

Yep, that's true. I did see the bit about Lphoto doing image editing, etc.

[QUOTE=greenwom]I also have 'build-essentials' installed, I've already complied my kernal once and rane 'make' on different software so I know (think) I've got all the apps installed.....  Right now it looks like I need a certian version of PyQt[/QUOTE]

Did you try to install python-qt-dev? I found that after searching the apt repository thusly:

$ apt-cache search python | grep qt

It was the only thing that came up that looked like it might help. You already (obviously) have make installed, so I don't think that's the issue. You're right, the error message seems like it wants a different PyQT.

Here's a link to the Ubuntu package description ([http://packages.ubuntu.com/hoary/python/python-qt-dev](http://packages.ubuntu.com/hoary/python/python-qt-dev)), which reads:
> Development .sip files with definitions of PyQt classes. They are needed to build PyQt, but also as building blocks of other packages based on them, like PyKDE.

HTH,

lt_kije

---

### Post by rickwood on 2005-05-10
This certainly isn't an optimal solution, but it might work.  I know that LPhoto has been compiled and packaged for Mandrake and is available on the net.  Perhaps you could try using alien to convert the Mandrake rpm to a deb file.

I haven't tried this with LPhoto, but it has worked for me with some other software (seems like it works for about half the packages I've tried).

---

### Post by rwabel on 2005-05-10
[QUOTE=greenwom]Ok (newbee)
Lphoto is a linspire supported piece of software that I want.

I grabbed the source code [Lphoto pool]("http://software.linspire.com/pool-src/l/lphoto/") 

I extracted the tar file in gnome.

in the terminal I ran 'make'
[color=Navy]mike1@mikesubuntu:~/marlin_build_lphoto-1.0$ make
python2.3 install.py
Sorry, please install PyQt.
make: *** [install] Error 1[/color]

So I ran 'apt-get install pyqt-tools'  - that installed fine but I get the same error above.

So I downloaded a different PYQT file that need a SIP file none of these worked.

Am I chasing a dream here as a newbee, maybe someones done it already
Let me know :)[/QUOTE]

[i]I've also tried to install lphoto. I could compile it but it doesn't work to start. I've installed some python-qt and sip, Don't know which versions 2.3 or 2.4 and I got then this error messages upon start
rwabel@RALPH:~/compiling/marlin_build_lphoto-1.0 $ lphoto
Traceback (most recent call last):
  File "/usr/lib/python2.3/site-packages/Lphoto/lphoto.py", line 3, in ?
    from kdeemul import *
  File "/usr/lib/python2.3/site-packages/Lphoto/kdeemul.py", line 6, in ?
    from kdecore import *
ImportError: No module named kdecore[/i]

I've then played around and tried alot of different packages of python stuff...Couldn't solve that problem.

maybe someone achieve it. I've also found compiled packages from xandros, but they obviously don't work:
[http://www.archlug.org/apt/](http://www.archlug.org/apt/)

good luck and any solutions are appreciated :-)

---

### Post by Ptero-4 on 2005-05-10
[QUOTE=rwabel][i]I've also tried to install lphoto. I could compile it but it doesn't work to start. I've installed some python-qt and sip, Don't know which versions 2.3 or 2.4 and I got then this error messages upon start
rwabel@RALPH:~/compiling/marlin_build_lphoto-1.0 $ lphoto
Traceback (most recent call last):
  File "/usr/lib/python2.3/site-packages/Lphoto/lphoto.py", line 3, in ?
    from kdeemul import *
  File "/usr/lib/python2.3/site-packages/Lphoto/kdeemul.py", line 6, in ?
    from kdecore import *
ImportError: No module named kdecore[/i]

I've then played around and tried alot of different packages of python stuff...Couldn't solve that problem.

maybe someone achieve it. I've also found compiled packages from xandros, but they obviously don't work:
[http://www.archlug.org/apt/](http://www.archlug.org/apt/)

good luck and any solutions are appreciated :-)[/QUOTE]
 Try installing the kdecore or kubuntu-desktop metapackage. That should solve the "importError: No module named kdecore" error.

P.D: By the looks of the traceback Lphoto expects to find KDE and won't compile w/o it.

---

### Post by az on 2005-05-10
Format: 1.0
Source: lphoto
Version: 1.0.61-0.0.0.50.linspire0.1
Binary: lphoto
Maintainer: Brian Thomason <brian@lindows.com>
Architecture: any
Standards-Version: 3.5.8
Build-Depends: debhelper (>> 4.0.0), python2.3-dev
Files: 
 5320053da48401ad15d053d6fec61dd4 203851 lphoto_1.0.61-0.0.0.50.linspire0.1.tar.gz



You should try to build the package using dpkg-source -x <package.dsc>
cd into the directory and then

dpkg-buildpackage

---

### Post by rwabel on 2005-05-11
[QUOTE=Ptero-4]Try installing the kdecore or kubuntu-desktop metapackage. That should solve the "importError: No module named kdecore" error.

P.D: By the looks of the traceback Lphoto expects to find KDE and won't compile w/o it.[/QUOTE]

I've both installed, that's the strange thing. I guess there is another dependency problem around. Ont hat forum: [http://kde-apps.org/content/show.php?content=19947]("http://kde-apps.org/content/show.php?content=19947") they talk about python kde bindings. I've python2.3-qt3 installed

---

### Post by rwabel on 2005-05-11
[QUOTE=azz]Format: 1.0
Source: lphoto
Version: 1.0.61-0.0.0.50.linspire0.1
Binary: lphoto
Maintainer: Brian Thomason <brian@lindows.com>
Architecture: any
Standards-Version: 3.5.8
Build-Depends: debhelper (>> 4.0.0), python2.3-dev
Files: 
 5320053da48401ad15d053d6fec61dd4 203851 lphoto_1.0.61-0.0.0.50.linspire0.1.tar.gz



You should try to build the package using dpkg-source -x <package.dsc>
cd into the directory and then

dpkg-buildpackage[/QUOTE]
unfortunately there is no package.dsc around

---

### Post by greenwom on 2005-05-16
I tired the installing KDE to fic the kdecore problem.

That didn't do anything but give me a chance to play around with KDE.

I uninstalled it and removed almost all of it's packages (I'm still working on getting them all off.)

I'll stick with gnome but I'd like to get Lphoto or Avidmux to work.

---

### Post by moontide on 2006-06-21
[QUOTE=azz]Format: 1.0
Source: lphoto
Version: 1.0.61-0.0.0.50.linspire0.1
Binary: lphoto
Maintainer: Brian Thomason <brian@lindows.com>
Architecture: any
Standards-Version: 3.5.8
Build-Depends: debhelper (>> 4.0.0), python2.3-dev
Files: 
 5320053da48401ad15d053d6fec61dd4 203851 lphoto_1.0.61-0.0.0.50.linspire0.1.tar.gz



You should try to build the package using dpkg-source -x <package.dsc>
cd into the directory and then

dpkg-buildpackage[/QUOTE]

I know this an old string but I thought I would give it a go as it's the best I've seen for trying to get lphoto going on ubutu,

Tried the above but now get 'ImportError: No module named qtgl' (instead of the previous one about kde module.

---

### Post by moontide on 2006-06-21
[QUOTE=moontide]I know this an old string but I thought I would give it a go as it's the best I've seen for trying to get lphoto going on ubutu,

Tried the above but now get 'ImportError: No module named qtgl' (instead of the previous one about kde module.[/QUOTE]

Over came 'No module named qtgl' by installing the qt-dev now lphoto install and try's to run but then complains about missing buttons.

---

### Post by greenwom on 2006-06-21
I'm still a Linux grub newbe but are there any experts out there that can help us build a .deb for this.  It looks like a greast ap but man.....  I haven't found anyone who can get it done.

---

### Post by moontide on 2006-06-22
[QUOTE=azz]Format: 1.0
Source: lphoto
Version: 1.0.61-0.0.0.50.linspire0.1
Binary: lphoto
Maintainer: Brian Thomason <brian@lindows.com>
Architecture: any
Standards-Version: 3.5.8
Build-Depends: debhelper (>> 4.0.0), python2.3-dev
Files: 
 5320053da48401ad15d053d6fec61dd4 203851 lphoto_1.0.61-0.0.0.50.linspire0.1.tar.gz



You should try to build the package using dpkg-source -x <package.dsc>
cd into the directory and then

dpkg-buildpackage[/QUOTE]

Sorry I got a bit tired and sloppy with my request for help las night. I am now at a stage where lphoto tries to load but fails with the message: 
rbw@moontide:~$ lphoto
Link points to "/tmp/ksocket-rbw"
Link points to "/tmp/kde-rbw"
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
Reading Library
Creating Default Empty Library
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/Lphoto/lphoto.py", line 784, in ?
    mw = LMainPhoto(app)
  File "/usr/lib/python2.4/site-packages/Lphoto/lphoto.py", line 54, in __init__    self.initModePanel(self.mainView)
  File "/usr/lib/python2.4/site-packages/Lphoto/lphoto.py", line 367, in initModePanel
    self.newAlbumButton = self.createToolBarButton(None, "buttonadd.png", hb, i18n("add a new album"))
  File "/usr/lib/python2.4/site-packages/Lphoto/lphoto.py", line 326, in createToolBarButton
    b = QPushButton(label, vb)
TypeError: argument 2 of QPushButton() has an invalid type
DCOP aborting call from 'anonymous-5965' to 'lphoto'
lphoto: ERROR: Communication problem with lphoto, it probably crashed.

 I am interested in lphoto as a means of producing a digital still photo display on a dvd with music in the background.

---

### Post by vinodis on 2006-06-22
maybe it would only work with Linspire.

---

### Post by greenwom on 2006-07-07
Well Update for those who care...
The purpose to getting Lphoto to work is to make DVD slideshows with nice transitions and music in the background... 

There's a package called "dvd-slideshow"  it's a command line script.  There's two GUI for the script slcreator and photo-dvd-slideshow (I thinkI got the name right)

slcreator's GUI os ruff and not the easiest to use upfront. 
The photo-dvd-slideshow GUI doesn't work on my laptop due to a resolution scaling issue with the GUI.  (I'm working on getting my desktop back up to test it.)

the script is in the repos and the GUI are on sourceforge.  If anyone wants to try them out and report that would be great.  The projects seem to need some support so that would be a good thing to... 

software like this is really popular on Apple and Windows based platforms.  A good slide show program with a nice GUI in a MUST for Ubuntu, a great marketing tool...

---

