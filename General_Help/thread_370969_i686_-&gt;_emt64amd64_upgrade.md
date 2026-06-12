---
title: "i686 -&gt; emt64/amd64 upgrade?"
date: 2007-02-26
forum: General Help
---

### Post by SarahKH on 2007-02-26
Greetings, 

It dawned on me that I have a core 2 duo machine, which should (I believe) have emt64 capabilities.  I'm currently running I686 SMP/Generic (with i386 kernel+modules floating around for long haul/suspend/hibernate). 

Is it possible to install the AMD64 6.10 on this system and in effect dual boot?  What are the gotcha's for 64bit (i.e. suspend/hibernate won't work, graphics drivers, and so on)?

---

### Post by housam on 2007-02-26
There isn't much software produced for 64bit processors. keep 32bit running.

---

### Post by SarahKH on 2007-02-26
Hmm.  Fair enough; I'm guessing things like ndiswrapper would have a funk as well in a 64bit enviroment?  

Still, I686 (I must get round to suspend2ing the kernel) is giving me a lot of bang for buck as it were :)

---

### Post by William Pickett on 2007-03-11
I currently have the now obsolete amd64 K8 version, which I didnt know was, I may look for newer linux kernals to upgrade to- be careful on AMD 64 though because I have been looking and what I see says keep 6.06 until they actually come up with an upgrade of everything. Just one view based on posts I have seen- Ubuntu and other forums. William:)

---

### Post by russell.h on 2007-03-11
> **housam said:**
> There isn't much software produced for 64bit processors.

Thats pretty much just wrong (no offense intended). I'm running 64 bit Feisty right now, and have 21,000+ packages listed in the (official) repos I have enabled.

Pretty much anything that is open source is available for both 32 and 64 bit.

Things that are problematic are:

1. Flash Player - Since flash player isn't open source you have to install 32 bit firefox to use it. Kilz has a great tutorial/script on that which I used, totally painless, took only a few minutes, and firefox now does everything that it ever did in 32 bit, with the exception of printing straight from firefox.

2. Drivers - closed source drivers may be a problem depending on what you need. I haven't used ndiswrapper myself, but I think there is a way to do it.

3. Wine - I haven't used it in 64 bit, but apparently you have to do something to make it work?

4. Certain media codecs - specifically I still can't play WMV 10 files, although I have yet to encounter one that I want to play other than the one on the site I used test the mplayer plugin. There is some sort of workaround for this too.


Other than that.... some packages aren't compiled for 64 bit so you have to do it yourself. As far as I know most everything in the official repos is avaiable for 64 bit, but things you find off on random 3rd party pages might not be.

I've been running 64bit for.... 3 weeks now I think, and I have no plans to go back. Certain things are significantly faster (encoding audio and video for example), and in general everything just feels a bit "snappier" (although that might be the Edgy -> Feisty effect).

---

