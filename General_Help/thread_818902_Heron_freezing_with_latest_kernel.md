---
title: "Heron freezing with latest kernel"
date: 2008-06-04
forum: General Help
---

### Post by bkline on 2008-06-04
I ran update manager today on my main workstation running Ubuntu 8.04, which pulled in a new kernel, 2.6.24-18-generic.  Then when I started up the system it didn't make it a minute before freezing solid: wouldn't accept keyboard or mouse input, couldn't ssh into the box, couldn't get to the console, nothing.  Power cycling to restart (more than once) showed the problem to be very repeatable.  Dropped back to 2.6.24-17-generic and the machine seems to be OK again.  Didn't see anything in launchpad.  Anyone else experiencing this with today's new kernel?

Linux ws 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux

---

### Post by carlolovearianne on 2008-06-04
After updating, I lost my wireless. I reinstalled the driver. It's ok now but did get annoying when one cant even surf or listen to one complete song without the OS freezing on you.

I removed the older kernels in Synaptic. So far so good.

I wonder, why are old kernels kept anyway?

---

### Post by werries on 2008-06-04
older kernels are kept for the specific reason that things break when you upgrade sometimes.

---

### Post by TransitMan on 2008-06-04
Older kernels are kept just in case you get a borked update that makes it impossible to login to your system. It is a safety net of sorts, always having at least one older kernel available in grub so as not to have to resort to drastic measures.

---

### Post by ohiomoto on 2008-06-05
I removed my older Kernels also.  Worked for me.

[http://ubuntuforums.org/showthread.php?t=818241](http://ubuntuforums.org/showthread.php?t=818241)

---

### Post by bkline on 2008-06-05
> **carlolovearianne said:**
> After updating, I lost my wireless. I reinstalled the driver. It's ok now but did get annoying when one cant even surf or listen to one complete song without the OS freezing on you.

I removed the older kernels in Synaptic. So far so good.

I wonder, why are old kernels kept anyway?

Sorry, I'm having trouble making sense of your reply.  I just described an update which hosed my system by installing a broken kernel, which I worked around by dropping back to the previous kernel.

---

### Post by bkline on 2008-06-05
> **ohiomoto said:**
> I removed my older Kernels also.  Worked for me.

[http://ubuntuforums.org/showthread.php?t=818241](http://ubuntuforums.org/showthread.php?t=818241)

I followed that link to the thread in which you described problems you had with the latest kernel for Heron.  One difference between the situation you described and my own experience was that you booted up into a blank desktop, whereas each time I rebooted into 2.6.24-18 my desktop came up intact; the system didn't freeze until after I had done a little work.  Granted, that distinction may just be a question of timing (I was only able to do a few seconds of work - always less than a minute - before things locked up solid).  A much more relevant difference is that you reported that dropping back to the previous kernel made no difference to the symptoms you were experiencing, whereas in my case that seemed to have stopped the failures (the system was been working without problems for over 10 hours).  You said yourself that you don't understand why removing the older kernel images could have solved the problem, and I agree that it's hard to see how just having the bytes for those older kernels sitting in the file system could possibly cause the behavior you described.  I would be extremely interested in anything further you learn to corroborate the theory.

Getting back to the original question: has anyone else experienced what I am seeing: 2.6.24-18 renders Ubuntu unasable, and reverting to 2.6.24-17 works just fine?

---

### Post by christianxxx on 2008-06-05
I was on the brink of updating, but decied to wait a little. 
How do we know if it's safe to upload?

---

### Post by bkline on 2008-06-05
> **christianxxx said:**
> I was on the brink of updating, but decied to wait a little. 
How do we know if it's safe to upload?

You could wait for the next kernel release and then see if postings in the forums confirm that the problems were solved.  Or you could track any bug reports that arise out of the behavior we're running into.  I was planning to file a report myself after testing the waters here to see if anyone else had been bitten.

---

### Post by wkulecz on 2008-06-05
No issues with 2.6.24-18-rt here.  In fact I was getting random lockups if multiple users were active on the system via "fast user switcher" with 2.6.24-16 and 2.6.24-16-rt.

Something about the time of 2.6.24-17 made the problem go away, been lots of updates to lots of things so can't specifically credit/blame a particular kernel.

--wally.

---

### Post by ggtsu on 2008-06-05
I've encountered the same issues with the latest kernel upgrade. I can only use my laptop for a few minutes until the screen blanks white, or just looks all corrupted and locks hard. I would love to see if the old kernel works, but as of the last lockup my computer won't even boot anymore. Insert angry smiley here...

---

### Post by bkline on 2008-06-05
> **bkline said:**
> You could wait for the next kernel release and then see if postings in the forums confirm that the problems were solved.  Or you could track any bug reports that arise out of the behavior we're running into.  I was planning to file a report myself after testing the waters here to see if anyone else had been bitten.

I filed a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/237612").

---

### Post by ohiomoto on 2008-06-05
> **bkline said:**
> I followed that link to the thread in which you described problems you had with the latest kernel for Heron.  One difference between the situation you described and my own experience was that you booted up into a blank desktop... Sorry for any confusion, but my system did in fact boot "properly".  Once booted, I noticed all sorts of problems.  The blank screen I experienced was while attempting to shutdown or reboot the system.  


Since removing the old kernels my system has been working perfectly.  I still don't know why.  Like I said, I didn't have much to loose.  None of my Kernels were working and I didn't feel like spending all day typing commands (that I hardly understand) in the terminal, so I figured I'd take a chance.  Seems to me that it's possible the new kernel is fine by itself, but doesn't play well with others.  I know, I'm killing you with my technical jargon here!  

I am still interested in the explanation as to why my system is working.  I've taken a few linux administration courses and all of this is still "out there" to me.  

Anyway, good luck with your problem.

---

### Post by ggtsu on 2008-06-05
Just to update, I'm not sure my problem is related to the kernel anymore. I think my laptop just died.

---

### Post by carlolovearianne on 2008-06-05
> **bkline said:**
> Sorry, I'm having trouble making sense of your reply.  I just described an update which hosed my system by installing a broken kernel, which I worked around by dropping back to the previous kernel.

Sorry for the confusion as well. What I meant is that I encountered problems as well after updating.

1. My wireless ceased to work (wired connection is no longer an option in Network Manager) so I had to re-download and re-install the Atheros driver.

2. My system also locks up after the kernel update so what I did was I removed libflashsupport and the older kernels.

The workaround in #2 seems to be working well cause its been almost a day since I did that and I haven't had one system freeze since.

---

### Post by Ameneon on 2008-06-05
> **bkline said:**
> <snippage>

Getting back to the original question: has anyone else experienced what I am seeing: 2.6.24-18 renders Ubuntu unasable, and reverting to 2.6.24-17 works just fine?

Not quite, however when going from .16 to .17 (and further on to .18 ) the system would lag/freeze for a second or so every few seconds, every 15-25 seconds or so. Very distinct and happening consistently on both .17 and .18, while system works and for all I can tell functions perfectly well when booting the .16 kernel.

So I for one am glad the old kernels are kept, I don't know what I'll do the day a forced update come and I no longer can use the .16 kernel if the problem is still there. System is not practically usable on .17 or .18

Not answering your question but something along the same tangent at least.

---

### Post by bkline on 2008-06-10
I rashly did some experimenting to help with the process of diagnosing the problems with the latest kernel, which resulted in the inability to boot this machine with **any** of the installed kernels.  Ended up re-installing 8.04, and I plan to stick with 2.6.24-16 until the problems with the later kernels have been resolved.  For further details see this [related thread]("http://ubuntuforums.org/showthread.php?t=818241").

Cheers,
Bob

---

