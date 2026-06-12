---
title: "Laptop Heats Up Faster"
date: 2023-03-17
forum: General Help
---

### Post by dhelafrank on 2023-03-17
I just got an Intel core i5 laptop, first thing i did was to install Ubuntu on it, i have observed that the laptop heats up very fast even though am running only Visual Studio code.
This heating up to 54°C according to the temp monitor when the OS is idle has led to my fan always on, and it drains the batteries faster in like 1-2 hours.
This really affects my productivity as the battery health as shown by the stats is still healthy.
The OS sometimes shuts off at the range of 18-24% of battery capacity without warning.

Please any fix to this

---

### Post by mIk3_08 on 2023-03-17
> **dhelafrank said:**
> I just got an Intel core i5 laptop, first  thing i did was to install Ubuntu on it, i have observed that the laptop  heats up very fast even though am running only Visual Studio code.
This heating up to 54°C according to the temp monitor when the OS is  idle has led to my fan always on, and it drains the batteries faster in  like 1-2 hours.

Thus your laptop machine came with MS  windows? If yes, then Linux Ubuntu is not MS Windows and Linux Ubuntu  Operating System as what I have observe is very sensitive when it comes  to hardware machine. Totally, not the same with MS Windows. Thus the  processor fan seems so very noisy and loud? I also encounter this to my  laptop machine. The the processor fan is so very loud and very noisy.  What I did is just cleaning and put lubricant to the processor heat sink  fan. Then, the issue is okay now.  
> **dhelafrank said:**
> This heating up to 54°C according to the temp monitor when the OS is  idle has led to my fan always on, and it drains the batteries faster in  like 1-2 hours.

In my case, because the fan can't perform  normally which is not usual. Can't perform normally maybe because of the  build up dust that is why it consumes more power than normal. The fan temp reaches same as yours 54°C and the fan sounds goes wild. But its okay now and the temp reaches only up to 42°C. Hope it  helps. Regards and cheers.

---

### Post by Impavidus on 2023-03-17
It looks like some task is running in the background, preventing CPU throttling and converting battery energy to heat. Use top, htop, task manager or some similar tool to find what it is. Sometimes this is related to graphics drivers. Have you used to additional drivers tool to check for proprietary drivers for your hardware?

I don't think Visual Studio code is supposed to run a lot of stuff in the background, but I don't use that software myself, so can't be sure.

What version of Ubuntu did you install? There's no real reason not to use 22.04, unless you really want the latest stuff with 22.10.

---

### Post by mIk3_08 on 2023-03-17
> **Impavidus said:**
> I don't think Visual Studio code is supposed to run a lot of stuff in the background, but I don't use that software myself, so can't be sure.
Totally agree with Impavidus. 
> **dhelafrank said:**
> I just got an Intel core i5 laptop, first  thing i did was to install Ubuntu on it, i have observed that the laptop  heats up very fast even though am running only Visual Studio code.
This heating up to 54°C according to the temp monitor when the OS is  idle has led to my fan always on, and it drains the batteries faster in  like 1-2 hours.
This really affects my productivity as the battery health as shown by the stats is still healthy.
The OS sometimes shuts off at the range of 18-24% of battery capacity without warning.
Please any fix to this
To know details of your Linux Ubuntu Operating System please run this command below in your terminal and paste the results here in thread wrap with code. 
```
lsb_release -a
```
Regards and cheers.

---

