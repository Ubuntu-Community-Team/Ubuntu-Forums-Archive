---
title: "32-bit options for Ubuntu"
date: 2020-09-06
forum: General Help
---

### Post by marklopez9 on 2020-09-06
Hi,

I've been combing through Ubuntu and so far I can see 32-bit is no longer supported. I have a bunch of old but still working computers which I would like to put Ubuntu on so they are usable when I donate them.

Is there a documentation/guide out there which I could follow to compile Ubuntu manually as 32-bit?

---

### Post by HermanAB on 2020-09-06
I would suggest that you install either Slackware or OpenBSD for the best 32 bit support.

The trouble is that if you make a bespoke version of Ubuntu, then you are not really doing the new user a favour, since he won't be able to install any other software.  So a new user would have to reinstall the machine again anyway.

---

### Post by crip720 on 2020-09-06
About the only ubuntu favours still supported for 32bit would 18.04 Lubuntu or similar, but they will be coming out of support next year I think and will be finish also.  Can also try some of the small Linuxs made for old computers.  Ubuntu seems to be dropping all support for 32bit computers, so you will not be able to upgrade from 18.04 anyway when support ends.

---

### Post by ajgreeny on 2020-09-06
Forget any of the Ubuntu family as there are only 7 months of support left for Lubuntu 18.04, the only 32bit system still in support.

In your situation I would move to another distro as mentioned above, but would also add Debian 10 Testing to the suggestions, which I am using on an old Netbook with:-
CPU:       Single core Intel Atom CPU N270 (-HT-) cache: 512 KB flags: (nx pae sse sse2 sse3 ssse3) 
           Clock Speeds: 1: 1600.00 MHz 2: 1067.00 MHz
Graphics:  Card: Intel Mobile 945GSE Express Integrated Graphics Controller 
           X.Org: 1.17.1 drivers: intel (unloaded: fbdev,vesa) Resolution: 1024x600@60.0hz 
           GLX Renderer: Mesa DRI Intel 945GME x86/MMX/SSE2 GLX Version: 1.4 Mesa 10.5.9

It's fairly slow but certainly usable for web-browsing using **epiphany-browser**, email using **geary**, and music using **audacious**. I don't use **libreoffice** on it as it's far too large and slow, so I install **abiword** and **gnumeric** instead.  Low resolution videos play with **VLC** but any HD is pushing the hardware just a bit too much.

---

### Post by mastablasta on 2020-09-07
> **marklopez9 said:**
>  I have a bunch of old but still working computers which I would like to put Ubuntu on so they are usable when I donate them.


how old are these computers? 15+ years old? netbooks with Atoms? old Pentiums? why would you donate these instead of recycle them? they use a lot of energy and really are (usually) in configuration too slow for even modern web browsing. I mean people are donating or selling cheap first gen core i generation which support 64 bit and can be usable at least in some ways.

Since AMD64 one can use 64 bit OS. i use an old single core 16 years old PC. and it is only good (for my every day use) due to configuration i made and upgrade it received. it also has 64bit CPU.

---

### Post by marklopez9 on 2020-09-07
> **HermanAB said:**
> I would suggest that you install either Slackware or OpenBSD for the best 32 bit support.

Thanks. I've heard of OpenBSD but didn't know they still support 32-bit (perhaps because I was focused at Linux options only). I'll check it out to see if it works for my intended purpose.

---

### Post by marklopez9 on 2020-09-07
> **mastablasta said:**
> how old are these computers? 15+ years old? netbooks with Atoms? old Pentiums? why would you donate these instead of recycle them? they use a lot of energy and really are (usually) in configuration too slow for even modern web browsing.

They are netbooks with Atoms. The batteries are dead but the power adapters still work, so they are still fairly usable when plugged in to a power source. Since they are netbooks, they won't be much of a power hog so no pain done on the recipient's end as far as their utility bill is concerned.

I'm planning on donating them both for charitable causes and to promote learning/using Linux here in my country.

---

### Post by guiverc on 2020-09-07
A number of *flavors* supported x86/32-bit for 18.04; however only Xubuntu and Lubuntu continued past then (releasing 18.10, but only *alpha* build of 19.04, which was supported it's fully life with packages should you have installed). Either way, only 18.04 remains supported being an LTS release.

I tested a number of flavors of the recent 18.04.5 ([http://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/](http://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/)) *flavors* on x86 pentium 4 desktops, pentium M laptops (even a celeron desktop) which were all 2003 or newer, and only x86.

They are pretty good, the lightest in my opinion is Lubuntu 18.04 LTS, however as always the apps being used can mean the lightest desktop as installed, does not end up being the lightest/fastest with that application.

I still use x86 (a thinkpad r50p, thinkpad t42p & t43).

18.04 has 5 years of support, however *flavors* only have 3 years, so you'll only get partial support as already stated, after April 2021.

My next choice would be straight Debian, and Debian 10 will also run on all boxes I've used for Ubuntu *flavor* testing (or my own use).

FYI: 

I have 1x atom netbook in my list of 27 test boxes

```
asus eepc 1000HE (intel atom n270, 1gb, intel mobile 945gse integrated), wireless RT2790
```

It ran Lubuntu, Xubuntu, Kubuntu 18.04.5, and of course Debian 10. I mention those *flavors* as that's all I recall testing last month; but I suspect it would have run others had I have tried (*though it's likely underpowered for some and I'd opt for something lighter like what I tested*).

---

### Post by Dennis N on 2020-09-07
Also available: [Ubuntu MATE 18.04.5 32-bit]("http://cdimage.ubuntu.com/ubuntu-mate/releases/18.04.5/release/ubuntu-mate-18.04.5-desktop-i386.iso"). 

I use it on my 32-bit Dell 1505 Laptop.

---

### Post by MoebusNet on 2020-09-07
Debian, from which Ubuntu derives, still supports 32-bit machines, for older hardware that requires it. Setting up the desktop to you liking can be a bit of a chore, but is eminently doable:

[https://www.debian.org/](https://www.debian.org/)

If you want something a bit more user-ready, BunsenLabs, which is basically Debian with some preconfigured software choices for a usable desktop, is a decent choice if your hardware meets the minimum specifications:

[https://www.bunsenlabs.org/](https://www.bunsenlabs.org/)

---

### Post by HermanAB on 2020-09-07
OpenBSD is known to support museum pieces.  I think there is still a version of OpenBSD for Adam's original Abacus used in the garden in Iraq to count Eve's apples.

---

### Post by mastablasta on 2020-09-08
> **marklopez9 said:**
> They are netbooks with Atoms. The batteries are dead but the power adapters still work, so they are still fairly usable when plugged in to a power source. Since they are netbooks, they won't be much of a power hog so no pain done on the recipient's end as far as their utility bill is concerned.

I'm planning on donating them both for charitable causes and to promote learning/using Linux here in my country.

ah i though it must be laptops/netbooks. bare in mind that many Atoms do not have the GPU working well. Debian or Debian based with the desktop of your choice or whatever works best and presents best to new users. still at some point they will stop being supported as well. but they might have a bit more life in them left. in additon the issue are most used apps that take more and more ram. so go with light desktop preferably something that doesn't use GPU acceleration. 

in my opinion - not a very best showcase to *promote *linux. i have old Ahtlon which i think is 32 bit or one of the first 64 bit. It was handed down. still it had only 384 RAM (maxed out), it had 32 MB S3 GPU chip which left 350 MB ram for the OS. windows XP was installed on it. it was sloooooooooow. well slow after SP1. before it was kind of OK. anyway i used Debian (at the time Chrinchbang - now Bunsenlabs). the OS took 110 MB, using stripped down XFCE. so that left about 240 MB ram for apps. it could run firefox with one tab open. i doubt it would still work. maybe... had great keyboard until the kid decided he will pull out the keys. the proud voice in that "look daddy! look what i did!" . 

anyway you CAN bring life to old hardware, but not a good showcase. OS was limited in what it could do and for a while it did it's job as portable computer.

---

### Post by HermanAB on 2020-09-08
OpenBSD on a Netbook:
[https://www.aeronetworks.ca/2017/02/openbsd-on-netbook.html](https://www.aeronetworks.ca/2017/02/openbsd-on-netbook.html)

---

### Post by mastablasta on 2020-09-08
in just 24 easy steps.

though it could be fast, and might work well.

however, it won't promote linux but BSD :) :P

---

### Post by ActionParsnip on 2020-09-08
[http://puppylinux.com/index.html#download](http://puppylinux.com/index.html#download)

Nice light distro here. Works well on low end hardware. Obviously you want the 32bit options. Trusty is 32bit available but is end of life next year

---

