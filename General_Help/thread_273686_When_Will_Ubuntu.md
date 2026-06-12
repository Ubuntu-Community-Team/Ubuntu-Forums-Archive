---
title: "When Will Ubuntu"
date: 2006-10-08
forum: General Help
---

### Post by Drifter on 2006-10-08
Question is when will ubuntu get a distro out that will be easy to run.  Such things as burning cd's & DVD's and that does not have the terminal commands that need to be remembered.  It seems that someone could build a distro with user friendly Gnu etc.

---

### Post by aysiu on 2006-10-08
[quote=Drifter]Question is when will ubuntu get a distro out that will be easy to run. Such things as burning cd's & DVD's and that does not have the terminal commands that need to be remembered.[/quote]When? I'd say about four months ago.

> It seems that someone could build a distro with user friendly Gnu etc.Many people have built distros "with user friendly Gnu etc." Try PCLinuxOS, Mepis, or Linspire/Freespire.

Ubuntu is not the be-all and end-all of point-and-click. In fact, of all the "user friendly" distros out there, Ubuntu is probably still the most command-line-dependent.

---

### Post by Cronjob on 2006-10-09
Ubuntu is pretty easy to run out of the box as it is.

No, it isn't as easy as Microsoft and if you want to run on a non-i386 architecture, it can be a hassle. And if you want to get sound working properly, it can be a hassle (and even then, you might have to tolerate a lot of snapping, crackling and popping). And getting your high-resolution monitor to display at max capacity can be a hassle. And getting proprietary formats (mp3, etc) to work consistantly through all your applications can be a hassle. And Flash can be a hassle. And you'll actually likely encounter lots of crashing in certain environments (hell, amarok has crashed about 20 times just this evening on me, VNC has crashed several times today, krusader has crashed a half dozen times today, azureus has hung three times today, etc) . . . 

But if easy is what you want, you really shouldn't move to linux as a full tme environment anyway. I've run linux servers for almost a decade (slackware, then debian) and only recently moved to it full time on the desktop (with Kubuntu) after years of CDE on Solaris and OSX -- and I don't run linux because it's "easy". In fact, linux can be a total whore sometimes. But I like the general idea, philosophy and I like not having to jump through hoops to setup development environments with postgresql, perl, python, ruby, apache, etc that I would in another environment (even in OSX -- it can be a pain in the *** to find all the packages you want and you will often have to compile from scratch, which gets old after awhile).

As I said, I've been using linux for about eight years (though 99.5% via the command line with 'screen' as my "window manager") and I found getting things to work on my 3800+ AMD64 Dual Core / Nvidia 512 7800gt / Audigy 2 / Apple Cinema Display 30" system to be a real difficult task. And I'm a software engineer of eight years (pretty much my entire adult life) and have been building machines, compiling, running BBSes and variously hacking this or that for almost two decades. 

So no, it's not "easy". Meaning, I wouldn't suggest that my mom or anyone else who isn't a full time computer geek run linux without having a willingly available geek to help them through rough times and I wouldn't reccommend that anyone without a lot of experience try installing it.

I think it's all to easy for those of us who have been using it for a long time to say "oh, it's easy and stable!" but the truth is, while my servers run for years without a reboot, by linux desktops are usually not a whole lot more reliable (either in means of the entire OS or just crashing applications) than a good XP64 install.

Linux is easier when you're using older hardware, for sure. It's hard to find a retail 32bit CPU these days, but 64bit can pose some pains (though in my opinion, they're worth it). And high end video cards can be a complete mess. Hell, I put off linux on the desktop for the last two years because until Dapper, I could never get any linux to properly display in full 2560x1600 resolution on my monitor. I doubt anyone's grandmother would find editing ModeLines in xorg.conf to be "easy". And when SATA drives are not read in the proper order (for instance, a lot of us have found that things will install properly, but then we can't boot into the OS because linux will see the third SATA channel as the first and the rest of them are moved accordingly... and I don't know a lot of people who are not software engineers or hardware guys or otherwise heavy hobbiests that would know how to conclude that they need to burn a livecd so they can boot into their system through it, go into root to edit the /etc/fstab and manually edit the drive mappings and then rebooting -- or opening up their box and rearrange their drives accordingly.

And sure, there are great places like these forums - but if it's your only machine, how are you going to do that when your system isn't working becuase it won't even boot because of a SATA problem? And people will still see it as a matter of "well, I don't have to go into forums and hope some guru will answer my questions just to get Windows to install and boot".

Desktop linux is "manageable" if you're very experienced. If you're not, it is in no way easy and I think we ignore the elephant in the room if we pretend the average (even somewhat experienced) user will approach linux for the first time and not find it utterly frustrating and confusing.

Linux (and ubuntu) is awesome for what I need. I have no illusion that it is something that would be appropriate for my 50 year old office-worker mother or my 20 year old massage therapist sister or my 24 year old fashion designer girlfriend or even my 19 year old tech-support-monkey brother.

Hopefully we'll get there someday, though. :)


As for burning CDs and stuff . . . I'm not sure what you need to do by command line? I used k3b to burn a data CD within five minutes of installing Kubuntu. Didn't even have to install or configure it. Just clicked on the icon in the menu, clicked on the iso I wanted to burn and did so.

Of course, if you want to deal with mp3s or something to CD... it might be a bit more difficult.

---

