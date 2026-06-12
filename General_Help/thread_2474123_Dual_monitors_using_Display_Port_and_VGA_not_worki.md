---
title: "Dual monitors using Display Port and VGA not working"
date: 2022-04-22
forum: General Help
---

### Post by wcnackers on 2022-04-22
Hi,

Not sure where this should be posted so I thought general would be a good place to start.  I do tech support and hardware testing for a computer engineering firm.  I have a computer with uses Coffee Lake S Intel processors.  The processor outputs video to the Display Port (DP).  The processor is connected to the Intel C246 PCH which then connects to an ASPEED 2500 BMC that outputs video to a VGA port.  I can get either the DP to come up or the VGA to come up but I can't both to come up to do dual display.   When I run "lspci | grep VGA" both controllers are listed.  But if I run xrandr, it only lists the DP or the VGA, not both.  My Linux/Ubuntu knowledge is limited...the company I work for is Windows based and so that is what I familiar with.   I can tell you that dual display dos work in Windows once the Intel and ASPEED drivers are installed.   

I am hoping that someone can point me in the right direction as to what I need to do to solve this problem.  I have a customer that is expecting us to find an answer 

Thanks in advance for your help,

wcnackers

---

