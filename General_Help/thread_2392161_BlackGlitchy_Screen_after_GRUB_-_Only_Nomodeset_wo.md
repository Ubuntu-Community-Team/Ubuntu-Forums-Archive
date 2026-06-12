---
title: "Black/Glitchy Screen after GRUB - Only Nomodeset working"
date: 2018-05-17
forum: General Help
---

### Post by foxtrotbalpha on 2018-05-17
Greetings,
This is my first post here, so I'm still pretty rookie when it comes to fixing stuff in Ubuntu.

Yesterday I had my Ubuntu 18.04 system do updates before shutting down my desktop, after that I got the infamous black screen after GRUB, indicating a problem with video drivers after the update, now I can only boot using nomodeset command on GRUB command lines, but I don't know how to fix it and reinstall the drivers so I can boot and use hardware video again.

I have a AMD RX470 video card, I had the default driver that came with the Ubuntu install (Mesa I believe, but I'm not sure), how can I reinstall it and reconfigure Xorg to have it working properly without nomodeset again? 

Running the lshw -c video doesn't gives me any driver info, the output is:
"configuration: latency=0"


Thanks in advance for any help

---

### Post by foxtrotbalpha on 2018-05-17
I've tried to make a reinstall of Ubuntu via Live USB, managed to still save my personal data, but very oddly I still needed to use nomodeset even on the Live USB! 
Or else I'd get glitchy colored pixels on the boot from the USB, then after the installation Ubuntu added nomodest itself on my GRUB config file, I tried to remove it and boot with no luck, the same problem even after a reinstall. 
I can't believe I'm wasting over 20 hours of work just because of a random update that broke my whole system.  

Interesting fact: If I run the command:```
 lspci -nnk | grep -i vga -A3 
```
I get the following result:
```

09:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480] [1002:67df] (rev cf)
    Subsystem: PC Partner Limited / Sapphire Technology Radeon RX 470 [174b:e349]
    Kernel modules: amdgpu
09:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 580] [1002:aaf0]


```

AMDGPU is installed somewhere but not being used by my kernel, how can I force my kernel to run it?

---

