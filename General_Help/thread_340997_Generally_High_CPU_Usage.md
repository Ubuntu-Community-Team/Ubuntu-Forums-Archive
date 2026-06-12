---
title: "Generally High CPU Usage"
date: 2007-01-18
forum: General Help
---

### Post by k0ma on 2007-01-18
I'm running Ubuntu 6.10 on a 2.8 GHz Pentium 4 with 768MB RAM, and for some reason Ubuntu uses a lot of CPU to do just about anything, from opening programs, to running programs, to simply just scrolling through web pages or text files.

I'm not sure it's a graphics issue, as I'm running a 64MB ATI Radeon 7500 with the "ati" driver, and Beryl is running fine (for the most part). It's not being caused by Beryl, as far as I know, because even if I turn Beryl off, I still experience this CPU issue.

My CPU temp stays hits above 60 degrees Celcius constantly, causing my laptop's fans to kick into high gear. 60 degrees might not sound like much, but I don't have this problem at all while booted into Windows XP, so I'm wondering if there's something I'm doing wrong here?

---

### Post by highneko on 2007-01-18
You seem to know what you're doing, but maybe there could be something else causing this high cpu usage? What does top output?

---

### Post by k0ma on 2007-01-18
> **highneko said:**
> You seem to know what you're doing, but maybe there could be something else causing this high cpu usage? What does top output?

It seems Xorg is what's causing the CPU issue. When Firefox loads pages, Xorg easily uses over 50% CPU while FF uses around 20%.

Why is Xorg sucking up so much CPU?

---

### Post by PrinceArithon on 2007-01-18
From what I have read about Ubuntu, it seems that it alots more usage to things you use more.  So if you often run a certain media player for music, then it will give it a lot of cpu usage.  Since you use xorg all the time, it will give a lot of cpu usage to it.  It's supposed to make the machine more efficient or something like that.  So don't worry things are running as they should, or at least from what I read.

---

### Post by k0ma on 2007-01-18
> **PrinceArithon said:**
> From what I have read about Ubuntu, it seems that it alots more usage to things you use more.  So if you often run a certain media player for music, then it will give it a lot of cpu usage.  Since you use xorg all the time, it will give a lot of cpu usage to it.  It's supposed to make the machine more efficient or something like that.  So don't worry things are running as they should, or at least from what I read.

I doubt things are running as they should, since Xorg's eating all my CPU constantly, and it causes slowdowns when using Firefox and other heavy apps.

Things I do in Ubuntu are noticeably slower than when I do the same things in Windows, and I'm pretty sure it's a Xorg issue now. But what it is, I have no idea.

It really sucks because after more than 10 or 15 minutes of this, it becomes pretty unusable.

---

### Post by tommcd on 2007-01-18
> **PrinceArithon said:**
> From what I have read about Ubuntu, it seems that it alots more usage to things you use more.  So if you often run a certain media player for music, then it will give it a lot of cpu usage.  Since you use xorg all the time, it will give a lot of cpu usage to it.  It's supposed to make the machine more efficient or something like that.  So don't worry things are running as they should, or at least from what I read.

I think this applies to RAM and not CPU usage.
Koma, was it like this before you installed Beryl? If not I would uninstall Beryl as a first step in troubleshooting.
Do a search for 'high cpu' as title of thread in the forums. There can be many causes (some reported with Beryl) and many possible solutions. Are you sure your ATI driver is properly installed?

---

