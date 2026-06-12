---
title: "System added to Ubuntu Pro, a question.."
date: 2023-12-14
forum: General Help
---

### Post by LVDave on 2023-12-14
I recently added my KUbuntu 22.04 workstation to the Ubuntu Pro program. Since its free for home use, and up to 5 systems, I added both my 22.04 workstation and
my 20.04 server. My question is this: I'm seeing a message when I login to the 22.04 system via ssh that follows: "System restart required. Kernel SRU period has ended"

I've rebooted and I'm still seeing this message via ssh login. Not sure what's going on here..

Edit: 2nd question: What is the support period now for Kubuntu 22.04?

---

### Post by MAFoElffen on 2023-12-14
First question:
Please post the results of this within CODE Tags
```

ls /boot/initrd.img-*
uname -r

```
Second Question:
The Date for End Of Support for Kubuntu 22.04 is April 2025, while for Ubuntu Desktop 22.04, that is April 2027. Ubuntu Pro pushes the underlying Ubuntu Base packages out another 5 years for a total of 10 years.

So your 20.04 Ubuntu Server's official support is about the same end point as Your 22.04 Kubuntu Desktop system. Confusing right?

The difference in support dates... The support for Kubuntu (and other Ubuntu flavors) is by their respective flavor community volunteers. They are not paid Canonical staff. 3 years of support for them, is a compromise for the flavors so that it is manageable for those volunteers.

---

### Post by LVDave on 2023-12-14
> **MAFoElffen said:**
> Confusing right?


Sure is.. 


[dave@sluggo ~]$ ls /boot/initrd.img-*
/boot/initrd.img-5.15.0-24-lowlatency

[dave@sluggo ~]$ uname -r
5.15.0-24-lowlatency
 
This is actually the KUbuntu "Ubuntu Studio" spin, thus the "lowlatency" kernel. I use the audio production tools quite a bit, but I'd heard that with a modern kernel (5x or newer) you
don't really need "lowlatency" kernels. 

Thanks!!!

---

### Post by MAFoElffen on 2023-12-14
I don't get it.

You installed 22.04. You updated. On a new install of 22.04.3, it has been long enough that you would have had at least one kernel update after the fresh install...

Yet there is only one kernel there.

I'm asking myself what is wrong with that picture.

---

### Post by LVDave on 2023-12-14
Yeah. I'm not sure why I only have one..When I get a bunch of old kernels, I purge them, but sure am NOT going to with only one, were it even POSSIBLE to do...

---

### Post by LVDave on 2023-12-15
Will do, thank you!

---

### Post by TheFu on 2023-12-15
> Support lifespan
Kubuntu 20.04 LTS will be supported for 3 years until April 2023. 


[https://wiki.ubuntu.com/JammyJellyfish/ReleaseNotes/Kubuntu](https://wiki.ubuntu.com/JammyJellyfish/ReleaseNotes/Kubuntu)
> Support lifespan
Kubuntu 22.04 will be supported for 3 years. 

Only the Gnome-based, bloated, "flagship" Ubuntu Desktop gets 5 yrs of standard support that can actually be extended under ESM.  I hate to say this, but you fell for Canonical's FUD marketing.  There are probably some items which get slightly longer support under PRO/ESM, but if you run KDE, best to just move to the next LTS release within 1 yr of that release so you are always on a supported version.  

Some installed packages will lose support.  Heck, I suspect some don't actually have support on the day we install a new OS.

On a 20.04 system here:
```
$ ubuntu-security-status 
This command has been replaced with 'pro security-status'.
1719 packages installed:
     1295 packages from Ubuntu Main/Restricted repository
     390 packages from Ubuntu Universe/Multiverse repository
     28 packages from third parties
     6 packages no longer available for download
...
This machine is receiving security patching for Ubuntu Main/Restricted
repository until 2025.
This machine is **NOT attached to an Ubuntu Pro subscription**.

Ubuntu Pro with 'esm-infra' enabled provides security updates for
Main/Restricted packages until 2030.
...
Ubuntu Pro with 'esm-apps' enabled provides security updates for
Universe/Multiverse packages until 2030. **There are 31 pending security updates**.
```

Scary when you read that, right?
From what I can tell, "pro" is a way to track systems running Ubuntu in a little more depth.  I see it as FUD, using human nature for corporate types to want to pay, which is 100% fine. Actually, for servers in a corporate world, ESM makes all sorts of sense if the team can't migrate to the next LTS easily.  There are always systems in a corporate IT farm with that problem.

---

