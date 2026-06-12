---
title: "Clock setting in dual boot arrangement"
date: 2019-04-18
forum: General Help
---

### Post by kesetyan on 2019-04-18
Hi,

I am based in the UK and have a Lubuntu 18.04 with Windows 7 dual boot desktop system.  Recently, here in the UK, the clocks moved forward one hour and since then I have had a problem with the computer clock.

The problem is both interesting and irritating and, so far, I have been unable to resolve it.  Both operating systems are set to synchronize time via the internet but if one gives the correct time then the other will be one hour out.  For example, if I boot into Lubuntu and it shows the correct time, when I restart and boot into Windows 7, the clock will be one hour slow.  I can easily synchronize the time with the internet to correct the clock but then, if I restart the system and boot into Lubuntu, the clock will be one hour fast.  Again I can synchronize the clock with the internet but restarting and booting into Windows 7 shows the clock to be one hour slow.

Before the daylight saving time change (I still think of it as GMT to BST), there was no problem as the clocks for both operating systems matched..  There has also been a recent Windows Patch Tuesday update but I don't know if that may have caused the problem.

Any comments, help and advice would be much appreciated.

Thanks and best regards.

---

### Post by Impavidus on 2019-04-18
See here: [https://ubuntuforums.org/showthread.php?t=2321876](https://ubuntuforums.org/showthread.php?t=2321876)

Windows keeps the clock on local time, Linux keeps it on UTC. The problem arose with the change to summer time, as before that UTC and local time were identical (in Britain). The solution is to reconfigure one of them so that both use the same time. Reconfiguring Linux to use local time is easier, but less robust. Think of what happens when both try to switch back to standard time.

---

### Post by kesetyan on 2019-04-18
Hi Impavidus,

Thanks very much for your help.

I am trying out switching the Lubuntu clock to local time (using command 'timedatectl set-local-rtc 1').  Presumably I can reverse this with the command ''timedatectl set-local-rtc 0'.  If I have misunderstood and got this wrong, please let me know.

UPDATE:
I carried out the command 'timedatectl set-local-rtc 1' in the lxterminal in Lubuntu and have switched between Lubuntu and Windows a few times - now the clocks for both show the correct time.  I've made a note of what I did and copied the relevant information from the link (and its sub-links) that you gave me and filed both documents for future reference. Thanks again for your help and providing me with a little more insight into the workings of Linux for which I am a novice.  If you can confirm that, come next October, when our UK clocks lose an hour, using the command 'timedatectl set-local-rtc 0' will get me back to the position I was in before, I can mark this thread as resolved.
Regards.

---

### Post by Frogs Hair on 2019-04-18
Another Source: 

[http://www.webupd8.org/2014/09/dual-boot-fix-time-differences-between.html](http://www.webupd8.org/2014/09/dual-boot-fix-time-differences-between.html)

---

### Post by kesetyan on 2019-04-19
Hi Frogs Hair,

Thanks for that link - it's very comprehensive and explains very well to a novice like me.

---

### Post by kesetyan on 2019-04-19
Hi,

Impavidus and Frogs Hair have been extremely helpful - I am confident now that I can mark this thread as solved.  Yet again this forum has proved its value to a novice Linux user and shown why it is my first port of call when I require help with Ubuntu and its derivatives.

Cheers.

---

### Post by Impavidus on 2019-04-19
> **kesetyan said:**
> If you can confirm that, come next October, when our UK clocks lose an hour, using the command 'timedatectl set-local-rtc 0' will get me back to the position I was in before, I can mark this thread as resolved.
Regards.
There's no need to change any settings in October, Lubuntu knows that after October local time is identical to UTC. The worst thing that can happen is that the first system you boot after the change to standard time (or the system running when the change happens, if you keep your computer running at night) will change the clock to standard time. The other system, when booted later, will then change the clock to UTC-1, but after a one-time fix it should all work until the next time change.

---

### Post by kesetyan on 2019-04-20
Hi Impavidus,

Thanks for the information - that's reassuring.

Come next January when Microsoft support ceases, for security reasons I will be disabling the internet on Windows 7 but maintaining it in Lubuntu, hence my reason for adopting the dual boot arrangement.  I do not want to 'upgrade' to Windows 10 but wish to have a Windows system for particular software and computer peripherals.  I like Lubuntu, and the more I learn about it and Ubuntu (I have an Ubuntu desktop too), the more I appreciate the flexibility and the relative ease of dealing with most problems - should the worse happen, it seems to me that if I have to do a complete re-installation, there's much less hassle than with Windows 10.

Cheers and best regards.

---

