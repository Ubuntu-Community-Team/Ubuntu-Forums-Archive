---
title: "Laptop won't wake up after suspend"
date: 2018-07-10
forum: General Help
---

### Post by eera5607 on 2018-07-10
Hi. I have a laptop HP Spectre x360 with an Nvidia GeForce MX150. Yesterday I did a fresh Ubuntu 18.04 install and almost everything worked just fine. The only issue that I have is that when I suspend the laptop, when I want to use it again I only get a black screen with this message:

[187.425322] NVRM: Xid (PCI:0000:01:00): 32, Channel ID 00000000 intr 800400000

After that, I can't do anything. Just force shutdown and restart again. What can it be? I'm using the proprietary drivers (nvidia-driver-390). Suspension works fine with Nouveau drivers.

Thanks

---

### Post by eera5607 on 2018-07-11
[COLOR=#111111][FONT=Ubuntu]If anybody else is having the same issue, the solution seems to be on kernel 4.17. According to the Nvidia documentation, this type of event (meaning event 32)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]"...is logged when a fault is reported by the DMA controller which manages the communication stream between the NVIDIA driver and the GPU over the PCI-E bus. These failures primarily involve quality issues on PCI, and are generally not caused by user application actions."[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]In this case and according to the logs, the GPU (GeForce MX150) fails to power on after suspend and that would be an ACPI bug in the kernel. According to other users, this issue with this specific GPU is solved if kernel 4.17 is installed. In my case I prefer to wait until that, or a superior version is pushed for Ubuntu 18.04. If everything goes as usual, it is posible that Ubuntu 18.04.1 will come with the same kernel of Ubuntu 18.04 (4.15). And is also posible that Ubuntu 18.10 will come with kernel 4.18 or superior. In that case, Ubuntu 18.04.2 will also come with that kernel version. So it is probably going to be next year (February?) that we have a solution for this issue. Meanwhile you can use the Nouveau drivers or manually update de kernel to 4.17. I'm not sure if that is recommended or not.[/FONT][/COLOR]

---

