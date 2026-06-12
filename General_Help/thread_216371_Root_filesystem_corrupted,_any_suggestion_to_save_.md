---
title: "Root filesystem corrupted, any suggestion to save my system?"
date: 2006-07-15
forum: General Help
---

### Post by Ramses de Norre on 2006-07-15
Today I was looking around on launchpad and I saw a bug reported about xine causing a kernel panic with the fglrx driver, out of curiosity I started xine and guess what.. everything froze. So I had to hard reset and when I rebooted I got a grub error 17.
So I booted up a dapper live disc and ran fsck on / and /home. / was full of errors but after finishing fsck I was able to load grub. When I booted up my system the boot process hang after mounting root filesystem.
I returned to the live session and I was able to mount my root partition. I noticed that there were a hell of a lot of files in lost+found so I think I can conclude that many files are corrupted..
My question: how the hell could this happen and is there anything I can do to save my system?
I'd hate to reinstall..

---

### Post by infoburner on 2006-07-15
sounds to me like your hard drive is hosed. i think re-installing is your best bet.

---

### Post by Ramses de Norre on 2006-07-15
I'll reinstall then.. man this surely shrinks my confidence in Linux and ubuntu..

---

### Post by taurus on 2006-07-15
Let me get this right.  You knew full well there was a bug with xine and fglrx, causing kernel panic, but you went ahead and ran it anyway and claimed "man this surely shrinks my confidence in Linux and ubuntu..."  I think in this case, the problem lies between the keyboard and the chair!!!  What filesystem did you use anyway?  Never have any problem with ext3 even though I have done a few hard resets and power outages here...

---

### Post by infoburner on 2006-07-15
i doubt it's a linux problem, i think its probably entirely hardware related. the only time ive had a problem like that it was the same in all 3 OSes i had on the same machine (FreeBSD, Ubuntu, Win2k). files dissapeared, some stayed but the size was zero and there was nothing in it etc. mayhem.

---

### Post by Ramses de Norre on 2006-07-15
Yes, maybe you can call it stupid that I tried to start xine, but that's the program I use all the time for movies and I never had a problem with it.. I guess I didn't used it with the newer fglrx and kernel yet and I would have started it anyway whether I read about the bug or not.
My big dissapointment is about the filesystem, it is ext3. I've needed to do some hard resets before too and never did an fsck report any corruption, but now my whole filesystem seems broken, I have 13493 folders and files in my lost+found directory..

---

