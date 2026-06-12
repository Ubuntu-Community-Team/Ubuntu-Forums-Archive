---
title: "[SOLVED] Error message  'update-manager' package"
date: 2007-10-15
forum: General Help
---

### Post by TaoBoogie on 2007-10-15
Hi there.
I have tried to install VirtualBox 1.5 on my Ubuntu Feisty to-day unsucessfully and now i keep getting this message when I click on the Update icon "star " that appeared shortly after. 
> An unresolvable problem occurred while initialising the package information. 

Please report this bug against the 'update-manager' package and include the following error message: 

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'

I noticed in a previous post on a similar problem that advice was given to post the results of typing 
> cat /etc/apt/sources.list
So here are my results:

> tao@tao-desktop:~$ cat /etc/apt/sources.list

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to

# newer versions of the distribution.



deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted

deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties



## Major bug fix updates produced after the final release of the

## distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu

## team, and may not be under a free licence. Please satisfy yourself as to

## your rights to use the software. Also, please note that software in

## universe WILL NOT receive any review or updates from the Ubuntu security

## team.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 

## team, and may not be under a free licence. Please satisfy yourself as to 

## your rights to use the software. Also, please note that software in 

## multiverse WILL NOT receive any review or updates from the Ubuntu

## security team.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse



## Uncomment the following two lines to add software from the 'backports'

## repository.

## N.B. software from this repository may not have been tested as

## extensively as that contained in the main release, although it includes

## newer versions of some applications which may provide useful features.

## Also, please note that software in backports WILL NOT receive any review

## or updates from the Ubuntu security team.

# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse



deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe

deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

# deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main

tao@tao-desktop:~$ 


The reason I tried to install VirtualBox is to attempt to run Photoshop. Shall I keep trying to install VirtualBox or do you think perhaps Wine may be better?
My first objective though is to "repair" the Update manager or whatever is causing the error messages.
Thanks in advance.
Tao

---

### Post by Pumalite on 2007-10-15
You might want to try:

sudo dpkg --remove --force-remove-reinstreq virtualbox
Then reinstall if need be.

---

### Post by TaoBoogie on 2007-10-15
Thanks Pumalite
I tried your suggestion and It seems to have worked but I'll restart and run update again just to make sure. Then I'll report back.
These are the messages I got from your suggestion:
> tao@tao-desktop:~$ sudo dpkg --remove --force-remove-reinstreq virtualbox

Password:

dpkg - warning, overriding problem because --force enabled:

 Package is in a very bad inconsistent state - you should

 reinstall it before attempting a removal.

(Reading database ... 

dpkg: serious warning: files list file for package `virtualbox' missing, assuming package has no files currently installed.

124599 files and directories currently installed.)

Removing virtualbox ...

tao@tao-desktop:~$ 


---

### Post by Pumalite on 2007-10-15
Sometimes you have to break some eggs to make an omellette

---

### Post by HelixAgent on 2007-10-15
> **Pumalite said:**
> Sometimes you have to break some eggs to make an omellette lol!

Try using Automatix to install Virtualbox is much easier!

---

### Post by TaoBoogie on 2007-10-15
Yes, that seems to have done the trick, thank you for your time and help Pumalite. I'd be totally lost without this forum and people like yourselves giving novices like me a helping hand.
I've more or less got Ubuntu working the way I like it, beautifully. I just wanted to go that extra mile and get Photoshop, which is the main software I use, working from within Ubuntu. I think I'll just use XP on another drive for that. I really don't want to mess any more and break this installation.
There again my curosity may make me try out Wine and Automatix (which I've never heard of before). Decisions, decisions! =)

---

### Post by Pumalite on 2007-10-15
What about Gimp?. Not a photoshop user since 2000.

---

### Post by TaoBoogie on 2007-10-15
Yes I have looked at Gimp. It's just that I  ** *know* ** Photoshop quite well. It has taken me the best part of five years to get to the stage I'm at now, it fits me like a comfortable glove. I'm rather reluctant to start the learning process over again almost from scratch, especially when I've a lot of RAW files to edit from week to week.
I feel like I've got my hands full (so to speak) learning and finding my way around Ubuntu I don't want to have to learn another new piece of software like Gimp unless I really have to. Don't get me wrong, I will play with Gimp and get to know it that way, It's just that If I have to process a gigs worth of RAW images ready for selection and upload to various sites I could do it in Photoshop in a day or two. it would take me an awful lot longer using Gimp and I don't think the results would be as good.

I've been looking around the forum for information on Automatix and it seems there can be a lot of problems installing software with that too so I don't think I'll bother unless i read some good reviews. Thank you for the suggestion though Pumalite, I really do appreciate the time and effort.
Tao

---

