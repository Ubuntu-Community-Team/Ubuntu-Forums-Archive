---
title: "Anyone have experience with installing Inkscape 0.92 on Ubuntu 16.04?"
date: 2018-06-16
forum: General Help
---

### Post by emilyjane2 on 2018-06-16
Hello all,

I am interested in possibly [using a PPA to install Inkscape 0.92]("http://ubuntuhandbook.org/index.php/2017/01/install-inkscape-0-92-ppa-ubuntu-16-04-16-10-14-04/") for Ubuntu 16.04 because there's a bug fix I would like to benefit from, but I am very wary of installing the unofficial distribution of a package. 

The [bug fix]("https://bugs.launchpad.net/inkscape/+bug/1373311") I'm interested in is one that allows you to change the default units of a document from mm to px and still be able to save guide positions.

Has anyone here used the PPA to install 0.92 and if so, did it cause any problems for you later on down the line? 

Thanks for your help!

---

### Post by dragonfly41 on 2018-06-16
I had a look at my Inkscape and it was version 0.9.1.
I had not installed it via Synaptic, probably manual installation, so could not remove it.

What I have just done is to rename the folder /usr/share/inkscape to /usr/share/__inkscape.

This effectively disabled Inkscape 0.9.1 (I know it is a crude method).

Then I applied PPA and I now have Inkscape 0.9.2 running.

I'll remove the old version after some testing of 0.9.2.

---

### Post by PaulW2U on 2018-06-16
The fix that you referred to was from 2015 although the bug report was not closed until a year or two later and you linked to a web page from January 2017. :(

The [Inkscape Stable]("https://launchpad.net/~inkscape.dev/+archive/ubuntu/stable") PPA seems to be about official as you can get without those packages actually being in the Ubuntu repositories. The latest update was less than three months ago.

For anyone running Ubuntu 16.04 there is a simple choice: use Inkscape 0.91 from the Ubuntu repositories or Inkscape 0.92 as supplied by the **official** development team via their PPA. I have no experience of using Inkscape but I can confirm that I have never been let down by using a PPA that is administered by the official development team

---

### Post by deadflowr on 2018-06-16
If you don't want to deal with the ppa you can install the snap version.
It's published by inkscape.

---

### Post by mörgæs on 2018-06-17
A clean install of Ubuntu 18.04 will bring Inkscape 0.92 by default. 16.04 is a museum for old bugs.

---

### Post by monkeybrain20122 on 2018-06-17
> **mörgæs said:**
> A clean install of Ubuntu 18.04 will bring Inkscape 0.92 by default. 16.04 is a museum for old bugs.

Actually a lot of software on my 16.04 is newer than 18.o4's default offer. :) I use some ppas and compile some myself. So far I much prefer 16.04. 18.04 is ok for 'basic' use but under the hood many things are not working properly, library's paths have changed  for no good reasons and programs that I used to be able to compile no longer build (this is a big issue for me, prepackaged deal from Ubuntu is usable but far from optimized for some software that I use) , default java is too new so that almost all third party java applications don't work etc.

I don't recommend trading in a working OS for a very new release (at least wait til 18.04.1 IMO) just for a few applications. If OP can find a ppa that is the way to go.

---

### Post by monkeybrain20122 on 2018-06-17
> **emilyjane2 said:**
> Hello all,

I am interested in possibly [using a PPA to install Inkscape 0.92]("http://ubuntuhandbook.org/index.php/2017/01/install-inkscape-0-92-ppa-ubuntu-16-04-16-10-14-04/") for Ubuntu 16.04 because there's a bug fix I would like to benefit from, but I am very wary of installing the unofficial distribution of a package. 



Why wary? I have been using many ppas and they have never caused me any problem. You just need to know which ones to use. In general ppa published by developers such as inkscape,smplayer, libreoffice are good, the well known ones such as webupd8, gimp-edge, multimedia ppas by mc3man etc are good, in general avoid those that want to upgrade a lot of things (so if you get new version of foo from ppa 1 and ppa 2, all other things being equal, pick the 'smaller' one which would not upgrade a lot of things you don't intend to upgrade) Be careful with ppas that upgrade system components such as graphic drivers, they are useful sometimes but can be a bit risky. Finally install ppa-purge in case anything goes wrong.
  
IMO upgrading end user applications via ppa makes a lot more sense and is a lot lot less risky than updating the whole system every 6 -9 months. The absolute worst case scenario with ppa going wrong is that you have trashed your system beyond repair that you have to reinstall your os (almost zero probability if you use ppa with care like said above), and that would be exactly the same as the "official" way to upgrade software by reinstalling the whole system every 6 to 9 months. 

Being able to easily upgrade end user applications with ppa is one reason why I prefer Ubuntu over Debian, and being able to choose what you upgrade and roll back if needed (via ppa purge) is why I prefer Ubuntu over Arch and derivatives.

---

### Post by dragonfly41 on 2018-06-17
And installing y-ppa-manager makes it easier to manage PPA ..  

```
sudo apt-get install y-ppa-manager
```

---

### Post by mörgæs on 2018-06-17
> **monkeybrain20122 said:**
> I use some ppas and compile some myself.

You are a more advanced user than most people here. I for one have not compiled anything for many years.

My advice to original poster is still to try 18.04 as a first attempt. If any serious bugs should appear, which I doubt, there is always the option of reverting to 16.04.

---

