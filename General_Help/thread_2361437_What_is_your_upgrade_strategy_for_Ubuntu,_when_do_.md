---
title: "What is your upgrade strategy for Ubuntu, when do you start using newer versions?"
date: 2017-05-16
forum: General Help
---

### Post by locam on 2017-05-16
I'm wondering how do you all deal with newer Ubuntu versions.

I have installed 17.04 when it came out, but I find it pretty unstable for everyday use: the backup process will crash when installing, and then whenever it makes a backup; there are some UI glitches; some software (google chrome for example) don't install on the first few tries...

So how do you handle upgrades? Do you only stick to LTS versions, do you wait for the point release to upgrade, do you always stay one version behind latest (so16.10 for now)?

I love using Ubuntu, but the problems in 17.04 greatly hamper my daily use of it. And I use a very well supported ThinkPad.

---

### Post by Impavidus on 2017-05-16
You may get as many different answers as there are users at these fora.

I do a fresh install of the first interim release after an LTS release on a different partition. When it works satisfactory, I move my home partition over, keeping the old LTS release to use in case something is wrong with my primary system. That may not be ideal (data partition instead of home partition may have been slightly better), but it happened for historical reasons. I upgrade the interim release three times to get to the next LTS release, next I install the next interim release over the old LTS release:```
sda1: 12.04> -----> -----> 14.10> 15.04> 15.10> 16.04> -----> -----
sda7: 13.04> 13.10> 14.04> -----> -----> -----> -----> 16.10> 17.04
```I install or upgrade about 2–8 weeks after release.

I found 17.04 to work fine most of the time, although I've been hit twice by a not so nice kernel bug.

There's also an older computer in the house just moving from one LTS to the next, having done so since 6.06, usually upgrading, but last time I made it a fresh install.

---

### Post by &amp;KyT$0P# on 2017-05-16
On bare-metal systems, I always stick to LTS.  And I don't upgrade to the latest LTS right as soon as it comes out.  I wait several months for most of the bigger kinks to get worked out.

When a new LTS version comes out I try it out in a virtual machine right away.  Among other things, this lets me see "ahead of time" some of the issues I'll run into, and figure out how to deal with them.  Makes it far smoother and easier to upgrade the bare-metal systems down the line.

---

### Post by mörgæs on 2017-05-16
> **Impavidus said:**
> You may get as many different answers as there are users at these fora.

Yes :-)

For new hardware I always use newest software. 

For old hardware running the latest L/Xubuntu LTS will normally do. I don't have a recommended time for switching but as the LTS's overlap with a year there is plenty of freedom. The only exception to the rule is that if I need to install something when 17.10 is out (say some old hardware is given to me) then I pick this one and not 16.04. The reason is that if I eventually want a fresh install of 18.04 LTS (which I do) then there is no benefit from installing 16.04 LTS. The operative system will only live for a few months anyway until 18.04 takes over.

---

### Post by RobGoss on 2017-05-16
This depends on the user  for my self I will stick with what works. I'm currently running 16.04.2 and have no plans on upgrading. I would wait some time before I upgrade and when I do it's always a clean installation never a upgrade. I only run LTS release's this way I don't have to upgrade every 9-months

Jumping on a new distribution as soon as-it's released will almost always be problematic and that's normal

---

### Post by gordintoronto on 2017-05-17
I suggest you should stick with the LTS, as long as your computer was released before it was! New hardware, old software, guaranteed  problems.

My personal approach is different. I like to see what's new. I installed Xubuntu 17.04 when it was at beta 2, and have seen zero problems. It has been my "daily driver" ever since.

I built my computer seven years ago, using "one step back from the bleeding edge" components. I paid a lot of attention to the reviews on Newegg, and the result has been wonderful. My upgrades include more memory (to get familiar with Windows Server, for work) a free blu-ray drive and an SSD, keeping the (640 GB) rotating disk.

I have difficulty understanding how your experience with 17.04 is unacceptable, and mine has been wonderful. I have various versions installed on a couple of Thinkpads, and they are similarly trouble-free, although the 10-year-old one is dreadfully slow.

---

### Post by Keith_Helms on 2017-05-18
Unless I have some problem with hardware being supported and I KNEW a non-LTS version fixed that problem, I just stick to the LTS versions and give them a few months to shake out the bugs when a new LTS comes out.  That being said, I have installed the hwe packages on my Xubuntu 16.04 system, which gets me to the later kernel versions that come with 16.04.2 and future 16.04.n refreshes.

Of course, this is my bread and butter system that I use for personal finance, multimedia, web browsing and so forth.  I prefer that it be in a working state all the time and am not using it to experiment with new features or software.

---

### Post by Tadaen_Sylvermane on 2017-05-18
Awhile back I had upgraded perfectly fine containers and server to 17.04. Had some difficulties but was mostly ok. My goal has changed however and my server at home has become somewhat critical to the function of my lan now, a few families living on the property here rely on it to work all the time perfectly. I needed to redo a few partitions anyway so I reinstalled with 16.04 to make it easy on myself instead of risking resizing and moving partitions. Now I update every 2 weeks or so, and I don't plan on upgrading to the next lts (18.04) until it has been out for at least 6 months to a year. I'm aiming for max stability. No need for the absolute latest packages for my purposes. 

I will stick with LTS for the foreseeable future. No reason to go off that track. I have learned to look at ubuntu the same way I look at debian. There is only one debian, stable. Testing & unstable are just that, but they are not the official releases. Likewise LTS imo is the official release of ubuntu. The rest are testing grounds.

---

### Post by sp40140 on 2017-05-18
This thread might help...

[https://ubuntuforums.org/showthread.php?t=2358431](https://ubuntuforums.org/showthread.php?t=2358431)

---

### Post by Kris_M on 2017-05-18
14.? --> 16.04.1 --> 16.04.2 --> 16.04.x -->   18.04.1 in a different partition

---

### Post by missmoondog on 2017-05-18
i only use lubuntu LTS 32bit and 64bit and so far i have just let the last two updates fly as soon as my machines picked them up. didn't have any issues with those 2 upgrades. :)

plan on doing exactly the same thing with next upgrade.

---

