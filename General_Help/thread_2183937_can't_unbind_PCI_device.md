---
title: "can't unbind PCI device"
date: 2013-10-27
forum: General Help
---

### Post by spam2 on 2013-10-27
I am trying to pass a radeon 7970 to a xen virtual machine with VT-d. I've been able to this with a PCI USB card, but I can't get it to work with the video card. My dom0 is Kubuntu. 

lspci -k

02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT [Radeon HD 7970/R9 280X]
        Subsystem: Hightech Information System Ltd. Tahiti XT2 [Radeon HD 7970 GHz Edition]
         Kernel driver in use: radeon
02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT HDMI Audio [Radeon HD 7970 Series]
        Subsystem: Hightech Information System Ltd. Device aaa0
        Kernel driver in use: snd_hda_intel

To unbind 02:00.0 I can use this command: [COLOR=#181818][FONT=verdana] echo -n 0000:02:00.0 > /sys/bus/pci/drivers/radeon/unbind, I must be root to issue the command and after a few seconds it drops me back down to my regular user. lspci -k then shows this

[/FONT][/COLOR]02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT [Radeon HD 7970/R9 280X]
        Subsystem: Hightech Information System Ltd. Tahiti XT2 [Radeon HD 7970 GHz Edition]

02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT HDMI Audio [Radeon HD 7970 Series]
        Subsystem: Hightech Information System Ltd. Device aaa0
        Kernel driver in use: snd_hda_intel

So far so good. Now I try to unbind 02:00.1, I can try this with two different commands: [COLOR=#181818][FONT=verdana]echo -n 0000:02:00.1 > /sys/bus/pci/drivers/snd_hda_intel/unbind, or [/FONT][/COLOR][COLOR=#181818][FONT=verdana]echo 0000:02:00.1 > /sys/bus/pci/devices/0000:02:00.1/driver/unbind[/FONT][/COLOR]

[COLOR=#181818][FONT=verdana]
In either case the result is the same, nothing happens and my terminal hangs forever. I am forced to close the terminal, and lspci -k still shows the audio device as being bound to snd_hda_intel

I try to pass the video controller to the pciback interface

[/FONT][/COLOR][COLOR=#181818][FONT=verdana]echo 0000:02:00.0 > /sys/bus/pci/drivers/pciback/new_slot[/FONT][/COLOR]
[COLOR=#181818][FONT=verdana]echo 0000:02:00.0 > /sys/bus/pci/drivers/pciback/bind

unfortunately it doesn't work and gives the error "[/FONT][/COLOR][COLOR=#181818][FONT=verdana]-bash: echo: write error: No such device"

I have two problems, the first problem is that I can't unbind the audio device and the second problem is that pciback doesn't recognize that 0000:02:00.0 is a device. I don't know why it doesn't think there is such a device as it shows up in the output of lspci. I had no trouble following these steps to passthrough other PCI devices, but the video card is being difficult. I have asked for help with this at the Xen website and various other forums, so far nobody has responded. I very much hope that I can figure this out, please help me if you can. [/FONT][/COLOR]

---

### Post by gorm-oppermann on 2013-10-27
I would like to know this to as i also own a R9 280X.
i sort of got this working with the old KVM passthrough method on Ubuntu 13.04 / 12.04 as host by blasklistning radeon and when i restart or shutdown it drops the monitor signal and autoswitch back to the host as it should but at the point where the gpu takes over for the second time (reboot or start up after shutdown) the hole system freezes 
i think it has something to do with how the guest release or reasign the gpu becource if i use deveject script on guest the system dosent freeze but the monitor signal hangs and i have to manualy switch between input sources..

---

