---
title: "Ubuntu 8.04 Sluggish Response"
date: 2008-06-26
forum: General Help
---

### Post by Bosconian on 2008-06-26
I had a laptop which came with Vista which was just horrible. I made a decision to remove it and replace it with either Ubuntu or XP. In the end I decided to dual boot both before making a final decision.

I had read about how Linux was so much faster and more efficient than Windows but I am finding exactly the opposite. I wondered if I am doing anything wrong.

For example. when I click the main menu button, the hard drive starts thrashing and it takes a good 5-6 seconds for the menu to appear. Much worse than the XP I just installed.

Applications seem to take longer to load as well.

My laptop is a Acer Aspire 5633 with 2Gb RAM, 120Gb HD, nVidia 7300 gfx card.

---

### Post by Bosconian on 2008-06-30
Anyone know how to fix this?

---

### Post by danwood76 on 2008-06-30
Well my laptop is a lower spec than your and runs super quick with ubuntu hardy heron.

It might be that there is a hardware conflict or something chewing up your CPU.
Have a look in the system monitor and see if anything is using up your CPU time.
The system monitor can be found System -> Administration -> System Monitor.
Check the CPU and RAM usage and then the running processes to see which processes are using the most.

If you use a lot of ram ubuntu may be swapping it out which can produce slow speed, with 2GB of RAM you should be fine though, I only run on 1GB on my laptop and it never swaps RAM out.

---

### Post by mikjp on 2008-06-30
Really strange. 

This looks one of the situation where it is difficult for a newbie to get things corrected. I was not able to google anything interesting for your laptop.

Your hardware should certainly have no problems running Ubuntu, as it should be show no symptoms described by you even with 256 MB.

Maybe you should try some other distro instead? I would suggest trying the new openSUSE 11.0.

Greetings,

mikko

---

### Post by madjr on 2008-07-06
> **Bosconian said:**
> I had a laptop which came with Vista which was just horrible. I made a decision to remove it and replace it with either Ubuntu or XP. In the end I decided to dual boot both before making a final decision.

I had read about how Linux was so much faster and more efficient than Windows but I am finding exactly the opposite. I wondered if I am doing anything wrong.

For example. when I click the main menu button, the hard drive starts thrashing and it takes a good 5-6 seconds for the menu to appear. Much worse than the XP I just installed.

Applications seem to take longer to load as well.

My laptop is a Acer Aspire 5633 with 2Gb RAM, 120Gb HD, nVidia 7300 gfx card.

well as everyone knows XP is the best OS on **fresh install**, but after a week it starts **degrading** and you'll find it more and more **sluggish**.

in 2 or 3 months you'll try to **clean the registry and spywar**e, later on you'll think about **re-formating**.

That doesn't happen to linux, 2 or 3 years after the speed is the same.

anyway i do have a Dell laptop with **1gb** of ram and everything is speedy.

like others suggested you could try another distro like **linuxmint 5 R1**

[http://www.linuxmint.com/](http://www.linuxmint.com/)

is based on Ubuntu but further optimized and with things like codecs, flash, java, etc already pre-installed.

---

### Post by ugm6hr on 2008-07-06
> **Bosconian said:**
> For example. when I click the main menu button, the hard drive starts thrashing and it takes a good 5-6 seconds for the menu to appear. Much worse than the XP I just installed.

Applications seem to take longer to load as well.

My laptop is a Acer Aspire 5633 with 2Gb RAM, 120Gb HD, nVidia 7300 gfx card.

This is not normal Ubuntu behaviour.  5 seconds to open a menu?  And it should not require HD access.

Sounds like you are using swap.  System monitor should give you a clue.

---

### Post by tact on 2008-07-06
I have full-blown hardy running on an asus eeepc 900 just for the heck of it.  Its running full on Compiz eye-candy (transparency, wobbly windows, scale, expo, etc etc) and is pretty snappy.  Remember these things are tiny little Intel Celeron M clocked at 900MHz with 1Gb RAM.

So with that tale, and so many others sharing their experience - we can hope you are convinced its not Hardy. :)  

You asked "...or have I done something wrong?"  It would seem so.  Perhaps if you give some more detail about how you installed your dual boot system people can help.

You installed XP on a clean formatted HDD?  Did you let XP format the entire drive as NTFS as one partition?  Did you make several partitions?  What are they?  Did you then install ubuntu and let it take xGB of freespace on the NTFS drive?  How much space?  Or how else did you do the install?  etc etc...

---

### Post by mnmus on 2008-10-20
AMD 64X2 5200
4GiB RAM
250GiB+ free disk space

Similar problem here too. Hard drive thrashing. Amend that: hard drive activity simply never ceases. System monitor reports plenty of free RAM. CPU-0 is pegged out at 99-100% and CPU-1 just blips occasionaly up to 11% or so.

Difference here: Ubuntu 8.04 is a clean install on a bare drive.

Hard drive constantly thrashing. Anyone with a clue?

====

*sigh*

My issue was probably not related. Had a brain storm (more like tempest in a teacup): I had recently installed MythTV. Uninstalled that and my thrashing went away. NOTE: System Monitor did NOT note any measurable CPU activity or memory use associated with MythTV, but when I uninstalled it, the hard disk stopped thrashing for the first time in days (since I began noting the problem... which also happened to coincide with the MythTV installation).

So, my issue was apparently unrelated to the initial post in this thread.

---

### Post by ugm6hr on 2008-10-20
> **mnmus said:**
> Hard drive constantly thrashing. Anyone with a clue?

Does system monitor suggest continuous swap usage?

I had a similar (transient) problem once.  A restart of X sorted it, and it never recurred.  Something to do with nautilus (I think).

---

