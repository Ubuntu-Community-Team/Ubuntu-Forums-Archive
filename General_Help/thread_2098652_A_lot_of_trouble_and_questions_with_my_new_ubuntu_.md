---
title: "A lot of trouble and questions with my new ubuntu 12.04 LTS"
date: 2012-12-27
forum: General Help
---

### Post by The Gambler on 2012-12-27
Hello I'm new to this forum,
At the moment I'm really frustrated. After using LinuxMint on my desktop computer for some time I bought a Asus X55U laptop with preinstalled Ubuntu 12.04 LTS. After setting everything up in my preferred way I updated it and the wired connection was gone. After looking in the forum I found out that more people had this problem and maybe I shouldn't have updated it before researching. I tried some of the suggested fixes, nothing worked. So back to square one I reset the system and of course it worked again, but some kind of automatic update slipped through and here we go again...reset the system turn off all updates (while trying to turn off the updates it rejected my password until I began doubting my mind, so I did a reset once more, still didn't work, I wanted to give up then it suddenly worked again). So I tried to leave the system as it is no updates and stuff just as long as it works, but still with no changes made the wireless connection works for 20 min. then it starts turning on and off, on and off. Another problem more people seem to have. I tried the "turn off power management" fix. It did not work. Overall it seems a buggy mess. I don't know what to do. Should I wait until better updates are out? Install another Linux? Try to work out the problems one by one?
For the beginning it would help to have stable wired and wireless connections, so I can work with this thing.

Thanks for reading my long post :-)

---

### Post by The Gambler on 2012-12-27
Ok I found out that the password did not work because the evil machine seems to be changing keyboard layouts.
For my main problem: lspci says my Network controller is "Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe"
and Ethernet controller is: "Atheros Communications Inc. AR8161 Gigabit Ethernet"
I heard Atheros is often trouble with Linux but I thought when Asus has it on a preinstalled Linux Laptop it should be alright (They might have tested it, before putting it on the market), maybe I was wrong...

---

### Post by The Gambler on 2012-12-27
"sudo apt-get install linux-backports-modules-cw-3.4-precise-generic
 sudo modprobe alx"

seemed to stabilize the connections. I don't know if I can say it's solved, but it looks a lot better now.

---

### Post by Mac Boy on 2013-02-05
I am having the same issues.
I managed to update to 12.10 thinking all the back ports would have been included. The WFI just remains a problem.  It often works for a short while after a Reboot but then Turns on and off continuously.

I have tried installing the latest drivers but I could easily have messed up there because I'm not that smart.

I bought the computer because I wanted a cheap laptop to mess around with and learn Linux but I can't do that without the internet.

Any chance you have a update or a solution?

---

