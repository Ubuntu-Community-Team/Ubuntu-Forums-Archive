---
title: "Linux's ability to multi-process vs Windows' ability"
date: 2007-01-17
forum: General Help
---

### Post by Ted_Smith on 2007-01-17
I have read somewhere recently that one of the significant advantages of Linux over Windows is it's ability to multi-process running apps with greater stability and efficiency. 

When discussing this with a friend of mine he said that that was certainly the case prior to Win 2000 and Win XP, but since then, and with the invent of Vista he claims there's no real difference. But I did not know enough about it to further clarify. 

I wonder if anyone could either point me in the direction of an in-depth report\web page etc on this issue, and if not, whether anyone could shed a little more light as to why and how Linux is better than Windows in this regard and whether what my friend says is substantiated. 

Thanks

Ted

---

### Post by floke on 2007-01-17
Maybe your friend should point you in the direction of anything which substantiates his point.
Perhaps it resides in the Get the Facts website?

---

### Post by foob on 2007-01-17
Anything stated concerning the debates in this area should be approached with great care. Sometimes information is tainted and sometimes egoism gets in the way of logic. Then again, sometimes we can really rely on those that are well informed. My advice is for you to do a little investigating on your own and make sure the sources are reliable. :)

---

### Post by floke on 2007-01-17
Of course Windows also forces you to perform more tasks, such as...

Install software applications once OS has been installed
Reboot (x ??)
Install anti-virus software
Update
(reboot)
Install anti-adware / spyware etc.
Update
(reboot)
Remembering to update each regularly, and perform once weekly scans....

Is this what MS mean by making you more productive? If they interpret this as 'getting you to do more jobs' then they might have a point :mrgreen:

---

### Post by kidders on 2007-01-17
[COLOR="DarkOrange"]**Edit:** foob makes a good point ... I hope this post doesn't overstep the boundaries![/COLOR]

Hi there,

There is some (relatively superficial) detail on memory management improvements with Vista on the MS website, although Linux and Windows RAM & virtual memory management techniques remain fundamentally different.

> I have read somewhere recently that one of the significant advantages of Linux over Windows is it's ability to multi-process running apps with greater stability and efficiency.

Imo, stability and efficiency are often two opposing forces in memory management. Simplistically speaking, you *could* describe the MS model as one that frequently sacrifices stability to achieve efficiencies that wind up putting your entire system's usability at the mercy of the programmers of the individual apps you are running. On the other hand, the Linux kernel seems to accept the fact that certain kinds of allocation techniques are fundamentally unwise, condemning itself to a certain degree of _*in*_efficiency right from the start.

Theoretical arguments aside, you don't have to be an expert to see the pay-off though. Linux boxes are perfectly efficient, and still manage to stay up for months on end, unaffected by misbehaving applications, without having to be constantly restarted.

Most of the improvements Microsoft claims it's built into Vista seem targeted at increasing speed and uncapping silly limits on when and how memory is allocated for specific purposes (and how large such allocation operations can be), rather than revising flawed management techniques. Apparently, using the traditional Microsoft memory model, Vista can now make effective use of more memory, faster than ever before ... leading to the natural assumption that Windows systems will now misbehave sooner, and on a larger scale than ever.

The last thing I want to do is spark a religious war :-? but perhaps I could say this: If you come from a school of thought that believes the Linux memory management model is superior to that of Windows XP, then Vista seems, on paper, to offer you absolutely nothing new.

There's absolutely truckloads of documentation on the web comparing and contrasting various approaches to memory management in multitasking environments ... although much of it is of a very low standard imo. If you're interested, have a read. I've always believed that the *real* distinction lies in the practical day-to-day experience of an OS, though.

---

### Post by insane_alien on 2007-01-17
*deleted* turned out i misunderstood the origional question and this post is irrelevant.

---

### Post by Patrick-Ruff on 2007-01-17
windows vista's memory management seems logical to me.  RAM has a 5NS latency on average, whereas the hard drive has a 1-5MS latency . . . I mean think about it, loading everything to ram and then unallocating it as the computer demands it is a pretty constructive way of doing things (so long as the system doesn't screw up.)

the way I see it, vista has better memory management at the moment.

---

### Post by kidders on 2007-01-17
> **Patrick-Ruff said:**
> RAM has a 5NS latency on average, whereas the hard drive has a 1-5MS latency . . . I mean think about it, loading everything to ram and then unallocating it as the computer demands it is a pretty constructive way of doing things (so long as the system doesn't screw up.)

the way I see it, vista has better memory management at the moment.
Yep :-) Naturally, working from RAM where possible is preferable, but you can't expect to fit everything you need in there, on a heavily-loaded multitasking environment. I imagine the o/p presumes a fairly heavy amount of paging.

---

### Post by lswb on 2007-01-17
There is more to multitasking than memory management. I use Linux on my personal system but have to use XP at work. It is not unusual for certain IO tasks in XP to freeze the system, including other running but non-related programs, until they complete. I've not encountered this phenomena in Linux (yet?)

---

### Post by majoridiot on 2007-01-17
> **kidders said:**
> rather than revising flawed management techniques. Apparently, using the traditional Microsoft memory model, Vista can now make effective use of more memory, faster than ever before ... leading to the natural assumption that Windows systems will now misbehave sooner, and on a larger scale than ever.

that is, without a doubt, the funniest dead-on characterization of M$ i've seen in a long time. :D

i run XP at work and dapper at home; both are similar computers.  my work system requires
rebooting at minimum once a day, unless i am "updating", which usually requires "updating
the updates" ad-nauseum- with reboots each time.  my home system is taxed easily 50% more
and might get rebooted once a week.  the HD in the work box works almost constantly once i
get a few windows and apps open, compared to dapper, which amazes me how little HD axx
is needed, even with a dozen or more windows open on different desktops and mythtv
streaming happily along.

i'm sure there are all kinds of benchmarks, diagrams and dissertations about ms/vista vs. 
linux. i completely agree with kidders that the real distinction lies in the practical 
day-to-day experience of an OS... and my personal experience is that for speed/stability, my
ubuntu box has it in spades over my XP box.

---

