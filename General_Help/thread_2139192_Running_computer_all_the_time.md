---
title: "Running computer all the time"
date: 2013-04-26
forum: General Help
---

### Post by jsvidyad on 2013-04-26
Hello,

  Is there any problem if I run my computer for a long time without shutting down? I have been running my computer continuously for the past few months with only occasional reboots when I install a kernel upgrade. I was wondering if this might damage the hard drive in any way. I have got critical files on this computer.
  Can this cause any other problems with my computer?

---

### Post by slickymaster on 2013-04-26
From a software perspective, an operating system and the programs you run on it tend to accumulate all sorts of cruft over extended periods of use - temporary files, disk caches, page files, open file descriptors, pipes, sockets, zombie processes, memory leaks, etc. etc. etc.
However, different computers and OS's are not all equally affected by this phenomenon. Generally, a computer with a lot of RAM can go for much longer than a computer with only a little RAM. A server, on which you just start up a few programs and then let them work, will be fine for much longer than a desktop computer, where you're constantly opening and closing different programs and doing different things with them. Plus, server operating systems are optimized for long-term use. 
From a hardware perspective, hard drives, because they have moving parts, will age when they are kept powered on. Silicon chips age with heat and power on cycles. Even though the operating system will run without a problem, the hardware will age when left on and when initially powered on.

---

### Post by Giantmundo on 2013-04-26
I never switch my computer off.  This one has been running for over three years without any problems.  Of course I reboot ever now and again but I never power it even when I go on holidays.  Hard drive is sweet.

---

### Post by CatKiller on 2013-04-26
If you've got critical files then you need to make backups regardless of uptime. Really. Do it now.

Other than that, your main enemy will be heat. If your computer's on 24/7 then the fans will be drawing in dust 24/7. If the intakes get clogged, temperatures will rise. Higher temps will shorten the life of all the components.

In principle, having the hard drive spinning all the time will eventually wear out the motors, but most drives will spin down when not actually accessed which will mitigate against that. The same isn't necessarily true of your fans, so as well as cleaning them from time-to-time you should make sure that they're spinning.

If you're leaving it unattended for extended periods of time you might want to use a UPS.

---

### Post by grahammechanical on 2013-04-26
You might find the Disks utility useful. I do not know hat version of Ubuntu that you are using but the Disks utility thar comes in 13.04 will let you access the hard disks SMART data which will tell you is the drive is healthy and run some tests. It will also give you access to drive settings where you can set the time period for when the drive will go into standby mode. A lot will depend on whether the drive and the motherboard can let Disks utility do this.

You might also want to install Psensor (in the Ubuntu Software Centre). That will give you temperature and fan speed read outs. It is useful for keeping an eye on things.

I suggest that you worry more about the build up of dust and fluff that will reduce the airflow and cause the temperatures inside the case to rise. Grills get blocked with fluff.

I switch my machine off every day and I have done for five - six years. Things are still working fine. Same hard drive as well. Hardware is tested for durability. There are figures relating to MTBF (Mean Time Between Failures). How long is the device expected to work before the risk of failure becomes great? Check the device's MTBF results on the manufactures web sight.

Regards.

---

### Post by 3rdalbum on 2013-04-26
I wouldn't recommend it for laptops, but for desktops it's fine. My parents have a home server that they keep on 24/7; it has a desktop HDD for file storage and a laptop HDD for the operating system. I haven't checked out the SMART stats for more than a year but I haven't had any complaints about the machine not working anymore, so I guess it's all fine!

If you're not going to use your computer for some hours, it would be a really good idea to suspend it. That'll spin down the hard disks and fans, and put only a minimum of power through the computer. You'll save power and wear and tear. It only takes a couple of seconds to awake the computer.

---

