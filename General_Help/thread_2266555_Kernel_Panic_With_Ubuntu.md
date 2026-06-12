---
title: "Kernel Panic With Ubuntu"
date: 2015-02-23
forum: General Help
---

### Post by Hastur_The_Unspeak on 2015-02-23
So I've been having an issue as of late. It happens when I try to play Dota 2. I get into a match, and sometimes my computer will crash randomly leaving this error dump: [http://imgur.com/8SgeYyf](http://imgur.com/8SgeYyf)

Keep in mind these crashes are completely random. It is also not the first time I have been plagued by such issues. My previous install of Ubuntu did the same thing, and it resulted in my upgrading my distro to fix it. It worked for a while, but now it seems the error is back. Does anybody know how to fix this?

Another Crash Dump
[http://postimg.org/image/wsuqumvtx](http://postimg.org/image/wsuqumvtx)

Memtest86+ Result
[http://postimg.org/image/jgjrqaz09](http://postimg.org/image/jgjrqaz09)

SMART Test Results
Part 1: [http://imgur.com/0Izj4ME](http://imgur.com/0Izj4ME)
Part 2: [URL="http://imgur.com/jxBB87I"]http://imgur.com/jxBB87I


[/URL]

---

### Post by dino99 on 2015-02-24
is that crash also happen when you are not playing Dota 2 ?
Logs might help you find possible reason(s)

---

### Post by Hastur_The_Unspeak on 2015-02-24
The crash only happens with Dota 2. As for crash logs, I can't find any. I've both checked in .steam and in the actual /var/ directory to no avail.

---

### Post by dino99 on 2015-02-24
so Dota 2 have to be blamed. What Dota forum says ?

---

### Post by Hastur_The_Unspeak on 2015-02-24
That not the underlying issue. Plenty of people running the same distro I am have no similar issues or experiences. There is no dedicated Dota 2 forum, but the steam forum has been inconclusive.

---

### Post by nadarockyraccoon on 2015-02-25
Run a memtest off the boot menu of a live install disk. Kernel panic=memory to cpu miscommunication.

---

### Post by Hastur_The_Unspeak on 2015-02-25
> **nadarockyraccoon said:**
> Run a memtest off the boot menu of a live install disk. Kernel panic=memory to cpu miscommunication.

Alright that's the best advice I've gotten thus far. I'm going to run it while I work out, then come back and see what horrible problems it spits back at me. I have a baaaad feeling it's corrupted RAM, and then the RAM effed my hard drive up in turn. Thanks for the advice, I did not think about doing this!

---

### Post by Hastur_The_Unspeak on 2015-02-25
Alright so I finished the memtest, and after 2 passes it found no errors. So I honestly have no idea where to go from here.....

---

### Post by nadarockyraccoon on 2015-02-26
By two passes do you mean it ran two test or did it hit 100% complete for all test? I have found that if you have two two gig sticks it will test the primary first and then the secondary, this can take several hours. Maybe a faster way to test it would be pulling all the ram but one stick, boot, play and see what happens. If every thing works then try the next one on it's own. Usually with just one stick you'll find out on boot if it is bad.

The only reason I ask is because I have run into kernel panics quite a few times(refurb old comps) and it is almost always the ram. It wasn't until computers started coming with large quanities of ram that linux would even install without error with bad ram. The first time what you are experiencing happened to me it threw me through a loop because linux installed and the first half of memtest came back fine. It wasn't until I tried pulling the ram and testing each stick individually that it became apparent what was wrong. 

Worse to worse it shouldn't have damaged the hard drive, maybe just wrote some corrupt data, and simply writing over it should fix it.

---

### Post by Hastur_The_Unspeak on 2015-02-28
Yea, I only have one ram stick. So what you're saying is to run more than two passes? Does the version of memtest matter either? Because I am using an outdated iso version. And when you say "write over it, do you mean get a whole new operating system? Also, could this have caused HDD damage? Because sometimes the HDD will make some whining or clicking noises.

---

### Post by bookrt on 2015-02-28
Isn't swap device typically your HDD/SDD? Try doing a SMART test and see if there are some corrupted sectors. This may be a symptom of your HDD beginning to fail.

---

### Post by Hastur_The_Unspeak on 2015-03-01
Alright, so I ran the test 3 diffrent times, and all of them came up without an error. [http://postimg.org/image/jgjrqaz09](http://postimg.org/image/jgjrqaz09) 

Another kernal panic occoured last night, and it mentioned my motherboard. Could this possibly be a motherboard error?

---

### Post by Hastur_The_Unspeak on 2015-03-01
> **bookrt said:**
> Isn't swap device typically your HDD/SDD? Try doing a SMART test and see if there are some corrupted sectors. This may be a symptom of your HDD beginning to fail.

Going to try that right now

---

### Post by Hastur_The_Unspeak on 2015-03-01
> **bookrt said:**
> Isn't swap device typically your HDD/SDD? Try doing a SMART test and see if there are some corrupted sectors. This may be a symptom of your HDD beginning to fail.

These are the results of the SMART test. I don't know to make heads or tails of it. Everything is either "old age" or "pre-fail," but the overall disc status is OK? That seems contradictiory to me...
Part 1: [http://imgur.com/0Izj4ME](http://imgur.com/0Izj4ME)
Part 2: [http://imgur.com/jxBB87I](http://imgur.com/jxBB87I)

---

### Post by bookrt on 2015-03-13
The SMART test checks out. "Old age" or "pre fail" just means what a failure would indicate. The "Assessment" column is the key and you are "OK" on all. No bad sectors. 

I would suspect memory (even though it passed the memtest), video card, or graphics driver issue. The fact that this happened after an upgrade and it is only playing games has me leaning to the latter. What are the specs of your CPU and GPU?

See if you can borrow memory from another computer or if you have two sticks use one at a time to rule out bad memory sticks. In the meantime, do a search for your GPU and try updating your drivers.

---

