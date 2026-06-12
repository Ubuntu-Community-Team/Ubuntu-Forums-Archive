---
title: "Title bar buttons disappear and random colored stripes appear"
date: 2017-04-24
forum: General Help
---

### Post by sayantan-auddy on 2017-04-24
Hello everyone,

For a few days now I have been having this problem whenever my laptop wakes up from sleep. The minimize, close, maximize buttons disappear from the title bar and some randomly colored stripes and pixels appear around the edges of windows. The problem goes away after a fresh restart. I also have Windows 8.1 installed on my computer and that works without any similar problem, so I am guessing that it is not a hardware related error. I have a NVidia GeForce 930M graphics card on an Asus X555LF laptop (running Intel core i3) and my Ubuntu version is 14.04. I have also reinstalled the latest NVidia driver but the problem persists. Please find below a screenshot of the problem.

[ATTACH=CONFIG]274741[/ATTACH]

Some relevant details

uname -a
Linux sayantan-X555LF 3.19.0-80-generic #88~14.04.1-Ubuntu SMP Fri Jan 13 14:54:07 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

$ nvidia-smi 
Mon Apr 24 12:13:53 2017       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 375.39                 Driver Version: 375.39                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce 930M        Off  | 0000:04:00.0     Off |                  N/A |
| N/A   37C    P5    N/A /  N/A |    158MiB /  2002MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+

+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID  Type  Process name                               Usage      |
|=============================================================================|
|    0      1610    G   /usr/bin/X                                      92MiB |
|    0      2402    G   compiz                                          21MiB |
|    0      2750    G   ...s-passed-by-fd --v8-snapshot-passed-by-fd    44MiB |
+-----------------------------------------------------------------------------+


I have searched in the ubuntu forums but haven't been able to find a proper solution. If anyone knows of a thread that addresses this issue, please provide a link. It would be really helpful if someone can help me find a solution. Please let me know if any further information is required.

Best,
Sayantan

---

### Post by vasa1 on 2017-04-24
[http://askubuntu.com/questions/896221/strange-artifacts-along-window-borders-after-waking-computer-from-sleep-mode](http://askubuntu.com/questions/896221/strange-artifacts-along-window-borders-after-waking-computer-from-sleep-mode) of any help?

---

### Post by Impavidus on 2017-04-24
You run kernel 3.19. That's the kernel that came with Ubuntu 14.04.3, which means you use an unsupported HWE stack. For 14.04 only the 3.13 and 4.4 kernel series are still supported. I suggest you upgrade to a supported version. Maybe some recent upgrade is incompatible with your old kernel.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by sayantan-auddy on 2017-04-28
> **vasa1 said:**
> [http://askubuntu.com/questions/896221/strange-artifacts-along-window-borders-after-waking-computer-from-sleep-mode](http://askubuntu.com/questions/896221/strange-artifacts-along-window-borders-after-waking-computer-from-sleep-mode) of any help?
[FONT=arial]
[COLOR=#000000]Thank you for the link. Updating to nvidia-381 solves the issue. However I needed to install the CUDA 8.0 toolkit ([/COLOR][http://docs.nvidia.com/cuda/cuda-ins...nux/index.html]("http://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html")[COLOR=#000000]) and doing this again replaces nvidia-381 with the buggy nvidia-375. As of now I think I will stick to the temporary solution of executing [/COLOR][COLOR=#111111]compiz --replace, but all the same it was good to know the exact cause.[/COLOR][/FONT]

---

### Post by sayantan-auddy on 2017-04-28
> **Impavidus said:**
> You run kernel 3.19. That's the kernel that came with Ubuntu 14.04.3, which means you use an unsupported HWE stack. For 14.04 only the 3.13 and 4.4 kernel series are still supported. I suggest you upgrade to a supported version. Maybe some recent upgrade is incompatible with your old kernel.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Thanks for replying. I did upgrade to the 4.4 kernel but that wasn't the cause of this problem. The problem is with the nvidia driver that I have.

---

