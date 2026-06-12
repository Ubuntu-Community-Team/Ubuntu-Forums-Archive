---
title: "Session Freezing"
date: 2017-10-05
forum: General Help
---

### Post by beenny on 2017-10-05
I'm running Ubuntu 16.04 on Kernel 4.4.0-96-generic

Off and on for the past few months my session will occasionally freeze on me (maybe twice a day, maybe once a week) and I have to do a hard reboot. This is not a complete freeze, in that I can still move my mouse (though only to one screen - I have duel screens) and if music is playing it will continue playing. However, the load monitor doesn't move and I can't click on anything etc. 

This isn't a RAM issue as I have 64 gb and my processor is a Intel i7-5960X so the system shouldn't be overloading.

The other (I don't know related) issue is that when I try logging back in I get to my login screen enter my password and then nothing comes up. It just freezes on my background and it sounds like the processor is whirling. I may have to reboot 2 or 3 until I'm lucky enough to get it to load up.

I followed the solutions posted here but it hasn't worked:
[https://askubuntu.com/questions/761706/ubuntu-15-10-and-16-04-keep-freezing-randomly](https://askubuntu.com/questions/761706/ubuntu-15-10-and-16-04-keep-freezing-randomly)

Any suggestions would be greatly appreciated.

Thanks,

Ben

---

### Post by TheFu on 2017-10-07
Review the system logs and dmesg files.  Best to use a different computer and ssh into the "stuck one."

If the system isn't really freezing, just the GUI, then it is probably a display driver issue.  

The dmesg logs are overwritten at reboot, so if you cannot ssh in from another machine to check them, then you'll need to boot from alternate media, manually mount the /var/log storage and look through the logs.  Without actual logs, we would just be guessing.

---

### Post by beenny on 2017-10-08
I've actually been meaning to set this computer up so I can log into it so this is a good excuse to do it. Will try to post log next time it happens.

I'm assuming you are just asking for the output from 
> dmesg

anything else?

Thanks for reply.

Ben

---

### Post by TheFu on 2017-10-09
> **beenny said:**
> I've actually been meaning to set this computer up so I can log into it so this is a good excuse to do it. Will try to post log next time it happens.

I'm assuming you are just asking for the output from 
> dmesg

anything else?

I have ZERO interest in looking at your log files.  If you'd like help, I would be willing to look at **relevant** parts of any of the logs in /var/log/.  YOU need to review those and fine the issues.   Please do not post entire logs.

---

### Post by beenny on 2017-10-09
gotcha. What am I looking for in these log files. I've never really looked at them before.

Thanks,

bg

---

