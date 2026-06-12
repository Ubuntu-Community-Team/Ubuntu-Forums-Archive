---
title: "New to Ubuntu. Important Logs?"
date: 2022-07-14
forum: General Help
---

### Post by 11draft on 2022-07-14
[COLOR=#1A1A1B]Hey,  I just went from Windows 10 to Ubuntu 22.04 within the last 72 hours.  First thing I'll say is, I'll never go back to Windows again. Ubuntu  makes my laptop happy. No loud fan sound anymore, faster, smoother,  makes more sense all around, looks better, etc etc. The only thing I'm  having an issue with, is when I go to Show Applications > Utilities  > Logs, I get these messages



20:15:16 systemd: Failed to start Tracker metadata extractor.

20:15:16 systemd: Failed to start Tracker metadata extractor.
20:14:47 systemd: Failed to start Application launched by gnome-session-binary.
20:14:47 systemd: Failed to start Application launched by gnome-session-binary.
20:14:47 systemd: Failed to start Application launched by gnome-session-binary.
20:14:15 kernel: mtd device must be supplied (device name is empty)
20:14:15 kernel: mtd device must be supplied (device name is empty)
20:14:06 kernel: mtd device must be supplied (device name is empty)
20:14:06 kernel: x86/cpu: SGX disabled by BIOS.
20:14:06 kernel: x86/cpu: SGX disabled by BIOS.
20:14:06 kernel: x86/cpu: VMX (outside TXT) disabled by BIOS


Is  there anything that I need to do? I would 100% appreciate help if any  is offered. Thank you, and have a great evening! The computer is running  perfectly fine, I just happened to notice the messages in the logs.

[/COLOR]

---

### Post by dragonfly41 on 2022-07-14
BIOS setting?

[https://askubuntu.com/questions/1406760/sgx-disabled-by-bios-in-ubuntu-22-04](https://askubuntu.com/questions/1406760/sgx-disabled-by-bios-in-ubuntu-22-04)

---

### Post by grahammechanical on 2022-07-14
A little knowledge is a dangerous thing. So, some information.

SGX = Software Guard Extensions.

[https://en.wikipedia.org/wiki/Software_Guard_Extensions](https://en.wikipedia.org/wiki/Software_Guard_Extensions)

Your SGX are disabled in the BIOS settings utility, which is properly called UEFI settings. You can leave them disabled or enable them. It is your choice. My laptop with Ubuntu pre-installed has SGX enabled. It does not prevent Ubuntu from loading.

VMX = Virtual Machine Extensions 

[https://superuser.com/questions/1584771/what-is-difference-between-vmx-and-vt-x](https://superuser.com/questions/1584771/what-is-difference-between-vmx-and-vt-x)

MTD = Memory Technology Device.

[https://en.wikipedia.org/wiki/Memory_Technology_Device](https://en.wikipedia.org/wiki/Memory_Technology_Device)

I am still none the wiser. :)

Regards

---

### Post by 11draft on 2022-07-14
Thank you fellas. I'll just leave the important logs in the same format, since they are posing me no issues. I appreciate you both taking your time to help me! Have a blessed evening or day!

---

### Post by mIk3_08 on 2022-07-15
On how to mark this thread as solve,
Please Click the "[COLOR=#ff0000]**Solve thread**[/COLOR]" link below. Regards and cheers.

---

