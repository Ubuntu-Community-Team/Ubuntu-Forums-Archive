---
title: "Keeping Track of What I Install"
date: 2008-05-04
forum: General Help
---

### Post by svk on 2008-05-04
Hello,

One of my absolute favorite things about Ubuntu is the elegance of the package system, and the multitude of software backing it, all of it available to install in a snap.

But it's very easy to get lost.  During my recent upgrade to 8.04, instead of leaving the computer unattended, I just sat by and watched the hundreds, if not thousands, of packages being updated, one by one.  It struck me that I was unaware of most of them.  I googled some of the packages that I did not install myself, and they would have proved very useful to me -- if I were aware that they existed (writer2latex is one example).  It also struck me when I saw a couple packages go by that I myself installed a very long time ago and have since completely forgotten about: packages that could have been very useful if I had remembered that I installed them in the first place (zim, I'm looking at you).

To make a long story short, I want to have some way of keeping track of what I installed myself.  From searching, I could tell that this is a popular feature request, and I sincerely hope that the developer team will consider adding something of this nature in the future.  I know that Synaptic lists all the packages that are installed, but the problem is it lists not only the packages that I chose to install myself, but also all the dependencies that go along with them.

Ideally, I would want something no more complicated than a text file that lists each package I installed on a line by itself.  I do NOT want the dependencies of those packages to be listed in the file.

For now, I'd like to hack together a homemade solution -- but I will need some help.  Assume that I install everything from the terminal, using apt-get.  How can I modify apt-get to log what I install to some text file?  Is it possible at all?

Thanks in advance for any help.

---

### Post by markbl on 2008-05-04
> **svk said:**
> Hello,
Assume that I install everything from the terminal, using apt-get.  How can I modify apt-get to log what I install to some text file?  Is it possible at all?
Just use aptitude instead of apt-get. The you get a log of package installs/removes etc in /var/log/aptitude*.

Aptitude has many advantages over apt-get anyhow. E.g. see [http://www.oneunified.net/blog/OpenSource/Debian/aptitude.article](http://www.oneunified.net/blog/OpenSource/Debian/aptitude.article) .

---

### Post by zvacet on 2008-05-04
In **synaptic>edit tab>history** you can find what you installed or removed.

---

### Post by svk on 2008-05-04
Thank you both for you help!

It seems that Synaptic history shows *all* packages, including dependencies.  However, because it shows all the changes *by date*, it is a major step up from what the alternative: the alphabetical list of all installed packages.

Thanks, markbl, I wasn't even aware that aptitude was preferred over apt-get, and for so many reasons.  When I installed more packages, I'll explore the logs it generates to see if it is roughly what I wanted.

---

### Post by Oldsoldier2003 on 2008-05-04
```
sudo dpkg --get-selections > mypackages.txt
``` will give you a list of all packages instaled on your computer

the cool thing about this is you can use this list to install these packages again on the same computer at a different date...

---

### Post by bodhi.zazen on 2008-05-04
As will :

```
sudo dpkg -l > Installed_Packages.txt
```

---

