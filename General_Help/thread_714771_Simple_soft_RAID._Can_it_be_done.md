---
title: "Simple soft RAID. Can it be done?"
date: 2008-03-04
forum: General Help
---

### Post by pcjunkie on 2008-03-04
I have tried using several versions of soft raid and frankly its atrocious and a nightmare to go through. 

I have an Nvidia bus with RAID 1 desirable. 
Sure I could bang in windows and that would be it. Everything would be set up on install or forever after. What I need though is a samba share dir and a backup dir for emails, data and so on. I have 2 500gb drives waiting to go and on thier own Linux (ubuntu) is fine with them but trying to RAID 1 them is god awful.

Is there a simple method to get Ubuntu to see them as 1 disk and use it as 1 disk. So far I have tried mdadm method and a couple of other Soft raid solutions. but none so far have been able to be mounted. I need this to work as I am trying to get an office over to Ubuntu and the RAID server is the Data bank. I need raid 1 to keep it safe. 

Any help would be a bonus at this moment.

---

### Post by yota on 2008-03-04
Hi pcjunkie,

setting up a raid through mdadm requires some effort to learn the tool, but once the setup is done it works really well: I've various setups with RAID 0/1/5 done with it and I can say I'm really satisfied.
Usually fake-raids like the one implemented in nvidia chipsets do not work very well in linux, so I would not advise to go in that direction (dmraid is what you would need in that case).

Undoubtedly the user friendliest way to have a raid up and running in ubuntu is to install it using the "alternate cd", which can create a mdadm array automatically.
See [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) for details.

Hope this helps!

---

### Post by pcjunkie on 2008-03-06
Will take a look, cheers.

---

