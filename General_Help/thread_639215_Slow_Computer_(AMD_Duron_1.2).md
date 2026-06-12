---
title: "Slow Computer (AMD Duron 1.2)"
date: 2007-12-12
forum: General Help
---

### Post by notiones on 2007-12-12
I have an AMD Duron 1200 with 512MB RAM running Gutsy. It is really slow. I have tried several other distros and they too run slow. When I say slow, I mean about the same as my PIII 450 512MB RAM with RHEL 4 running sendmail, apache, named, and just about everything but the kitchen sink. You get the picture. 

Logs don't indicate anything in particular. I have disabled many services without making much of an impact. I even tried a diff graphics card, hard drives, bios settings, you name it. This has been going on for a couple of years now and is on a box typically used for testing, which means it has had everything changed at one time or another except the processor and main board. Could it just be a bad cpu? I can open just about any window and it will load up the cpu.

In short, where do I start digging into this? Are there any good references online?

---

### Post by Lostincyberspace on 2007-12-13
Try Xubuntu if you can it use less resources than Ubuntu. Also go into system monitor and try turning things off one at a time and seeing if it is helping.

---

### Post by Warren Watts on 2007-12-13
I have had similar experinces with a 1.0GHz Duron.  My 450 MHz PIII ran circles around it.  Oddly enough, I have a 700MHz Duron system with only 256MB, and it doesn't seem to suffer from the same speed related issues.

Maybe it's the motherboard, I don't know.

---

### Post by linuxlizard on 2007-12-13
I  have a laptop that's a 700 mhz pentium 3 with 192mb ram and a crappy old 4mb video card. Any variant of ubuntu runs painfully slow on this machine. I highly recommend pcfluxboxos. It's fast, has a package selection comparable, though not quite as extensive as ubuntu, but you will still have hundreds of apps available with a couple of clicks, and it's just a really nice little distro. It's got a great control center, and installing things is really easy. The only downside to it is you have to edit your menu by hand when you install new apps. It's not very difficult and a quick look at the default menu file will tell you all you need to know to add new items in a few seconds.

Other than that- it's great- it feels faster on that little old laptop than ubuntu gutsy on my athlon 2800+ with 756mb ram and 256mb video card. In fact- it boots up in less than 30 secs and stuff pops open almost instantly.

---

### Post by notiones on 2007-12-13
I have turned most services off already and have tried all kinds of distros. Remember, this is/was a test machine and I used it to install/test everything from Gentoo to Centos. And everything in between. Nothing seems to help. I would very much like to keep Gutsy as that it what I use on on the rest of my computers. It makes moving work between systems painless. Anyone in a mixed environment knows what I am talking about. 

The one thing I haven't tried in a year or two is a custom rolled kernel. Does anyone think that would help?

---

### Post by notiones on 2007-12-26
I have been running PCI video adapters because the built in doesn't support my preferred resolution. (There isn't an AGP expansion slot). Sure enough I went back to the built in  graphics adapter and it is running great. The motherboard is a Gigabyte GA-7VKMLS rev 4.0. Sorry, I didn't get the BIOS rev number.

---

