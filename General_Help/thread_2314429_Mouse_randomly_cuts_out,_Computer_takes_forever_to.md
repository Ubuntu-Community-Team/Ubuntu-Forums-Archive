---
title: "Mouse randomly cuts out, Computer takes forever to shutdown"
date: 2016-02-21
forum: General Help
---

### Post by junkhere on 2016-02-21
What it says in the title. My mouse suddenly cuts off when I'm using the computer and it doesn't even work if I swap to a different one. When I try to shut the computer off, it just stays on the shutdown screen with the ubuntu logo forever. I checked the disk health and it says disk is ok. I ran a SMART self test and it was the same result.

This is all just before uni is supposed to start. Would the quickest way to try and resolve this just be to reinstall ubuntu? or are there some other steps I can take to  try and resolve the problem that aren't too time consuming first?

---

### Post by claracc on 2016-02-21
It would be useful in order to help to know more about your hardware and software:

Particularly, what is your CPU, RAM and graphics videocard?, what is the ubuntu release you are running?

In this link: [http://www.cyberciti.biz/faq/linux-tell-which-graphics-vga-card-installed/](http://www.cyberciti.biz/faq/linux-tell-which-graphics-vga-card-installed/) you can find different methods to gather information about your hardware

---

### Post by junkhere on 2016-02-21
Oh right sorry:  

CPU: 2xintell celeron  CPU B830 @ 1.80GHZ  

RAM: was this what you needed? memory total: 3836 used: 1785 free: 2081 shared: 188 buffers: 102  

Graphics card: Intel 2nd generation core processor family integrated graphics controller  

Release: 64 bit Ubuntu 14.04 LTS

---

### Post by mörgæs on 2016-02-21
> **junkhere said:**
> Would the quickest way to try and resolve this just be to reinstall ubuntu?

If you don't have anything of value on it then yes, I would suggest that. Since it takes only 20 minutes and it has helped similar cases there is no point in not trying. Go for a 64 bit 15.10.

---

### Post by coldraven on 2016-02-21
You don't mention which version of Ubuntu you are using. I'm on 15.10 and a kernel update stopped me from being able to shutdown or suspend. To fix this I reverted to an earlier kernel and now everything works as normal.

---

### Post by junkhere on 2016-02-21
I corrected that: It's ubuntu 14.04. I was pretty stressed out so I forgot initially.

> **mörgæs said:**
> If you don't have anything of value on it then  yes, I would suggest that. Since it takes only 20 minutes and it has  helped similar cases there is no point in not trying. Go for a 64 bit  15.10.

It's a very big download, that's the main thing that's stopping me going higher. Is 15.10 pretty stable and worth the upgrade atm?

---

### Post by mörgæs on 2016-02-21
Yes, 15.10 is highly stable, else I would have warned you. It has the most complete hardware support of all buntus.

You can also see how it all behaves in a live boot before deciding.

---

### Post by junkhere on 2016-02-23
I reinstalled ubuntu 14.04 because I have the usb for that and I didn't want to do too big a download until my quota resets. It worked fine for a while and now I've got the same issue.   Might try reverting to an older kernel like coldraven did but it looks a tad tricky for someone with my lack of knowledge. I don't want to mess things up even more.

---

### Post by junkhere on 2016-02-24
Trying to just upgrade to 15.10 now. I didn't want to muck around with the kernel stuff because I read you can mess things up if you delete the wrong thing. Now the update looks permanently stuck on  "preconfiguring packages ... " with no way to safely cancel. Unless it's supposed to be stuck there for a very *very* long time with no indication of progress? It's been somewhere between 30 minutes to an hour. Not sure exactly how long.

---

### Post by mörgæs on 2016-02-24
Never upgrade a Buntu, always do a clean install.
If download size is a problem why don't you fetch the 15.10 ISO somewhere else using the USB stick?

---

### Post by junkhere on 2016-02-24
So from someone else who has ubuntu 15? I'm not sure I know anyone but I could look into it. At this point I'm probably just going to do whatever it takes to fix the problem. if upgrading doesn't fix it I'm going to assume its some kind of hardware issue.    I guess I should just kill the update then.

---

### Post by mörgæs on 2016-02-24
I meant that you can download the 15.10 ISO on any computer on the net and bring it home. Buntu, Windows, Mac, OS/2, BSD ...

---

### Post by junkhere on 2016-02-24
installed ubuntu 15.10 successfully. Problem hasn't been fixed. The mouse/usb pot is more and more frequently cutting out, and from experience it's just going to stop working eventually and I'll have the same issues shutting down. I performed the disk check it lets you do from the menu that comes up when you use a usb to install a new OS and it just said something along the lines of "2 errors"  nothing else.  Maybe there's still something in the automatic updates that's causing the issue? I how come I can still boot from a usb and install an entire OS? The usb port was obviously working fine for that length of time but when I log in I have these issues after I use the mouse for a while. I'm a bit stumped for what to do from here.

---

### Post by mörgæs on 2016-02-25
Please post in detail all error messages that you see.

---

### Post by junkhere on 2016-02-25
From memory there weren't any other details apart from the fact that there were 2 errors. Maybe there was some other way to bring up more details but that software was from the bootable usb and I've already completely installed ubtunu 15.

I know there's other software for checking the health of the hard drive and other components, but I've come across a different avenue: I phoned a place that fixes computers to see if it was worth sending my laptop to them. Apparently with my computer at least, the USB port is closely connected to other components. So any weirdness/shorting out there could explain problems in other areas. It could be quite expensive to fix if it's a hardware issue.

What I've done is unplugged my old headphones and replaced the old mouse (both in bad condition) with a new one and connected it to a different port than usual. So far I haven't had any major issues since then. That could just be because I did a clean install of ubuntu and it may become a problem again, but if that happens I'm just going to roll with it and back things up frequently because everything else has been fine apart from the issues I've mentioned. The touch pad worked fine just not the usb port and therefore any mouse connected to it. As inconvenient as it is, only having the touch pad doesn't stop me from being able to do the work I need to do.

It's worth mentioning that the issues with the usb ports not working and the computer not shutting down didn't happen unless I moved the mouse for a fairly short period of time. I suspect it's a hardware issue somewhere along the line. I might co[FONT=arial][SIZE=2]m[/SIZE]e b[/FONT]ack here in a couple of days and mark this as solved if there aren't any other issues, otherwise I'll look into getting repairs or a new laptop.

Thanks for the help mörgæs and everyone else.

---

