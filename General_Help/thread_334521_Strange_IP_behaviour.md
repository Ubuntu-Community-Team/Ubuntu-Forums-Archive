---
title: "Strange IP behaviour"
date: 2007-01-09
forum: General Help
---

### Post by JKoder on 2007-01-09
Hello
I have a questions. sometimes i use WindowsXP and UBUNTU ( but now ONLY ubuntu 6.10)
Can anyone tell me why in windows i have an IP number like: 86.xxx.xx.xx and in Ubuntu i have : 89.xxx.xxx.xxx, i need to mention that my IP is assigned via DHCP.
If i switch back to Win i will have the first IP, if i am using ubuntu i will have the second IP.
I can manualy set the first IP but i whant to find out why this is happening.

It does not happened before.
Thank you , for anyone cant talk to me about this !

---

### Post by Soarer on 2007-01-09
There are a few possible explanations, depending on where you get your IP addresses from and how long their leases are.

If you had an IP on the Ubuntu box already, and it is not yet expired, it will stay until it does expire. More likely is that you have two IP address sources on the LAN. 

Those aren't normal private addresses, so I guess they are coming from an ISP. They MAY both be in the range owned by the ISP, in which case it's not a problem.

---

