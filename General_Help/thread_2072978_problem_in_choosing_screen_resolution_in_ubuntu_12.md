---
title: "problem in choosing screen resolution in ubuntu 12.12"
date: 2012-10-18
forum: General Help
---

### Post by Yamlikha on 2012-10-18
What's up guys,

I just upgraded ubuntu from 12.04 to 12.10
however after the update, I couldn't choose the screen resolution that I want
it gives me jus 2 options (1024*768 and 800*600)
the biggest problem is I can't see or use the luancher, dash and the panel

the only way that I can get to the settings is by clicking right click and choose "change background" then I can reach settings

SO how can I fix this problem? :(

---

### Post by buckyaustin on 2012-10-18
This sounds like you are running Ubuntu on a system that can't handle the graphics required for Ubuntu. Try looking for tutorials on speeding Ubuntu up first. Then come back here after that if the problem is still there.

---

### Post by Yamlikha on 2012-10-18
the graphics card in my laptop is 1 GB ATI Radeon
ubuntu 12.04 was working without any problem!

---

### Post by pompel9 on 2012-10-18
Are you using the proprietary drivers for your graphic card? If not, try to activate it. The open drivers for ati sucks. I had troubles with my motherboard that had built in ati graphic. So much trouble, so I had to buy a nvidia card. I got the ati graphic working by using the proprietary drivers, but it was buggy still.

---

### Post by buckyaustin on 2012-10-19
This usually happens after a update. Seems updates on the graphics cards come out after updates on the distribution. Try "sudo apt-get update". Then "sudo apt-get upgrade". This should hopefully get you the latest driver and solve your problem. Also run "sudo dist-upgrade". just to make sure you update completly.

---

