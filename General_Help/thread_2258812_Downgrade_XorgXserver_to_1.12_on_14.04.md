---
title: "Downgrade Xorg/Xserver to 1.12 on 14.04"
date: 2014-12-30
forum: General Help
---

### Post by Totolanio on 2014-12-30
Hello,

Is it possible to downgrade Xorg/Xserver to 1.12 from the actual version (don't know if it's 1.13 or 1.14) on Lubuntu 14.04 (don't know if it's 14.04.1 neither) ??


I saw this thread [http://ubuntuforums.org/archive/index.php/t-2123983.html](http://ubuntuforums.org/archive/index.php/t-2123983.html)

But I wonder if it's still possible.

---

### Post by monkeybrain20122 on 2014-12-30
Why do you want to do that? I did it once on Ubuntu 10.10 for an old Nvidia card but it may not work now. 

If you explain your problem there may be better ways than to mess with xorg e.g installing xubuntu 12.04 which has old xorg,  is LTS and almost as light as Lubuntu if you have ~ 1G of ram, or get LXLE 12.04 which is basically lubuntu 12.04 but with LTS support from the LXLE team [https://www.osdisc.com/products/lxle?affiliate=lxle](https://www.osdisc.com/products/lxle?affiliate=lxle)

---

### Post by Mark Phelps on 2014-12-30
> But I wonder if it's still possible. 

It's possible -- but it will leave you with a "broken" and unstable system that then can not be updated without serious problems.

If you're doing this to get AMD fglrx drivers to run on Ubuntu 14.x with an AMD 2x/3x/4x-series card, that is a bad idea.

---

### Post by mc4man on 2014-12-30
> **Mark Phelps said:**
> It's possible -- but it will leave you with a "broken" and unstable system that then can not be updated without serious problems.

If you're doing this to get AMD fglrx drivers to run on Ubuntu 14.x with an AMD 2x/3x/4x-series card, that is a bad idea.
Definitely a poor idea though in this case it's likely the Op has a GeForce 4xx (nv17 or so) card which isn't going to work well or at all with 14.04 anything. 
(- even nouveau support could be quite poor for nv17

---

### Post by Totolanio on 2014-12-31
> **Mark Phelps said:**
> It's possible -- but it will leave you with a "broken" and unstable system that then can not be updated without serious problems.

If you're doing this to get AMD fglrx drivers to run on Ubuntu 14.x with an AMD 2x/3x/4x-series card, that is a bad idea.

Geforce 4 Mx 440. Some suggest to do this since last year.
What can be broken and unstable please ?

> **mc4man said:**
> Definitely a poor idea though in this case it's likely the Op has a GeForce 4xx (nv17 or so) card which isn't going to work well or at all with 14.04 anything. 
(- even nouveau support could be quite poor for nv17

Yes, that's the problem. I use "nomodeset" because with the normal mode, there are missing icons everywhere. In normal mode (nouveau driver I guess) I have 1280px width.
In nomodeset, there isn't any bug anymore, BUT the resolution max is 1024px ! It's really giving headaches and sore eyes.

> **monkeybrain20122 said:**
> Why do you want to do that? I did it  once on Ubuntu 10.10 for an old Nvidia card but it may not work now. 

If you explain your problem there may be better ways than to mess with  xorg e.g installing xubuntu 12.04 which has old xorg,  is LTS and almost  as light as Lubuntu if you have ~ 1G of ram, or get LXLE 12.04 which is  basically lubuntu 12.04 but with LTS support from the LXLE team [https://www.osdisc.com/products/lxle?affiliate=lxle](https://www.osdisc.com/products/lxle?affiliate=lxle)

If you did it, which problems did you encounter please ? What can be broken and unstable please ?
There are no perfect solutions to this problem.
Can't  use Xubuntu because my computer has only 750MB of ram (and very slow  CPU). Also using 12.04 means it will be soon unsupported, no?
And  finally, LXLE is over 700MB I guess and so I can't use a DVD on this  computer (at least not DVD RW, didn't try with DVD but it seems like it  wont work) and I think this computer never boots from the USB-key. And  LXLE download = torrent xD


===========

If you know how to increase the resolution to 1280px in nomodeset or which linux distribution is very light AND with Xorg 1.12 or 1.11, please tell me :P
( I know there is puppy linux but it will not fit my mother's needs, since it's not for me, it's too different for her I guess)

---

### Post by monkeybrain20122 on 2014-12-31
Well if you can't make a dvd for lxle and can't boot from usb maybe you can reinstall lubuntu 12.04 and add the lxle ppa [https://launchpad.net/~lxle/+archive/ubuntu/stable](https://launchpad.net/~lxle/+archive/ubuntu/stable)

Since most of lubuntu 12.04's core components and software are the same as ubuntu 12.04's they will be supported for a long time. The ppa probably takes care of some of the lxle stuffs, so while it may not be a full lts, probably 'almost'.

Have you considered upgrading your hardware? You can probably get a much better one on craiglist for < $100. Otherwise you may want to consult  a thread here on using very old hardware just because you can, someone may be able to give you a link.

lubuntu 12.04 download links still work [http://cdimages.ubuntu.com/lubuntu/releases/precise/release/](http://cdimages.ubuntu.com/lubuntu/releases/precise/release/)

---

### Post by Totolanio on 2015-01-01
Using Lubuntu 12.04 with LXLE apps ? It won't be as unstable as downgrading ? And how long till it's unsupported ? 2017 ?

And why some did downgrade successfully ? Why not me ? :'( You said you did it monkeybrain20122 !

Upgrading the hardware is a too lengthy process and I have no time to compare, find which things goes with this old hardware etc (and few money too). Especially if it's only a little problem like this :'(

**Can't I increase the resolution in nomodeset upto 1280 width ??**

Aren't there another distribution with Xorg 1.12 based on ubuntu (and not debian) ?

---

### Post by monkeybrain20122 on 2015-01-02
Lxle 12.04 is basically lubuntu 12.04 + lts so it is stable. Is 2017 not long enough? Are you planning to use that kind of old hardware for another decade? :)

I did downgrade successfully but things have changed quite a bit since Ubuntu 10.10 so the same procedure may not work and it may very well toast your machine. By upgrading hardware I mean buy a new machine, not the parts and you can get a 5-6 year old machine very cheap.

---

### Post by Totolanio on 2015-01-07
> **monkeybrain20122 said:**
> Lxle 12.04 is basically lubuntu 12.04 + lts so it is stable. Is 2017 not long enough? Are you planning to use that kind of old hardware for another decade? :)

I did downgrade successfully but things have changed quite a bit since Ubuntu 10.10 so the same procedure may not work and it may very well toast your machine. By upgrading hardware I mean buy a new machine, not the parts and you can get a 5-6 year old machine very cheap.

Lol, After many researches and installations, I realised the problem came from the monitor.
In fact, you can have better resolution using "nomodeset" if you have a better monitor, it's not really related to the nvidia driver.

Thank you for all the help, it helped me to find the solution in the end.

---

