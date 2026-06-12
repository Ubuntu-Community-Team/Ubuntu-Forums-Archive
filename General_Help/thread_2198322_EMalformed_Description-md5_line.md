---
title: "E:Malformed Description-md5 line"
date: 2014-01-08
forum: General Help
---

### Post by jakefish on 2014-01-08
Hello,
I have just came to my pc and discovered this error.

Can anybody help ??

Thanks

John


E:Malformed Description-md5 line; includes invalid character '0091391c46e3a713dva8c5d3e724918a', E:Malformed Description-md5 line; includes invalid character '2e694f5517ce3b176ud46e53ef48736f', E:Malformed Description-md5 line; doesn't have the required length (32 != 33) '`2151e805dca17d197034db9a122c92c7', E:Malformed Description-md5 line; includes invalid character 'e3c0f090d9b74cefa45e3c8sf89ef70f', E:Malformed Description-md5 line; includes invalid character 'a41d14da27b1f5a8000bd147dcya36d6', E:Malformed Description-md5 line; includes invalid character 'a41d14da27b1f5a8000bd147dcya36d6', E:Malformed Description-md5 line; includes invalid character '41ba67e08cs76f19300862b539718469', E:Problem opening /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy-updates_universe_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.

---

### Post by sudodus on 2014-01-08
Please describe your system and what happened with more details. What were you doing/trying to do? Did you perform some kind of update/upgrade?

Those strings are md5sums (and should be hexadecimal (digits 0-9,a-f). For example u and y are found but not allowed in those strings.

---

### Post by ibjsb4 on 2014-01-08
Try this

[http://ubuntuforums.org/showthread.php?t=2190797&p=12860782#post12860782](http://ubuntuforums.org/showthread.php?t=2190797&p=12860782#post12860782)

---

### Post by jakefish on 2014-01-11
Hello sudodus, this ususally happens when my electricity goes off, my computer always restarts a little ill :-) 


I am running Ubuntu 13.10
2GB memory
AMD Athlon11x4 630 processor x4
64 bit


cheers

John Attewell

---

### Post by jakefish on 2014-01-11
Hello ibjsb4,

I have just tried this and it appears to have cleared the problem thank you


John Attewell

---

### Post by sudodus on 2014-01-11
> **jakefish said:**
> Hello sudodus, this ususally happens when my electricity goes off, my computer always restarts a little ill :-) 


I am running Ubuntu 13.10
2GB memory
AMD Athlon11x4 630 processor x4
64 bit


cheers

John Attewell

I am glad that you have solved the problem :-) but I will add a comment about problems when your electricity goes off:

If the computer has no backup supply of electric power, it cannot shut down the processes and flush buffered data to the disks. It means that data are lost, and in the worst case, some important file is corrupted, so that the system won't boot properly. It can also cause a corrupted file system.

If you have frequent power outages, I suggest that you get a system with a backup supply of electric power. The cheapest and simplest system would be a laptop or netbook with a battery good enough for a controlled shutdown. After backup you should also check that the system really will shut down in a controlled way, when the battery is getting low. There are separate systems for desktop and server computers, UPS system. See this link

[https://en.wikipedia.org/wiki/Uninterruptible_power_supply](https://en.wikipedia.org/wiki/Uninterruptible_power_supply)

---

