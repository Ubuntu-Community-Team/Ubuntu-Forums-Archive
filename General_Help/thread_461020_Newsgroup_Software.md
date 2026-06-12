---
title: "Newsgroup Software"
date: 2007-06-01
forum: General Help
---

### Post by shavenlunatic on 2007-06-01
Hi,

There are very few things now standing between me and ditching windows (games mainly.. but happy to dual-boot purely for that purpose)

I am looking for opinions on software to be used for:

Newsgroups - Now, I don't give a hoot about 'reading' the newsgroups, I just purely want to download from the binaries - I tried 'pan' but it lacked some functions which I like (e.g. being able to see how many active threads in newsgroups etc.)

DVD writing software - Now, in windows I pick and choose between a few packages, Nero being one of them (not my preffered, but it will do as an example), An all-in-one package which will take a .AVI, convert it, and burn it to a DVD with the option to create a menu system.  There is plenty of linux software which will convert avi to dvd but I can't seem to find a package which will to everything I want in a nice GUI. 

Thanks in advance.

---

### Post by indytim on 2007-06-01
For the DVD burning s/w, recommend you check out k3b (my favorite) - it's in the repositories,

IndyTim

---

### Post by shavenlunatic on 2007-06-01
> **indytim said:**
> For the DVD burning s/w, recommend you check out k3b (my favorite) - it's in the repositories,

IndyTim

erm, plenty of burning tools, but where does it let you load an .avi, convert it to dvd, setup a menu system and then burn it to disk?

If i'm being blind, please tell me cos I can't find it..

---

### Post by Campingman on 2007-06-01
You could try Klibido for your newsreader, it is the one I settled on after trying most of them.  It is in the repositories.

---

### Post by shavenlunatic on 2007-06-02
Klibido seems lovely (single click download a little annoying but 'm sure tht will be in options somewhere) but overall its just what I was looking for :) thank you


now, any further suggestions about DVD writing stuff (i have no idea why this thread is only called newsroup software, I didn't title it just that.. oh well).. is there any software I describ ed above for gnu/linux?

---

### Post by kinkdxm on 2007-06-08
**Klibido** - been using it for months and months now works great!
**GPar2** - gui tool for .par files works great!

**AcidRip** (DVD > avi)
**DeVeDe** (avi > DVD) - Haven't tried it myself.
"Note for Ubuntu Feisty users: currently (as April 20, 2007), the Mplayer/Mencoder version in Ubuntu Feisty is buggy and produces noisy sound when used with DeVeDe. While the maintainer doesn't fix it, you can use the .deb package created by from the SVN sources (it's available in the Download section)."
[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)
**ConvertXtoDVD** (under wine) - heard that works. loved it in xp
**Nero for Linux** - Found out yesterday about this
"Enjoy the same functionalities as in Nero Burning ROM 7"
hmm wonder if that really true or not
would be sweet if I could get it for free by mailing them my windows Nero that came with my dvdr/cdr drives.
Bet not 
[http://www.nero.com/eng/NeroLINUX.html](http://www.nero.com/eng/NeroLINUX.html)

---

### Post by frodon on 2007-06-08
For par2 files, i wrote a nautilus script which makes the check and repair even more easy :
[http://ubuntuforums.org/showthread.php?t=394585](http://ubuntuforums.org/showthread.php?t=394585)

As for burning software k3b is a rock solid one.

---

### Post by kinkdxm on 2007-06-08
> **frodon said:**
> For par2 files, i wrote a nautilus script which makes the check and repair even more easy :
[http://ubuntuforums.org/showthread.php?t=394585](http://ubuntuforums.org/showthread.php?t=394585)

NICE!

note GPar2 is a gui tool for pararchive.
didn't even know it existed till i reinstalled Feisty and went to install parchive and GPar2 popped up.

---

### Post by shavenlunatic on 2007-06-08
been using gpar2 for a while now, does the job and that's all I need :)

nero linux i tried but tbh, it was crap

plenty of burning software around.. but none with menu creation functionality (at least none in the GUI, but I expect setting up nice menus, backgrounds and animations is a bit of a nightmare from a command line anyway!)


running some stuff under wine might be my best option... I have a few windows apps that I like so hopefully one of them will work well under wine, plus it will give me a chance to test out winedoors which I setup and then never used :)

It's so fustrating, I want to drop windows so badly, if it wasn't for dvd burning and goddamn games it would have been ditched.  Admittedly games support underr wine is getting better.. and if the vid card manufacturers do end up opensourcing their drivers it will only get better.. but for the immediate future I guess XP will still have a special space set aside on a hard drive :(

---

### Post by mrbungle on 2007-06-10
newsbin pro with wine works the best for me.

plus they have built in autorar and par.  still beta a little, but for the most part works fine.

---

### Post by andrew.46 on 2007-06-11
Hi,

 Well if you want to go hard_core linux for newsgroups you would do worse than trying slrn. My angle here is that I am in the middle of writiing a setup guide for slrn:

[http://people.aapt.net.au/~adjlstrong/sneak_preview.html](http://people.aapt.net.au/~adjlstrong/sneak_preview.html)

 But if you are after a flashy GUI and a lot of porn slrn may not be for you :-)

                        Andrew

---

### Post by TNBY963 on 2007-06-24
If you're not afraid of the command line (and you shouldn't be), nothing beats hellanzb. It's a python script that monitors a folder where you put your nzb's. When you start it, it will automatically download, check the pars and unrar.
The best thing about it is that it only downloads the par files you need, so no unnecesary downloads.

Here is a well-written guide: [http://ubuntuforums.org/showthread.php?t=169749](http://ubuntuforums.org/showthread.php?t=169749)

This is a program I miss when I'm on Windows :-)

Gert

---

### Post by technotika on 2008-03-10
Hi there

I just got set up with HELLANZB recently and have to agree, it's the absolute shiznit. Instantly hits top speeds and I am getting better download speeds than when I was in windows with newsleecher. It doesnt hog your cpu and just runs virtually un noticed in the back ground.....hey just put it on another side of the cube, eh? :-) 

It might seem like hard work to set up but there are a couple of walkthroughs on this site and i counted maybe 4/5 changes. adding your usenet account, setting unraring and setting folder location. So give it a go.

All i need now is some tips on choosing a NZB webiste. I saw NGINDEX and NEWSBIN and wondered if anyone used them and can confirm or otherwise if they are worth suscribing to???

thanks 

Jerry:guitar:

---

### Post by Kerry_W on 2008-03-10
I tried HellaNZB but my download speeds were a third of what i get with Klibido.  nothing i changed in the config seemed to make any difference.

---

