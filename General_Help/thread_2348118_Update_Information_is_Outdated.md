---
title: "Update Information is Outdated"
date: 2016-12-31
forum: General Help
---

### Post by daniell59 on 2016-12-31
I do not understand why I am getting the following notification.

The Update Information is outdated. This may be caused by network
problems or by a repository that is no longer available. Please update manually by
selecting show updates from the indicator menu, and watching for any failing repositories.

Show Updates

Show Notifications

Preferences

Ubuntu 14.04 32

Any assistance will be appreciated

---

### Post by TheFu on 2016-12-31
Run **sudo apt update**. If there are any issues, post the command and any relevant issues. We don't need to see 500 lines of the same problem.
Also, use "code tag" so it is readable. Unreadable posts don't get much help.

---

### Post by daniell59 on 2017-01-01
I hope that this is relevant to my problem.

W: There is no public key available for the following key IDs:
1397BC53640DB551
W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release)  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

---

### Post by ajgreeny on 2017-01-01
Google-chrome is no longer available for 32 bit systems, hence your error message.

Disable the repository for google-chrome in your software sources and the error will go away.
I suggest you use chromium instead which will remain available for 32 bit systems and is the open source browser on which chrome is based.

---

### Post by mörgæs on 2017-01-01
In addition to the advice above:
If your hardware is 64 bit you could also do a fresh install of a 64 bit 16.04.1 in which Chrome is available.

---

### Post by daniell59 on 2017-01-01
> **ajgreeny said:**
> Google-chrome is no longer available for 32 bit systems, hence your error message.

Disable the repository for google-chrome in your software sources and the error will go away.
I suggest you use chromium instead which will remain available for 32 bit systems and is the open source browser on which chrome is based.

It makes perfect sense what you have said. I am at Software and Updates but do not know how to locate the Google-Chrome repository. Thank you for your assistance. This is a great learning opportunity for me.

---

### Post by howefield on 2017-01-01
> **daniell59 said:**
> I am at Software and Updates but do not know how to locate the Google-Chrome repository.

Try the *"Other Software tab"* in the Software & Updates application.

---

### Post by daniell59 on 2017-01-01
> **howefield said:**
> Try the *"Other Software tab"* in the Software & Updates application.

I did hit the other software tab but do not know where to go from here.

---

### Post by howefield on 2017-01-01
> **daniell59 said:**
> I did hit the other software tab but do not know where to go from here.

Click on the google line to highlight it and press the remove button.

---

### Post by daniell59 on 2017-01-01
> **howefield said:**
> Click on the google line to highlight it and press the remove button.

Thanks, I removed it.

---

### Post by daniell59 on 2017-01-01
If your hardware is 64 bit you could also do a fresh install of a 64 bit 16.04.1 in which Chrome is available.

This computer is quite old. I only have two Gigs of RAM. It has a 64 bit processor however. I think that it would be better for me to build a new computer at some point.

---

### Post by TheFu on 2017-01-01
So this issue is solved?
If so, please mark the thread as SOLVED in the thread tools. This helps everyone here. Those wanting to help and those looking for answers.

---

### Post by mörgæs on 2017-01-01
> **daniell59 said:**
> I think that it would be better for me to build a new computer at some point.

I don't. What needs to be changed is software, not hardware. Try a fresh install of a 64 bit Lubuntu 16.04.1.

---

### Post by daniell59 on 2017-01-02
> **mörgæs said:**
> I don't. What needs to be changed is software, not hardware. Try a fresh install of a 64 bit Lubuntu 16.04.1.
 
I guess I am looking for an excuse to build a new computer.

---

### Post by TheFu on 2017-01-02
> **daniell59 said:**
> I guess I am looking for an excuse to build a new computer.

I've gotten that bug too.  For about $500, it is amazing what can be built with dual Xeons today. Faster than a $1800 Core i7.
[http://www.techspot.com/review/1155-affordable-dual-xeon-pc/](http://www.techspot.com/review/1155-affordable-dual-xeon-pc/)
I found the CPU they were using to be more power hungry than I wanted, but a slightly slower version drops to 95W/CPU.
A used Intel Xeon E5-2660 CPU is $85/ea.

Since DDR3 RAM is used, cheaper RAM is available. Might be able to reuse some. The same for a case, PSU, old GPU, storage, etc.  I only needed to buy:
* 2x CPUs (it is a SERVER)
* 2x CPU fans
* Motherboard (leaning towards a supermicro)

The resulting system should be in the 22K passmark range.   My current Core i7 is about 5.6K passmark, so a nice jump in performance and definitely ready for running lots of virtual machines or other heavy workloads.  I wouldn't want to be in the same room with it - too noisy - but put it in the basement on the end of a GigE or dual GigE connections and WOW!  Not bad for $500-ish.  The Xeons can be amazing, but some of that CPU line are slow, power sucking, and generate lots of heat, so be careful which CPU is selected.

Or for half that budget, a respectable Core i5 can be built. I've been spending about $200 on the CPU and $100 on MB for my upgrades for about a decade about every 5-7 yrs. 

BTW, for a happy end-user, only about 1500 Passmark is needed on a low-end desktop (netbook/chromebook).  It won't break any speed records for transcoding video, but Grandma will be happy surfing and emailing.  I haven't looked in about a year, but the G3258 was the best bang-for-the-buck back then. Built one (about $120 total) for my Plex Server, Calibre Server, Storage (NFS) server, and it does a few other things too. Just under 4K passmarks [https://www.cpubenchmark.net/cpu.php?cpu=Intel+Pentium+G3258+%40+3.20GHz](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Pentium+G3258+%40+3.20GHz)

Lots of options.

---

