---
title: "Keeping a &quot;mixed system&quot;"
date: 2014-08-15
forum: General Help
---

### Post by LinuxUser666 on 2014-08-15
Hello fellow Ubuntu users, I have a question about something I just recently heard about, that is mixed system. If I got it correctly it is having one OS version and have the ability to use software packages from different versions of same OS. My source: [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html) paragraph 3.8. That is Debian, my concern is it applicable in Ubuntu/Linux Mint? Because I am currently running 13.10 and I'd like to try LXQt, currently explained on 14.04. And please appoint to me if I was wrong, where was I wrong in understanding of "mixed system" concept. 

My regards, stay brutal. :guitar:

---

### Post by JKyleOKC on 2014-08-15
I didn't find a reference to such a system in your link, but I must admit that I didn't read every word of that chapter. While the various flavors of *buntu are based on Debian, each of them differs somewhat from the others and from their common parent, so not everything you find in the Debian documentation necessarily applies to your own system.

As a general rule, attempting to run old and new packages in the same system often results in strange behavior that's almost impossible to diagnose. It's almost a law of nature that any modification to a program or library to fix a known bug will introduce at least one brand-new problem, and often creates more than just one. When an older program encounters these, results are totally unpredictable and more often than not somewhat disastrous.

That said, sometimes such a mix is necessary. As an example in my own systems, the official version of a "panel applet" that I find extremely useful had a problem that made the applet unusable. When I learned that a later version had cured the problem with no known ill effects, I hastened to replace the malfunctioning original. To do so I had to make other changes; the final outcome was that my word processing program now fails to respond to the mouse wheel, because of the changes I had to make to get the (seemingly totally unrelated) panel applet working. I can live with that, though.

Bottom line is that such mixing is possible, but you have to be prepared for unexpected problems and sometimes must choose between two undesirable results. Good backups of all critical files -- documents, photos, music and the like -- are your best insurance against total disaster. Remember that your system is yours alone; nobody else's permission is needed to make changes, but be prepared to have to re-install it from scratch if things go totally wrong!

And welcome to the forums. Just ask when anything puzzles you; there's almost always someone around to offer help.

P.S. -- Your 13.10 system is getting close to obsolete; you may want to run Long Term Support versions (such as 14.04) which are supported for much longer than six months. I'm still on 12.04 LTS and expect to stay with it for at least another several months...

---

### Post by grahammechanical on 2014-08-15
In Ubuntu we can get software through Personal Package Archives (PPA). When a new version of Ubuntu comes out the developer needs to upgrade his archive to the new release. And that sometimes takes time. I have successfully installed and used software from a Saucy (13.10) PPA on a Trusty (14.04) version of Ubuntu.

But you want to do it the other way around. Install software that is being written for 14.04 on 13.10 and this is software that is still under development and not recommended for installation except by those willing to test the software and who are prepared to have the OS break.

> [COLOR=#4F4F4F][FONT=Lato]LXQt is in active development and so it is [/FONT][/COLOR][COLOR=#4F4F4F][FONT=Lato]not recommended[/FONT][/COLOR][COLOR=#4F4F4F][FONT=Lato] for use on any device you hold dear.[/FONT][/COLOR]

[http://www.omgubuntu.co.uk/2014/05/next-gen-linux-desktop-lxqt-makes-first-public-release](http://www.omgubuntu.co.uk/2014/05/next-gen-linux-desktop-lxqt-makes-first-public-release)

But you may be in luck. The Lubuntu PPA that installs this software has a version for 13.10

[https://launchpad.net/~lubuntu-dev/+archive/ubuntu/lubuntu-daily](https://launchpad.net/~lubuntu-dev/+archive/ubuntu/lubuntu-daily)

Just click Technical details about this PPA and select 13.10 from the menu. Be prepared to re-install.

A couple of points more. You are running Lubuntu, are you not? And 13.10 has reached end of life. So, it is best to upgrade/fresh install Lubuntu 14.04 and do it proper. You may find that this 13.10 version of the Lubuntu PPA does not have the code for the LXQt user interface.

Regards.

---

### Post by vasa1 on 2014-08-15
LXQt is still a work in progress. Unless you have sufficient experience, I suggest you avoid it and things like daily ppas.

---

### Post by tgalati4 on 2014-08-15
Many times you can take a package and recompile it for your system.  So, assuming you can get the source code, you create a proper build environment on your system and compile it.  You will quickly find out what dependencies are not satisfied.  Sometimes you can ignore those dependencies (like minor version changes on libraries) but sometimes you have to fix the code to get it to work with older frameworks.  All of this is a lot of work--measured in Agony Units.

So, it is generally not recommended to install newer packages than what is in the repository to keep a stable system, but it is tempting!

---

### Post by Rob Sayer on 2014-08-16
You don't necessarily need multiple DEs to "have the ability to use software packages from different versions of same OS".  For example this netbook runs xubuntu 14.04 but I use Dolphin, which is the KDE/Kubuntu file manager.  I don't want to use any other file manager.  It pulls in a shedload of KDE dependencies but I don't care.

You can install multiple DEs on one machine, I've done it, but I won't do it any more and don't recommend it after hearing a lot of convincing arguments by really seasoned linux geeks.  You can cause problems that are really hard to diagnose.

I may make an exception for installing KDE on a GTK based ubuntu DE install like the other 3 ubuntu DEs.  KDE uses different libraries so there's less chance for conflict.

Actually I did try LXQt in 13.10 but that was only because I knew I was going to install xubuntu 14.04 quite soon.  As mentioned, it's a beta/development release and, while I thought it was really very good for a beta, I wouldn't install it again until the stable version comes out.

An example of what could happen would be if you had an lubuntu system and then you installed LXQt.  Installing that means you have to enable the lubuntu bleeding edge daily builds ppa.

Which means that in addition to installing an unstable beta DE, you'd have just made your existing Lubuntu system unstable.  Ouch.  I've seen blogs telling you to do this but anyone who recommends that should not be listened to in the future.  There are some crappy linux blogs out there.

---

### Post by JKyleOKC on 2014-08-16
> **Rob Sayer said:**
> Which means that in addition to installing an unstable beta DE, you'd have just made your existing Lubuntu system unstable.  Ouch.  I've seen blogs telling you to do this but anyone who recommends that should not be listened to in the future.  **There are some crappy linux blogs out there.**Absolutely! Before you enter **any** commands you find on the web, be absolutely sure you know what they are supposed to do.

Most of us here will try to explain exactly what's expected to result, but not all the blogs and how-tos you find via a Google search are that careful, and a few -- thankfully **very** few -- are downright malicious.

It's also important to be certain that when you do type in a command, rather than copy-and-pasting it, you match the capitalization and spacing exactly, because Linux is much less forgiving than other systems about such matters. As a horrible example, it's possible to wipe a system out completely just by inserting a blank space at the wrong point in a command while attempting to clean out a directory.

I don't mean to inspire fear, just emphasize the need for understanding and caution.

---

### Post by vasa1 on 2014-08-16
> **JKyleOKC said:**
> ...
It's also important to be certain that when you do type in a command, rather than copy-and-pasting it, you match the capitalization and spacing exactly, ...
Some copy-pastes from web pages also drag in "smart quotes".

---

### Post by LinuxUser666 on 2014-09-01
Many thanks to all of you for your support regarding "mixed system" issue. I got that, no mixing repositories that are intended for other(newer) distro versions, because it may break something. 

Now regarding LXQt. I followed instructions here: [http://linuxg.net/how-to-install-lxqt-on-ubuntu-14-04-and-ubuntu-13-10/](http://linuxg.net/how-to-install-lxqt-on-ubuntu-14-04-and-ubuntu-13-10/).
Plus I listened what Spatry had to say, after installing: [http://youtu.be/6oDvcBNmtAM?t=4m40s](http://youtu.be/6oDvcBNmtAM?t=4m40s) 
It is working. It is under development, but it is working. So far it has been stable, without glitching and had very, very low memory consumption. Some things that can get annoying, if used to Whiskers in Xfce is that neat look and quick search of apps, you don't get it here. Luckily, you can use Gnome-Do dock or Cairo-dock. Also one problem there, LXQt does not have composition enabled by default(needed for them docks to work), so one must install composition manager. Currently using *xcompmgr. *Like I said, it all works fine so far, it just needs some functionality added in their default menu(LXDE rewrite of Whiskers would be cool). Basically, you experienced users should not be afraid to test it out, because memory consumption is low and worth at least giving it a try. 

Versions used: 
LXQt 0.7.0
xcompmgr v1.1.6
Openbox 3.5.2
Docky 2.2.0

My regards, stay brutal.

---

### Post by Rob Sayer on 2014-09-01
Installing a compositor in something like LXQt is, IMHO, silly.  If you want eye candy install a DE that was actually *designed* for it.

I do the same thing as an app dock in  xfce with a simple auto hide panel.

---

