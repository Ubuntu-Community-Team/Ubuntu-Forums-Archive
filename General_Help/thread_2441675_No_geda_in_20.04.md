---
title: "No geda in 20.04"
date: 2020-04-25
forum: General Help
---

### Post by habana on 2020-04-25
There is no geda (electronic design software) in the 20.04 repositories. Does anybody know why this so? I can find the .deb files in debian but there are many dependencies some of which have further dependencies. Maybe these are older versions that won't work with newer applications? 

Please don't suggest kicad, I am not interested.

---

### Post by mc4man on 2020-04-25
Well there was a build attempted on Jan. 10, it failed a test run during the build.
On Jan. 18 the source was removed from focal . Probably for good reason and it's not maintained anymore.

Certainly seems possible to package build now, at least locally. You'd need to install basic build and package tools plus all the build deps for geda.
Then a simple  dpkg-buildpackage -us -uc -b will produce as in screenshot. Whether any runtime issues no idea as have no use for..

Source acquired here, [https://launchpad.net/ubuntu/+source/geda-gaf/1:1.8.2-11ubuntu1](https://launchpad.net/ubuntu/+source/geda-gaf/1:1.8.2-11ubuntu1)

Edit: tried build in launchpad, that one test also fails in ppa. So local build may be  the way to go 
(- test failure is on the gsch2pcb backend
See[ here]("https://launchpad.net/~mc3man/+archive/ubuntu/tmp-tests"), will leave up for a couple of days uless feedback is provided..

---

### Post by habana on 2020-04-26
Thank you for that. I see that it uses python2 which I believe is no more. Maybe that is the problem.  Anyway, I will give it a go.

---

### Post by habana on 2020-04-26
@mc4man. Not sure what I am doing wrong. I added the PPA, which shows up in my Software Sources, but sudo apt-get update doesn't download anything.

---

### Post by HermanAB on 2020-04-26
Howdy, 

KiCAD and Freerouting work pretty good:
[https://www.aeronetworks.ca/2020/02/kicad-schematic-and-pcb-design.html?m=1](https://www.aeronetworks.ca/2020/02/kicad-schematic-and-pcb-design.html?m=1)

---

### Post by mc4man on 2020-04-26
> **habana said:**
> @mc4man. Not sure what I am doing wrong. I added the PPA, which shows up in my Software Sources, but sudo apt-get update doesn't download anything.
Well if it doesn't exist there nothing to upgrade.
I know nothing about this but the meta-package is geda so
 sudo apt install geda

or install synaptic > Origin > pick ppa listing, ect.

Don't see any dep or recommend on python2, if so and any issue install
sudo apt install python-is-python2

---

### Post by habana on 2020-04-26
@mc4man. Sorry I should have tried that! All working OK. I will have to sort out gsch2pcb (a bridge between geda and pcb which _is_ in synaptic). That's the one that requires python2.

Many thanks for your help with this. I will mark this thread as solved.

---

### Post by mc4man on 2020-04-26
> **habana said:**
> @mc4man. Sorry I should have tried that! All working OK. I will have to sort out gsch2pcb (a bridge between geda and pcb which _is_ in synaptic). That's the one that requires python2.

Many thanks for your help with this. I will mark this thread as solved.

If your gsch2pcb is or is not a package then install the python-is-python2 package.
This will install available python2.7 packages and put back the /usr/bin/python symlink.
(- also should have a Provides: python to take care of that dep

If gsch2pcb requires python-gtk2 then you can download and install the eoan python-gtk2 package _with apt_.

---

### Post by habana on 2020-04-26
@mc4man. The package that requires python2 is actually xgsch2pcb which is the graphic interface for gsch2pcb. The latter is a CLI command within geda so if I work out how to use that I may be able to avoid messing around with the deprecated python2 altogether. More study for me! Thanks again.

---

### Post by darmint on 2020-07-15
> **habana said:**
> There is no geda (electronic design software) in the 20.04 repositories. Does anybody know why this so? I can find the .deb files in debian but there are many dependencies some of which have further dependencies. Maybe these are older versions that won't work with newer applications? 

Please don't suggest kicad, I am not interested.



Hello.
I also use the gEDA package.
Unfortunately, it has been neglected by developers for a long time and in Ubuntu 20.04 it is not there yet.
I have no knowledge to change it. I only trimmed the symbols.
I tried to install gEDA packages in turn using GDebi. Packages for ease of download
  [https://pkgs.org/search/?q=geda](https://pkgs.org/search/?q=geda)
I installed one by one with the missing dependencies. GDebi displays hints.
At the moment, gesch works, although I haven't checked everything.

---

### Post by darmint on 2020-07-28
Hello.
There is gEDA available in Ubuntu under the name:
lepton-eda

[https://github.com/lepton-eda/lepton-eda](https://github.com/lepton-eda/lepton-eda)

---

### Post by edras on 2020-08-07
> **darmint said:**
> Hello.
I also use the gEDA package.
Unfortunately, it has been neglected by developers for a long time and in Ubuntu 20.04 it is not there yet.
I have no knowledge to change it. I only trimmed the symbols.
I tried to install gEDA packages in turn using GDebi. Packages for ease of download
  [https://pkgs.org/search/?q=geda](https://pkgs.org/search/?q=geda)
I installed one by one with the missing dependencies. GDebi displays hints.
At the moment, gesch works, although I haven't checked everything.

I would like to help too. I have lots of projects using gEDA and I think there is no converter for KiCad.
What are the steps needed to compile a new updated gEDA package?

---

### Post by habana on 2020-08-08
As gEDA seems to have been abandoned, I have installed lepton-eda via synaptic as suggested by darmint. lepton-eda is a fork of gEDA and appears to be active. Thus far I have established that i can open my old gEDA schematics but haven't had time to go any further.

---

### Post by sambeet075 on 2020-08-18
Compiling from source tarball ([http://wiki.geda-project.org/geda:download]("http://wiki.geda-project.org/geda:download)of") )gEDA/ gaf still works in ubuntu 20.04.When we do $./configure --prefix=$HOME/geda --enable-silent-rules, we obtain the list of dependencies.All dependencies can be downloaded from ubuntu 20.04 repository directly except the python2 libs and this will show a "python2 not found" dependency error.We can then do # sudo apt-get install python-dev-is-python2.That will do the trick, and gEDA/gaf i.e the schematic capture, netlister, symbols, symbol checker, and utils work properly like in previous ubuntu versions.I have not checked the pcb and gerbv as I use gEDA only for schematic capture for ngspice.

---

