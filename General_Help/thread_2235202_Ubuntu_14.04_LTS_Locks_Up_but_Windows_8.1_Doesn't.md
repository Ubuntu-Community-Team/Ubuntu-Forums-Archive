---
title: "Ubuntu 14.04 LTS Locks Up but Windows 8.1 Doesn't"
date: 2014-07-19
forum: General Help
---

### Post by rmoenck on 2014-07-19
Hello Ubuntu Forums,
My (fairly new) PC randomly locks up when I am running Ubuntu 14.04 LTS.
When I say 'locks up' I mean the screen freezes, there is no response to mouse or keyboard and the only resolution is to power down.
The 'lock up' is random in that it can occur at any time. Sometimes even before the login prompt appears.
Sometimes it can run for an hour before it locks up.
I suspect flakey hardware except that when running under Windows 8.1 (it is a dual boot set up) it doesn't appear to do this.
As a long time Linux User this really frosts my socks because I have to put up with all the 'software deamons' that jump on you when you run windows these days.
The basic hardware configuration is an ASUS M5A99X R2.0 AM3+ with an AMD FX-8350 cpu.
I bought it with the hope it would be a hot-rod but so far it is just a source of frustration.
Since this is a multi-processor situation I wondered if the threading is getting tangled (just a thought).

Any advice you might have would be welcome.
Thanks,
Bob Moenck

---

### Post by Mark Phelps on 2014-07-19
It could also be video drivers.  Please post info on your video chipset.  IF you don't have it, open a terminal in Ubuntu, enter "lspci", look for the line containing "VGA" and post that info back here.

---

### Post by 3rdalbum on 2014-07-19
Another possibility is bad RAM. Windows uses RAM a bit differently to Linux - it reserves up to 2 GB for the operating system and then barely uses any of it - so it's possible that the bad portion of RAM could cause problems in Linux but not in Windows.

Theoretically, it could happen vice-versa too - everything okay in Linux but random crashes in Windows.

I recommend running Memtest86+ for eight hours. If the computer crashes or it displays error messages, then you have bad RAM. Even if everything passes, you might still have bad RAM. I found a good way to immediately identify bad RAM is to try running the memory benchmarks from Phoronix Test Suite, they will crash your computer if you have bad RAM.

Also, if you have multiple sticks of RAM in your computer, try removing one of them and see if that helps. If it doesn't help, then put it back in and remove another one, see if it helps, etc.

---

### Post by at_first_light on 2014-07-20
Nice motherboard dude. Some questions:

- Do you have a swap partition? 
- How big is your swap partition? 
- How much ram do you have? 
- What kind of storage device are you using (eg: Nand-flash solid state drive, 7200rpm hard drive, 5400rpm hard drive)? 
- Are you using any custom swappiness settings?

---

### Post by slooksterpsv on 2014-07-20
I second Mark's theory in Video Drivers, what kind of video card do you have? I've had that exact issue where not having proper video drivers would cause crashes.

---

### Post by rmoenck on 2014-07-21
Thanks for your advice.
This is what I get.
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series]

---

### Post by Mark Phelps on 2014-07-21
> Radeon HD 5000/6000/7350/8350 Serie

Not good ... almost certainly some part of the problem is video drivers. What with all those differnt Radeon versions, it's possible the default Radeon drivers won't work well.

If Additional drivers offers an fglrx driver to you, I would try that.

But, BEFORE I did that, I would use Clonezilla to make an image backup of my Ubuntu install.  Takes only a few minutes to do that, and restoring that working version (in the event of a video driver problem) is a LOT faster than trying to fix the driver problem.

---

### Post by rmoenck on 2014-07-22
Thanks to all for their advice.
I will explore upgrading the video drivers and report the results to this thread.
For those that suggested bad memory,
I ran the grub memory diagnosic for 12 hours (5 passes on the 8 Gb memory) with no errors reported.
There is only one panel of memory so I can't try pulling panels.
Yes, I do have 8 Gb of swap space, but with my current usage only about 2 Gb of the main memory is used 
and so swap is never in play.
I will try the Phoronix Test Suite to see if something is reported.

Thanks again for your advice.

---

### Post by rmoenck on 2014-08-12
[h=2][/h]This is an update on this issue.
 I still don't have any resolution.
 Some of the things I have tried:
 1) I have left the machine running under Win 8.1 for a longer time to see if it would lock up.
     It ran for 4.5 days without issue.  
     Under Ubuntu I rarely get more than a couple of hours and sometimes it halts before a logon prompt.
 2) I have tried Phoronix Test Suite but my take on this is that it more of a bench marking tool,
      a “My machine is faster than your machine” tester.
      I have a problem running some of the Phoronix test suites as the machine locks up before they complete.
 3)  I did convert to the fglrx video driver but still no joy.
      The video card is a Radeon HD 5450 which I take to be a low-mid end video card from a well
       known manufacturer.  Something that I would hope would be well supported by Linux.
 

 I would welcome any suggestions of other things to try.

---

### Post by QIII on 2014-08-12
The HD 5450 is definitely entry-level, but it shouldn't be giving you this much grief.   If you have installed the proprietary video driver and it still fails, let's set that aside as a candidate for the problem for a bit.

Since it is failing before login at times, the driver would not have been in use yet anyway.

Which of the Phoronix tests fail?  Those test are worthwhile as more than benchmarks.  They exercise your machine and can point out problem areas.

Please run memtest as suggested.  Do it over night so it makes several passes.

---

### Post by slooksterpsv on 2014-08-12
Try the amd driver directly from AMD.com you can. fglrx is working on my Radeon HD 8400, but the AMD one works as well (first time that's ever happened lol). But the drivers are a bit different. I'd try a couple of these things below as well:

When grub loads up and asks how you want to load Ubuntu press e, go to where it says quiet splash and add nomodeset
If that doesn't help try:
noapic - Interrupt controller
And finally you can also try:
noacpi - Power

On my older laptop I had to use noacpi, but it was to do with how the power transitioned for the video card. noapic, while it may not be the best, disables certain controls of the advanced programmable interrupt controller. And nomodeset disables setting specific settings for the video card.

---

### Post by QIII on 2014-08-12
Just as a point of clarification:  the fglrx driver in the repo IS the proprietary driver from AMD/ATI current at the release dates of Ubuntu versions.

ATI updates monthly most of the time, so the one from the ATI site may be newer.

---

### Post by slooksterpsv on 2014-08-12
I didn't know that, I thought there were three and they laid out like this:
Open Source generic - other
Open Source AMD - fglrx
Close Source AMD - amd driver

So it's just:
Open Source generic - other
Close Source AMD - fglrx
Newer close source AMD - amd.com driver

---

