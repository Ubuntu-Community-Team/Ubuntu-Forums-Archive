---
title: "Help me identify what's wrong with my system"
date: 2019-12-30
forum: General Help
---

### Post by kaanalpar on 2019-12-30
Hi everyone, I hope everybody is having a good day. I'm having issues with my GPU and I'm not sure what is going on, so please help me identify it.

This is my laptop: [COLOR=#111111][FONT=&quot]Acer Aspire E 15 Laptop, 15.6" Full HD, 8th Gen Intel Core i5-8250U, GeForce MX150, 8GB RAM Memory, 256GB SSD, E5-576G-5762

As you can see I have a GeForce MX150 graphics card but I'm suspecting that my system is not using it. My CPU usage is very high even when watching YouTube or just having the steam launcher open. Nothing launches when I click Nvidia XServer Setting on activities.

$nvidia-settings
[/FONT][/COLOR]ERROR: Unable to find display on any available system

Also inside Settings -> Details -> About my graphics is Intel® UHD Graphics 620 (Kabylake GT2)
I'm assuming this should be Nvidia but I also learned that some cards have hybrid functionality and not sure if this is how it would be.

I have nvidia-driver-435 selected on Software and Updates -> Additional Drivers

And nvidia-smi shows this, although no processes i ever listed under processes even when I'm playing games which should be using the GPU.
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 435.21       Driver Version: 435.21       CUDA Version: 10.1     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce MX150       Off  | 00000000:01:00.0 Off |                  N/A |
| N/A   39C    P8    N/A /  N/A |      0MiB /  2002MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+

---

### Post by oldrocker99 on 2019-12-30
You have to enable the nVidia card in your BIOS, I think. It's not the OS.

---

### Post by kaanalpar on 2019-12-30
I don't think that's the issue. I actually ended up reinstalling Ubuntu and it works now. BIOS is the same.

---

