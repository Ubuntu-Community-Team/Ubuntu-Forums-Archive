---
title: "Heavy disk IO on all machines"
date: 2020-06-11
forum: General Help
---

### Post by mrhavercamp on 2020-06-11
I have 3 laptops and 1 desktop computer which seem to display the same issue, they all become randomly unresponsive during general usage.

I have two T series Lenovo Thinkpads and an X1 Carbon. All machines have 8 Gb of RAM and SSDs. I also have a generic desktop computer with two drives (the main one SSD and /home on a 1TB mechanical disk) with 16Gb of RAM.

All machines are running some modern version of Ubuntu (a mix of 19.10 and 20.04) although this problem has been plaguing all machines since around 18.x.

One of the thinkpad T-series will, out of nowhere, will start heavy disk writing (I think), with the disk led lit up solidly. Once this happens, the machine never recovers and it needs to be hard reset. The other thinkpad does the same but does recover after about 30 seconds to a minute. The X1 Carbon appears to just lock up. I thought it might be the CPU but it does recover before freezing up again. By freezing up, I mean there is no keyboard or mouse input and I can't Ctrl+Alt+F* to a terminal. Again, a hard reset is required as the machine will just completely lock up (although difficult to tell if it is the disk as there is no IO led). Another thing to note, the fan goes into overdrive.

The desktop's 1TB disk experiences the same thing; heavy disk IO all of a sudden. With enough time it will recover, maybe 5+ minutes.

As this seems to be a problem for me across the board, my feeling is there is probably a configuration change I can make.

What are the steps to diagnose this issue and does it, from first impressions, seem to be some kind of misconfigured disk management?

I run Ubuntu exclusively so don't really have anything to compare against (e.g. other distros/Windows).

---

### Post by CatKiller on 2020-06-11
It sounds most like an Out Of Memory situation. You can monitor your RAM usage with something like htop.

---

### Post by dragonfly41 on 2020-06-11
I was curious and searched "[ubuntu cryptojacking]("https://bitsonline.com/cryptojacking-discovered-ubuntu-store/")" ... you can inspect snap usage by installing Stacer dashboard or just through command line.

[P.S.] I have a Lynis auditing tool in my 18.04 (under System Tools) which is handy to scan for vulnerabilities.

---

### Post by mrhavercamp on 2020-06-11
> **CatKiller said:**
> It sounds most like an Out Of Memory situation. You can monitor your RAM usage with something like htop.

Thanks for the recommendation. Good point on out of memory. Does this mean I need to increase swap space or will that cause more disk swapping? What would be the ideal size these days?

I have used top a few times to check whether memory is running out. I find Firefox consumes a huge amount of memory over time.

---

### Post by dino99 on 2020-06-11
First you need to know which app(s)/process(es) is/are building such hard IOs by using tool like System-monitor (gnome) or htop.
Then are you using some 'external' source(s) which can be untrusted ?
Be sure to use cleaned systems: run tool like bleachbit (as root, carely opt-in options) to get rid of old settings, broken things like links, unneeded/deprecated versions, ...
And indeed avoid mixing packages/apps coming from different releases to avoid conflicts/races

As your ram amount  is well enough for the usual needs, at first glance that point to an other culprit; except if :
- you are using some huge app
- in case of non standard system install (nowadays swap is dynamic inside the system)
- the storage (ssd/hdd) become too full (at least let 15 % free space to let the system working)

---

### Post by mrhavercamp on 2020-06-16
Thanks for the suggestions. I installed htop and I've been monitoring the x1 carbon in particular over the past couple of days.

Indeed, htop reported I was almost out of memory (swap was fully and I had a about 300Mb left) before I launched another process and I got a lock up. I left the machine running for about 45 minutes to see if it would recover (I.e. maybe an app would crash and memory would be freed up) but it never happened and I needed to hard reset.

Today I got a lock up but without warning. I had htop running; still lots of memory, cpu not working that hard then suddenly a lock up. Again needed to hard reset. 

I'm wondering if I've got a couple of different problems going on here. What would be the next step(s) to diagnosing this problem?

---

### Post by Impavidus on 2020-06-16
It's a bit uncommon for a computer with 8GB of memory to use any swap, let alone run out of it. Use top or htop to find out which application uses more memory than it should. With things like shared memory and cache it's not always easy to analyse what is used where, but you can probably get an idea.

When an application suddenly uses a lot of memory, the system may freeze even before htop reports it.

---

### Post by mrhavercamp on 2020-06-18
Thanks for the reply and suggestion. So the big memory hog is Firefox. It can eat up a lot of memory on its own. However, I'm not sure how much memory Firefox should be using. It's also worth noting I'm not running many tabs, maybe 8 or 10 at any one time.

---

### Post by Impavidus on 2020-06-18
Web browsers are notorious for that. Webpage designers consider web browsers to be a kind of virtual machine on which they can run whatever they want, using all the resources of the visitor. I can't say the usability of websites has increased much over the past 20 years.

I rarely open more than 5 tabs at a time (currently 2). It matters what's on those webpages. Ubuntuforums and Wikipedia are fine, commercial websites are worse. A script blocker may help, but it may make some websites completely unusable.

---

