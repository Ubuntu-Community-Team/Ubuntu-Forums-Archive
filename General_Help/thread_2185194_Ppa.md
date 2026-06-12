---
title: "Ppa"
date: 2013-11-01
forum: General Help
---

### Post by Chelidze on 2013-11-01
I have a question about ppa's 

Why does not software that is being installed from ppa's does not work on every ubuntu version out there. 

Why does it happens that you can find a software on launchpad and it does not supports the version of ubuntu you are using ??

Does it requires a lot of work to make it support a never version of ubuntu, so that is why it take davs so long to make them??

For example it took handbrake to add 13.10 support at least two weak or more. was it hard for them to make it ? or the devs just did not have time.

Is it possible to put one file on launchpad and every ubuntu version would install from it or you need different files for every different version of ubuntu ??

Thank you for your answers

---

### Post by TheFu on 2013-11-01
Different versions of supporting libraries is the real issue.
Making a new version is not always trivial and newer versions still need to be tested. Many of the programs are supported by 1 guy - he has a life - perhaps he doesn't use Ubuntu, so that part of the "itch" isn't really something he likes to scratch.  Lots of developers elect to use different distros, so setting up an Ubuntu dev environment just for a new release (x32 and x64) is a hassle.

Handbrake is a fairly complex piece of software with many, many dependencies.  Those dependencies are always moving targets - if they choose to use the version that Ubuntu uses, then they are WAY behind.  Ubuntu usually runs 2-24 months behind on that stuff. Sometimes much farther.

As a business owner, I'd prefer that developers ignore non-LTS releases from Canonical and concentrate all their limited effort on supporting only LTS releases.   I say this as a cross-platform dev with 15 yrs supporting code for customers on 10+ different platforms. Usually, we had to drag clients off 5-8 yr old OSes kicking and screaming. With non-Linux OSes, backward compatibility was almost always guaranteed.  With Linux, libc might have changed between 1 release and the next.

Don't get me started on the GUI libs that seem to completely ignore backwards compatibility.  Those people deciding that is OK should be taken out and shot in the foot. It is their lack of thought that is screwing over Linux on the desktop. Why has Android taken 80+% of the smartphone market?  Backwards compatible GUI APIs - that's why. Linux GUI devs need to learn that lesson, KDE, Unity, Gnome all need to agree on standard GUI APIs and decide to suppose the core functions - without change - for 10-20 yrs.  Sure, we can program to the Xt, Xm and XLib levels, but nobody will anymore. The newer GUI competitors really are very nice to use.

After all, I can still use win32 APIs from 1995 on Windows - that is our real competition.

---

### Post by grahammechanical on 2013-11-01
Those that provide software through a PPA are volunteer developers working in their own time. A PPA is a Personal Package Archive. The software has to be packaged for each version of Ubuntu because each version of Ubuntu has been upgraded. Linux is under constant development and so the libraries in Ubuntu 13.10 are newer versions of the libraries in Ubuntu 13.04.

An application will make use of certain libraries which have to be installed with the software if they are not already installed by default. All the libraries have version numbers. This is necessary in case the library causes bugs in the software. It would be necessary to identify what version of the library has the buggy code.

So, software installed through a PPA in Ubuntu 13.10 will look for certain versions of the libraries it needs. The same software installed in 13.10 will not find those libraries because newer versions with different version numbers have been installed. So, for that same software to run in 13.10 the developer will have to modify his code in some way. This cannot be done before the latest version of Ubuntu has been released because code in Ubuntu might be changed up to released day. The last few days of any Ubuntu development cycle are spent fixing bugs.

By the way, the technical term is 'dependencies.' Packages may well 'depend' on other packages. And often depend on certain versions of packages.

Regards.

---

### Post by Chelidze on 2013-11-01
Thank you for your replies

That is all I wanted to know

Now I know packaging ubuntu software actually require a lot of work.

---

