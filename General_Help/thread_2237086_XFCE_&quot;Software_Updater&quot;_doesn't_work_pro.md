---
title: "XFCE &quot;Software Updater&quot; doesn't work properly"
date: 2014-07-30
forum: General Help
---

### Post by beatme101 on 2014-07-30
The "Software Updater" program, which was removed from all menus and is hidden away halfway down in a huge settings manager, can't find updates properly anymore. It claims that everything is up to date, but Synaptic can see that many packages are out of date. Here is an example after opening both and clicking "Mark All Upgrades" in Synaptic.

[http://hurr.org/i/Software_Updater_is_worse.png](http://hurr.org/i/Software_Updater_is_worse.png)

Please tell me how to fix Software Updater, or how to get back the Update Manager that worked so well in 12.04.

I am on Xubuntu 14.04.

As "Software Updater" is new, there is no information available on search engines for this or other problems.

---

### Post by ajgreeny on 2014-07-30
This is probably a result of "phased updates" which are enabled in the update-manager but not in synaptic.

See posts 10 and later in [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1320683](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1320683)

---

### Post by ian-weisser on 2014-07-30
Software Updater works fine.
Since 13.04, SU has implemented phased updates. Synaptic does not.
See [http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04](http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04)

---

### Post by beatme101 on 2014-07-30
What a disappointing feature. Thanks for informing me about it.

I guess by "works fine" you mean how the developer wanted (crippled, useless) and not how users want & expect, sure.

---

### Post by ian-weisser on 2014-07-30
Well, I think users want and expect updates that won't break their systems when pushed to them.

The 'phased update' concept is a safeguard to catch updated packages that cause big problems that are not identified during testing. Updates that surprised us all with reversions or breakage when they arrived, and that flooded these forums with complaints. They still happen, but now most of the community can be protected from them....

Phased updates have been a _very_ good thing for this community.

---

### Post by ajgreeny on 2014-07-31
> **ian-weisser said:**
> Well, I think users want and expect updates that won't break their systems when pushed to them.

The 'phased update' concept is a safeguard to catch updated packages that cause big problems that are not identified during testing. Updates that surprised us all with reversions or breakage when they arrived, and that flooded these forums with complaints. They still happen, but now most of the community can be protected from them....

Phased updates have been a _very_ good thing for this community.

+1
I have to totally agree.  I have been using Ubuntu long enough to remember an xorg update that completely broke certain hardware setups many years ago and left me with a machine that would only boot to a command line.  Imagine how you might feel if that happened to you, and you were a newer user who was left with just a cli to mend it.

Phased updates mean that only a smaller percentage of users get updates immediately they are available and therefore if a major breakage happens the number of users left in the lurch is much reduced and that update can be removed from the repos and the old version put back.  Any broken systems can then be mended with a quick command line action to reinstall the old package version.

---

