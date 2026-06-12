---
title: "Live CD w/ Kalzium pre-installed"
date: 2007-10-25
forum: General Help
---

### Post by Ian505 on 2007-10-25
I need a Live CD that has a program and all its repositories ready to run right after boot. Is it possible? I know that you can put repositories on a separate CD but I CANNOT install Ubuntu on this machine and do not have internet access, and from what I know you cant remove the Ubuntu CD when running it in Live CD mode. (Or whatever you want to call it.)  I do have a thumb drive if that is useful... and the machine in question has a floppy drive- though I doubt that will be of any use.

The program is called Kalzium. It is in the default ubuntu 7.10 repos for sure, and I think its in 7.04

[http://edu.kde.org/kalzium/](http://edu.kde.org/kalzium/)

Please help. I greatly appreciate even the smallest bit of info, as I am a relative beginner @ linux in general as well as Ubuntu.

-Ian

EDIT- Forgot to say that I am using Ubuntu 7.10

---

### Post by Happy_Man on 2007-10-25
You can use an application called AptOnCD (in the repos) to choose what packages you want on your own shiny customized-to-your-taste LiveCD iso! Burn a disc using that and selecting to have Kalzium on it, and you should be OK.

---

### Post by Ian505 on 2007-10-25
> **Happy_Man said:**
> You can use an application called AptOnCD (in the repos) to choose what packages you want on your own shiny customized-to-your-taste LiveCD iso! Burn a disc using that and selecting to have Kalzium on it, and you should be OK.

Awesome! I am going to try this right now!

-Ian

---

### Post by Ian505 on 2007-10-25
Okay, I installed it, but how do I know which packages to include in the disk to run the program?

There are 2 entries that have the word 'kalzium' in them-* kalzium* and *kalzium data* and I know that it requires the kdeedu-data but other than that I have no idea on how to find out if it needs anything else. Can you help?

-Ian

---

### Post by Happy_Man on 2007-10-25
Run the command ```
apt-cache depends kalzium
``` in a terminal to get a list of dependencies.

---

### Post by Ian505 on 2007-10-25
Okay, this seems weird- ubuntu 7.10 is just under 700MB- and ubuntu w/ extra packages is only 23? I don't think I included ubuntu. What did I do wrong? I need to have both the packages and ubuntu on the SAME CD so I can use them right after boot from Live CD.

-Ian

---

### Post by Ian505 on 2007-10-29
> **Ian505 said:**
> Okay, this seems weird- ubuntu 7.10 is just under 700MB- and ubuntu w/ extra packages is only 23? I don't think I included ubuntu. What did I do wrong? I need to have both the packages and ubuntu on the SAME CD so I can use them right after boot from Live CD.

-Ian

Okay, I gave up. I wanted a USB hard drive anyway and this is my excuse to get one. :wink:
I am going to install Ubuntu on the hard drive, install Kalzium while connected to a internet connected machine, the move to the machine in question and boot it with that on it.

-Ian

EDIT- Also, several of the dependencies that I got with "apt-cache depends kalzium" were not detected by AptOnCD- even though I was able to run and install it when on a Internet connected LiveCD.

---

### Post by Happy_Man on 2007-10-29
Uh... sorry to burst your bubble and all.... but that probably won't work. Mainly because the screen will not show, due to the way Linux detects and uses screen/gfx card settings. The theory is fine, though.... just be prepared to have to deal with some CLI magic first.

---

### Post by Ian505 on 2007-12-27
Okay, I gave up on this and ended putting this on a portable hard drive. Before you say it will be hard to do, this is what I did.

MojoPac is a free little app that installs itself on your portable drive (flash or hard) and creates another mini-desktop on top of the host PC's XP. (XP is required on the host, see the [website]("http://www.mojopac.com/portal/content/hellomojo.jsp") for better description.)

What I did was install MojoPac on my portable drive. (faster than a flash drive by far) In the mini-desktop I installed VirtualBox and pointed that to a virtual disk I had with ubuntu- and kalzium- on it. 

And so my problem was solved... 

Load mojopac, boot Ubuntu, use Kalzium. Yay!

I hope this helps someone in the future.

-Ian

---

### Post by Rhubarb on 2007-12-27
It is possible to make your own customised live CD / DVD with:
[Remastersys]("http://www.remastersys.klikit.org/") or [Reconstructor]("http://reconstructor.aperantis.com/")

To add Kalzium to the live CD and still keep the image under 700MB, you may have to prune off some packages that you don't need.

---

### Post by Ian505 on 2007-12-27
I will definitely try this in the morning. *Yawn* not tonight though,

---

