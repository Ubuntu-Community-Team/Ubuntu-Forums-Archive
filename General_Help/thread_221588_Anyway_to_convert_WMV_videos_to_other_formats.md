---
title: "Anyway to convert WMV videos to other formats?"
date: 2006-07-23
forum: General Help
---

### Post by taekwondodogoof on 2006-07-23
Hi, I don't want to download an illegal codec if I don't have to. Is there a ubuntu-compatible program that can convert these to other formats such as avi? Thanks in advance :D

---

### Post by scxtt on 2006-07-23
i don't see how you can convert wmv --> avi if you don't have a wmv ("illegal", gasp!) decoder installed ...

not saying it's impossible (in ubuntu), but the logic of it doesn't add up ... windows movie maker might be able to assist you, depending on what codecs you have installed ...

seems easier to me to just d/l a codec pack from the repos ...

---

### Post by taekwondodogoof on 2006-07-23
Ok, I decided just to download the w32codecs for the AMD 64 bit architecture. I have them on my desktop, how do I install them, I tried using sudo dkpg then the name of the file, but it said it could not be found? Sry, I'm sort of new at this lol

---

### Post by scxtt on 2006-07-23
if it's a tar (tape archive) or zip file (even bzip), possibly w32codecs.tar.bz2 you can just extract it, then move all the files to /usr/lib/win32 (the default location where most medial players look for windows codecs ...

---

### Post by taekwondodogoof on 2006-07-23
Ok, I extracted the files to there, but I still can't play the .wmv file, does it matter if I have a 64-bit architecture?

---

### Post by scxtt on 2006-07-23
i don't see how it could, since these files aren't executable ...

what codec pack did you install? (was it from the repos?)
what media player are you using?

---

### Post by taekwondodogoof on 2006-07-23
Ok,
1)w32codecs_20060611.orig.tar.gz
2)I'm trying to use MPlayer, but any would work for me, I don't care,

Thanks for all your help so far scxtt =D! I appreciate it

---

### Post by scxtt on 2006-07-23
i would advise using the w32codec .deb that's in the repos - look it up in synaptic as w32codecs - you may need to add the following to your /etc/apt/sources.list:
[indent]deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free[/indent]

i don't have mplayer installed, and haven't used it in years - but i don't see why it shouldn't work ...

and i'm glad to help! :)

(if this doesn't work, i do know that codecs from mplayerhq.hu and xine 0.99.3 work, that what i use)

---

### Post by mllr on 2006-07-23
> **scxtt said:**
> you may need to add the following to your /etc/apt/sources.list:
[indent]deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free[/indent]

and after doing it:

```
sudo apt-get install w32codecs
```

And if your mplayer don't runs, use it:

```
sudo apt-get remove mplayer
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install mplayer
```

[]'s

---

### Post by Kilz on 2006-07-24
If you are running 64bit Dapper you need to setup a 32bit mplayer and the 32bit win32codecs to watch wmv's. [There is a howto here.]("http://www.ubuntuforums.org/showthread.php?t=188974")

---

