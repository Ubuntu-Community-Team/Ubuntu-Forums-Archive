---
title: "No network on HP N40L microserver with 12.04.2LTS"
date: 2013-05-15
forum: General Help
---

### Post by relli10 on 2013-05-15
Hi,

I had been running 10.04LTS desktop problem free up until a couple of days ago when I decided to upgrade to 12.04LTS. The upgrade process from 10.04 to 12.04 was smooth without any errors, the problem however was once 12.04 booted, I had no network connection. After a little bit of searching, I discovered it could be a tg3 driver issues with the Broadcom [FONT=Arial][COLOR=#333333]BCM5723 based network adaptor. As 12.04.2LTS was packaged with the 3.121 version of the tg3 driver, I upgraded it to the latest 3.124c version from the broadcom website. I then reloaded the tg3 module, but I still did not get any activity from the network card. All my logs seemed OK, with the only signs of trouble was dmesg saying that eth0 was not ready. But eth0 was still being listed as a device. 

Thinking it was an issue with the upgrade, I downloaded a 12.04.2LTS .iso and ran it as a live CD. For both x86 and x64 version of 12.04.2LTS, I could not get network activity. To rule out hardware issues, I downloaded the 10.04.1LTS iso and when booting into this, the network was normal and stable.

To test if it was an issues with Ubuntu, I downloaded Knoppix 7.0.5 and run this from a live cd. In knoppix I also experienced the same "eth0 was not ready" errors. This lead me to believe that there is some kind of hardware compatibility issue with 3.X.X series kernels as 12.04.2 runs 3.5.x and Knoppix run 3.6.x while 10.04 runs 2.6.x.

Has anybody else had these issues with a broadcom chipped network adapter?
Can anybody make any other suggestions to help resolve this issue?

Thanks
Paul[/COLOR][/FONT]

---

### Post by 13eastie on 2013-05-16
Paul,

I'm using the on-board adapter (and the remote-access card) on my N40L and have had no problems using static addresses with fast or gigabit ethernet under Ubuntu 12.04.2 LTS with the default driver.

I'm wondering whether something in the upgrade process has changed your network settings?

What do **cat /etc/network/interfaces** and **ifconfig** give and have you compared these with those given by the 10.04.1 live CD?

---

