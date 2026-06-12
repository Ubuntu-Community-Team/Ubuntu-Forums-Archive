---
title: "Boot Time"
date: 2006-10-29
forum: General Help
---

### Post by Tempurite on 2006-10-29
I have a 2 "problems" with Edgy Eft.


- How to configure an Alps Touchpad?:confused: 

- Edgy takes around 2+ minutes to boot on my machine...](*,) 


*Intel Pentium M 1.86GHz processor
*512 MB RAM

---

### Post by NeoLithium on 2006-10-29
I'm not quite sure about the touchpad; but as for speeding up your boot time, you can stop the system from booting services that you do not use when you start your computer.

For gnome, I use the boot up manager, which is available from the repositories; so you can get it through automatix or synaptic if you prefer gui, or just ```
 sudo apt-get install bum 
``` If you search the forums, there are a few posts that help identify services a little more in depth so you can know what you can safely disable. Just remember, when in doubt; leave it on for now, until you absolutely know what the function is :)

---

### Post by Tempurite on 2006-10-29
Is really annoying to wait 2 minutes until ubuntu boots...

---

### Post by reacocard on 2006-10-29
> **Tempurite said:**
> - Edgy takes around 2+ minutes to boot on my machine...](*,) 

*Intel Pentium M 1.86GHz processor
*512 MB RAM

2 minutes?! I have Pentium M 1.73Ghz and 1 GB RAM. Took ~50 seconds with default install. After some tweaking, it's less than 35 seconds. Here's a few threads with tweaks that may help you:

[http://ubuntuforums.org/showthread.php?t=206022](http://ubuntuforums.org/showthread.php?t=206022)
[http://www.ubuntuforums.org/showthread.php?t=254263](http://www.ubuntuforums.org/showthread.php?t=254263)
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by Tempurite on 2006-10-30
This is weird...

When my laptop runs from the battery ubuntu boots in 35-40 seconds.

---

### Post by volanin on 2006-10-30
When your laptop runs from the battery, Ubuntu skips some expensive startup
processes in order to consume less power. If I remember correctly, one of
the processes it skips is the fsck.

I can almost garantee that you're using reiserfs.
This filesystem take a LONG time to mount, and is the greatest responsible
for slow boot times in every distribution. It can be really slow for big
partitions.

So in order to improve boot times, make a backup of your files and format
your partitions with any other filesystem. I personally recommend JFS for
laptops (smaller CPU usage, battery lasts longer), or XFS if you are all
about speed.

Be aware that XFS for desktops can be risky if you don't have UPS.
One power outtage and is can really mess up your files.

---

### Post by Tempurite on 2006-10-30
Yes, I'm using ReiserFS...

It's possible to format without deleting my files?

---

### Post by volanin on 2006-10-30
Not that I know of.

---

### Post by Tempurite on 2006-10-31
Thanks, but I formated the partition and didn't work....](*,)

---

### Post by volanin on 2006-10-31
Strange, very strange.
Well, as a last resource, install bootchart.
It will create an image displaying the time each process take during your boot sequence.
This way, you will know EXACTLY what is holding you back.

P.S.:
By the way, out of curiosity.
Did you reformat all your partitions?
Which filesystem did you choose for them?

---

### Post by Tempurite on 2006-10-31
I have a dual boot system (Windows XP/ Ubuntu 6.10)

I formated the partition where I had Ubuntu (ReiserFS) to JFS, and the swap of course.

---

### Post by Tempurite on 2006-11-01
Problem solved!

I was using the generic kernel, so I installed the 386 kernel.

---

### Post by ~LoKe on 2006-11-01
> **Tempurite said:**
> Problem solved!

I was using the generic kernel, so I installed the 386 kernel.

The 386 kernel is working out better for you than the generic?  That's an odd one, but perhaps someone knows why.

Oh, and as for speed and reliability, the default ext3 seems to be the best bet?

---

### Post by volanin on 2006-11-01
Reliability, no doubt.
Speed... don't believe so.

---

