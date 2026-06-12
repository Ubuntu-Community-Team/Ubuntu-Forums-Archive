---
title: "Too frequent kernel updates in 13.04"
date: 2013-06-19
forum: General Help
---

### Post by SeijiSensei on 2013-06-19
Today I got another batch of updates that required yet another change to kernel 3.8.0 for 13.04.  This marks the fourth kernel update in about a month.  I can't remember a time when the kernel seemed so unstable.  Are these all security updates?  Is this a problem with 3.8.0 in general?  Upstream changes at Debian?  Linus not paying as much attention as he should?  

To me, kernel updates for a released version of Ubuntu should be an infrequent event.  Even more often than once per month seems excessive.  Moreover recent changes have introduced regressions that later needed correction.  My Intel wifi card failed to work after one of these updates, though it was fixed a week or two later.  

I can see pushing out new kernels when they have security issues, as was apparently the case today.  Should I conclude from the pace of change that the 3.8 kernel has a lot of vulnerabilities that need fixing?  It may not simply be the kernel that is vulnerable either; today's update seemed to result from a fix to dbus.

Unless all these changes were to fix newly-found vulnerabilities, I don't see any argument for this pace of change in the kernel.  For non-security issues, they should just be compiled into a single update, perhaps on a monthly basis.

---

### Post by Frogs Hair on 2013-06-19
Are proposed updates enabled ? I have used proposed updates for a few releases and one result is  frequent kernel updates. If proposed updates is not enabled they must be necessary updates.

---

### Post by MichelNL on 2013-06-19
I believe you wont get a kernel upgrade unless you do a **apt-get dist-upgrade**:confused:

---

### Post by matt_symes on 2013-06-19
Hi

No idea why there are so many kernel updates.

Looking here, under Ringtail, there are 4 since mid April in the different repos.

Clicking on the kernel link itself will give you the change log.

[https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux)

What repos do you have enabled ?

Kind regards

---

### Post by SeijiSensei on 2013-06-19
> **Frogs Hair said:**
> Are proposed updates enabled ? I have used proposed updates for a few releases and one result is  frequent kernel updates. If proposed updates is not enabled they must be necessary updates.

That doesn't seem to be an option in the Muon Update Manager that comes with Kubuntu.  I have "Available Updates" and "System Upgrades" enabled.  Maybe the latter generates kernel changes?  I always assumed that if I was asked if I wanted a correlated kernel upgrade I should say yes.

> **MichelNL said:**
> I believe you wont get a kernel upgrade unless you do a **apt-get dist-upgrade**:confused:

Some software upgrades will trigger a kernel update.  Usually you will be asked if you want to install some "additional files" which are usually kernels.  That was the case today, where the dbus update appears to have triggered a dependent kernel update as well.

The kernel for 13.04, 3.8.0, is now in its 25th revision, and the last four of those occurred just in the past month or so.

---

