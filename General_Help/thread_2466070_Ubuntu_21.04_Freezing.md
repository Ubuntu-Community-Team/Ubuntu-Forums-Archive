---
title: "Ubuntu 21.04 Freezing"
date: 2021-08-19
forum: General Help
---

### Post by lava2 on 2021-08-19
Hi, a fresh install of Ubuntu 21.04 on a Dell G3 frequently freezes on me. The mouse stops moving, alt-tab does nothing, ctrl-alt-delete does nothing.

I have Googled a bit and attempted to look at logs after powering off the machine with a long-press of the power button, but I am not sure I am looking in the right place or know exactly what to look for. The behavior does not seem to happen with any particular program running. I ran a BIOS-level diagnostic on the hardware and everything passed. 

If anyone has any ideas why this is happening or steps to help me figure it out, I would appreciate it.

---

### Post by Impavidus on 2021-08-19
Before pressing the power button, try alt+SysRq+reisub. That may prevent filesystem damage. If SysRq isn't labelled on your keyboard, it's probably the PrintScreen button. And if you're not on a qwerty keyboard, use the keys that would have been reisub if it were a qwerty keyboard.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

The log files have timestamps. Best to look for entries created in the seconds before the freeze happened, before you rebooted.

---

### Post by lava2 on 2021-08-30
Tried alt+SysRq+reisub, didn't seem to do anything at all. 

I tried switching from Wayland to Xorg, and I went a whole day without a crash so I thought that might have fixed it, but then the issue came back. I also tried switching from open source to proprietary video card drivers, but no dice. 

Can you tell me what folder I need to be looking in for logs, and what will the name of the log file be?

---

### Post by Impavidus on 2021-08-30
Logs are in /var/log. There are many of them. The file names with a number affixed are the older logs, those with .gz affixed are older compressed logs. syslog may be most likely to give a clue, but I would just check all of them at the relevant time.

---

### Post by lava2 on 2021-08-30
And what am I looking for in the logs? I see some entries are red and some just say "ERROR" - are those entries that I'm looking for and therefore the only things I should post in this thread? Or is it better to post the entirety of the log?

Here's apport.log, it's short:

```
ERROR: apport (pid 4585) Sun Aug 29 12:40:35 2021: called for pid 4425, signal 6, core limit 0, dump mode 1 
ERROR: apport (pid 4585) Sun Aug 29 12:40:35 2021: executable: /usr/lib/libreoffice/program/soffice.bin (command line "/usr/lib/libreoffice/program/soffice.bin --writer file:///home/*****/*****/******/********.docx") 
ERROR: apport (pid 4585) Sun Aug 29 12:40:35 2021: debug: session gdbus call: (true,) 
 
ERROR: apport (pid 4585) Sun Aug 29 12:40:40 2021: wrote report /var/crash/_usr_lib_libreoffice_program_soffice.bin.1000.crash
```

Here are the errors from dmesg.0:

```
[    0.458006] kernel: ACPI Error: Aborting method \_SB.PCI0.SPI1.FPNT._CRS due to previous error (AE_AML_INVALID_RESOURCE_TYPE) (20201113/psparse-529) 
[    0.458021] kernel: ACPI Error: Method execution failed \_SB.PCI0.SPI1.FPNT._CRS due to previous error (AE_AML_INVALID_RESOURCE_TYPE) (20201113/uteval-68) 
[    0.460154] kernel:  
[    0.460156] kernel:  
                       Initialized Local Variables for Method [_CRS]: 
[    0.460157] kernel:   Local0: 000000001594aaff <Obj>           Integer 0000000000000000 
[    0.460164] kernel:   Local1: 00000000c08ef710 <Obj>           Integer 0000000000000000 
[    0.460168] kernel:  
[    0.460169] kernel: No Arguments are initialized for method [_CRS] 
[    0.460170] kernel:  
[    0.460173] kernel: ACPI Error: Aborting method \_SB.PCI0.SPI2.FPNT._CRS due to previous error (AE_AML_INVALID_RESOURCE_TYPE) (20201113/psparse-529) 
[    0.460187] kernel: ACPI Error: Method execution failed \_SB.PCI0.SPI2.FPNT._CRS due to previous error (AE_AML_INVALID_RESOURCE_TYPE) (20201113/uteval-68)
```

That's pretty much it. 

I guess that first log kind of places the blame on Libreoffice, but yesterday was the first time the crash had ever happened while using that particular program.
And does the second log imply that I should try turning off ACPI?

---

### Post by Impavidus on 2021-08-31
Look for a problem that happened at the same time when your computer froze. Some logs have human-readable timestamps; the [   12.345678] timestamps indicate time in seconds since Ubuntu started loading. But it's not guaranteed that the problem is logged.

Freezes are often kernel or hardware related. You could try a different kernel. Try booting an Ubuntu 20.04.1 live disk. It has a different (older) kernel.

FYI, I only once had a kind of freezing problem in 15 years of using Ubuntu. It's the only problem I ever diagnosed using the logs. I found the error message in the logs and Google found the bugreport belonging to it. It wasn't a complete freeze; it was a lockup of one CPU core at a time. After the first core locked up, the other cores would lockup within a few minutes, making the system completely unresponsive. But with only one or two cores locked up, I could still save my work and reboot the system, unlocking the CPU. This was solved with a kernel update.

---

### Post by lava2 on 2021-09-01
So the logs I posted above, were the only logs in /var/logs that were within an hour of yet still prior to the time of the crash. That's all that was in there. Are there other places to look?

---

### Post by tea for one on 2021-09-01
> **lava2 said:**
> Tried alt+SysRq+reisub, didn't seem to do anything at all.

Ubuntu does not ship with REISUB fully enabled.

It can be enabled by editing a system configuration file:-
```
sudo nano /etc/sysctl.d/10-magic-sysrq.conf
```
Then change the number in line 26 from 176 to 244 i.e. **kernel.sysrq = 244**

I found the solution at this site [https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/](https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/) and the information was in section 3.

By the way, the last letter in the process **B** reboots your system, sometimes you may want to power off completely by substituting the **B** for an **O**

---

### Post by lava2 on 2021-09-04
Thanks for the advice. That's a handy page. I am currently running the low latency kernel - do you think it's possible that if I switched to the standard kernel in GRUB that it might fix the issue?

---

### Post by tea for one on 2021-09-05
> **lava2 said:**
>  I am currently running the low latency kernel - do you think it's possible that if I switched to the standard kernel in GRUB that it might fix the issue?

It is worth a try.

Secondly, I believe that your device has a NVME drive?

Is this info any help [https://tekbyte.net/2020/fixing-nvme-ssd-problems-on-linux/?](https://tekbyte.net/2020/fixing-nvme-ssd-problems-on-linux/?)

---

### Post by lava2 on 2021-09-06
> **tea for one said:**
> It is worth a try.

Secondly, I believe that your device has a NVME drive?

Is this info any help [https://tekbyte.net/2020/fixing-nvme-ssd-problems-on-linux/?](https://tekbyte.net/2020/fixing-nvme-ssd-problems-on-linux/?)

Unfortunately, I'm using a SATA SSD, not NVME. But thank you.

I just ran for two days without a crash on an Ubuntu 20.04 flash drive, so perhaps it is a 21.04 kernel issue. I will try running on the standard kernel and not low-latency to see what happens.

---

### Post by mIk3_08 on 2021-09-06
> **lava2 said:**
> Unfortunately, I'm using a SATA SSD, not NVME. But thank you.
I just ran for two days without a crash on an Ubuntu 20.04 flash drive, so perhaps it is a 21.04 kernel issue. I will try running on the standard kernel and not low-latency to see what happens.

If the 21.04 didn't work on your hardware system. For me, maybe it could be the
kernel hardware support issue. Because mostly new releases issue encounter this 
new hardware issues support. It maybe the new releases 21.04 has not yet scheduled 
for enablement to a newer platforms and components that required functionality 
delivered in these newer kernels. That is why 21.04 has not yet mark as LTS. 
Its the LTS Enablement Rolling Update. 
Good luck and regards.

---

### Post by lava2 on 2021-09-06
I tried the following kernels:

5.11.0-31-lowlatency
5.11.0-31-generic
5.11.0-25-lowlatency
5.11.0-25-generic

All of them still crash. Guess I need to go back and do a fresh install of 20.04 and forget about using 21.04 for the time being.

---

### Post by lava2 on 2021-09-15
This problem was fixed by reverting to 20.04. Always stick with the LTS release, I guess.

---

