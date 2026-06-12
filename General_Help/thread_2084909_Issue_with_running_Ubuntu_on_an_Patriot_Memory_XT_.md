---
title: "Issue with running Ubuntu on an Patriot Memory XT Rage and an embedded processor"
date: 2012-11-16
forum: General Help
---

### Post by dsurfer21 on 2012-11-16
Hi,

I am working on an interesting project with an embedded processor and 32GB and 64GB Patriot Memory XT Rage flash drives.
I have installed Ubuntu 12.04 on both of these drives and have tested  them separately.  I bought these because I saw they have fast read and  write speeds.

I have an embedded processor with a duo core I7 configuration running  off battery power.  Ubuntu 12.04 loads up fine and runs fine but every  once in a while I have problems when booting up.  The embedded system  manufacturers logo will freeze after attempting to boot up.  As soon as I  remove the Patriot flash drive it then unfreezes and I can go into BIOS  settings or on to the screen that says "no operating system found".  
If I remove the Patriot flash drive and put it in my netbook running  ubuntu, I can read the contents of the drive and then eject it and the  embedded processor boots it up perfectly.  

I was told by the embedded processor manufacturer that maybe the drive  is doing some weird type of latch operation.  I can seem to unlatch it  with my netbook which is really weird.

I have installed Ubuntu after formatting the drive to ext2 and with no  swap partition enabled.  I did this using an Ubuntu Live CD and with  gparted.
Whenever I am finished running the embedded processor with ubuntu, i use  the shutdown button to power down, or if I am at the terminal, I will  use "sudo shutdown -h now". Is there any obvious reason I may be  observing the above behaviors?  

This happens every few days or so and every single time I have the  freeze issue on boot, I remove the Patriot drive and just read the drive  contents with my netbook to "unlatch" it.  Then when I go to boot the  embedded processor, it works right away.  Unfortunately this is super  annoying because the embedded processor and Patriot drive go inside  sealed enclosures and accessing them takes a while.  I have seen this  issue with both the 32GB and 64GB drives.

Thanks!

---

### Post by gbalstad on 2012-11-18
I am having the same problem with two of my Patriot flash drives with linux ubuntu 12.04.  In addition, my Patriot flash drives won't even boot without any OS on them.  If I have a freshly formatted drive in my system when it boots, it freezes on both my Acer and HP laptops, and using both of my 32GB flash drives, one USB 2.0 the other 3.0.  

Very frustrated...

---

### Post by dsurfer21 on 2012-11-18
Wow at least there is someone else out there with the same problem so we  can try and help each other figure it out.  This is very useful because  I am using an embedded processor that is made by a small company so the  support from them requires a bit of back and forth emails and trial and  error tests.

I had suspected maybe when the battery supply is getting low on my  embedded processor that the Patriot Memory "latches".  Last night I let  the XT Rage 64GB run Ubuntu on the embedded processor until the batter  drained fully.  I spent today letting the battery recharge and the last  couple of hours I've been testing Ubuntu again.  It hasn't given me that  freeze boot up issue.  In my case I seemed to only see if every few  days or so which is weird.  I'm trying to shutdown different ways (cut  power off, use sudo shutdown -h now command and using the GNOME desktop  shutdown button).  So far I can't get the freeze boot up issue to  replicate at will.

I used my netbook to install ubunto onto the 64GB XT Rage.  With a spare  4GB USB drive I made a bootable "Ubuntu LIVE CD" .  I installed Ubuntu  onto the 64GB XT Rage after I created an ext2 partition with gparted.  I  did not add a swap partition.  Then I connected the 64GB XT Rage to my  embedded processor system.

Are you planning to use ext2 for formatting the drive?  I had used that  because it is supposed to extend life of a USB drive when Ubuntu is  installed on it.

Also,

I have tried this with a couple of 32GB XT Rage drives and some 64GB XT  Rage drives.  I did not have the boot freeze issue with any of those  drives after initially installing Ubuntu on them.  I seemed to have that  freeze only after a few days of testing them and it seemed random to  me.  I could always "unlatch" them by plugging them into my netbook  running ubuntu and merely just looking at the drive contents and then  ejecting. Afterwards I could put it in the embedded processor's usb port  and it would boot right up perfectly.

---

