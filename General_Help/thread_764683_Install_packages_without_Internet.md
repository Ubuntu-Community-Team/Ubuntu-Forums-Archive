---
title: "Install packages without Internet"
date: 2008-04-24
forum: General Help
---

### Post by ravi.xolve on 2008-04-24
I have got 'absolutely' no Internet connection to my computer (i.e. I can't even do an apt-get update). But I can access the Internet from my local cyber cafe which run on all windows XP. 

Is there a way i can download the packages list bring them back on a pen drive to my computer, update the apt-get. Then generate the list of packages required to be downloaded (thorugh apt-get --print-uris) and then download the required packages copy them to /var/cache/apt/archives and install then from there.:popcorn:

Please suggest your methods to do this. :confused:

---

### Post by Periswell on 2008-04-24
if you download them from a different computer then you generate package download script option in synaptic. mark the packages you want to install, then select the option from the file menu, which will generate the shell script that you can run to download the packages. then you transfer the packages to your ubuntu box and either put them in /var/cache/apt/archive or use the 'add downloaded packages' menu option in synaptic to install them. you will need wget so you need this installed on your computer to use for the downloading. 

hoped it helped

-josh

---

### Post by jespdj on 2008-04-24
You can manually download packages from [http://packages.ubuntu.com](http://packages.ubuntu.com) and then install them just by double-clicking the .deb file, or with dpkg -i in a terminal:
```
sudo dpkg -i filename.deb
```

---

### Post by Canis familiaris on 2008-04-24
> **jespdj said:**
> You can manually download packages from [http://packages.ubuntu.com](http://packages.ubuntu.com) and then install them just by double-clicking the .deb file, or with dpkg -i in a terminal:
```
sudo dpkg -i filename.deb
```

Well I'm not sure but this may push the user to dependency hell.:confused:

---

### Post by Canis familiaris on 2008-04-24
You can try this thread which I posted for similar problem.

[U][http://ubuntuforums.org/showthread.php?t=348107](http://ubuntuforums.org/showthread.php?t=348107)
[/U]

But I think you need Ubuntu to be running in the Cyber Cafe Computer for this.

---

### Post by Archmage on 2008-04-24
Sorry, but why do you want to upgrade at all? You are not in danger that someone will hack you over the internet.

Download each 1/2 year the next release (or if you want to be long time stable only each 2 years the LTS) as an alternate CD, put this in your CD-Rom drive, answer that you want to upgrade and be happy.

---

### Post by twright on 2008-04-24
you can use nonetdebs:
[http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/)

---

### Post by angry_johnnie on 2008-04-24
jespdj put you on the right track.  Just keep an eye on those dependencies, and try to keep those packages organized.  It takes a lot of patience, but it can be done :-)

---

### Post by brijith on 2008-04-24
YES nonetdeb will really help you !!!

I have been using nonetdeb for downloading packages with out any dependency problem. I find it is very easy to use

:guitar:

---

