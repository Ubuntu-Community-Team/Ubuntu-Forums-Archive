---
title: "External Monitor Causing 100% CPU Usage"
date: 2014-08-18
forum: General Help
---

### Post by eldavar on 2014-08-18
Good morning. Hopefully someone can explain what's going on here. I've got Lubuntu running on an Acer Aspire D270. Everything runs fine, actually smoother and faster than I expected for this little laptop with only 1 gig of ram. 

Here's the situation: Since the screen on this laptop is pretty small for regular use, when I'm home I connect to an external monitor. If I connect the monitor **after** the laptop is already turned on, everything works perfectly with no issues. However, if I power down the laptop and leave the monitor connected, the next time I turn on the laptop the CPU usage is at 100%. The load constantly shifts from one processor to the next, but always at 100%. 

Here's a screenshot:
[IMG]http://goo.gl/w9ASYj[/IMG]

I've discovered that the process causing the load is pcmanfm, which makes no sense to me because it's the file browser. It's listed at the top of the processes list, and always says 25% CPU usage. I've tried stopping, ending, and killing the process, but it always returns immediately and jumps back to 25%. 
[IMG]http://goo.gl/m9c4oI[/IMG]

Plus, while this is happening, if I try to open the file browser, nothing happens. So the computer is running at 100% the whole time, I can't stop the process, and I can't view files. The only remedy is to shut down the laptop, unplug the monitor cable, restart the laptop, then reconnect the cable. Sure, if I could just remember to unplug the monitor cable every time I'm done, that would prevent this from happening. But, that does nothing to solve the problem or explain why it's happening. 

Does anyone have an idea as to why this is happening? Is there a way to get more info about what's going on with the pcmanfm process when this occurs? 

Even better, is there someone who's also running Lubuntu 14.04 on an Acer Aspire One who can tell me if this also happens to them?

---

