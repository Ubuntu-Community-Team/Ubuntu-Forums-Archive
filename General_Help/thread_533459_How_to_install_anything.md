---
title: "How to install anything"
date: 2007-08-24
forum: General Help
---

### Post by arvadawest on 2007-08-24
Hi,
I am a newbie to Ubuntu Linux (or Linux period).  I have been stumbling through on how to install applications or how to get them from repositories, etc.  I notice that I can mark them for installation, but where do I go to install.  I basically need a 101 course on how to install, where to find apps, how to bring them over to install, etc.  Thanks for your help.  There are a great group of people on this site.  -aw

---

### Post by aysiu on 2007-08-24
Read this:
[How to install anything in Ubuntu](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by mannylarson on 2007-08-24
Just go under "Application" and click on "Add/Remove" is the most simple way; I would try and stay with approved Ubuntu software...

---

### Post by arvadawest on 2007-08-24
> **aysiu said:**
> Read this:
[How to install anything in Ubuntu](http://www.monkeyblog.org/ubuntu/installing)

Wow, thanks to both of you.  I appreciate your  help.  I will read up on this.  Have a good night!  -aw

---

### Post by aysiu on 2007-08-24
You may also want to check out [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Andre Schoeman on 2007-08-28
Another newbie,

I followed the recommened instruction(s) and this was the reponse.
I'm trying to load the minicom terminal.

andre@ubuntu:~$  sudo apt-get install minicom
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package minicom

This was supposed to be the easy method? I'm guessing that minicom is not on the Ubuntu server as a standard package?

I have downloaded a .deb version of the package which claimed to be for ubuntu, unpacked it into a new directory and 'unzipped' the .gz files. There is a minicom file but it does not run. Do I need to compile this lot? Does not look like source files though.

Please help.
Andre

---

### Post by Steveway on 2007-08-28
No don't unpack the .deb files!
Just doubleclick on them.

---

### Post by Wolki on 2007-08-28
> **Andre Schoeman said:**
> 
This was supposed to be the easy method? I'm guessing that minicom is not on the Ubuntu server as a standard package?


That's strange, minicom should be available from the repositories without adding the community-supported or nonfree sections. Which Ubuntu version are you using? It should be Version 6.06 (Dapper) or newer. Please try doing a "sudo apt-get update" in case the list of available programs is outdated. If this doesn't work, please post the contents of your /etc/apt/sources.list file.

You can also try the graphical programs synaptic or gnome-app-install, they should be easier than using apt-get directly especially if you're not used yet to how it works.

Also, while it's possible to install things from .deb files, it's best to install them from the official repositories if you can.

---

### Post by Andre Schoeman on 2007-08-28
Thanks for the reply.

I'm using version 5.04. I was handed the CD a few years back.

First, double clicking only opens the .deb archive and allows it to be "unpacked".

OK, so I should use a newer version. I had already downloaded version 6.06 as an ISO file. PROBLEM? I don't think there is suitable CD burning software on Ubuntu. I also downloaded Brasero for Ubuntu as a .deb package.(not sure if this can write an ISO file, if not what should I use)

How do I install it?

I could transfer the ISO file to one of my Windows PC'sand burn it there, but I can't see the Windoes network. The next best bet is a USB disk, but I don't have a 1GB drive for the 700MB+ file.

When I upgrade will I lose axisting data? Not too serious this time around as I have not done much yet.

Should I rather install version 7.04?

Regards
Andre

---

### Post by gundumfx on 2007-08-28
well you are a newbie well go to add an remove in applaction then donwload games an things you want 
then go to webs 
an find things for deb an download then use apt or terminal an you well get use to it

---

### Post by gundumfx on 2007-08-28
> **aysiu said:**
> Read this:
[How to install anything in Ubuntu](http://www.monkeyblog.org/ubuntu/installing)

well i just checked out your link an that was nice an for a new bie this is a good web

---

### Post by Steveway on 2007-08-28
5.04? Wow, you're 2 years behind.
In your case I would just download 7.04 and install that over your old one.

---

### Post by Wolki on 2007-08-28
> **Andre Schoeman said:**
> 
I'm using version 5.04. I was handed the CD a few years back.

Yes, this version is not supported anymore and packages for it aren't really available anymore. Ubuntu releases are usually supported for 18 months, LTS (Long-term-support) releases which should happen every 2 years are supported for three years 8 and five for the server parts). Ubuntu 6.06 is the latest LTS, the next one is scheduled for april next year.

> First, double clicking only opens the .deb archive and allows it to be "unpacked".

Installation of single .debs via double-clicking was introduced in 6.06 if I remember correctly.

> OK, so I should use a newer version. I had already downloaded version 6.06 as an ISO file. PROBLEM? I don't think there is suitable CD burning software on Ubuntu. I also downloaded Brasero for Ubuntu as a .deb package.(not sure if this can write an ISO file, if not what should I use)


There is CD burning software included, you should be able to right-click the ISO file and choose "burn" or something similar.

If I were you, I'd make sure you get the 6.06.1 version, as it contains several bugfixes including some related to installiation. A 6.06.2 version was supposed to be released soon (or maybe already is), but you can update your system after installation.

You can also upgrade from one Ubuntu release to the next (and will be able to upgrade from one LTS release to the next once a second LTS version is released), but the Ubuntu release after yours (5.10) has already ended support as well, so you probably won't be able to update easily anymore. In this case, I'd recommend reinstallation.

> When I upgrade will I lose axisting data? Not too serious this time around as I have not done much yet.


If you did not put your data on a separate partition, reinstallation will overwrite it. You can setup a separate partition for your data during installation or do it later. This is called having a separate home partition, an explanation is probably on the wiki (I'll look later). If you want to avoid data loss, you can also copy the /home directory to an usb stick or other external storage medium.

> Should I rather install version 7.04?

This is a difficult question. 7.04 has some features that make it easier for new users (such as simple installation for multimedia codecs) as well as newer software and often better compatibility for hardware. 6.06 is older and had more time to mature, but may containn bugs that were removed in newer versions of applications. If bandwith is not a big concern, I'd suggest trying both via the live-cd and using 7.04 if it works well on your computer, 6.06 if it doesn't.

[edit] couldn't find a simple howto for creating a separate home partition, unfortunately... If you're interested, I'll explain it myself.

---

### Post by Andre Schoeman on 2007-08-28
Hi Wolki,

Thanks for the profesional response, much appreciated.

I will upgrade to version 6.06.1 and start again. I don't really have any data so no loss there, but will drop in another drive or partiition for data.

I'm not too concerned about sound and that sort of stuff.

My target is embedded Linux on an ARM7. I may be a newbie in Linux, but I have used GCC and the ARM7 is an old friend.

Regards
Andre

---

### Post by Wolki on 2007-08-28
Always glad if I can help people.

> **Andre Schoeman said:**
> 
I will upgrade to version 6.06.1 and start again. I don't really have any data so no loss there, but will drop in another drive or partiition for data.


If you're reinstalling anyway, a separate home is rather easy. Simply create three partitions instead of two (/, swap and home). Sizes depend on the harddrive space you have available, usually ~1 gb of swap is sufficient, / should probably have 4-10 gb (depending on how many programs and stuff you want), home can take all the rest. The installer should offer you to choose what you want to put where.

> I'm not too concerned about sound and that sort of stuff.

My target is embedded Linux on an ARM7. I may be a newbie in Linux, but I have used GCC and the ARM7 is an old friend.


OK, then 6.06 sounds like a good choice. Make sure the version of gcc and any libraries you need is sufficient, as there are usually no version updates in stable releases. You can find out which packages are available for which version on [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

