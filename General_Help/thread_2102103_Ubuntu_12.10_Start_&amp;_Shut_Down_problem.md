---
title: "Ubuntu 12.10 Start &amp; Shut Down problem"
date: 2013-01-06
forum: General Help
---

### Post by altintasi on 2013-01-06
Hi folks.

I'm an Ubuntu user since 5-6 years. I have a problem with Ubuntu 12.10 x86. Problem is a little weird.

I can install 12.10 without any problem. My PC is working very well after first start. But..

When i want to shut down, star or restart my pc problems are starting.

1-If i want to start my pc, there is nothing to happen. Pc start bu there is no bios screen or smth like that. Then i can shut down pc pressing on power button for 5 seconds. After that i can start my pc without any problem.

2-If i want close my pc, ubuntu is closing but hardware dont close and freeze on purple screen. This situation is also happens trying to restart.

I havent any problem when i want to use Ubuntu 12.04, Linux Mint 13 and others.

This problem is also avaliable on Ubuntu 12.10 based OS. (Voyager XFCE, Mint 14, Xubuntu 12.10 etc..)

I googled and find a few problem posts but there is no solution. I think this problem is about Windows Secure Boot. I dont use any Windows. I installed only Ubuntu.

Thanks for reply..:popcorn:

My laptop is TOSHIBA Satellite A100-036(PSAANE-03K00RTE)

---

### Post by Muratturat on 2013-01-06
> **altintasi said:**
> Hi folks.

I'm an Ubuntu user since 5-6 years. I have a problem with Ubuntu 12.10 x86. Problem is a little weird.

I can install 12.10 without any problem. My PC is working very well after first start. But..

When i want to shut down, star or restart my pc problems are starting.

1-If i want to start my pc, there is nothing to happen. Pc start bu there is no bios screen or smth like that. Then i can shut down pc pressing on power button for 5 seconds. After that i can start my pc without any problem.

2-If i want close my pc, ubuntu is closing but hardware dont close and freeze on purple screen. This situation is also happens trying to restart.

I havent any problem when i want to use Ubuntu 12.04, Linux Mint 13 and others.

This problem is also avaliable on Ubuntu 12.10 based OS. (Voyager XFCE, Mint 14, Xubuntu 12.10 etc..)

I googled and find a few problem posts but there is no solution. I think this problem is about Windows Secure Boot. I dont use any Windows. I installed only Ubuntu.

Thanks for reply..:popcorn:

My laptop is TOSHIBA Satellite A100-036(PSAANE-03K00RTE)

Did you installed ubuntu before windows or after windows or inside of windows?

---

### Post by altintasi on 2013-01-06
Before yes, i used Windows. Actually in installed Windows 8 a few months ago. But i dislike dual boot. So if i use an operation system, i install only which i want to use..

---

### Post by Muratturat on 2013-01-07
> **altintasi said:**
> Before yes, i used Windows. Actually in installed Windows 8 a few months ago. But i dislike dual boot. So if i use an operation system, i install only which i want to use..

I had the same problem 2 years ago with  my laptop.
This should work 
Type in terminal:
1. sudo gedit /etc/default/grub
2. Find the line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
3. Change this to: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
4. Save the file and close the file. 
5. And then sudo update-grub

---

### Post by altintasi on 2013-01-08
Thanks a lot. I will try your suggestion. I'll reply the result.;)

---

