---
title: "How to recompile and load my WiFi driver (bis)"
date: 2013-11-08
forum: General Help
---

### Post by John_Rose on 2013-11-08
Hello,

 I am working under Ubuntu 12.04.3 LTS (kernel 3.2.0-56-generic-pae) on a Dell Vostro 3700 portable. I am not a computer specialist.

 I am having trouble with my WiFi driver (brcmsmac for Broadcom BCM4313 WiFi chip). I have tried everything in terms of configuration and backporting to resolve my problem (with help from the Ubuntu forums Networking and Wireless group, see [http://ubuntuforums.org/showthread.php?t=2176808&page=3&p=12807769#post12807769](http://ubuntuforums.org/showthread.php?t=2176808&page=3&p=12807769#post12807769)).
 
 I am am now absolutely convinced that I have to change a line in the brcmsmac source code which is integrated in the kernel (in the program "drivers/net/wireless/brcm80211/brcmsmac/channel.c"). The people helping in the Networking and Wireless group could not advise me on how to do this.

 I am simply not able to understand the different documentation and postings on the subtleties of recompiling and loading this driver (whether I have to recompile the kernel, the headers, a module, whether I have to generate a config file, etc.). I would be extremely grateful if someone could walk me through this exercise step by step? Thanks and best regards, John

P.S. The same question was answered at [http://ubuntuforums.org/showthread.php?t=279628](http://ubuntuforums.org/showthread.php?t=279628) but it was for a much older Ubuntu version and there are some things there I don't understand.

---

