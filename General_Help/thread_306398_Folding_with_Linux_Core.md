---
title: "Folding with Linux Core"
date: 2006-11-24
forum: General Help
---

### Post by Scottla on 2006-11-24
Hi, Newbie here.  Thanks for any help you can provide.

I'm an avid folder and recently built a new PC to, in part, learn the Ubuntu environment.  Starting to become a big fan, but that's not the purpose of the post.

Mod: if this belongs somewhere else, please move accordingly.  I did not see a F@H forum here.

So, I just cobbled together an AMD 64 4000+ machine out of spare parts to set up as a folder. I put Ubuntu on it, put the FAH504-Linux core on it, and let it run.

Well, I am 3 days in and it's crunched a whopping 10% of the first WU it's working on. In the same time, my 3700+ has delivered 1.5 WUs.  Even tho the machine pulled down a massive WU, the FAH database says the average completion time for it is 10.5 days.  At this rate, it's going to take over a month!

My machine is OC'd to almost 2.8ghz, so I know it's not the PC.  I am unfamiliar with the Linux core; I'm assuming at this point I've set the wrong flags or not done something I need to do to make it fold efficiently.

Any help from experienced Ubuntu/Linux folders appreciated.

---

### Post by dcstar on 2006-11-24
> **Scottla said:**
> Hi, Newbie here.  Thanks for any help you can provide.

I'm an avid folder and recently built a new PC to, in part, learn the Ubuntu environment.  Starting to become a big fan, but that's not the purpose of the post.

Mod: if this belongs somewhere else, please move accordingly.  I did not see a F@H forum here.

So, I just cobbled together an AMD 64 4000+ machine out of spare parts to set up as a folder. I put Ubuntu on it, put the FAH504-Linux core on it, and let it run.

Well, I am 3 days in and it's crunched a whopping 10% of the first WU it's working on. In the same time, my 3700+ has delivered 1.5 WUs.  Even tho the machine pulled down a massive WU, the FAH database says the average completion time for it is 10.5 days.  At this rate, it's going to take over a month!

My machine is OC'd to almost 2.8ghz, so I know it's not the PC.  I am unfamiliar with the Linux core; I'm assuming at this point I've set the wrong flags or not done something I need to do to make it fold efficiently.

Any help from experienced Ubuntu/Linux folders appreciated.

What kernel are you using, and what Ubuntu version (32 or 64 bit)?

---

### Post by Scottla on 2006-11-25
The folding core is 5.04 (FAH504-Linux.exe).  I'm not sure about the bit version of Ubuntu.  Didn't know how to tell.  The version is 6.10 *Edgy Eft*.  It says this supports 64-bit for AMD64 processors (which I have), but I never set it to do one or the other.  Just downloaded the ISO image and burned to a disc.

---

### Post by Scottla on 2006-11-25
**Update:** I downloaded the 64-bit core for F@H for kicks and installed it.  Tried running it and it said: "This kernel supports 64-bit...  Your machine is i686."  I assume that means I've got the 32-bit version of Ubuntu?

---

### Post by bollix47 on 2006-11-25
Open a terminal. (Applications - Accessories - Terminal)

Type:

```
uname -a 
```

Copy and paste the output here so we can see exactly which kernel you're using.

---

### Post by Belboz99 on 2006-11-25
Just to clarify, what work unit are you working on?

Also, check top and be sure FAH is using as much of the CPU time as possible (should be 95% or higher).  top is a command-line tool you run from the terminal, just open a terminal, type top, and hit enter. ;)

One other thing to be sure of is that FAH is using the SSE extensions.  Look for "SSE boost OK" near the start of the WU in the folding logs.

Once you get it setup properly, be sure to check out Tech Report's guide on configuring Folding @ Home as a service that launches at boot on Linux:


[http://www.techreport.com/etc/folding/#Linux](http://www.techreport.com/etc/folding/#Linux)

---

### Post by Scottla on 2006-11-25
OK.  Thanks for all the feedback.  Answers to various questions as follows:

CPU Util is 97.5%. I also see "100%" is Sytem Monitor.  The program using it is the FAH core

Kernel = Linux ubuntu-desktop 2.6.17-10 -generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686

Protein = p1487_DPPC-DOPC_CHOL

I looked for the SSE Boost in the sequence and did not see it.  Is turning this on a flag you must type when you launch the .exe?

Thanks for all your help!!

---

### Post by bollix47 on 2006-11-25
Your kernel looks correct to me.

That protein may be the problem.

See [here]("http://forum.folding-community.org/viewtopic.php?t=15978&highlight=p1487dppcdopcchol") for a discussion of that one.

Are you having other problems?  i.e. Does browsing the net seem to be working okay and at an appropriate speed?

---

### Post by Scottla on 2006-11-25
Interesting.  This seems to be a thorny one.

I put the -forceasm flag in place to see if that would aid the situation.  If that accelerates it, I'll let it run and see where I get.  If it breaks at 66% I'll throw a tantrum, then move on to another WU.

Any other thoughts appreciated.

The rest of the machine's performance seems fine.  The only thing I'm to pleased with is the video performance.  I'll put up a separate post about that.

---

### Post by bollix47 on 2006-11-25
If you search for that protein in their forums you will find a number of threads/posts about it.  Since most everything else is working okay I'd quit that one and try for another.

---

### Post by Scottla on 2006-11-25
Adding the -forceasm flag has really helped (at least I think that's it).  The core is producing about 1% of the WU every hour and 30 minutes now.  That's a VAST improvement.  If this pace holds, it will complete the WU in another 5 days or so.  I'll keep you posted.

---

### Post by Scottla on 2006-11-26
ERR!  The WU timed out at 48% complete.  Good news is, I got a new, more manageable WU.  Bad news, of course, is I lost a week's worth of work on a biggie.  Oh well, that's how the protein folds I guess.

---

