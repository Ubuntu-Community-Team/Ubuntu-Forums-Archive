---
title: "Kubuntu stuttering/lockups"
date: 2021-11-20
forum: General Help
---

### Post by Dan_Bowser on 2021-11-20
Hi,

Usually I try to have a more focused post but I haven no idea what's wrong or how to fix it. Anyways, I ruined a hard drive recently and I just yesterday got it replaced. After I installed kubuntu and some games I've been having problems with stuttering/freezing. The video output just freezes for a few seconds then jumps into a new configuration after some inputs. I'm getting the stuttering now with just firefox tabs open and 1 active  file transfer. Last week with my old OS install and hard drive I had  perfect performance. 

I updated the nvidia drivers to the 495 version and turned down all the graphics but I get the same issues. At the time I thought the issue was 100% related to the game I was playing so I was trying to tweak it's performance.

First question, why does NVIDIA X server settings say that my video card is using at most 7% of the PCIe bandwidth when running world of warcraft?


There's a couple of threads here,

[https://ubuntuforums.org/showthread.php?t=2469111](https://ubuntuforums.org/showthread.php?t=2469111),

and

[https://ubuntuforums.org/showthread.php?t=2464359](https://ubuntuforums.org/showthread.php?t=2464359).

For the first link,

```
free -hm
              total        used        free      shared  buff/cache   available
Mem:           15Gi       2.4Gi       157Mi        43Mi        13Gi        12Gi
Swap:         2.0Gi       1.0Mi       2.0Gi
```

I guess that looks OK.

For the second link: I don't know if what's said there applies to me, I don't know how to blacklist the specified file, and if I want to install the specified package the syntax is "install packagename" is that right?

Is there anything else to do?

---

### Post by Dan_Bowser on 2021-11-21
I figured out what was wrong. Firefox was pasting some crypto software into the destination folder of any file transfer. I had to clean out an archive of teaching stuff I had transferred from backup after disabling all addons. 

What else should I do now?

---

