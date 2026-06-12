---
title: "it's normal that installation is without swap and that os freeze ?"
date: 2020-08-09
forum: General Help
---

### Post by oceanbottle on 2020-08-09
Hi,
I installed lubuntu some weeks ago, but the os freeze usually when I have 12-15 tabs open on firefox. 
I have a quadcore with 4 gb of ram.
Also I discovered that the swap was not been created then in my opinion the freeze depend of lack of ram.
My questions are:

- is that normal that the default install is without swap ?
- is that normal that a simple browser with around 15 tabs open make the os freeze ?

Thank you and please let me know your opinion.
OceanBottle.

---

### Post by ActionParsnip on 2020-08-09
Ubuntu uses a swap file now rather than a swap partition.

---

### Post by oceanbottle on 2020-08-09
How I know if it uses swap file ?
in the processes I don't see anything about swap...

---

### Post by deadflowr on 2020-08-09
> in the processes I don't see anything about swap...
What processes?
Is that a program or something?

---

### Post by HermanAB on 2020-08-09
The utility 'top' shows swap use.

The OS uses swap space for multiple things, including 'suspend'.   Browsers easily get into a situation where some swap space is needed and if your machine doesn't have any, then it will grind to a halt.

---

### Post by guiverc on 2020-08-10
You haven't said which release of Lubuntu you installed and are using.

Lubuntu 20.04 LTS does not have *swap* enabled by default, many users (particularly those using SSD) don't want it.

I'll refer you to [https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-20-04) as the Lubuntu manual doesn't have a *swap* partition page (yet; it's in the *to do* list). 

Lubuntu 18.04 LTS by default uses a /swapfile which I'd likely increase the size of for my boxes (esp. if using 4GB of ram or less); though most of my boxes have a swap partition.

---

### Post by Impavidus on 2020-08-10
A web browser with 15 tabs can easily use all your 4GB RAM. All those needless ads and spyware scripts take a lot of memory. Some websites are better, some are worse.

**top** and **free** can tell you about memory and swap usage. Note that a web browser may run multiple processes, one for each tab, and that memory usage per process isn't straightforward to analyse, as memory may be shared by multiple processes and other details.

---

### Post by poorguy on 2020-08-10
Go to the section about **Swappiness **and have a read and I suggest doing that tweak as it may offer a minor performance increase based on my experience.

[https://ubuntuforums.org/showthread.php?t=2130640](https://ubuntuforums.org/showthread.php?t=2130640)

No guarantee it will solve your problem as mentioned above 12 to 15 tabs opened will use a lot of memory.

---

### Post by oceanbottle on 2020-08-10
I solved the problem, but my question concern if it's normal that lubuntu (which is a distro for old pc) doesn't have a swap partition or file in fresh install especially if the os crash just opening the browser with 15 tabs. It's absurd!
So please read again my first post, because my question is NOT how to solve problem, but if it's normal that a fresh install of lubuntu come out without swap partition or file especially if just firefox can freeze the os.

---

### Post by kurt18947 on 2020-08-10
> **oceanbottle said:**
> I solved the problem, but my question concern if it's normal that lubuntu (which is a distro for old pc) doesn't have a swap partition or file in fresh install especially if the os crash just opening the browser with 15 tabs. It's absurd!
So please read again my first post, because my question is NOT how to solve problem,** but if it's normal that a fresh install of lubuntu come out without swap partition or file especially if just firefox can freeze the os.**

#6 above answers your question. It is normal for Lubuntu to not have swap enabled by default. People with SSDs but quite a bit of RAM (8 GB+) don't want swap enabled by default, swap creates unnecessary writes/wear on SSDs. It's not difficult to create a swap file. Here is a pretty straight forward set of instructions, it doesn't look like the 'flavor' matters.

[https://www.fosslinux.com/1064/how-to-create-or-add-a-swap-partition-in-ubuntu-and-linux-mint.htm](https://www.fosslinux.com/1064/how-to-create-or-add-a-swap-partition-in-ubuntu-and-linux-mint.htm)

---

### Post by guiverc on 2020-08-10
> **oceanbottle said:**
> I solved the problem, but my question  concern if it's normal that lubuntu (which is a distro for old pc)  doesn't have a swap partition or file in fresh install especially if the  os crash just opening the browser with 15 tabs. It's absurd!

Many users (including of Lubuntu) don't want *swap* as default; because it does harm to their SSDs and other reasons.  Myself, a user of older PCs it's of benefit, but I'm alas not in the majority of Lubuntu users.  Most users use Lubuntu because it's light & *flies* on modern hardware.

Lubuntu doesn't gear itself for *old* computers... that ceased after the Lubuntu 18.04 LTS release as it's direct aim, ie. refer to [https://lubuntu.me/taking-a-new-direction/](https://lubuntu.me/taking-a-new-direction/)

Myself, I'm using my Lubuntu *groovy* (will be 20.10) install on my primary PC, which was made by Dell in 2009, and it works perfectly for me.

I tested Lubuntu releases up to 19.04 on machines from as old as 2004 with as little as 1GB of RAM, and really was most impressed.  But the truth is few people use PCs that old, or with that little RAM. Out of the box though, Lubuntu ran better than any other Ubuntu flavor (*rather subjectively on the old pentium M & pentium 4 processors i used to test releases up to 19.04, on more modern c2d & 2gb and better the difference was less obvious*).

Your detail or *assertion* about Lubuntu being aimed at *old pcs* however is *historical*, and ended what is now over two years ago. 

I think it was a mistake that we (Lubuntu) didn't have a page in our manual guiding users to using *swap*, but as soon as it was detected, it was suggested and subsequently approved within *hours*, and is now just waiting for volunteers to write & submit the changes to the manual. As is often the case with open-source or volunteer projects, there are few willing to step up and help, so things take time..


*We (Lubuntu) always need more help! Feel free to [join]("https://lubuntu.me/links/")  our development channel (which is bridged three ways to Matrix,  Telegram, and IRC) and talk to us there. Whether you know another  language, have some spare time to help us [test Lubuntu]("https://phab.lubuntu.me/w/testing/"), are good at writing documentation, or just want to stay &#8220;in the know,&#8221; that is the place to be.*

---

### Post by GhX6GZMB on 2020-08-10
> **oceanbottle said:**
> but if it's normal that a fresh install of lubuntu come out without swap partition or file especially if just firefox can freeze the os.

When installing Lubuntu, it's up to ***you*** to set up your partitions, default is just a / partition. You seem to have missed a step here: the first thing to do ***before*** even installing is to plan your partitions.

Can Firefox freeze your OS? Yes, certainly. Firefox is the most resource-hungry browser around today and has miserable memory management, where you need to restart it every few days because of overflows. A swap partition/file will not solve the problem, just postpone it.

---

