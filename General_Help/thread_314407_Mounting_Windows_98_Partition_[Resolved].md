---
title: "Mounting Windows 98 Partition? [Resolved]"
date: 2006-12-07
forum: General Help
---

### Post by Banagor on 2006-12-07
Hey there,

Recently, a client of mine gave me an old computer of his to fix up. He doesn't use it much. It's a 5 year old Sony Vaio desktop which runs Windows 98.

Well, I suggested to him that I put in an old HD (bigger than his and absolutely good working condition), and I install Linux on it. He only uses the computer to browse the web and email, as well as make audio files for a radio show he hosts a few times a week. So I figured Ubuntu is the way to go.

So I did just that. Last night, I put in an extra HD, made it the master, installed Ubuntu - everything flawlessly. Great job.

So the Master has Ubuntu (and yes, Grub is working just fine at bootup), and the Slave is Windows 98. My question is the following:

I want to migrate all his old files over to Linux just by copying them over. I can't, however, appear to mount his Windows partition. It's listed as NTFS for some reason (not sure if that's correct). It also reads it as /dev/hdb (hda being Linux).

Any quick/easy suggestions as to what to do? I just want to mount, and then select-drag all relevant files to new folders in Linux for him.

Oh and anyone have a suggestion for a nice and freeware type of program to record radio shows in for Linux where somebody can drag/drop files? I'm thinking of Audacity but haven't checked if it runs on Linux, though my PC and Mac both have it.

I still, btw, can't get over how nice Ubuntu looks. Seriously. Really really slick and glossy and easy to use. :)

---

### Post by bodhi.zazen on 2006-12-07
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Most likely```
sudo mkdir /media/windows && sudo mount /dev/hda1 /media/windows -o umask=000
```

---

### Post by Banagor on 2006-12-08
Awesome! That worked and thank you very much.

Just what I needed. :)

---

