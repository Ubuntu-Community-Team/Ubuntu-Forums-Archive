---
title: "Driving the hardware hard..."
date: 2007-05-24
forum: General Help
---

### Post by starbase1 on 2007-05-24
Hi All,
I am having some problems with my PC, and I am not sure if it is hardware or not...

The main symptoms show when I run it under XP - It does not appear to crash when I boot into Ubuntu (no surprises there!).  ;)  But I am suspicious that this may be because I don't do stuff under Ubuntu that really pushes the processor, drives or graphics very hard.

For example if I leave it ticking over with a screensaver overnight I have no problems with either OS.

But when I start doing heavy duty assembling of panoramas or 3d rendering it seems like I get a couple crash to reboot several times an hour. 

So, a couple of things spring to mind.

1. Is there something simple I can run under ubuntu that will stress the machine a bit? Unfortunately I don't have my internet connection running under ubuntu yet, so I need something that is either included, or that can be downloaded and installed independantly.

2. Are there any progs for Ubuntu that will test the hardware, like memory checkers or similar? (For various reasons I am slightly more suspicious of memory and graphics related processing).

It's a Mesh core 2 Duo if that helps...

I'm still fairly new to this, so be gentle with me!
Thanks,
Nick

---

### Post by hardyn on 2007-05-24
Well crashing under heavy mathmatical operations is when its going to happen; its shoudn't but errors in programming do happen.

what you are describing however may be yes a memory problem, or weak power supply.
memtest86, is supplied by ubuntu, i have never run it.

if your hardware tests okey, yet you still have loaded crashing, you may wish to try a higher quality power supply, pull one from another machine you own, or borrow one from a friend.

---

### Post by hessiess on 2007-05-24
if you want somthing to stress your computer in ubuntu, download blender, find a verry high poly modal from somwere, hit f12. the prosessor will emediatly jump to 100%:)

---

### Post by psusi on 2007-05-24
Yes, run memtest86.  You will find it on the grub boot menu.  Let it run for a good 30-60 minutes.  If it reports any errors, you have a hardware problem.

---

### Post by starbase1 on 2007-05-24
Thanks for all the rapid responses...

I did try an MS memory tester under windows. It found no problems, but then the problems stopped for a couple of weeks! I already tried replacing the power supply with something more meaty, (which made no difference but was a good idea anyway), replacing the graphics card with a new one that was a different brand, (to try and avoid any common driver component to that might be causing problems), checking the core temperatures, (no correlation between temperature and crashes).

The latest one was that I came back from a holiday, and when I turned on the Bios told me that my attempt to overclock had failed! And I've never tried anything like that...

It's really utterly inconsistent, which makes me think if I have more than one problem... And the nature of the crashes makes me think it's hardware, but if it doesn't crash under Ubuntu, that doesn't make sense either... Which is why I am looking to test as much as possible frim Ubuntu, (quite apart from this being a good way to learn more, and progress my move to using it for everything).

Sometimes I can use it for a couple of weeks without a problem, yesterday it started locking up with something as simple as a drag and drop to move some files.

[COLOR="Red"][SIZE="7"]Argh![/SIZE][/COLOR]

---

### Post by NumberOne on 2007-05-24
It could be a heat related problem.  Todays computers have the ability to shutdown when temps get to high.  Check all the vents and fans and heat sinks and make sure they are clean.

---

### Post by hessiess on 2007-05-24
> **NumberOne said:**
> It could be a heat related problem.  Todays computers have the ability to shutdown when temps get to high.  Check all the vents and fans and heat sinks and make sure they are clean.

or just take the side off your box and see if that fixis it:D

---

### Post by psusi on 2007-05-24
No, removing the side of the case usually makes heat problems worse as the airflow is disrupted.  If you open the case you also need to put a good size fan next to it to blow tons of air around.

---

### Post by starbase1 on 2007-05-24
Thanks guys, I did upgrade the cooling, and tried running with the side off and  a big fan pointing in. I repeatedly ran with core temp monitoring software, (checking that the extra cooling was making a difference), and it crashed at a very wide range of temperatures...

There's lots of stuff to try, but I am unaware of any systematic method to identify the root cause...

Sigh...

---

### Post by psusi on 2007-05-24
Have you done the memtest86 yet?

---

### Post by hardyn on 2007-05-24
Random crashes, are in my experience, almost always a bad motherboard.

---

### Post by starbase1 on 2007-05-24
Pass 1of the memory test  completed, no errors...

---

### Post by Barrius on 2007-05-24
Nick,

I've had similar problems with two machines in the past month.    The first was a poor power supply (spiking?)   Windows XP on that one had the same symptoms you describe (I run Folding@Home which stresses CPU's/memory like nothing else).      I've replaced the PSU, and will reload Windows (Ubuntu was solid as a rock).

Second machine failed (Windows Server 2003) with similar symptoms.   Brought it back up and it repeatedly failed.   Turn out that a SATA cable was dinged up - low-level formatted the drives, replaced the cable, resinstalled the OS and now fiine.

First and foremeost under Windows go to Control Panel / Administrative Tools / Event Viewer.  To prevent yourself from chaing rabbits CLEAR the events from each class.    Keep the OS up, and periodically clear if nothing fails.    Once it does crash, reboot and check the SYSTEM log.  Check the entries in RED.

You can also save your data, verify the hard drive is good, reformat (not quick) and reload the OS.    Windows OS just degrades in a matter of months, unlike other OSes.

---

### Post by starbase1 on 2007-05-24
Thanks Barrius, I am going to be busy with lots of stuff to try! (Which is good).
:D

---

### Post by starbase1 on 2007-05-25
As an aside, it's exactly this kind of stability and reliabilty that got me interested in Linux in the first place... 

I had an XP machine die on me and it would not do anything. A freind suggested I look at a Linux Live CD as a starting point, which would at least let me see what hardware was fried, if any.

Sure enough, hardware was fine, but windows was bollixed. 

Now this could happen to any OS I suppose, but I started to think - Why can't windows give me a disk to let me do this in the first place? The answer I came up with was that the last thing they wanted was people with portable copies of ttheir expensive software.

It made me realise that there are some things that propriertry OS'es will simply never want to do, and that this is inherently bad for the user. I can see this becoming a lot more important in the near future, as more people start to discover the advantages of things like U3 usb drives with poortable applications, and virtual machines / virtual appliances.

USB sticks are already seriously cheap - but they are still getting bigger and cheaper. I look forward to the day when I can have something like a 16 Gb bootable USB that has all my applications and key data on it, as well as the OS. Plus a backup of, course. 

Nick

---

### Post by starbase1 on 2007-06-03
Just in case it is of use to others, I think I finally nailled the problem.

One of the things I tried was a demo version of System Mechanic 7 - and I found a bunch of stuff on Amazon.com where people said how it pretty much destroyed system stability, did all sorts of nasty stuff like hiding it's processes, and generally acting in a manner more like malware. Worst of all, it did not uninstall when you ran the uninstall.

With the help of various web sites, I was able to remove it, (and of course, Ubuntu was not victim to its hiding tricks!)

Thanks to all for taking the time to make suggestions.

Now to get on with moving over to a proper OS!
:D

Nick

---

