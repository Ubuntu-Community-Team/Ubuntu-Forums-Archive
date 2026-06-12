---
title: "slow internet new installation issues"
date: 2008-04-01
forum: General Help
---

### Post by wolvie09 on 2008-04-01
i am running windows xp and ubuntu 7.1 on same machine, mozilla is very slow with the internet. but when i run windows xp, the speed is fine and if i run speedtest i get 12mb download and 2mb upload speeds.... not sure whats going on.

i have tried dhcp but it failed to get the ip info. i set to static and im online but its slow from page to page takes about 1 minute to load a page.... again when i boot in windows xp its fine so i know hardware, speed and connections are all good.

i have my ip set like this... and i CAN get online just VERY slow...
ip: **192.168.100.150**subnet: **255.255.255.0**
gateway: **192.168.100.1**
dns: **192.168.100.1**

could use any help on this. thx :confused:
-Mike

---

### Post by plucky on 2008-04-02
wolvie09,


This could be an **IPv6** issue with the internet.

In firefox open a new tab and type in **about:config**. 
Then in the filter window type in **ipv6**.
It will display **network.dns.disableIPv6** 
Select the line and right click and toggle the value to true.


Also see this [thread]( http://ubuntuforums.org/showthread.php?t=87798&highlight=ipv6) for more information about disabling ipv6.

Good Luck

---

