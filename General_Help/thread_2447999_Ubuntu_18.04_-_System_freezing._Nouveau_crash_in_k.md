---
title: "Ubuntu 18.04 - System freezing. Nouveau crash in kern.log - nVidia K2200 - Dell T5500"
date: 2020-07-30
forum: General Help
---

### Post by Monkadelicd on 2020-07-30
This issue is  happening on an old Dell T5500 I brought home from work when we cleaned  out old systems. It was intended to be my dedicated rig when I'm on  call. Now its my all day rig since we all work from home during the  current pandemic.
 
Sometimes once or twice a day my system will crash. All 3 displays  and applications freeze. My mouse cursor stops responding. I cannot  switch virtual consoles. My only option is to hard reset with the power  button on the PC or magic sys request keys to sync, umount, and reboot.
 
I had this issue since fresh  installing a little less than a year ago or maybe 6 months ago. Its  always been Ubuntu 18.04. I tried changing to the proprietary nVidia  drivers at some point but that caused a whole host of other issues with  desktop not displaying and displays not being detected. I gave up on  that and moved back to nouveau. I just need this system to work so I can  support our customers. Corporate budgets are locked down due to the  pandemic so I can't just ask for a new workstation like I normally  would. Besides that, a new workstation wouldn't have all the cores and  memory I have now. I scavenged other PCs that were being scrapped to add  a CPU and memory to this one. I do a lot of testing in VMs so the extra  hardware really helps.
 
I've struggled with this for a while so I'm finally reaching out. I  do still have the proprietary nVidia drivers present and I'm not sure if  that's exacerbated my problem or not. That is all shown in the output  below anyway.
 
I have an old AMD Radeon 6670,  nVidia NVS 510, and nVidia Quadro  K2000D that I can swap out for troubleshooting the hardware. I haven't  done this yet but can if that will help in troubleshooting.
 nouveau errors from most recent crashs in kern.log:

```
Jul 22 16:05:30 DSHOMEUBUNTU kernel: [117409.626941] nouveau 0000:03:00.0: fifo: SCHED_ERROR 0a [CTXSW_TIMEOUT]
Jul 22 16:05:30 DSHOMEUBUNTU kernel: [117409.626954] nouveau 0000:03:00.0: fifo: runlist 0: scheduled for recovery
Jul 22 16:05:30 DSHOMEUBUNTU kernel: [117409.626969] nouveau 0000:03:00.0: fifo: channel 13: killed
Jul 22 16:05:30 DSHOMEUBUNTU kernel: [117409.626975] nouveau 0000:03:00.0: fifo: engine 0: scheduled for recovery
Jul 22 16:05:30 DSHOMEUBUNTU kernel: [117409.627610] nouveau 0000:03:00.0: Xorg[2079]: channel 13 killed!
...
Jul 23 10:13:54 DSHOMEUBUNTU kernel: [ 9642.074759] nouveau 0000:03:00.0: gr: TRAP ch 13 [00fe089000 Xorg[5804]]
Jul 23 10:13:54 DSHOMEUBUNTU kernel: [ 9642.074773] nouveau  0000:03:00.0: gr: GPC0/TPC0/MP trap: global 00000000 [] warp 3e0009  [ILLEGAL_INSTR_ENCODING]
Jul 23 10:14:10 DSHOMEUBUNTU kernel: [ 9657.536749] nouveau  0000:03:00.0: fifo: fault 00 [READ] at 0000004d01c26000 engine 00 [GR]  client 08 [GPC0/PE_2] reason 00 [PDE] on channel 13 [00fe089000  Xorg[5804]]
Jul 23 10:14:10 DSHOMEUBUNTU kernel: [ 9657.536763] nouveau 0000:03:00.0: fifo: channel 13: killed
Jul 23 10:14:10 DSHOMEUBUNTU kernel: [ 9657.536765] nouveau 0000:03:00.0: fifo: runlist 0: scheduled for recovery
Jul 23 10:14:10 DSHOMEUBUNTU kernel: [ 9657.536769] nouveau 0000:03:00.0: fifo: engine 0: scheduled for recovery
Jul 23 10:14:10 DSHOMEUBUNTU kernel: [ 9657.536774] nouveau 0000:03:00.0: fifo: engine 5: scheduled for recovery
Jul 23 10:14:10 DSHOMEUBUNTU kernel: [ 9657.536792] nouveau 0000:03:00.0: Xorg[5804]: channel 13 killed!
```
 
The pastebin link is the output from the "diagnostic" command recommended at [https://help.ubuntu.com/community/GraphicsTroubleshootingProcedure](https://help.ubuntu.com/community/GraphicsTroubleshootingProcedure)
[https://pastebin.com/u8V9f2rc](https://pastebin.com/u8V9f2rc)

---

### Post by CelticWarrior on 2020-07-30
Before troubleshooting the hardware, troubleshoot the drivers -> Try Nvidia drivers instead. Open Additional Drivers, select and apply the recommended version.

---

### Post by Monkadelicd on 2020-07-30
I tried that a couple of months ago. I was getting black screen instead of the login screen or not all displays (3 monitor setup) worked. I'll probably try the driver again then the video adapter. After that I'm just going to use a T7810 I have.

---

### Post by Monkadelicd on 2020-08-03
I swapped out the video card and moved to the proprietary drivers. The issue I had with the proprietary drivers was that I couldn't set the correct resolution on my center monitor ,HP Pavilion 32". The native resolution is 2560x1440. The nVIDIA Settings application would only show up to 1920x1080.

This time I realized the issue I was having. The DVI->HDMI adapter I was using at the monitor was a Dell model that only supported up to 1920x1080. I don't know why this wasn't a problem on the nouveau drivers. I rotated which monitor was plugged into which port on the video adapter so one of my side screens, 24" Asus 1920x1080, was using the DVI->HDMI adapter.

Its back to work today, so I'll see if I get any issues and report back here. If not I'll try a CPU and GPU stress test. I wonder if overheating isn't an issue. Its an old PC that's never had the thermal paste changed for either CPU.

---

### Post by Monkadelicd on 2020-08-10
Its been one week since I moved to proprietary drivers and swapped the card. Still no lockups. I'm willing to bet the drivers were the solution.

---

