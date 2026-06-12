---
title: "Ubuntu 14.04 wake up from suspend crashes on laptop"
date: 2014-05-22
forum: General Help
---

### Post by imaginois on 2014-05-22
I've recently purchased HP zbook 14 and immediately installed ubuntu on the newly formated hard drive.

I have ubuntu 14.04 and it seems stable for now besides one thing. After waking up from suspend it crashes. If I've been watching video before I close the lid it resumes the audio and the frame is frozen. Everything is unresponsive and the only option I have is to power it of by holding the power button.

**If I switch to the open source drivers, seems to be fine**. **Proprietary drivers crash** it on wake up. It obviously appears to be an issue with the drivers. Question is how to fix it. The video card is  **AMD FirePro M4100**

*Some thing to bear in mind:*
[LIST]
[*]I have installed ubuntu on the ssd drive which is originally meant to be used as caching patition for windows. It's RAID and the bootloader is on the HDD.
[*]Windows on the same machine but installed on the HDD suspends and unsuspends okay
[*]Also OpenSuse again on the hdd works properly
[*]4gb ram added aftermarket
[*]Both harddrives have been formated upon upacking
[/LIST]


[This is the machine]("http://www8.hp.com/us/en/campaigns/workstations/zbook-14.html")

---

### Post by imaginois on 2014-06-18
New discovery. I went into tty the suspended then resumed. Few messages on the board the last on is ```
ahci 0000:00:if:3 port does not support device sleep
```

---

