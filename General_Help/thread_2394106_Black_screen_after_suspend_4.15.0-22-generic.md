---
title: "Black screen after suspend 4.15.0-22-generic"
date: 2018-06-12
forum: General Help
---

### Post by Glen_Wilson on 2018-06-12
After updating (upgrading?) to 4.15.0-22-generic, my screen stays dark when resuming from suspend. Happens in both Xubuntu and Linux-Lite. I am running these systems on a Lenovo G-series laptop.

After checking everything in the world, went back to kernel 4.13.0-43-generic and everything works fine. It is not a hardware or bios issue. It is not an XFCE issue.

There's a bug in the new kernel.

If anyone hears that this has been fixed or knows (knows, not speculates) of a work around, please respond with a post in this thread.  Thanks.

---

### Post by ajgreeny on 2018-06-12
There is now a 4.15.0-23-generic kernel image; have you tried that in place of the 22 version?
I have the most recent 4.15.0-23-generic kernel running well in several machines all of which suspend and wake with no problem, so I wonder if this is a hardware specific problem with your machine.

Tell us more detail of the hardware, and also which OS version you are running.

---

### Post by designatedduff on 2018-06-12
I have the same issue on my desktop

Fresh install of 18.04 after suspend gpu fan would run constantly at  full speed. Installed nvidia 390 driver I think that fixed the fan but  now there is no display after suspend. I have installed pm utils

CPU~6 core Intel Core i7-5820K (-MT-MCP-) speed/max~1200/3600 MHz  Kernel~4.15.0-22-generic x86_64 Up~52 min Mem~1593.7/15865.9MB  HDD~128.0GB(16.5% used) Procs~264 Client~Shell inxi~2.3.56 

+-----------------------------------------------------------------------------+
| NVIDIA-SMI 390.67                 Driver Version: 390.67                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+=================  =====+======================|
|   0  GeForce GTX 950     Off  | 00000000:06:00.0  On |                  N/A |
|  0%   60C    P0    26W / 110W |    280MiB /  1999MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+

---

### Post by kappe401 on 2018-09-06
I am having a similar issue. All I get is a black screen when waking my desktop from sleep. All the hardware starts up fine but no screen. I'm using ubuntu 18.04 with the [COLOR=#000000][FONT=&amp]Latest Nvidia driver [/FONT][/COLOR][FONT=&amp][[COLOR=#000000]396.54[/COLOR]]("https://www.nvidia.com/Download/driverResults.aspx/137211/en-us")[/FONT][COLOR=#000000][FONT=&amp]. The only way I have gotten my screens to come back is to hard power down and boot back up.

If there is any info I can gather to help look further, let me know.[/FONT][/COLOR]

---

