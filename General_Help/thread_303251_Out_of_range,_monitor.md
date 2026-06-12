---
title: "Out of range, monitor"
date: 2006-11-19
forum: General Help
---

### Post by sqdtnz on 2006-11-19
Hey there,

I've been looking around and found some posts here and there with a very similar content. I feel though, that my situation is still different.

The situation:
I installed from the CD, everything went perfectly. After the first reboot I had to add 'noapic' to the grub boot-loader, no problem. The system seemed to work perfectly well.

Really now, the problem:
I think 4 out of 5 times I start up the computer with ubuntu, ubuntu loads, the loading screen with all modules is passed without any problem, then when you'd expect the login screen, there comes this monitor's 'out of range' message.

So I read many posts etc.. And adjusted my xorg.conf, also I tried the reconfigure tool (sudo command thing). The thing is that it only works once in a while.

CTRL-F1 or CTRL-ALT-F2, etc... don't work when I get the out of range message.

I really want to fix this soon, I don't like to perform a cold reboot until it does work each time. Anyone has any ideas? I do have to add that normally there is a sound when the login screen appears, but the sound also doesn't come up, so I think it may be something else than the monitor's setting themselves?

---

### Post by dcstar on 2006-11-19
> **sqdtnz said:**
> 
.......
CTRL-F1 or CTRL-ALT-F2, etc... don't work when I get the out of range message.

I really want to fix this soon, I don't like to perform a cold reboot until it does work each time. Anyone has any ideas? I do have to add that normally there is a sound when the login screen appears, but the sound also doesn't come up, so I think it may be something else than the monitor's setting themselves?

Ok, sometimes the monitor itself gets confused enough that the only thing to do is switch it off and then back on after a few seconds, try that next time you have the problem.

---

### Post by sqdtnz on 2006-11-22
Thanks for the reply.

I found out something really odd:

After the modules loading screen, if I keep moving my mouse quickly, the monitor ALWAYS stays on. It seems to somehow lose track of what's happening if there are no events, maybe it does have to do with that noapic timer issue?

---

