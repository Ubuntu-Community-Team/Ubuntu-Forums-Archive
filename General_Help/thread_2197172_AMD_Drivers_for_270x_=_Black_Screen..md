---
title: "AMD Drivers for 270x = Black Screen."
date: 2014-01-02
forum: General Help
---

### Post by gagnon-k59 on 2014-01-02
Hello everyone, I really want to work on Linux. Also, I'd like to play my games on Linux to finally get rid of the infamous MS Windows.

But I'm affraid i'm having a very bad start.

I installed Ubuntu 13.10 and then proceed to install the lastest AMD Beta drivers wich are supposed to support my 270x but after reboot I get a black screen. I have no problems when I use the open-source drivers but I need the AMD drivers to get optimal gaming power.

I tried the FanClub AMD drivers instalation tool to help me along the way after my first attemp and it turned out to be a failure too.

The only solution I have so far is to purge fglrx but then again, it's not the solution I'm looking for.

My Screen resolution is 1680x1050.

After reading on the subject, alot of people been able to install the AMD drivers with their 270x without problems. (except for one HDMI audio problem)

I'm currently running a clean 13.04 Install.

What should I look for / try next ?

---

### Post by Kirk Schnable on 2014-01-02
Let's get some basic troubleshooting information on this thread so we can assist you further.  Can you please paste us the output of these commands:

```
lspci
```

```
uname -r
```

---

### Post by gagnon-k59 on 2014-01-02
After spending all day reading / searching and trying stuff (at least I learned alot), I got a little frustrated and I just installed Elementary OS Luna. I just finished the installation so it is completly fresh. This time around, I'm going to read alot before the Catalyst install instead of reading alot AFTER the install. :)

Thanks for your time Kirk, also next time I'll post something I'll give the basics info.

I'm going to mark the thread as closed.

EDIT : Can't close it without changing it to Solve so I'm going to leave it like this.

---

### Post by JDorfler on 2014-01-03
> **gagnon-k59 said:**
> After spending all day reading / searching and trying stuff (at least I learned alot), I got a little frustrated and I just installed Elementary OS Luna. I just finished the installation so it is completly fresh. This time around, I'm going to read alot before the Catalyst install instead of reading alot AFTER the install. :)

Thanks for your time Kirk, also next time I'll post something I'll give the basics info.

I'm going to mark the thread as closed.

EDIT : Can't close it without changing it to Solve so I'm going to leave it like this.

What version of Catalyst are you trying to install and what version of Ubuntu were you trying to install it to?  The latest drivers for AMD/ATi and Ubuntu 13.10 need a bit of a hack to work.

---

