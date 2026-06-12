---
title: "New install, all 4 browsers crashing"
date: 2017-08-24
forum: General Help
---

### Post by spaceboy909 on 2017-08-24
Hi all,

I'm coming back to Linux after about a 4 year break from it.  I've had plenty of ups and downs and hair pulling times with Linux over the years, but with a brand new Lubuntu 16.04 install on an old system, I feel like I've just been slapped in the face right out of the gate with this problem.

I hope some will be able to help with this.

I have two very old systems that I'm shaping up to give away with Linux on them.  I decided to try Lubuntu 16.04 Alternate first.  It's surprisingly sluggish so I may end up trying some other distros, but if I do go with Lubuntu, I obviously have to get this browser issues sorted first.

My box is an AMD Athlon XP @1.2Ghz with 1Gb ram.  I went with the alternate even though it said it was for sub 700Mb ram systems because I wanted speed to be paramount (is that a mistake?  Would 'full' be faster with 1Gb ram?).

The installation went fine, just basic guided.  I then did all the auto updates through the pkg manager.  Then I started using Firefox but it began crashing on me right away with just 1 to 3 tabs open, and on simple pages such as google and Ubuntu wiki.

Over and over, it's guaranteed to crash, but the length of time varies before it crashes, although it's never very long.  

I decided to install Chromium and try that, but it crashes too.  However, Chromium never even fully loads.  I see it pop in the task manager, it gets to about 40Mb or so and then just dies.

I then installed Midora and Qupzilla and both are loading and crashing the same as FF.

So, since it's affecting all of them, I imagine that will make it an easier fix.  I found a thread from 6 months ago where someone stopped the FF crashes by switching desktop themes.  I tried 1 new theme, but it's still crashing.  I'll run through the rest of them later today.

Any help is appreciated!

---

### Post by bcschmerker on 2017-08-24
**I suspect a hardware problem.**  I'm running the Hot Rod gPC™ with a backup CPU:  An Advanced Micro Devices® Athlon64® 3500+ (Socket AM2), needed to fill in for an X2 5600+ whose memory manager broke in service.  In MemTest86+®, one clue to a failing memory manager is consistent bad paragraphs of main memory even after changing out modules - two modules in the same slot shown as having the same address(es) bad would be the tipoff.

---

### Post by spaceboy909 on 2017-08-25
> **bcschmerker said:**
> **I suspect a hardware problem.**  I'm running the Hot Rod gPC™ with a backup CPU:  An Advanced Micro Devices® Athlon64® 3500+ (Socket AM2), needed to fill in for an X2 5600+ whose memory manager broke in service.  In MemTest86+®, one clue to a failing memory manager is consistent bad paragraphs of main memory even after changing out modules - two modules in the same slot shown as having the same address(es) bad would be the tipoff.
Hmm, well, there were no problems running Win XP.  I guess I can't rule it out, though.  I can run a memtest all night and see what happens, but I'm also going to be installing 2 or 3 more distros to see which one is fastest, and I'll do thorough browser testing in each one.

---

### Post by spaceboy909 on 2017-08-25
Oh, I forgot to mention this.  I got very lucky coming across this post.  This person says that he discovered a problem with lack of support for SSE2 instructions:

From (comments):  [https://www.linux.com/news/best-lightweight-linux-distros-2017](https://www.linux.com/news/best-lightweight-linux-distros-2017)

> [COLOR=#4A4A4A][FONT=OpenSans]The problem is not only lightness, but some tricky issues as CPU internal instructions, applications language and code (large documents and internet home-pages) that require more than just the clock-cycles of a processor. **I recently had problems with a quite fast Athlon XP processor that could handle many 32 bits distros, but not open Firefox or Chromium due to the lack of SSE2 instructions**[/FONT][/COLOR]

---

