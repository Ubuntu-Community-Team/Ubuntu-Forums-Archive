---
title: "Why does unrar-free failed to unpack my rar archive?"
date: 2006-10-16
forum: General Help
---

### Post by OldboyJack on 2006-10-16
Hi everybody,

just happily installed unrar-free software. But when I tried to unrar my rar archive it show me that unpacking it failed. Why does it so? Can anybody help me, please?

Sincerely yours

OldboyJack

---

### Post by droppedd on 2006-10-16
not that it's a proper solution, but try unrar-nonfree (make sure universe/multiverse are turned on in Synaptic's repository list). The free version can't unrar all files, probably due to some patent restriction or another. If you don't have a deep-seated moral opposition to non-open-source software, you're better off with unrar-nonfree anyways.

---

### Post by OldboyJack on 2006-10-16
> **droppedd said:**
> not that it's a proper solution, but try unrar-nonfree (make sure universe/multiverse are turned on in Synaptic's repository list). The free version can't unrar all files, probably due to some patent restriction or another. If you don't have a deep-seated moral opposition to non-open-source software, you're better off with unrar-nonfree anyways.

Hi,

big thanks for your post. I've tried to install this unrar-nonfree software using Synaptic, but I failed. Why? Synaptic show me this software only in narrow left panel, so I can't do anything with it. Any ideas how to unrar my rar archive??

I would be grateful for any additional help

Your

OldboyJack

---

### Post by taurus on 2006-10-16
What file are you trying to unpack and what is the error message?

---

### Post by OldboyJack on 2006-10-16
> **taurus said:**
> What file are you trying to unpack and what is the error message?

Hi,

Thanks for your post. The archive I am trying to unpack is the set of songs (in .mp3) format send to me from a small indiependent record company - those are samples of music they are publishing. And the error message is: Extracting [name of file] Failed.
What am I doing wrong?

Thanks again

Your

OldboyJack

---

### Post by taurus on 2006-10-16
Can you show me the exact command you used to unpack it?

---

### Post by OldboyJack on 2006-10-16
> **taurus said:**
> Can you show me the exact command you used to unpack it?

Yes, of course!
I used both commands:
**unrar-free** [name of the rar archive]
**unrar-free -x** [name of the rar archive]

Wrong commands?

Your

OldboyJack

---

### Post by Jucato on 2006-10-16
AFAIK, in Dapper, the nonfree RAR/UNRAR packages are called rar and unrar respectively. (In Breezy they were rar-nonfree and unrar-nonfree). Of course, you need to have the multiverse repositories enabled to be able to see and install them.

---

### Post by John.Michael.Kane on 2006-10-16
When I used the unrar programs I was able to right click the file,and extract the info. there was no need to type the command in the terminal.

---

### Post by OldboyJack on 2006-10-16
> **Jucato said:**
> AFAIK, in Dapper, the nonfree RAR/UNRAR packages are called rar and unrar respectively. (In Breezy they were rar-nonfree and unrar-nonfree). Of course, you need to have the multiverse repositories enabled to be able to see and install them.

Hi,

the problem is, that, although I have multiverse repositories enabled, Synaptic doesnt show any more rar/unrar stuff but this unrar-free :( 
Any solutions?

Take care!

OldboyJack

---

### Post by OldboyJack on 2006-10-16
> **SD-Plissken said:**
> When I used the unrar programs I was able to right click the file,and extract the info. there was no need to type the command in the terminal.

Hi,

this is my dream: to find and install a piece of software, which allows me to do it...

Thanks for your post

Your

OldboyJack

---

### Post by Jucato on 2006-10-16
> **OldboyJack said:**
> Hi,

the problem is, that, although I have multiverse repositories enabled, Synaptic doesnt show any more rar/unrar stuff but this unrar-free :( 
Any solutions?

Take care!

OldboyJack

That would indeed be strange. The only reason I could think of is that the correct multiverse repository is not enabled/added. If you could kindly post the contents of  your /etc/apt/sources.list, we'd be able to check.

---

### Post by Acyong on 2006-10-21
This circumstance is same to me. The context of sources.list is shown as below:

```
# 
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

Thanks!

---

### Post by Jucato on 2006-10-21
You do not have multiverse enabled. You need to edit this line

> # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe to this

> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse

---

### Post by Fsngruv on 2006-11-21
I'm having the same problem and can't determine whether or not I've truly enabled the Multiverse repository, here's my sources.list file

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by CatKiller on 2006-11-22
> **Fsngruv said:**
> I'm having the same problem and can't determine whether or not I've truly enabled the Multiverse repository, here's my sources.list file

I don't think you have. I think you've just got multiverse back-ports. Change this line:

```
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
```

to this:

```
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse
``` Or change it in Synaptic's Repositories section.

---

### Post by jahnni on 2007-09-13
> **OldboyJack said:**
> Yes, of course!
I used both commands:
**unrar-free** [name of the rar archive]
**unrar-free -x** [name of the rar archive]

Wrong commands?

Your

OldboyJack
Hi!
I had the same problem, finally tried with 
**sudo unrar-free** [name of the rar archive]
and it worked out!
irie
  Gio

---

