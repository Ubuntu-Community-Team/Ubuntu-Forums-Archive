---
title: "Changing Swap Space Size"
date: 2006-11-10
forum: General Help
---

### Post by Ulysses on 2006-11-10
Hello

IBM Thinkpad X22, Pentium 3, 800MHZ, 128Mb RAM, Ubuntu 6.06

System freezes often. Sef helped me out in another thread by figuring that it was swap space size.

I installed GPartEd and tried to see if I could increase the size myself, but it won't let me. The convenient GUI interface shows a pretty little padlock there next to the /dev and I can't seem to get it unlocked

If you haven't figured it out, I am a newbie. So be gentle and type slowly so I understand you.

Please help

RAR

---

### Post by mbeierl on 2006-11-10
The gparted that comes with Ubuntu is a little too old for some operations (such as moving partitions.)

The swap is probably locked because it is currently in use by the operating system.

I would recommend going to [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) and downloading the LiveCD ISO image for the latest version and burning that to a CD.

Boot your computer using that CD and all resize, etc, operations should be available to you, and the swap should not be locked because you are running from the CD instead.

---

### Post by Ulysses on 2006-11-10
Hey

But just to be clear here - this isn't a complete re install, it's just using GPartEd from a CD, right?

Thanks, by the way. I was up tuntil 5:00AM trying to figure this out and how to do it without reinstalling ubuntu ; though I was sure that was the best, easiest way. I hate using the easiest way

RAR

---

### Post by jeffathehutt on 2006-11-10
As with any operation that requires partitioning, make sure you back up your data first.  I have used the gparted livecd several times and I've never had a problem with it, but something could always go wrong.

And you are right, as long as nothing goes wrong you shouldn't have to reinstall ubuntu.

---

### Post by CatKiller on 2006-11-10
You can turn off your swap by using ```
sudo swapoff -a
``` This will allow you to resize the swap partition with GParted. As you've discovered, you can't resize a partition that's in use. Which means that if you also want to resize your / partition, which you're using to resize the / partition, you have a problem. Which is why people will tell you to use the GParted cd.

I'd advise you to do that, too.

Unless you're only creating partitions, rather than moving the start of any partitions. Then the live install disk is sufficient. You'll still need to turn off the swap though. And in your particular case, you don't have enough RAM for the Ubuntu live cd anyway.

---

### Post by Ulysses on 2006-11-10
Hey

When I run sudo swapoff -a in terminal I get this result

```
swapoff: /dev/hda5: Cannot allocate memory
```

So I went to [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) and downloaded the ISO for the Live CD and the whole thing took about 21 minutes, give or take. Simple as pie. And everyone loves pie.

So far I've tried a whole heckuva lotta things that ordinarily froze the laptop up and I can't seem to make it happen. I made the extended partition 1GiB ; might be overkill, but let's see what happens.

Next step? 2 different operating systems on one itty bitty laptop. PCLinuxOS, I think.

Anyone who says that the forums are of no help aren't helping themselves. Ubuntu rocks. I'm buying a poster and putting it over my daughter's bed and I'm gonna fight with my wife about what our daughter's first words are gonna be

Momma or Ubuntu. I think Ubuntu will be easier for her to say.

Thanks again.

RAR

---

### Post by CatKiller on 2006-11-10
> **Ulysses said:**
> Hey

When I run sudo swapoff -a in terminal I get this result

```
swapoff: /dev/hda5: Cannot allocate memory
```



Makes sense I suppose. The last thing I'd ever have wanted to do just to see what happens is turning off the swap memory on a computer without much physical memory.

Glad you're sorted now, anyway.

FWIW, the usual rule of thumb for swap size is the smaller of twice your physical RAM and 2GiB. The good thing is that if you install a different distribution for a dual boot, they can both use the same swap partition.

---

### Post by Ulysses on 2006-11-10
Hey

Yeah. Well. My hopes have been dashed. I challenged the system more and more and finally, yup, it did freeze. Though it did take longer than I thought.

I am thinking that this is truly a bandaid. I mean, the swap size really should be at 512MB and I really should have 256MB of RAM.

128MB of RAM should be reserved, I think, for DSL or maybe Xubuntu

But I haven't experimented with a session in Xubuntu to see if it freezes

And, for the record, you aren't that abrasive without the nicotine.
Though you will crave it for the rest of your damned life. Trust me. I crave them all the time. And if you sneak a smoke, it never tastes as good as the monkey on your back tells you it will taste.

RAR

---

### Post by CatKiller on 2006-11-10
DSL seemed very peculiar when I briefly tried it a while ago. Xubuntu seemed quite nice - although not as user-friendly as Ubuntu. I did read a thread today that suggeted that switching your Window Manager to something like IceWM rather than Metacity might help lower your memory usage. I've not ever tried it myself, though.

I'm glad that I'm not coming across too crabby - new users could probably do with a gentler touch than I've been giving recently, but I don't really know enough to usefully contribute that much in the other parts of the forum. I'd switched to rollies before I stopped, and ocassionally I'd try a proper cigarette again. They weren't as good as I'd remembered, either. Bummer that the cravings don't go away - I'm going to be as big as a Land Rover by the end of the year as it is.

Out of interest, have you tested the memory with memtest86? Although you can get memory problems caused by lack of memory, sometimes they are caused by, well, memory problems. Might be worth a look.

---

### Post by Ocxic on 2006-11-10
"sudo touch /swap/swap.img" makes a swap file

"dd if=/dev/zero of=/swap/swap.img"  ##this will make the file bigger buy writing zeros to it unfortuanlty there is no way to limit the amount of data, and must be stopped manually, if left running it will fill your hard drive to the max, run this for only for a few seconds to get the requierd swap size you wish, the bigger the file the longer you have to run it for. mannually stop it with ctrl-c.

"sudo swapon /swap/swap.img"   #will activate the swap file and expand your current swap size

add this to your fstab to make it perminant:
```

/swap/swap.img  none  swap  defaults  0    0

```

don't make the swap file bigger then 100MB and I'd reccomend 64MB

---

### Post by CatKiller on 2006-11-10
> **Ocxic said:**
> "dd if=/dev/zero of=/swap/swap.img"  ##this will make the file bigger buy writing zeros to it unfortuanlty there is no way to limit the amount of data, and must be stopped manually, if left running it will fill your hard drive to the max, run this for only for a few seconds to get the requierd swap size you wish, the bigger the file the longer you have to run it for. mannually stop it with ctrl-c.

Actually, you can make it the size you want, by specifying the **bs** and **count** options. I haven't tried it, but ```
dd if=/dev/zero of=/swap/swap.img bs=1M count=64
``` might work.

A good solution, though. I'll try to remember that.

---

