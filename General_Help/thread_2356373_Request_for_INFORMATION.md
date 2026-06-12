---
title: "Request for INFORMATION"
date: 2017-03-22
forum: General Help
---

### Post by bobr199 on 2017-03-22
Hi
     Silly me.... I thought this would be simply a matter of downloading the software to a CD and then using it as the boot disk for another machine....
BUT NOOOOO .... I'm working with a Compaq SR1910NX that has 2gb of ram, ( so far, I may upgrade that ) however is this machine too much of a dinosaur to use with any version of Linux?  Also I'm told that current state of the art software has grown bigger than will fit on a CD, so I'll have to use a thumb-drive. OK, pointer to specific info as to how to make that work?  or should it be considered that I'm too computer lame to get this so just give up? or ?  I'd really like to experiment with an alternative to Microslot stuff, anybody have any info, any help at all?
& Thanks much all .... 

Bob
.

---

### Post by QIII on 2017-03-22
Moved to General Help.

Forum Feedback & Help is for help with the forum software.

---

### Post by Autodave on 2017-03-22
First off, I would not try Ubuntu on that machine: go down to Xubuntu or even Lubuntu. You can still install all the same programs, but Ubuntu comes with a lot of "overhead" and will make that machine crawl. As far as the 2 gig RAM, you will be fine with one of the lighter versions. I use Xubuntu and a one gig RAN, 800 mhz machine and it is fine.

As for the bootable USB stick, someone else will remember the program needed.....my memory isn't so good at the moment. :-(

---

### Post by bobr199 on 2017-03-22
Thank you! & I'm looking to run something like GIMP on this experimental compute and fiddle around with graphics.  this is all on the toy computing end of things.
should it get more serious, I'm probably going to have to score one of the 64 bit computers to do real work on.
anyhow Thanks again .....

---

### Post by TheFu on 2017-03-22
**Yumi** is a program to make a multi-boot flash drive from Windows. There are 5 other options, but Yumi has worked best for me. Google will find it on the same website as unetbootin.

You can use **dd** or any similar program to make a single-boot flash drive from Unix.  There's also **mkusb**, which does some checking, but it is effectively dd.

I didn't look up that computer, but if it is pre-i686, then you're sorta stuck.  Few distros support that.  If post-i686, then any of the lighter distros - xubuntu, lubuntu, ubuntu-mate can easily be used. Get the LTS version (16.04) and let yumi do the work for you.

2G of RAM is overkill for most Linux distros that are lite.  512 is a little tight and 1G is fine, provided you don't run huge, RAM-sucking, browsers like Chrome, Chromium, or Firefox.  For a play machine, this shouldn't matter.

The GIMP does like RAM, so that will become an issue if you use too many layers.  A graphics workstation really needs 8G of RAM and a modern CPU.  There is good news - a used machine with a CPU 2 yrs old can be had for less than $200, just shop around a little.  I built a fair system about 3 yrs ago for $120-ish that can easily handle this stuff, but I used lots of old parts.  Only "new" stuff was the CPU+motherboard+8G RAM.  I learned long ago to buy standard stuff so it could be reused.  For example, I don't have any DDR4 systems here, still using DDR2 and DDR3. Plan to skip until we are forced to use DDR5.  This way I get to re-re-re-use cheap DDR3 RAM - and it is cheap.  Just 1 more $0 expense for my future upgrades.  Same for HDDs, PSUs, and I stopped buying GPUs in 2010 - when intel started including them in desktop CPUs. 1 less expense. Add those up and upgrades for $120 can make a system 3-5x faster cheaply - provided you use standard parts for a few years in advance.

---

### Post by SeijiSensei on 2017-03-22
If you deal with reasonably large graphics, GIMP will run pretty slowly on a machine with only 2 GB of memory and a Sempron processor.  If you want to give it a try, here's the guide to installing from a USB device: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

If you keep an eye on the Daily Deals at NewEgg you can pick up some pretty good buys like this one today: [https://www.newegg.com/Product/Product.aspx?Item=N82E16883282495](https://www.newegg.com/Product/Product.aspx?Item=N82E16883282495).  It has an i5, a 1 TB drive, 8 GB of RAM and Win7 Professional for $260.

---

### Post by mörgæs on 2017-03-23
> **bobr199 said:**
> ...going to have to score one of the 64 bit computers to do real work on.


You already have a 64 bit computer. 

It probably (but not certainly) has an Nvidia 6150 graphics processor. If this is the case then the install might be a little different from the norm. Please confirm if you have.

By the way, a title like *Request for INFORMATION* contains no information in itself. All posts in a forum are about requesting information. Better to change the title to *Compaq SR1910NX* or similar.

As for the advice regarding buying new stuff: I think you should forget about this until you have hands-on experience with the speed of your present gear.

---

