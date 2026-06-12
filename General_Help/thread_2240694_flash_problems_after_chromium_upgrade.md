---
title: "flash problems after chromium upgrade"
date: 2014-08-21
forum: General Help
---

### Post by jdefed on 2014-08-21
Hi,
Running Lubuntu 12.04lts. using chromium browser. I was running Ver. 32.xxx chromium and not having ant issues with flash plugins. I made the mistake of letting update manager update Chromium to ver. 36.xxx and now have no flash player. Chromium shows no plugins(chrome://plugins) installed. Can someone tell what directory plugins should be in. I did install Firefox, and flash works their, so I presume I have the flash plugin / player installed. I did try and force the old version I had installed, but there were other upgrades that would not allow me to force that version. I suspect that I need to get libflashplayer.so in the right directory for chromium to recognize it. I put all the plugins from Mozilla directory in Chromium directory, but that didnt help.
Thanks
Jim d

---

### Post by lisati on 2014-08-21
*Thread moved to **General Help**.*

---

### Post by ajgreeny on 2014-08-21
You will have to use the pepperflash plugin by following the info at [http://ubuntuforums.org/showthread.php?t=1976503]("http://ubuntuforums.org/showthread.php?t=1976503&page=2")

---

### Post by Dennis N on 2014-08-21
You can get **pepperflashplugin-nonfree** in the Ubuntu Software Center. Search for "Pepper Flash".

---

### Post by ajgreeny on 2014-08-22
> **Dennis N said:**
> You can get **pepperflashplugin-nonfree** in the Ubuntu Software Center. Search for "Pepper Flash".

Not in 12.04; it is only available in 14.04 as far as I'm aware.

---

### Post by Dennis N on 2014-08-22
> **ajgreeny said:**
> Not in 12.04; it is only available in 14.04 as far as I'm aware.

You are right of course. I wasn't paying attention to the version. There is a ppa for 12.04:

[https://launchpad.net/~skunk/+archive/ubuntu/pepper-flash](https://launchpad.net/~skunk/+archive/ubuntu/pepper-flash)

There are instructions given there that need to be followed.

---

### Post by Rob Sayer on 2014-08-23
One thing you may not be aware of is that Lubuntu 12.04 is *not* a long term support release, unlike other 'buntu 12.04 versions.  14.04 is the first Lubuntu LTS release ever.  So you're not getting proper lxde updates though you should still be getting ubuntu security updates.

So in your situation I'd install 14.04.  I updated rather than reinstall once and it went fine but doing a clean reinstall is more reliable.

Also, I gave up on chromium because the level of support isn't good enough for me.  I use Chrome nowadays.  It has better flash support even than Firefox, though I don't like having to use a plugin for what I consider basic things like auto deleting cookies.  But I still think it's better than using the latest firefox versions.

---

### Post by jdefed on 2014-08-27
This can be marked as solved. I had an extra hard drive that I put 14.04 lts on to experiment and chromium and flash worked fine. They made the pepperflash install very easy. So I attempted to upgrade 12.04 via upgrade manager and that was a disaster. So I had saved a couple of files I wanted and did new install. Ultimately, I got everything working, but it was a chore. I have a 160 gig hd which was partitioned, and I wanted to keep the partitions the way they where. when I got to the point of selecting how to install I just put replace 12.04 with 14.04, mistake because it used the whole hd. So I got everything working fine, but I wanted to add a partition. I put in Parted Magic cd and ran live and did partition, which went fine. So then I start up my new o/s to check and I have no internet connection. My Ethernet is not talking to my router. Went on another computer to google check and found this thread to fix. Here are the instructions that fixed it, 1) sudo ifconfig eth0 up 2) sudo service networking restart. Can someone explain why this happened? Also what are the pros and cons of locking the version of chromium and pepperflash I have so they don't upgrade.
thanks 
jim d

---

### Post by mörgæs on 2014-08-27
> **jdefed said:**
> This can be marked as solved.

You are the best to do it using Thread Tools.

---

### Post by vasa1 on 2014-08-27
> **jdefed said:**
> ...
My Ethernet is not talking to my router. Went on another computer to google check and found this thread to fix. Here are the instructions that fixed it, 1) sudo ifconfig eth0 up 2) sudo service networking restart. Can someone explain why this happened? ...
And you can start a new thread on this ^^^ issue. Doing so will keep the thread's content in sync with the thread title. 

We have other threads on "locking" or "pinning" or "holding" software at a particular version although it's probable that doing so could affect your security and hence isn't something to be done lightly. In particular, browsers and the flash plugin get repeated security updates.

---

