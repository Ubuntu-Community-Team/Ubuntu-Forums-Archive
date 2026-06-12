---
title: "multi-screen remote desktop support"
date: 2020-03-19
forum: General Help
---

### Post by edstevens on 2020-03-19
This is both a hardware and software question.
I have a System76 Gazelle running Ubuntu 16.04 LTS.  Purchased a little over two years ago.
I have installed reminna to give remote desktop to my workstation at the office. That workstation runs Windows 10 Pro, with dual monitors.  Of course, reminna only supports one monitor, so things feel rather cramped when working remotely.

So the question is, what -- hardware and software -- do I need to do to support dual-monitor remote desktop?

1 - hardware - obviously I'd want to purchase at least 1 external monitor. Preferably two, on some sort of docking station with the laptop lid/monitor closed.  Recommendations on docking station or other means of attaching the monitors?

2 - software - since reminna  only supports 1 monitor, what would I need to start using to support multiple monitors?

---

### Post by TheFu on 2020-03-19
[https://wiki.x2go.org/doku.php/doc:usage:multi-display](https://wiki.x2go.org/doku.php/doc:usage:multi-display) supports multi-display setups.

But I think Windows could be a problem.

---

### Post by edstevens on 2020-03-20
> **TheFu said:**
> [https://wiki.x2go.org/doku.php/doc:usage:multi-display](https://wiki.x2go.org/doku.php/doc:usage:multi-display) supports multi-display setups.

But I think Windows could be a problem.

Thanks for the link.
And it does look like Windows (as the target) will be the  problem.  I'm still seeing that even with Win10  (I had already run into this a few years ago with Win7) that Pro edition will not support it - you have to upgrade to Premium.  Unfortunately, that machine is my company workstation, so I have no control over the OS installation. 

So it looks like I'm still stuck with my current arrangement.  :-(  

Thanks again for responding.

---

### Post by TheFu on 2020-03-20
Yep.  Windows is usually the problem.

There might be some other options.  i simply don't know about them.  Nobody is an expert on everything.  Does Windows support something like Ximera?

[https://coderwall.com/p/b982hw/linux-remote-desktop-multiple-monitor-support](https://coderwall.com/p/b982hw/linux-remote-desktop-multiple-monitor-support)
says to use 
```
$ xfreerdp /multimon /u: <username> /v:<remote windows machine name>
```

---

