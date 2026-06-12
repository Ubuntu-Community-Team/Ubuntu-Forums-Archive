---
title: "Internal System Clock and fsck problem"
date: 2007-02-27
forum: General Help
---

### Post by slumcat05 on 2007-02-27
OK, probably not a common probelm here, but I'll give it a shot.

I have a problem with my internal system clock, and have for a long time. Back when I had Windows, I noticed if I left the computer off for an extended period of time, the clock would gradually lose time, so that when I booted, it would be off by anywhere from several hours to several years. If left long enough, it would reset to Dec 31, 1999. I tried replacing the little watch battery on the motherboard, to no avail. The problem was easy to fix superficially, however, by using a small applet that reset the clock from a time server upon booting the OS.

Now that I am running Ubuntu (Edgy) exclusively, I still have the problem, and again, I would just set the clock from a server upon booting the OS. The problem, however, is that I have added an extra partition on my drive that mounts when the OS boots as a spare storage location.

When running through the boot sequence, fsck likes to make sure your drives are ok, and for the main partitions (/ and /home) it counts how many times they have been mounted. This is no problem. But for that extra partition (in my case hda4), apparently fsck checks its logs and decides whether to run a check based on the elapsed time since the last check. You can see where this can be a problem for me. Anytime I leave the computer turned off for a while, during the boot fsck reports something like:

> hda1: Last check is in the future. Will check in 5 mounts.
hda3: Last check is in the future. Will check in 5 mounts.
hda4: Has not been checked in 2507 days.

and then proceeds to do an fsck of hda4 (it seems like it calculates the absolute value of the elapsed time since the last check, since in this case, the last check would be in the future).

Does anybody know how I can fix this to avoid scanning hda4 every time I boot? Is there a way to change the fsck rules, or does anyone have any idea what might be wrong with my system clock? Any help would be greatly appreciated.

---

### Post by schilcha on 2007-02-27
Just a probably-too-simple guess:

After booting and adjusting system-time to our universe, run fsck manually on hda4. Hopefully the partition is then marked as checked in Feburary 2007. If then reboot the machine (of course with waiting for your clock to travel back in time), also this partition should be marked as being checked in the future the last time. 
Does that make sense to you?

---

### Post by schilcha on 2007-02-27
So now, the probably-more-elaborated suggestion:

have a look at the man-page of tune2fs. It says:
> 
       -i  interval-between-checks[d|m|w]
              Adjust the maximal time between two filesystem checks.  No post&#8208;
              fix or d result in days, m in months, and w in weeks.   A  value
              of zero will disable the time-dependent checking.


Therefore I'd suggest to run tune2fs on hda4 with the parameter "-i 0" to turn off the time-dependent checking.

Good luck!

---

### Post by slumcat05 on 2007-02-27
Thanks, I'll try these out when I get a chance.

---

### Post by slumcat05 on 2007-02-27
OK, the "simple" solution didn't help, because fsck has the drive logged as "clean" since it runs a check each time it boots (I guess I could force a check, but I decided to go for Plan B).

So I used:

```
sudo tune2fs /dev/hda4 -i 0
sudo tune2fs /devhda4 -c 30
```

to turn off the time interval checking behavior, and activate the "count mounts" behavior, with the standard Ubuntu setting of checking every 30 mounts. Haven't rebooted yet to check, but I feel like this will work perfectly.

---

