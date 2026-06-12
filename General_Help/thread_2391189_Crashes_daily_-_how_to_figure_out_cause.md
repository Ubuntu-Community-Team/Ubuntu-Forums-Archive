---
title: "Crashes daily - how to figure out cause?"
date: 2018-05-07
forum: General Help
---

### Post by primuspaul on 2018-05-07
I have a Ubuntu desktop. It used to work fine until the Nvidia GPU started overheating (fan broke). The PC would also crash.

I took it out and started running with onboard video while I wait for a new card, but now it crashes a few times a day. Is there a way to figure out the cause?

---

### Post by primuspaul on 2018-05-10
Does anyone have any ideas? I also noticed that often the system crashes with blocky artifacts on screen. My guess is the integrated GPU hardware is messed up, but I never noticed it since I have always been using the PCIe GPU in the past.

---

### Post by primuspaul on 2018-05-10
Getting the same graphic artifacts and crash in SLAX (USB boot) and BIOS, so obviously a hardware issue.

If I'm getting artifacts before crashes, is it pretty much guaranteed to the the MOBO GPU? In which case, the only option is to replace motherboard?

---

### Post by primuspaul on 2018-05-17
Problem appears to be solved. Caused by poorly greased motherboard heat sinks causing the motherboard chips to overheat. Apparently they use some crappy "glue" to attach the heat sinks to motherboards and these lead to poor conduction of heat, especially over time. I applied some thermal grease after removing and cleaning the heat sinks and the system stayed up for almost a day until I shut it down manually. Before it was crashing on build in video after only half an hour.

---

