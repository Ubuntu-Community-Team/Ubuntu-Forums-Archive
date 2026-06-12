---
title: "Strange behavior of printer under 16.04.4"
date: 2016-10-20
forum: General Help
---

### Post by JKyleOKC on 2016-10-20
I recently did a clean install of Xubuntu 16.04.4 to one of my machines. That machine provides the physical connection for both my printers and acts as the print server for my other machine (which still runs 14.04.4). However since the upgrade the other machine has consistently been unable to print, reporting that the printer may be disconnected. While a ping to the other machine has no problem, any attempt to connected to it at port 631 was refused.

Netstat reported that the updated box was listening for ipp packets on "localhost:631" which immediately shed a bit of light on the problem. I edited the /etc/cupsd.conf file to change the "Listen" line to "*.631" and after restarting the service, that appeared to solve the problem.

But it didn't provide a complete solution. This morning, I attempted to print from the other machine, and the situation was right back to "connection refused" and "printer disconnected" although the print job DID load into a queue (I couldn't determine whether the queue was on the local box or the print server). I immediately went to the 16.04 box, which normally sits on the login screen, and logged in. And as soon as my desktop came up, the printer spit out the queued job!

In the past, the "print server" box accepted and ran print jobs regardless of whether a user was logged into it. Now, it seems that I must be logged in for printing to work. I've not been able to locate a configuration setting to account for the difference. Can anyone tell me how to make things work as they did in the past?

---

