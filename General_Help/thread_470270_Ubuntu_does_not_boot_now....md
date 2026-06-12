---
title: "Ubuntu does not boot now..."
date: 2007-06-10
forum: General Help
---

### Post by nym725 on 2007-06-10
after attempting to fix my previous problems... [http://ubuntuforums.org/showthread.php?t=470101]("http://ubuntuforums.org/showthread.php?t=470101")

i tried to get my internet working with ndiswrapper. i have a realtek wireless 8185. i was able to get the drivers to load, but the blacklisting of the automatic driver did not work. so i tried blacklisting r818x and r8187. now when i boot the ubuntu it loads slow and then the screen turns black with white text and says activing swap....checking root...ok

and it stops doing anything.

if i goto the recovery boot it stops at configuring network interfaces.

please i'm desperate here..nothings working now

---

### Post by confused57 on 2007-06-11
> **nym725 said:**
> after attempting to fix my previous problems... [http://ubuntuforums.org/showthread.php?t=470101]("http://ubuntuforums.org/showthread.php?t=470101")

i tried to get my internet working with ndiswrapper. i have a realtek wireless 8185. i was able to get the drivers to load, but the blacklisting of the automatic driver did not work. so i tried blacklisting r818x and r8187. now when i boot the ubuntu it loads slow and then the screen turns black with white text and says activing swap....checking root...ok

and it stops doing anything.

if i goto the recovery boot it stops at configuring network interfaces.

please i'm desperate here..nothings working now
You might be able to mount your root partition, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

then you should be able to edit your /etc/modules & remove the entries you blacklisted.

---

