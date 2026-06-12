---
title: "Video and Audio drivers"
date: 2006-09-26
forum: General Help
---

### Post by The Tronyx on 2006-09-26
Hello!  I have recently installed Ubuntu and will be finishing up my first 12 hours with my first Linux distro after this post when I sleep. =D  I was curious, and pardon me being a newb at this since I haven't made it too far into my Linux books yet, but do I need to install any drivers for my video card?  I tried to play an MP3 and it wouldn't work, I vaguely recall it saying something about missing drivers and/or support.  I would have gotten back to it but I got pretty side tracked.

What drivers do I need for my video and/or sound in order to play movies and MP3s?

Thanks for your help and assistance.

---

### Post by em3raldxiii on 2006-09-26
Heya 2point0, welcome to the community!

Well, your questions are probably among some of the most frequently asked questions.  There are a number of links in the official documentation about this subject, so when you have a sec, do some searching and you'll probably get some valuable info that I fail to mention.

1.  Video:  Yup, there are likely newer/better drivers available for your video card.  Unfortunately, manufacturer support for Linux is extraordinarily shoddy, so using this forum is the best way to get your card installed correctly.  There is a howto on here somewhere (I'm too tired and lazy to find it for you at the moment LOL).  But we really need to know what make/model of vidcard you have before we can progress much farther.

2.  MP3 and other audio formats are not covered under the open-source "100%" free software licensing that is "essential" to be included in the Ubuntu installation.  Luckily, there are a number of different ways to get the required packages installed without too much pain and frustration.  You would do well to search out the topic and learn a bit about it (since Linux is driven by the kinds of people who do), but you can try a couple of applications like **automatix** and **easyubuntu**.  I don't think they are in the regular Ubuntu repositories, so do a Google search for one or both of those (there are others, but I am unfamiliar with them).  Basically they are just largish scripts that open pretty windows to do all the complicated stuff behind-the-scenes for you.  They don't always work 100% because everyone's computer/software setup is different ... if you get crazy errors and stuff, feel free to post here and someone will be able to help you out :D

Also, there are a couple of "major" aspects to Ubuntu that you should do some learning about.  One is called Repositories.  (I am assuming you don't know about this stuff.  If you do, just ignore me ... I like to see my own typing).  There are tons of "additional" software packages in the Universe and Multiverse repositories (you should search/learn about thease) that you can install using the "sudo aptitude install" process in your command line, or using the Synaptic package manager (system > administration > synaptic).

Also, there are a gabillion different media players out there, each with different strengths and weaknesses (same as Windows except these are all free, legally).  I personally like to use a music player called **xmms**, and many other people will recommend **amarok**.  For movies, I personally like **gxine**, and many others will recommend **totem, mplayer, xine, and vlc player** among others.  Luckily, in Linux the programs are MUCH smaller than their Windows counterparts, so you can safely have 6 different players installed without too much concern over disk space.

Again, if you have any questions or problems or whatever, post to your heart's content.  But I SUPER EXTRA MAJORLY recommend reading some of the official documentation which will cover a lot of this stuff ... and it will help you wrap your head around some of our answers.  I speak from first-hand experience ... I am just a well-read newbie myself :D

---

### Post by The Tronyx on 2006-09-26
brooks@brooks-desktop:~$ wget [http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz)
--02:21:07--  [http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz)
           => `easyubuntu-3.023.tar.gz'
Resolving easyubuntu.freecontrib.org... 213.246.58.132
Connecting to easyubuntu.freecontrib.org|213.246.58.132|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 92,653 (90K) [application/x-tar]

100%[====================================>] 92,653       173.13K/s

02:21:08 (172.74 KB/s) - `easyubuntu-3.023.tar.gz' saved [92653/92653]

brooks@brooks-desktop:~$ tar -zxf easyubuntu-3.023.tar.gz
brooks@brooks-desktop:~$ cd easyubuntu
brooks@brooks-desktop:~/easyubuntu$ sudo python easyubuntu.in
System sanity check: PASSED!
amd64 detected
['/usr/sbin/synaptic', '--hide-main-window', '--non-interactive', '-o=dir::etc=./conf', '-o=dir::etc::sourcelist=sources.list']
In update ['/usr/sbin/synaptic', '--hide-main-window', '--non-interactive', '-o=dir::etc=./conf', '-o=dir::etc::sourcelist=sources.list', '--update-at-startup']In Install ['/usr/sbin/synaptic', '--hide-main-window', '--non-interactive', '-o=dir::etc=./conf', '-o=dir::etc::sourcelist=sources.list', '--set-selections']
brooks@brooks-desktop:~/easyubuntu$


The GUI for selecting packages loads and I make the selection of ATI drivers, some codecs, and a few other things.  It runs some downloads and installs some stuff then I get a popup that says "Could not apply changes. Fix broken packages first!"  I'm not sure what went wrong.

Previous to this I ran
udo apt-get install xorg-driver-fglrx
to try and install my graphics card.  It might help to consult 

[http://www.ubuntuforums.org/showthread.php?t=265491](http://www.ubuntuforums.org/showthread.php?t=265491)

Update: Ok, from [http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html) I downloaded the .deb installer and now I have applications>system & tools>easyubuntu but when I click easyubuntu, nothing happens.

---

### Post by em3raldxiii on 2006-09-26
Well, I ran into that problem once before too with Easyubuntu.  I think it was one of the other packages that actually gave me troubles.

Anyway, first up, try the same easyubuntu thing, but ONLY select the video driver.  Also, from what you say you chose the ATI driver - I then assume you have an ATI videocard, right?  I know it's a bit of an obvious question, but I wouldn't be thorough if I didn't ask.

Okay, now lets address this Easyubuntu problem.  It appears that it is not uncommon, and it is caused by *totem-gstreamer 1.4.3-0ubuntu1*.  From another post in this forum I found the following:

> 
Quoted from [http://ubuntuforums.org/showthread.php?t=229980]("http://ubuntuforums.org/showthread.php?t=229980") by [foolswisdom]("http://ubuntuforums.org/member.php?u=2302")

$sudo apt-get remove totem-gstreamer

(note packages that are removed)

$sudo apt-get install totem-gstreamer-firefox-plugin ubuntu-desktop

(ensure that all packages that were removed are now installed again)


This should remedy the problem ... I hope.  Please let me know if it works.

I found this interesting website while looking for the thread:

[Unofficial Ubuntu ATI Driver installation wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

Also, it appears as if ATI has provided Ubuntu users with hours of enduring frustration over their horrendous Linux support.  Check out this thread for some more potential help:  [http://ubuntuforums.org/showthread.php?t=185033]("http://ubuntuforums.org/showthread.php?t=185033")

---

