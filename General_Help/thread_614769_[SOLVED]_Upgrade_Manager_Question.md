---
title: "[SOLVED] Upgrade Manager Question"
date: 2007-11-16
forum: General Help
---

### Post by matthewcraig on 2007-11-16
Question about Ubuntu's Update Manager application.  I have started to question the logic of whether updates are really that critical to apply, lately.  I am one who feels the fewer changes made to a system, the more stable the system will be.  So when I see this particular patch pushed out, I wonder if I should just stick with the Security Patches:
[https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/147485](https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/147485)

My question is whether, with the nature of dependencies, it will be possible to accept the Security Patches and not the Recommended Patches.  Or will there be a danger of a Security Patch getting applied that assumed a Recommended Patch present?  Is there a link to where "best practices" for updates are recorded, so that I can better make my choice about what to update and when?

Thanks in Advance

---

### Post by ThrobbingBrain66 on 2007-11-16
I think your initial premise is flawed.  The updates that are pushed through to your system aren't just random code changes.  The changes are improvements and bug fixes.  They make your system MORE stable.  Just because you never experienced that bug specific to gnome-games doesn't mean it doesn't exist.

If you don't want the updates, that's your choice.  You can turn off any repo you wish in Software Sources.  Just keep in mind that if you ever want to *upgrade* to the next version of Ubuntu, you'll end up having to install all those updates beforehand anyway.

As far as best practices are concerned....most around here will tell you to stay up-to-date.  It's the only realistic way to ensure you are not the victim of security risks or experience other unpleasant bugs.

---

### Post by matthewcraig on 2007-11-16
If you look at the linked bug report, then you'll see that the change was pushed out because the game quits when the option for "super safe moves" is enabled.  This was not pushed out to make the system more secure or more stable.  I suspect it was pushed out because the upstream made it available.  I would rather limit the number of such changes.  From what you said, it sounds like an all-or-nothing proposition: Either keep up-to-date or turn the feature off.  Is this a correct understanding of what you said?

If so, then I may simply leave the Update Manager service off and wait until the next version within 6 months.  The Linux OS is hardened enough that I would feel confident doing so.

---

### Post by jdong on 2007-11-16
You may use the Software Sources Manager to disable Recommended updates (gutsy-updates) and still get Security updates. 

> **matthewcraig said:**
> 
If so, then I may simply leave the Update Manager service off and wait until the next version within 6 months.  The Linux OS is hardened enough that I would feel confident doing so.

This is a poor choice to make. Every piece of software is bound to have some sort of defect, no matter how good its reputation for security is. There's nothing special about Linux that excuses getting regular security updates

---

### Post by matthewcraig on 2007-11-16
I bugged the developers about this question and received the following response that really answered my question.  Thanks to the hard working developers for their patience in being interrupted to answer my question.  I will post the summary here, in case anyone references this thread.

"What you proposed is to disable gutsy-updates and only enable gutsy-security in the Software Sources Manager or /etc/apt/sources.list, that way you'll only get critical fixes. 

These two repositories are designed to be independent of each other.  -security doesn't require -updates, but -updates may require -security.  Indeed, packages in -security are normally pushed into -updates as well.  So, to all intents and purposes -security is a subset of -updates."

---

### Post by ThrobbingBrain66 on 2007-11-16
> **matthewcraig said:**
> If you look at the linked bug report, then you'll see that the change was pushed out because the game quits when the option for "super safe moves" is enabled.  This was not pushed out to make the system more secure or more stable.  I suspect it was pushed out because the upstream made it available.  I would rather limit the number of such changes.  From what you said, it sounds like an all-or-nothing proposition: Either keep up-to-date or turn the feature off.  Is this a correct understanding of what you said?

If so, then I may simply leave the Update Manager service off and wait until the next version within 6 months.  The Linux OS is hardened enough that I would feel confident doing so.

I read the bug report.  A crashing application lessens the stability of an OS, even if you personally don't experience the crash.  A patch was released that got rid of the crash.  The OS is now more stable (even if just a tiny bit). Just because you don't use a package (and therefore have never experienced the crash) doesn't mean it doesn't exist.

I'm glad you got your answer though.

---

