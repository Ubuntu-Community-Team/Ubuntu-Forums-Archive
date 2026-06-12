---
title: "Vlc .8.6"
date: 2006-12-15
forum: General Help
---

### Post by zombie_killer on 2006-12-15
I've been having the WORST time compiling VLC .8.6 on my Edgy box.  Is there a specific, step-by-step walk-through that'll work?  Or any packages out there?  Repo's just give me .8.5, still.

---

### Post by Lord Illidan on 2006-12-15
Install these from apt-get :
```
sudo apt-get install libpostproc-dev

```

and tell me how compiling goes.

---

### Post by zombie_killer on 2006-12-15
Didn't really help any.  Still having all sorts of problems with insane numbers of plugins needing to be installed, then ./configure still says some are missing, then installing other plugins results in more build dependencies not being met, and the cycle continues....

---

### Post by doobit on 2006-12-15
> **zombie_killer said:**
> Didn't really help any.  Still having all sorts of problems with insane numbers of plugins needing to be installed, then ./configure still says some are missing, then installing other plugins results in more build dependencies not being met, and the cycle continues....

I am no authority on this, but it looks like VLC needs all kinds of non-free components to function. That probably explains why they are not available directly from Ubuntu.
If 8.6 is based on 8.5, in anyway, then installing 8.5 first (using apt-get from the repos) would probably satisfy many dependancies, except, of course, the newest elements.

---

### Post by Lord Illidan on 2006-12-15
> **zombie_killer said:**
> Didn't really help any.  Still having all sorts of problems with insane numbers of plugins needing to be installed, then ./configure still says some are missing, then installing other plugins results in more build dependencies not being met, and the cycle continues....

Just managed to install mine. Give me the error messages if you want help.

---

### Post by zombie_killer on 2006-12-15
Do you have perhaps the transcript of commands you used to install it?  I've tried 3 different methods, now, and while some of the errors are the same, others are different.

---

### Post by fabbaz on 2006-12-15
i was just getting ready to get into some seriously painful installation-process  - 
when discovering it had already updated automatically. :D
maybe someone would like to follow the "official" installation guide: [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by cor2y on 2006-12-17
the problem is even with the correct repos enabled i still am not getting version 0.8.6.

I did manage to compile vlc but guess what the reason i was compiling it for didn't work in this case native wmv3  and flash video support.
I used the latest svn ffmpeg which has built in support and playing back wmv file in ffplay and a flash video worked.
But when i tried the compiled vlc  nothing.

---

### Post by jeremy on 2006-12-18
I have installed 8.6 from the repos, here is my sources.list

## Ubuntu
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse 

## Updates
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse 

## Backports
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse 

## Security Updates
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security main restricted universe multiverse 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security main restricted universe multiverse 

## CANONICAL COMMERCIAL REPOSITORY 
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) edgy-commercial main

---

### Post by lotusleaf on 2006-12-19
> **jeremy said:**
> I have installed 8.6 from the repos, here is my sources.list


But the version in the repos for Edgy at the moment is a pre-release. A quick check at packages.ubuntu.com confirms this. I'd guess a lot of people are interested in building the final for themselves.

---

### Post by jeremy on 2006-12-19
> **lotusleaf said:**
> But the version in the repos for Edgy at the moment is a pre-release. A quick check at packages.ubuntu.com confirms this. I'd guess a lot of people are interested in building the final for themselves.

Sorry, yes, you're right about that. However, it does seem to work just fine.

---

### Post by cor2y on 2006-12-20
The backport  seems only for Edgy anyone have a compiled version or backport for Dapper?

---

### Post by lucis on 2006-12-24
I posted a guide you may be interested in on compiling 0.8.6. [http://ubuntuforums.org/showthread.php?t=323855](http://ubuntuforums.org/showthread.php?t=323855)

---

