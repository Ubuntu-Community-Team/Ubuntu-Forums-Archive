---
title: "Black screen after screen lock"
date: 2022-06-29
forum: General Help
---

### Post by csete on 2022-06-29
I'm running latest Ubuntu 22.04 on a Dell XPS 15 (9500).  Recently I'm having an issue when my screen is blanked and locked.  In those cases, if I move the mouse or keyboard, the keyboard backlight comes on (the machine is alive), but the screen stays off.  I've found that I can use Ctrl-Alt-F1 to get it to turn on, but I end up at what appears to be the initial GDM login screen rather than the unlock screen (the one that allows user selection).  Interestingly, after I log in there, I do end up back at my desktop with all applications still as they were.  Thus, this is not a critical issue, but it is kind of annoying.  Does anyone have any thoughts?  I'm running Wayland on a hybrid Intel/NVidia setup, with Intel selected via prime-select.

Thanks,
Craig

```
&#9584;&#9472;&#10148;  uname -a
Linux XPS-15-9500 5.15.0-40-generic #43-Ubuntu SMP Wed Jun 15 12:54:21 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

```

```
&#9584;&#9472;&#10148;  nvidia-detector 
nvidia-driver-515

```

```
&#9584;&#9472;&#10148;  nvidia-smi
Wed Jun 29 09:12:53 2022       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 510.73.05    Driver Version: 510.73.05    CUDA Version: 11.6     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA GeForce ...  Off  | 00000000:01:00.0 Off |                  N/A |
| N/A   39C    P0     6W /  N/A |      2MiB /  4096MiB |      0%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A      3234      G   /usr/bin/gnome-shell                1MiB |
+-----------------------------------------------------------------------------+

```

---

### Post by #&amp;thj^% on 2022-06-29
Known problem for wayland, here is list of your issue: [https://www.google.com/search?client=firefox-b-1-d&q=wayland+dosent+come+back+after+screen+lock](https://www.google.com/search?client=firefox-b-1-d&q=wayland+dosent+come+back+after+screen+lock)

---

### Post by csete on 2022-06-29
> **1fallen said:**
> Known problem for wayland, here is list of your issue: [https://www.google.com/search?client=firefox-b-1-d&q=wayland+dosent+come+back+after+screen+lock](https://www.google.com/search?client=firefox-b-1-d&q=wayland+dosent+come+back+after+screen+lock)

Thanks.  Are you aware of a specific Launchpad bug?

---

### Post by #&amp;thj^% on 2022-06-29
Nobody here cares enough to file a bug against wayland.
[https://github.com/GSConnect/gnome-shell-extension-gsconnect/issues/1241](https://github.com/GSConnect/gnome-shell-extension-gsconnect/issues/1241)

[https://bugs.launchpad.net/ubuntu/+bug/1975884](https://bugs.launchpad.net/ubuntu/+bug/1975884)

[https://bugzilla.redhat.com/show_bug.cgi?id=1653026](https://bugzilla.redhat.com/show_bug.cgi?id=1653026)

I could go on and on but I won't

---

### Post by csete on 2022-06-29
> **1fallen said:**
> Nobody here cares enough to file a bug against wayland.

Out of interest, why is that?  I thought Wayland was the way of the future?

---

