---
title: "What happens when ubuntu updates to newer releases?"
date: 2016-02-14
forum: General Help
---

### Post by jerry50 on 2016-02-14
I've only been using Ubuntu 14.04 on my laptop for a little less than a year, and more recently 15.10 on a new computer build.   I'm not sure why 15.10 was installed instead of 14.04, but it was.  I didn't install it.  Both systems are dual boot with Win. 7.  Questions:  

1.  When the new Ubuntu 16.04 LTS, Xenial Xerus, comes out  on 4/21/2016, how can I update both versions?  I mean, will there be an automatic update notice or do I have to burn the ISO and install it just like the other versions?  

2.  Also, after the update, will the older version(s) be removed or over-written automatically?  

3. What happens if it is a dual boot system?

4.  Lastly, is there anyway to upgrade 15.10 to 14.04?  Although, technically, that wouldn't be an upgrade, or should I just wait until 16.04 comes out?

---

### Post by egeezer on 2016-02-14
1. There will be an update notice that informs you a new version is available and offers to perform it.   2. Yes.    3. Same thing - It updates the version and leaves anything else alone.    4.  Not sure, never tried it.  5. However, a lot of Linux old-timers prefer to do a clean install, saving data on an external drive.  Gives a fresh view, an opportunity to adjust configurations, provides reinstall media.

---

### Post by jerry50 on 2016-02-14
Good info.  Thanks.  Not going to do a clean install.  Too many things can go wrong...and do with me.

---

### Post by ajgreeny on 2016-02-14
Just be sure you have a backup of everything important to you, as in spite of your comment "Not going to do a clean install. Too many things can go wrong...and do with me. ", it is often the clean install that goes well and distro-updates that go wrong.

I have never done a distro-update so perhaps I'm the wrong person to give advice on this, but I do know that backups are extremely important at all times, and even more so when you are changing the OS in such a fundamental way.

---

### Post by kurt18947 on 2016-02-14
When upgrading, I believe it's recommended to disable/remove any PPAs, remove/disable any non-native device drivers such as wireless networking and if using proprietary video drives from Nvidia or AMD, switch to xorg/Nouveau prior to upgrading. This is an advantage to a separate /home partition. Most if not all settings are stored there and it's possible to upgrade the O.S. while maintaing the contents of /home and its associated settings.

If there's anything of consequence in your /home folders i.e. Documents, Downloads, Pictures etc. be sure to back those up before beginning the upgrade process. Reinstalling *buntu is trivial, restoring the settings and tweaks take me far longer.

---

### Post by frank18 on 2016-02-14
> **jerry50 said:**
> I've only been using Ubuntu 14.04 on my laptop for a little less than a year, and more recently 15.10 on a new computer build.   I'm not sure why 15.10 was installed instead of 14.04, but it was.  I didn't install it.  Both systems are dual boot with Win. 7.  Questions:  

1.  When the new Ubuntu 16.04 LTS, Xenial Xerus, comes out  on 4/21/2016, how can I update both versions?  I mean, will there be an automatic update notice or do I have to burn the ISO and install it just like the other versions?  

2.  Also, after the update, will the older version(s) be removed or over-written automatically?  

3. What happens if it is a dual boot system?

4.  Lastly, is there anyway to upgrade 15.10 to 14.04?  Although, technically, that wouldn't be an upgrade, or should I just wait until 16.04 comes out?


I also been using Ubuntu 14.04LTS since it came out, but i did a clean install and it has been working like clock work, now i have an extra HDD and was curious about Ubuntu 15.10 and went to try it and it was a mistake cause Ubuntu 15.10 on the same machine i run 14.04LTS worked horrible, what a crappy beta version,hope they do not come out with a 16.04 LTS as bad as 15.10.

---

### Post by buzzingrobot on 2016-02-15
> **frank18 said:**
> ... what a crappy beta version...,hope they do not come out with a 16.04 LTS as bad as 15.10.

You know, if you installed an actual beta release, you should have anticipated problems,  Betas are for pre-release testing.

---

