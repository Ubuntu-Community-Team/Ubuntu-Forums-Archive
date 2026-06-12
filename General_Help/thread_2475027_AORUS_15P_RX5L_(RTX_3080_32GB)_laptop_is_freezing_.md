---
title: "AORUS 15P RX5L (RTX 3080 32GB) laptop is freezing on Ubuntu 20.04"
date: 2022-05-14
forum: General Help
---

### Post by ptynecki on 2022-05-14
Dear community members, 

I have a new model of AORUS 15P RX5L notebook on my desk. The model name is SN21210J001585 with BIOS version FB03 and CPU model 11th Gen Intel(R) Core&#8482; i7-11800H.

I installed Ubuntu 20.04 64bit and upgraded GPU drivers from default to NVIDIA 510.60.02 and CUDA 11.6. Default kernel version was 5.13+.

After a few minutes of doing daily work on this machine I my desktop is freezing. I cannot use mouse or keyboard but was able to connect to it via SSH using second machine. In htop I discovered that Xorg is consuming 100% CPU: 

The process name:

```
/usr/lib/xorg/Xorg vt2 -displayfd 3 -auth /run/user/1000/gdm/Xauthority -background none -noreset -keeptty -verbose 3
```

I can reproduce that problem using external monitor with HDMI or without it. During the freeze I am not using CPU/GPU so much (I did not launch any AI calculations). NVIDIA was set up as prime GPU.

```
$ prime-select query
nvidia
```

Furthermore, I upgraded Linux kernel from 5.13+ to 5.17+ and reinstall NVIDIA drivers but it does not help at all.

Help me to diagnose the root of the problem.

Regards, Piotr

---

### Post by DuckHook on 2022-05-14
Welcome to the forums, ptynecki.

Since you are asking for help, I have moved your thread to a more appropriate sub&#8209;forum.

Also, please use standard fonts and styles when posting. Unusual formatting does not display properly on some browsers or on smaller screens.

*Thread moved to **General Help** as the more appropriate forum.*

---

### Post by #&amp;thj^% on 2022-05-14
When's the last you updated?
you "should" get a little better response on X11 session with:
```
nvidia-smi
Sat May 14 12:09:29 2022       
+-----------------------------------------------------------------------------+
|** NVIDIA-SMI 515.43.04    Driver Version: 515.43.04    CUDA Version: 11.7    ** |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA GeForce ...  Off  | 00000000:01:00.0  On |                  N/A |
| N/A   38C    P8     3W /  N/A |    370MiB /  4096MiB |      7%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A       617      G   /usr/lib/Xorg                     227MiB |
|    0   N/A  N/A      1017      G   xfwm4                               2MiB |
|    0   N/A  N/A      5723      G   /usr/lib/firefox/firefox          137MiB |
+-----------------------------------------------------------------------------+

```

---

### Post by ptynecki on 2022-05-14
Are you suggesting to install beta version of NVIDIA driver 515.43.04?

I am using recommended production version as I noted in the post.

---

### Post by #&amp;thj^% on 2022-05-14
It's not beta in 22.04.
I've already seen your post here:[https://forums.developer.nvidia.com/t/aorus-15p-rx5l-rtx-3080-32gb-laptop-is-freezing-on-ubuntu-20-04/214431](https://forums.developer.nvidia.com/t/aorus-15p-rx5l-rtx-3080-32gb-laptop-is-freezing-on-ubuntu-20-04/214431)
with no offered suggestions.
Before I suggest anything else, we need to know if you added the suggestion from that forum:
"[B] kernel parameter
intel_idle.max_cstate=1[/B]" >>and if made any difference?
Up to you, if they name it beta, then that's how i'll treat it in your use.
I've been on it for a full day now I have zero problems. this is on a newer version than you run 20.04.

---

