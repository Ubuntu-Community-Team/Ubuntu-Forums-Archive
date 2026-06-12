---
title: "Ubuntu 16.04 [gnome desktop] boots into a blank screen with a cursor on it."
date: 2017-08-22
forum: General Help
---

### Post by anidxi on 2017-08-22
Hey guys!

I've just dual booted my windows laptop with Ubuntu Gnome 16. I am not a new user, and have used linux in the past.

A disclaimer: I know that there are several posts which describe similar issues, and trust me when I say that I've tried to do most of the listed solutions - I have modified the grub command line with **radeon.modeset=0 and ****i915.modeset=0**, as well as **[B]grub_gfxmode**=1024x768x16  [/B]to try and bring up the login screen, but I had no success.  I've tried running **/chmod 755 /home** from the root terminal in the recovery mode setup.  I've uninstalled xdiagnose, and tried reconfiguring system/dpkg. 

I had the same problem with Linux Mint 18.2, which I had just prior to installing ubuntu.

When I try accessing the tty1 terminal (or any terminal for that matter), I can't login as I am simply flashed with a welcome message (that contains OS version, kernel version (4.4.0.21 and details about number of updates available) for a nano-second before the screen goes blank for about 5 seconds, before getting back to the tty1 login page. 

I had a similar problem with my installation of linux mint, except in that case the welcome message also displayed "setmntent: Permission denied". 

I have had issues with installing linux for a long time now - I could never get grub to install in the past, though seemed to be an issue with my EFI partitions that I assume had figured out already, the grub bootloader has installed since.

Laptop Specs: Intel Core i5 6200U + AMD Radeon R5 M335 on a hard drive whose partition table is GPT.


Any help would be appreciated. Thank you.

[B]SOLUTION - this worked for me: 
[/B]1. Boot to recovery mode and access the root terminal. In the root terminal, run the folllowing 2 commands:
```
chmod 777 /
shutdown -r
```
2. Then, when you reboot, you should be able to access the terminals from tty1 through 6. On any, log in and run **sudo apt-get upgrade**.
3. After all the updates are downloaded and installed, again restart by using  [B]shutdown -r.
[/B]4. Your startup will be slow, and for a while your laptop will probably boot into tty1, and you can see flashing, what should be your desktop. This implied that the display manager was not working/ non-exixtent, as with my case.
5. Your login page probably will turn up now, but you will not be able to login - the screen will go blank and turn back into the login page.
6. Now, go to tty1 and type the following out, serially one after the other: 
```

service lightdm stop //will ask you to authenticate, and might tell you that lightdm.service doesn't exist
sudo su - 
cd /usr/local/bin
wget -Nc smxi.org/sgfxi
chmod +x sgfxi
sgfxi -c
```

7. Follow the instructions as they pop up. I installed the drivers for the integrated Intel HD 520, and the Radeon failed to install.
8. Reeboot using **shutdown -r**.

And you should be done.

---

### Post by BenginM on 2017-08-22
Hiya , Welcome to the forums.

as the Intel core i5 6200U has a built-in Intel integrated graphic HD 520 . the system might be having a driver conflict 
the Radeon R5 M335 is only a bit more powerful than the HD 520 ..
   I suggest you disable the integrated intel's GPU from the BIOS , and boot with the AMD as the driver radeon is loaded in the kernel , and/or vise-versa .

 you should remove those kernel boot parameters (**radeon.modeset=0 and ****i915.modeset=0 , [B][B]grub_gfxmode**=1024x768x16  from the kernel line in grub and boot with the default .

and am not sure if the AMD R5 M335 is supported by the amdgpu , or amdgpu-pro .. if you run $ lspci , tell us the device ID ..
[/B][/B]

---

### Post by anidxi on 2017-08-23
Hey! Thanks for your post.


My BIOS did not have an option to disable any video cards - I updated it to a newer version, but there was no difference. My laptop uses an Insyde H20 BIOS. 


I ran **lspci** from a live USB and this is what I get: 
> 
00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation Sky Lake Integrated Graphics (rev 07)
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 08)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Sun XT [Radeon HD 8670A/8670M/8690M / R5 M335] (rev ff)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 07)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter


UPDATE:
After that, I accessed the root terminal in the recovery mode and ran **chmod 777 /**. After that, I got a blank screen with a mouse pointer on it. And also I could login to the tty terminal so I ran sudo apt-get upgrade. I'll update you when it's done.

UPDATE 2: 
After the update, the login screen opens up but doesn't log me in. I still can log into any of the tty terminals

---

### Post by anidxi on 2017-08-23
The following steps worked for me


1. Boot to recovery mode and access the root terminal. In the root terminal, run the folllowing 2 commands:
```
chmod 777 /
shutdown -r
```
2. Then, when you reboot, you should be able to access the terminals from tty1 through 6. On any, log in and run **sudo apt-get upgrade**.
3. After all the updates are downloaded and installed, again restart by using  [B]shutdown -r.
[/B]4. Your startup will be slow, and for a while your laptop will  probably boot into tty1, and you can see flashing, what should be your  desktop. This implied that the display manager was not working/  non-exixtent, as with my case.
5. Your login page probably will turn up now, but you will not be able  to login - the screen will go blank and turn back into the login page.
6. Now, go to tty1 and type the following out, serially one after the other: 
```

service lightdm stop //will ask you to authenticate, and might tell you that lightdm.service doesn't exist
sudo su - 
cd /usr/local/bin
wget -Nc smxi.org/sgfxi
chmod +x sgfxi
sgfxi -c
```

7. Follow the instructions as they pop up. I installed the drivers for  the integrated Intel HD 520, and the Radeon failed to install.
8. Reeboot using **shutdown -r**.

And you should be done.

---

