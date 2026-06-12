---
title: "audio issues - 7.1 vs 5.1"
date: 2023-01-28
forum: General Help
---

### Post by michael351 on 2023-01-28
I have Ubuntu 22.04 installed with a GP108 (GeForce 1030) HDMI audio/graphics card on a Dell optiplex 7020 SFF computer.

I use this system as a home theater PC with 7.1 speakers. I use HDMI from the PC connected to a Marantz multi-channel processor.
All worked perfectly for years. I update ubuntu regularly.

Recently, however, I notice I no longer have 7.1 channels working. When I test the speakers, the front, center and right speakers have no sound when 7.1 is specified.
When I change to 5.1, sound returns to the front, center and right speaker, but the rear left and right no longer play.

Is there anything I can do or is this just a bug introduced with the HDMI drivers (nvidia)

Nvidia-smi reports:
> 
-----------------------------------------------------------------------------+
| NVIDIA-SMI 525.78.01    Driver Version: 525.78.01    CUDA Version: 12.0     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA GeForce ...  Off  | 00000000:01:00.0 Off |                  N/A |
| 36%   31C    P8    N/A /  30W |     74MiB /  2048MiB |      0%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A      4872      G   /usr/lib/xorg/Xorg                 56MiB |
|    0   N/A  N/A      5002      G   /usr/bin/gnome-shell               16MiB |
+-----------------------------------------------------------------------------+

Any help appreciated. My movies just don't play the same anymore like they use to.

---

