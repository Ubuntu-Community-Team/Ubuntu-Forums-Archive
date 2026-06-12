---
title: "Firefox slow/freezes"
date: 2007-04-21
forum: General Help
---

### Post by CorranH on 2007-04-21
I've just recently installed  Ubuntu 6.10 and noticed Firefox was running slowly, occasionally freezing for short periods of time (about a minute or so), and generally being annoying.

I installed all the updates for Ubuntu and Firefox (except 7.04), and the problem persists. Does anyone know how to stop this behavior?

Thanks,

Corran

---

### Post by K.Mandla on 2007-04-21
What kind of connection to the Internet do you use? Does anything else stutter or pause at all? What kind of computer are you using?

Is there any kind of message or error reported in your dmesg output? Enter "dmesg" in a terminal and see if there is anything there that helps.

Sometimes errors at the kernel level are visible in dmesg, or inside the kernel logs in the /var/log/ folder.

---

### Post by CorranH on 2007-04-21
> **K.Mandla said:**
> What kind of connection to the Internet do you use? Does anything else stutter or pause at all? What kind of computer are you using?

Is there any kind of message or error reported in your dmesg output? Enter "dmesg" in a terminal and see if there is anything there that helps.

Sometimes errors at the kernel level are visible in dmesg, or inside the kernel logs in the /var/log/ folder.

I connect to the Internet through a network, but it is a dial-up connection. I haven't had any other programs stutter or pause. Though the package manager has had problems with failing packages, don't know if that could be related. 

My computer is a Cisnet 2.8GHz Celeron 512MB RAM. It's a little over a year old. Don't know more than that off the top of my head, and I don't know where the documentation is right now.

I didn't notice anything in dmesg, but I wouldn't really know what to look for.

One other thing I remembered. This problem seems to occur more often if other people are accessing the Internet through the network, or if I'm downloading packages/updates

---

### Post by K.Mandla on 2007-04-22
I'd hate to write it off as net congestion, but if you don't see anything suspicious in dmesg or in your kernel logs, it might just be that it's hanging waiting for its next burst of information. Is there any way you can troubleshoot it by moving to a new location or accessing the Internet from a different network?

---

### Post by CorranH on 2007-04-22
That's what I thought it could be too. (Stupid dial-up). I don't really have the ability to attach it to another network any time soon.

Thanks for all your help.

Corran

---

