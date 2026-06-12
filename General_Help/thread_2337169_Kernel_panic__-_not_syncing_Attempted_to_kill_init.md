---
title: "Kernel panic  - not syncing: Attempted to kill init!"
date: 2016-09-15
forum: General Help
---

### Post by ines-k on 2016-09-15
Hi there,

I am new to Linux and I am facing a real problem here as I my laptop won't boot for 2 days now due to this error. This is a follow up from this thread which started with not being able to fully update my Ubuntu 14.04 lts version: [https://ubuntuforums.org/showthread.php?t=2336877](https://ubuntuforums.org/showthread.php?t=2336877)

I have been reading up on how to solve this and I really hope there is another way of solving this than with an external mount drive with the risk of loosing data. Worth saying that a lot of posts on this out there are galactic speech to a newbie like me. Only have my phone at the moment and any help is greatly appreciated!

Thanks in advance!

---

### Post by ian-weisser on 2016-09-15
Try Boot Repair: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ines-k on 2016-09-15
Hi,

Thanks for the tool but it didn't work even though it said it had repaired the boot. So far I had to seek paid professional help to save all my data and install Ubuntu 16.04 LTS.

I'd still like to know roughly what happened to my system to produce this kernel panic situation after I followed your advice.

---

### Post by DuckHook on 2016-09-15
> **ines-k said:**
> I'd still like to know roughly what happened to my system to produce this kernel panic situation after I followed your advice.I sympathize with your misadventures. ian-weisser gave good advice on your previous thread, but it appears that the damage had already been done by the time he came on the scene to offer advice. It is simply impossible to answer your question: the kernel is a delicate piece of software and there are countless ways it can be destabilized enough to go into panic. This is the reason why ian-weisser counselled against partial upgrades. Such upgrades are always fraught with trouble. "There be dragons".

I can't tell from your previous thread whether you had added PPAs to your sources, outside sources, etc. and it's moot now in your case, but to general readers who may come across this thread, these are all invitations for trouble when upgrading. Many of them make changes to the system, or create dependencies to libraries that are not part of a default install. When you then try to upgrade, the upgrade process assumes a default system state, senses that some libraries/configuration files/system files are not the default ones and tries to handle these differences as elegantly as it can. But such elegance is largely an illusion. After all, how can you expect any programmer to anticipate the infinite ways in which a user can modify her initial installation?

This is why the first thing veterans will tell you is to remove from your system all PPAs and outside sources that you've added before trying to upgrade. This is based on trying to bring your installation back to as much of a pristine state as possible. Even better, don't add such non-default sources in the first place. Almost everything that a general user needs can be found in the repositories. If you add outside sources, there's really little that anyone can do to help you when things go wrong.

If nothing else, what this incident teaches is the truth of the caution in my signature: never upgrade without first backing up your data. I'm sure that you've learned to do proper scheduled backups from now on, whether upgrading or just in everyday computing.

---

