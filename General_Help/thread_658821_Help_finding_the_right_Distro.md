---
title: "Help finding the right Distro"
date: 2008-01-05
forum: General Help
---

### Post by Riffer on 2008-01-05
[SIZE="2"]To give you a (hopefully) quick background.  I'm a teacher  in Canada, who's school district runs a hodge podge of Debian servers, and depending on the school and or teacher, Macs and Windows for teacher workstations and classroom labs.  Events last spring led me to become an advocate and user of Linux and Ubuntu.

Frankly I became sick and tired of the PC vs Mac wars, and the constant upgrading to meet the 2 OSes needs.  As I did more research, I was appalled to find that most schools have rooms filled with perfectly good machines that were deemed unusable because they couldn't run XP (in my school we may have up to 100 of these machines stacked away).  

While at the moment I'm a lone voice, I think (hope) that with dwindling  funding that  both teachers a Admin will take a serious look at Open Source and Linux.  To further that end I'm thinking of holding a workshop introducing Linux to interested parties, using the old machines.

So I'm asking for help and advice in finding a desktop distro(s) that is very user friendly, compatible  with Debian servers, and can make an older machine run like a top.  And lol, comes with decent software preloaded, each machine should be internet ready, net workable and do fairly basic stuff like wordprocessing and the like.

What we have ranges from PII with 128 RAM up to P4 with perhaps 512 RAM, with the majority being PIII with 256 RAM with 20 gig HD.  The lucky thing is that most comps will be of the same specs.  I would like Linux to run from the HD rather then from a liveCD.

I have tried Edubuntu which runs but slow and Xubuntu which seems to be quicker, (which is to be expected), both on the PIII.  I've heard some very good things about Linux Mint, but when I went to their site I couldn't find any specs on system requirements.

Sorry for the long post and thanks in advance.                                      [/SIZE]

---

### Post by Craigus on 2008-01-05
Linux Mint 4.0 is based on Ubuntu 7.10, with some extra goodies. It runs gnome, so if standard Ubuntu is slow, Mint will be also.

I take it that whatever you choose will be required to run acceptably on the lowest spec machines as well?

If so, I think you may have to look at a fluxbox based distro.
You will want something with good repository support so that installing new applications is easy.

Have a look at Antix

[http://antix.mepis.org/index.php/Main_Page]("http://antix.mepis.org/index.php/Main_Page")

PCFluxboxOS

[http://pcfluxboxos.wikidot.com/]("http://pcfluxboxos.wikidot.com/")

Fluxbuntu

[http://fluxbuntu.org/js.html]("http://fluxbuntu.org/js.html")

Those PII 128Mb machines are still going to struggle a bit though.

---

### Post by Riffer on 2008-01-05
[SIZE="2"]I'm thinking that those PII might have to beconverted to thin clients in order to use.   Thanks for the links :)                       [/SIZE]

---

### Post by yourpalal on 2008-01-05
I understand that this is probably a little late but...
[http://damnsmalllinux.org/](http://damnsmalllinux.org/)
This distro is meant to be incredibly lightweight and is also based on debian = good repo support
it includes (I beleive) everything you will need on a simple machine but you could install more excinting things also!

---

### Post by Riffer on 2008-01-05
[SIZE="2"]Looks like a fun and interesting Distro.  Not quite what I'm looking for as it isn't as full featured out of the box as I would like.  But I will pass on the link to the IT teachers as they are always looking for projects for the seniors and I can see lots of possibilities with DSL.  Thanks :)                      [/SIZE]

---

### Post by gn2 on 2008-01-05
Zenwalk is also worth a look.

I'm using 4.8 on my old P3 laptop and it seems to perform slightly better than Xubuntu 7.04 did.

---

### Post by ugm6hr on 2008-01-05
If you are looking for something that can be installed straight off a CD onto a HD with minimal tinkering, then Xubuntu is a good choice (if it is fast enough).  Just remember to turn desktop effects off to speed things up.  

Another option is gOS ([http://www.thinkgos.com/index.html](http://www.thinkgos.com/index.html)), which *looks* really good, but has a few unusual behaviours at the moment, so is probably best left until it is more stable and intuitive.  But the idea is very good, with direct desktop links to online services (which can be modified) in addition to pre-installed desktop applications.

But the fact that you said that the majority of your hardware is identical leads me to my recommendation:
Someone needs to create a custom Linux for your needs, based on whichever distro you want (Ubuntu would be reasonable).  IceWM would be my suggestion for a Window Manager to keep things simple for Apple / Windows users.  This is a good example of what a simple interface could look like with IceWM: [http://ubuntuforums.org/showpost.php?p=1954760&postcount=172](http://ubuntuforums.org/showpost.php?p=1954760&postcount=172).

Having done that, you could use PartImage ([http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)) to just copy that setup and restore it direct to all the other computer hard drives.

I'm no expert on networking, but Ubuntu has plenty in the repos to help with Remote Access etc.  Perhaps planning the project for Ubuntu Hardy's release would be sensible (has support planned for 3 years), although Gutsy is probably stable enough at the moment.

Good luck.

It would be a shame for those old computers to go to waste.  At the very least, they could be used to set up additional computer labs just for internet access etc.

---

### Post by Riffer on 2008-01-05
[SIZE="2"]Thanks for all your replies.  Zenwalk looks interesting and is a possibility.  I've ruled out gOS because of its reliance on web based apps.  Access to many sites have been lock down pretty tight, (kids remember) I'll double check to see if its a problem.

I think that all the PII's are good for are for thin clients which would boot right from the network card.  So it looks like I will be concentrating on the PIII's and above. Xubuntu and perhaps Linux Mint Fluxbox edition seem to be likely candidates.

I like the idea using a base system (like Ubuntu or Debian) and build a system  using different managers, though right now its beyond my abilities.  Could be something that I or senior IT students can play with.

The chances of my district moving over to Linux this year (and next) is about the same as Adobe porting its software over to Linux this year.  The workshop I'm thinking of having, is to show people that Linux isn't a geek OS but rather one that can but used out of the box for all levels of users.

Thanks guys you've all helped me clarify my thinking and the direction I should go.                        [/SIZE]

---

### Post by ugm6hr on 2008-01-05
> **Riffer said:**
> I like the idea using a base system (like Ubuntu or Debian) and build a system  using different managers, though right now its beyond my abilities.  Could be something that I or senior IT students can play with.

The chances of my district moving over to Linux this year (and next) is about the same as Adobe porting its software over to Linux this year.  The workshop I'm thinking of having, is to show people that Linux isn't a geek OS but rather one that can but used out of the box for all levels of users.


Have a look at this: [http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

It explains how the basics of a very simple Ubuntu/IceWM setup can be achieved with minimal effort.  If the IT students are looking for a project - this might be reasonable.  I know of a school in the UK that set up an out-of-hours homework / internet lab from discarded hardware using Linux with significant input from the students.  Would make a good demonstration to the kids, and possibly also to the powers-that-be, if something could be put together that is entirely usable and cheap (from memory - a 20 computer lab was set up with under £200, mainly for power supplies and network cabling etc).

Good luck with this project!

---

### Post by msofer on 2008-01-06
Have you looked at [http://vectorlinux.com/]("http://vectorlinux.com/")?

---

### Post by Riffer on 2008-01-07
[SIZE="2"]Gee all incredible answers  and its was great reading up on other Distros.  I even been trying other window managers, which has led to a bunch of questions for other threads.  This has also led to me passing on some info to our IT teacher that might be of interest to him.

Right now I'm going to try out other window managers on Edubuntu, it does run on the PIII 256 RAM machine that I'm using as a test machine.  It runs but a bit slow, maybe another window manager will snap it up a bit.  Also I'm going to try Linux Mint the Fluxbox edition and see how that goes.

I can see I have to run out and buy more blank CD's, theres a few Distros I would like to try and maybe I'll finally get rid of Windows on my home comp.  ZenWalk look promising as well as Vector.  But I must say in so many ways I would rather stick to open source Distros so I'm leaving Vector alone for awhile.

Thanks all for your advice.                                            [/SIZE]

---

