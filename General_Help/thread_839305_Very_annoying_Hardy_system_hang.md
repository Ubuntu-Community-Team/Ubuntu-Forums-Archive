---
title: "Very annoying Hardy system hang"
date: 2008-06-24
forum: General Help
---

### Post by joum on 2008-06-24
Hi everyone!

I'm a new user to Linux, and I have recently installed the Hardy Heron AMD64 version on my laptop.

I'm actually loving this new release! Gutsy Gibbon used to be a real pain to configure in my machine, because it has a lot of shortly supported hardware in Linux, and that doesn't happen so much now.

I've been having a lot of system hangs and/or crashes though (not sure what to call it), that randomly occur while I'm working. I think they occur more often when I have some RAM chugger apps running, such as Firefox 3, aMSN and Transmission working at the same time (I only have 1gb RAM).

Picture this: the screen freezes, there is no mouse, keyboard or HDD reaction, Ctrl+Alt+Bksp or Ctrl+Alt+Del don't work...

I'm really concerned about this, as it always forces me to hard-boot my machine, which is kinda bad, as it may damage my HDD.

Anyway, I'd like to post the system logs and specs so as to shed some light about this problem to the forum users and/or dev team at Canonical, but I'm not sure where to find them and where/how to post them.

Thanks in advance for any type of help!

---

### Post by squashpup on 2008-06-24
I've installed Xubuntu Hardy on a very low resource machine (433mhz, 196 MB ram).

I've had no trouble, even when bogging down the system by running multiple apps.  My system has been up for over 24 hours straight.  

I'm beginning to wonder if the problem is related to Gnome or something.  I have only Xfce and LXDE installed, and have had no problems.  

Keep an eye on these forums and see whether its Ubuntu or Kubuntu or Xubuntu having the problems.  I'm inclined to think it's not related to Hardy itself.

---

### Post by bshosey on 2008-06-24
I get lockups every once in a while. But only when I use my Pantech PX-500 Sprint PCS EVDO Internet card.

---

### Post by VMC on 2008-06-24
Do you know the size of your Swap partition?

From a Terminal type this:

```
free
```
That will show you how much memory Swap is using.
Do that when you have enough apps open, but not enough to freeze the system

Also output this command from Terminal:

```
sudo fdisk -l 
```

---

### Post by danwood76 on 2008-06-24
What is the full spec of your system?

It could be a piece of hardware is causing this issue like a graphics card, on laptops they generally share RAM with the main system so it may be a graphics RAM leak or something caused by buggy drivers.

---

### Post by joum on 2008-06-24
My system specs can be found here: [link]("http://www.targa.co.uk/index.jsp?SID=0&NAV=236&DOC=&PAGE=1367&PCAT=2&PROD=248&PTUBE=12&PARAMS=undefined&PARAMS2=undefined&SPCAREA=undefined")

The output of "free" command is as follows (only using Firefox 3 and Transmission):


```
 total       used       free     shared    buffers     cached
Mem:       1028424    1019212       9212          0       7516     547880
-/+ buffers/cache:     463816     564608
Swap:      3012148        252    3011896
```

The output of "sudo fdisk -l" is:

```
Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x71231cda

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9358    75168103+  83  Linux
/dev/sda2            9359        9733     3012187+   5  Extended
/dev/sda5            9359        9733     3012156   82  Linux swap / Solaris
```

Not sure if this helps, but if anyone wants to see any other log, please let me know!

Thanks again!

---

### Post by danwood76 on 2008-06-24
Well you have very high RAM usage, which might be the reason if your system seems slightly sluggish as it will be swapping the RAM to the hard disk.

---

### Post by joum on 2008-06-24
> **danwood76 said:**
> Well you have very high RAM usage, which might be the reason if your system seems slightly sluggish as it will be swapping the RAM to the hard disk.

Any ideas on how I can fix this?

It isn't really all that sluggish... It performs rather fast really, when compared to the i386 version of Gutsy I had a while ago).
Since I started this thread it hasn't crashed again, but I haven't been pushing my machine a lot, I'm basically waiting and searching for a solution to this, as the hangs very annoying and unexpected. :(

Add:

Although in the command line, i get the information that almost 100% of the RAM is being used, the system monitor application tells me that the memory is in 42% usage. Is this supposed to happen? Is it normal?

---

### Post by Mincher on 2008-06-25
Oddly, I get the exact same issue. It seems to occur whilst running Firefox 3.0 or (horribly) whilst running synaptic/update manager.

Sys Spec:
Motherboard: Asrock 939Dual-Vsta
Processer: Athlon 64 4000+
Memory: 1.5Gb
HDD: 1x 250gb IDE drive (4.31Gb set for swap).
Graphics: XFX Geforce 8600GTS
Internet: Cisco Aironet Wireless Network Adapter

Any ideas would be much appreciated as crashes during synaptic use has the potential to rape my PC, resulting in me havnig to recover Ubuntu. :|

---

### Post by joum on 2008-06-25
Well guys, I'm sorry to let you all know that I've found the source of this problem, but I'm afraid I have some bad news (at least for me).

After trying to reason with Hardy, I gave up and tried Gutsy. For my surprise, the _**PROBLEM WAS STILL THERE!**_.

The way I see it, the probable cause to this has nothing to do with Hardy. Therefore, I did the memtest86 tests with my install disk, and BANG! I have a damaged RAM in my system! At the beginning of this thread I thought I had 1Gb, but actually, one of the RAMs was damaged, and that explains why I only got crashes and/or hangs when the system demanded 700Mb+.

The weird thing is that before I installed Hardy, I was using Gutsy in full potential, as I was making good use of the 1Gb I had at the time.

Anyway, until I have money for a new laptop, I'll be using Xubuntu Hardy on this one, making full use of my *new* 512Mb RAM.:(

**_NOTE 1:_**
I'm not actually sure about all this, but my suggestion to those that think they have the same symptoms is: to the memtest86 tests and take your own conclusions. Maybe you don't have the same problem that I have, and someone might be trying to find out what it may be.

**_NOTE 2:_**
If anyone thinks that my problem might have another origin, or has a different opinion related to the conclusions I made after the memtest, please let me know, after all, I'm still very new to this.

Well, thats all for now! Sad day for me, indeed!

---

### Post by danwood76 on 2008-06-26
> **joum said:**
> 
Anyway, until I have money for a new laptop, I'll be using Xubuntu Hardy on this one, making full use of my *new* 512Mb RAM.:(


Why not just buy another 512MB stick of RAM?
RAM is quite cheap these days and laptop RAM can be picked up very cheap on sites like ebay.

---

### Post by Mincher on 2008-06-26
Well, it seems like it is a memory problem. Although like joum, I had Gutsy & Vista running on this machine without this problem (Vista had other issues of course ¬_¬).

Running Memtest86 actually brought a tear to my eye. I'm surprised these memory sticks held out as long as they did.

---

### Post by joum on 2008-06-26
> **danwood76 said:**
> Why not just buy another 512MB stick of RAM?
RAM is quite cheap these days and laptop RAM can be picked up very cheap on sites like ebay.

I guess that's true. The problem is that this laptop is about to become 3 or 4 years old, not sure. The memory I have to use is about 40€ a piece (around 50$USD i guess). It's and early version of DDRs. Not even sure aboute the their speed.

I'm not going to invest on this machine any further beacuse it has other problems and limitations related to battery life and AC adapter connection.

For now, Xubuntu is doing the trick, although I miss some of the Ubuntu features. Is pretty much the same thing, except for some stuff being placed somewhere else, etc...

---

### Post by joum on 2008-06-26
> **Mincher said:**
> Well, it seems like it is a memory problem. Although like joum, I had Gutsy & Vista running on this machine without this problem (Vista had other issues of course ¬_¬).

Running Memtest86 actually brought a tear to my eye. I'm surprised these memory sticks held out as long as they did.


What surprises me the most is that just like you, Gutsy and Windows XP both ran perfectly before I tried to use Hardy. And after I intalled Hardy, all of the sudden, a RAM stick blows up! This sucks! I'm starting to wonder if Hardy might have been responsible for this.

I'm absolutely newb when this kind of talk comes along, and I might be saying something really stupid, but it sure feels like Hardy had something to do with this.

My next move is juridic action against Canonical! :lolflag:

Just kiding... Anyway, I kept my "bad" memory stick, and I'll try to memtest it somewhere else, just to check if it really was the stick that went bad, or if I might have a problem in the RAM slot (which could be far worse). If anything, I'd recommend you would do the same, Mincher.

Bye

---

### Post by danwood76 on 2008-06-26
FOr me a 512MV stick of DDR costs around £10 with postage (thats ebay)

I think the reason hardy has showed you the problems with your RAM is probably because it has a larger memory foorprint than XP or Gutsy so it uses the higher regions of the memory more.

It might be worth hoovering and blowing the RAM slots with compressed air, if theres dust on the data lines it may cause errors.
Its always worth a shot, I know it fixed many issues with my old home PC that had a supposed graphics and RAM failure but just turned out to be dust :)

---

### Post by joum on 2008-06-26
> **danwood76 said:**
> 
It might be worth hoovering and blowing the RAM slots with compressed air, if theres dust on the data lines it may cause errors.
Its always worth a shot, I know it fixed many issues with my old home PC that had a supposed graphics and RAM failure but just turned out to be dust :)

Hadn't thought of that yet... Might as well give it a try! :)

As to RAM prices, I live in Portugal, and I've checked out the main retailers here and the type of memory the laptop handles, I mean "old-school" DDRs at 266Mhz or so (not sure), aren't neither easy to come by or cheap. 1Gb costs 68,90€. That's 108$USD or 54,5£BP.

I'm not really interested in buying RAM sticks for now. It's a question of a couple of weeks or maybe a month or so for me to buy a new machine.

But, as obvious, I´d like to maintain this machine working as best as I can, so, if anyone has other suggestions, please goa ahead and share them here.

Bye!

---

### Post by danwood76 on 2008-06-26
Yeah but DDR400 will work in your system, DDR266 is the slowest I think so any DDR memory (Not DDR2 or DDR3 obviously) will workj in your machine.
You can run higher frequency ram at lower frequencies but not the other way round.

---

