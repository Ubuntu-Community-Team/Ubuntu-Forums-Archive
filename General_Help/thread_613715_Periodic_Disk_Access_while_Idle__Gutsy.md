---
title: "Periodic Disk Access while Idle / Gutsy"
date: 2007-11-15
forum: General Help
---

### Post by Dave / Mosaic on 2007-11-15
blink...  blink...  blink...  blink...  blink...  blink...  blink...  blink...  

Under Gutsy, that's what the disk activity LED does on my laptop all day long...  approximately every two seconds, as regular as a clock, there's a quick little "blink"...  even when the machine is completely idle, etc.

It didn't do this under Feisty...  With Feisty, once the machine booted, and some basic things got loaded into RAM, the machine could operate for long periods without accessing the disk, certainly while idle, but even while doing some things like browsing the internet or editing a file.

Gutsy seems different, though...  Gutsy needs to always fidget, constantly, like my four-year-old son:  "blink...  blink...  blink...  blink..." goes the light, on and on and on...

What on earth is it doing??  I've tried as well as I know how to puzzle it out, watching log files, looking at processes, examining crontabs, etcetera, but I can't for the life of me figure out what I need to turn off or disable.

Any ideas where to look??

--dave

---

### Post by blackfire on 2007-11-15
I can confirm it on my girlfriend's Dell Vostro 1500. I'm suspecting it's the strigi daemon, but I've not checked yet.

---

### Post by Damanther on 2007-11-15
This might be associated with the known issue of hard drives on laptops. There is an option on most hard drives that sets how many cycles to go through before "parking" the head of the drive. By default on laptops this is set to a fairly regular interval. There is are a couple of ways to get around this. I would sugges readinga  bit of [this ]("http://ubuntuforums.org/showthread.php?t=591503&highlight=hdparm") post before applying any changes

---

### Post by Dave / Mosaic on 2007-11-15
> This might be associated with the known issue of hard drives on laptops...

The fundamental problem underlying the issue you refer to, as I understand it, is:

> Your hdd parks the heads after a hdd access to protect the disk. Very soon thereafter, the heads unpark to access the disk (eg. ext3 journals every 5 sec).

Well, now...  I agree that this effect may (or may not) be occuring in practice on my laptop.  But, I feel, it isn't the cause of what I originally posted to ask about.

I'm asking this:  The system is sitting there, supposedly idle.  I'm not typing on it, not moving the mouse, not running any programs that I'm aware of, not playing music, nothing.  Yet, something keeps accessing the disk, every two seconds or so.  Now, the heads may be parking and unparking a lot, and that is definitely something interesting that I want to look into.  But, for the time being, I'd like to figure out what is accessing the disk every couple of seconds, and stop it, because my feeling is, that there can't be anything going on that is really legitimately necessary.

Then, the heads could just park and stay there,,, and the drive could spin down,,,  and the machine could sit there, booted and running, but still not accessing its disk, for a long time, nice and quiet.

Maybe it's the journaling??  Does journaling happen, even in the absence of things being written to the disk?  Is there a way I can disable journaling, to test if that's what's going on in my system?

All for now--

--dave

---

### Post by bingoUV on 2007-11-15
An crude diagnostic method : 
```

top -b -n 2000 -c -d 2 >>  ~/log

```

This will print top output every 2 seconds into the file ~/log.
Now leave the system for a minute, and examine the log. top would take a lot of CPU, but see what else needs cpu during this period. It is likely to be the culprit.

---

### Post by Dave / Mosaic on 2007-11-16
Okay, thanks - good clue...

Now, top led me to this process:

5176 (other junk deleted...)  hald-addon-storage: polling /dev/scd0 (every 2 sec)

Which, if I kill it, stops the blinking.  So, it looks like Ubuntu is polling for new USB drives, memory cards, or some such, every couple of seconds, and...  doing what?  Maybe updating some database stored on the disk, about what devices are plugged in?

There must be some way to make this run without it having to access the disk every two seconds...  I don't know where to look for documentation, however - some readme files in /usr/share/doc/hal* point me to [http://www.freedesktop.org/Software/hal](http://www.freedesktop.org/Software/hal), but there doesn't seem to be any useful documentation there...

Any ideas, how to configure hald, or hald-addon-storage, or at least where to look for documentation?

---

### Post by bingoUV on 2007-11-17
good find. The following will disable it. I have heard that some upcoming patch to the linux kernel will disable the need to poll. Meanwhile when you keep polling disabled, automount of CDs will not work, you will have to mount them manually.
```

hal-disable-polling --device /dev/scd0

```

Read [http://www.lesswatts.org/tips/disks.php](http://www.lesswatts.org/tips/disks.php).

---

### Post by Dave / Mosaic on 2007-11-17
> hal-disable-polling --device /dev/scd0


Hey, thanks for that - that works...  Better than just shutting down the whole hald, which breaks a lot of stuff...

One thing, though - it's not so much the polling that I find objectionable, but rather the disk access that seems to go along with it.

I wonder what hald is accessing the disk for...  rereading some configuration file every time, or updating some database file, or writing to some log...

How do you suppose I can find out... and maybe modify some configuration file, so that it can do it's polling, but not mess with the disk every two seconds?

---

### Post by bingoUV on 2007-11-17
I don't think it is supposed to access disk during that polling. Most of the times, it will not find any news, so it should go back to rest. On my system, I do not always disable polling but I do not see any recurrent hard disk activity. But I might be wrong, or there could be a bug.

Now, the disk activity LED of your laptop might be wrong. If it reports the activity of the IDE bus, it might light up during scd0 polling too.

For more information, no better place than lesswatts.org , that I linked to. Simple, end user centric, working tips.

---

### Post by Dave / Mosaic on 2007-11-18
Yes, thanks for that link - good information on the lesswatts site...

In any case, now with the CD polling turned off, I'm finding that there's still another source of chronic disk activity that I'm seeing...  This isn't as regular or predictable as the former activity (CD polling, every two seconds, like clockwork), but now every 5-10 seconds (sometimes as long as half a minute), there's something accessing the disk still, preventing it from spinning down when the machine is idle.

From these forums, I've found another way to look at what's accessing the disk.  First, I'm killing the syslogd process.  Then, I'm doing:

> echo 1 > /proc/sys/vm/block_dump


and then, following that, every few seconds I'm doing:

> dmesg -c


Now, from the output of this, it seems that kjournald feels that it needs to be mucking with the disk every 5-10 seconds or so, even after the system calms down, and nothing else is accessing the disk (which I assume to be the case, since mostly the only entries dmesg is showng are coming from kjournald (rarely, there are entries from dmesg itself, or from bash, but I expect both of these, since after all I'm sitting there entering dmesg -c into a shell...)).

So, I guess my questions now are:

-- Is this "journaling", as in what goes on in my filesystem (which is ext3)?

-- If so, then why is there journaling going on, in the absence of other filesystem activity to journal about?

-- Is this correct / normal behavior?

-- Are there ways to stop / affect this behavior?

The mystery continues...

---

### Post by bingoUV on 2007-11-18
Good questions and research Dave, I am learning a lot. Thanks

kjournald is indeed for journalled file systems. By the method you outline, I too get lot of IO by kjournald. But I just found a sort of solution. 

atime is causing the problem. I have 3 ext3 partitions, 
/dev/sdaX on /boot type ext3 (rw)
/dev/sdaY on /home type ext3 (rw,noatime)
/dev/sdaZ on / type ext3 (rw,noatime)

except boot, both are noatime. When I applied your technique to diagnose, I found kjournald is writing repeatedly to sdaZ (which is noatime). But when I remount sdaX as noatime, I find these repeated writes stop. Try that. May not be an option if you use atime.

So, something mysterious is being accessed in boot partition. This is causing atime writes to the / partition.

---

### Post by Dave / Mosaic on 2007-11-19
Curiouser and Curiouser...

Well, I think that's a good clue, turning off atime.  I added "noatime" to all the options fields in my /etc/fstab, and I think it's made a difference, less constant journaling.  Now, there are only dmesg entries from kjournald, in and around other legitimate file system accesses, like I'd kind of expect...  When something writes to a file, there's some twiddling by kjournald, then the actual write, then a little more fiddling by kjournald...

I still continue to see disk activity that I don't understand, however... now the process that I see coming up most is "pdflush"...  That's not ringing a bell for me as to what it is; time to do some more reading...

And, there is some other stuff that I don't really know what it is, like this:

> root@Z3300Ae:/home/zzzz# dmesg -c
[ 2755.092000] kjournald(4173): WRITE block 18128 on sda7
[ 2755.404000] gnome-power-man(5542): dirtied inode 554405 (profile-S5-3P24-discharging.csv.CC6E2T) on sda7
[ 2755.404000] gnome-power-man(5542): dirtied inode 554390 (?) on sda7
[ 2761.000000] kjournald(4173): WRITE block 9116960 on sda7
[ 2761.000000] kjournald(4173): WRITE block 18136 on sda7
[ 2761.000000] kjournald(4173): WRITE block 18144 on sda7
[ 2761.000000] kjournald(4173): WRITE block 18152 on sda7
[ 2761.000000] kjournald(4173): WRITE block 18160 on sda7


Nothing seems wrong about this particular excerpt to me, though I'm also now beginning to wonder what exactly dirtied inodes are all about...

---

### Post by Dave / Mosaic on 2007-11-19
There's another thing, now that I think about it, that is bugging me about the constant disk accesses every few seconds:  The disk activity, has a particular, distinctive *sound* to it - kind of a very predictable soft buuurp....buuurp, with about a second in between the two buuurp sounds...  It's the same sound, again and again, during these "Idle" periods, on and on...

I can't quite think of what, but somehow it sounds like the disk is doing something that isn't necessary, or maybe that it shouldn't be doing...  It's not a loud sound, or a sound as though something is broken, but just the pattern to it is weird.  If all that's happening is a write of a few blocks to a journal or something, then why exactly is the sound of it always in two separate chunks, about a second apart in time?  It's like the disk is coming in and out of dormancy, or something...

In this case, the sound is maybe more auditorily obvious and right in my face than it would be in a desktop system, since this is a laptop - and the disk drive is sitting right there, under my hand...

---

### Post by Shazaam on 2007-11-19
Small thread hijack here...
To see more install htop. It's in the repos.

[http://htop.sourceforge.net/](http://htop.sourceforge.net/)

---

### Post by bingoUV on 2007-11-20
> **Dave / Mosaic said:**
> There's another thing, now that I think about it, that is bugging me about the constant disk accesses every few seconds:  The disk activity, has a particular, distinctive *sound* to it - kind of a very predictable soft buuurp....buuurp, with about a second in between the two buuurp sounds...  It's the same sound, again and again, during these "Idle" periods, on and on...

I can't quite think of what, but somehow it sounds like the disk is doing something that isn't necessary, or maybe that it shouldn't be doing...  It's not a loud sound, or a sound as though something is broken, but just the pattern to it is weird.  If all that's happening is a write of a few blocks to a journal or something, then why exactly is the sound of it always in two separate chunks, about a second apart in time?  It's like the disk is coming in and out of dormancy, or something...

In this case, the sound is maybe more auditorily obvious and right in my face than it would be in a desktop system, since this is a laptop - and the disk drive is sitting right there, under my hand...


Perhaps you know this, and you have already checked ; but is it the sound of the disk head parking itself every 2 seconds? The infamous ubuntu bug which seems to cause premature death of hard drives. Is is Hitachi hard disk?

---

### Post by Dave / Mosaic on 2007-11-20
> Perhaps you know this, and you have already checked ; but is it the sound of the disk head parking itself every 2 seconds? The infamous ubuntu bug which seems to cause premature death of hard drives. Is is Hitachi hard disk?

BINGO...

I had come across this issue a while ago, but dismissed it, thinking, hey, surely the heads wouldn't be parking after only ONE SECOND of inactivity...

But now I can see, that, yes, that seems to be exactly what is happening...

By the way, yes, the disk is a 7200 RPM Hitachi Travelstar...

Last night I turned off the "agressive power management" with (going by memory here) hdparm -B 254, and the weird sounds stop instantly.

There's still occasional random disk access every few seconds to a few times a minute, but the sound of it is just a subtle flutter, like you'd kind of expect.

Sooo....

1) At least, I've figured out things this far, so that I can fix it so Ubuntu won't wear my disk out in a year, through excess parking...

2) It's not really a "solution" at this point, however, since now the disk is a) prevented from ever spinning down or entering a low-power state, no matter how idle the machine gets, and b) there's always the danger of the heads contacting the spinning disk, because they never will park, even if the machine is idle...

3) This whole scenario is kind of bad news...  The real problem, as I see it, is that Ubuntu wants to be accessing the disk something like every three seconds or so, and it's (apparently) not easy to stop it.  There's another thread on here, with over 400 posts on this issue, that I guess I'm going to have to dig into...  It seems to get into arcane things like how the kernel does paging, how to manage dirty inodes, etc...

4) I'm beginning to see, that maybe Ubuntu is well designed to be a high-performance desktop OS, but has some significant bugs to work out to perform well on a laptop.

Lots to learn, still...

--dave

---

### Post by Dave / Mosaic on 2007-11-20
By the way, regarding htop / top:

For anybody coming after and reading this:

I see a lot of posts in these forums, suggesting to people to use top / htop to get a handle on what is accessing disks in the background.  Top is better than nothing, of course, but it's not really very useful for this purpose.  Top sorts processes by things like processor utilization, memory allocation, etc., but what you really want to sort by is file system access...  and I don't see any way to do that with top (although, maybe somebody smarter than me, will correct me on this).  The granularity of top et al. is just too crude to useful as a basis for deciding what processes are accessing the disk...

Much more useful, to me, was the idea (that I got from another post) to: 

disable syslog, which I did by just killing the syslogd process, though maybe there is a less crude method; then> echo 1 > /proc/sys/vm/block_dumpand then watch what goes on with dmesg (dmesg -c works nicely for this).

---

### Post by remusmp on 2008-02-04
Hello,

I ran into the same problem today (after installing a linux distrib). Did you find a solution to that kjournald writing blocks to hdd? It's really annoying...

Thanks.

---

### Post by caraboy on 2008-06-10
Use iotop to view hdd activity: [http://guichaz.free.fr/iotop/](http://guichaz.free.fr/iotop/)

Extract the contents of the archive and run it with ./iotop.py

I set my hdd apm to 254 and use noatime on my ext3 partitions. I still get constant activity from kjournald, not as much though.

---

### Post by HighEntropy on 2008-06-19
If you're still having problems after trying all of the above, it might be because you have mythTV installed.

If so, removing mythTV will fix this problem. I'm not sure if it's a problem with myth, or if it's because myth didn't like me upgrading Ubuntu to 8.04, but removing it stops the horrible HDD grinding.

---

