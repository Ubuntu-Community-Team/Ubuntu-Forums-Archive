---
title: "Hang problem"
date: 2021-03-30
forum: General Help
---

### Post by soumyadipbarman on 2021-03-30
Hello,

My desktop configuration is : i7 processor, 16 GB RAM, 1 TB HDD, 256 GB SSD, nvidia graphics card - GeForce GT 710/PCIe/SSE2 / NVIDIA Corporation GK208B [GeForce GT 710].
OS : Ubuntu 20.04.2 LTS

The machine hangs randomly. Sometimes the mouse works and sometimes completely freezes. But i can log into the machine from different machine using ip address. So, I guess it is graphics problem,

The output of this command lspci -k | grep -A 2 -i "VGA" -
01:00.0 VGA compatible controller: NVIDIA Corporation GK208B [GeForce GT 710] (rev a1)
	Subsystem: NVIDIA Corporation GK208B [GeForce GT 710]
	Kernel driver in use: nvidia
 INTEL graphics is not showing. But whenever I use "[COLOR=#000000][FONT=&quot]sudo prime-select intel[/FONT][/COLOR]", the machine dont reboot. it remains blank screen after that process. 

Suggestions will be helpful.

Thanks,
Soumyadip

---

### Post by Autodave on 2021-03-30
You do not want to use the Intel graphics: that is what is on your motherboard.  And since you have an nVidia card, your monitor is not hooked up to the motherboard but rather to the nVidia card. 

Now, what version of 'buntu are you using?  What, if any, driver for the nVidia card are you using and where did you get it from?

The command that you are trying to run doesn't apply to desktops: that is for laptops that have 2 graphics cards built in.

---

### Post by soumyadipbarman on 2021-03-31
I am using [COLOR=#000000]Ubuntu 20.04.2 LTS.[/COLOR]
[COLOR=#000000]I have downloaded NVIDIA graphics driver from "update software". And i am using NVIDIA-460 driver.[/COLOR]

---

