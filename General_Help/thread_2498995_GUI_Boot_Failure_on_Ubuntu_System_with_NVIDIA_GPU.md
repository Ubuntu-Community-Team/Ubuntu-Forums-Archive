---
title: "GUI Boot Failure on Ubuntu System with NVIDIA GPU"
date: 2024-07-07
forum: General Help
---

### Post by joepareti54 on 2024-07-07
[COLOR=#333333][FONT=&amp]**System Configuration:**[/FONT][/COLOR]

[LIST]
[*]**Operating System:** Ubuntu 20.04.1 LTS
[*]**Kernel Version:** 5.15.0-58-generic
[*]**GPU:** NVIDIA GeForce RTX 2060
[*]**NVIDIA Driver Version:** 530.41.03
[*]**CUDA Version:** 12.1
[/LIST]
[COLOR=#333333][FONT=&amp]**Problem Description:** I am experiencing a persistent issue where my Ubuntu system fails to boot in GUI mode but boots successfully in CLI recovery mode. This issue has emerged despite the driver and kernel combination previously functioning without issues. The system is configured to dual boot with Windows, which operates without any problems, suggesting that the hardware is functioning correctly.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]**Symptoms:**[/FONT][/COLOR]

[LIST]
[*]The system hangs when attempting to boot into GUI mode.
[*]It is possible to initiate an xterm session through startx from CLI mode, indicating that some graphical operations are possible.
[*]The failure occurs regardless of whether the system is booted normally into Ubuntu or resumed from a recovery session to GUI mode.
[/LIST]
[COLOR=#333333][FONT=&amp]**Troubleshooting Steps Taken:**[/FONT][/COLOR]

[LIST=1]
[*]Reinstalled NVIDIA drivers and reconfigured them multiple times.
[*]Checked and monitored system logs for errors related to NVIDIA drivers and Xorg.
[/LIST]
[COLOR=#333333][FONT=&amp]**Critical Errors Observed:**[/FONT][/COLOR]

[LIST]
[*]Repeated failures related to the NVIDIA kernel module initialization.
[*]Xorg log files indicate issues with device recognition and configuration that seem to stem from NVIDIA driver interactions.
[/LIST]
I incude a report generated upon recommendation by Nvidia.

[COLOR=#333333][FONT=&amp]I would appreciate any guidance to resolve this issue, recommendations for further diagnostic tests or configuration adjustments.[/FONT][/COLOR]

---

### Post by oldfred on 2024-07-07
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

#What is installed
dkms status

Are you installing nVidia driver from Ubuntu repository.
You do not need ppa anymore and should not install directly from nVidia with its .run file.
Are you purging before a new install of driver. Otherwise you get conflicts and issues.

Purge & reinstall
If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://askubuntu.com/questions/1478024/how-do-i-install-an-arbitrary-proprietary-nvidia-gpu-driver-on-ubuntu-studio-22](https://askubuntu.com/questions/1478024/how-do-i-install-an-arbitrary-proprietary-nvidia-gpu-driver-on-ubuntu-studio-22)
[https://askubuntu.com/questions/813676/installing-ubuntu-mate-with-dual-boot-option-on-windows-10-usb-booting-not-hap/814413#814413](https://askubuntu.com/questions/813676/installing-ubuntu-mate-with-dual-boot-option-on-windows-10-usb-booting-not-hap/814413#814413)

What brand/model system?

Is firmware updated to latest available?
MSI X570 ACE motherboard and Nvidia RTX 2070 SUPER GPU.Asus
[https://askubuntu.com/questions/1317921/ubuntu-20-04-lts-needs-bios-reset-after-each-reset-to-boot](https://askubuntu.com/questions/1317921/ubuntu-20-04-lts-needs-bios-reset-after-each-reset-to-boot)

[https://www.phoronix.com/news/NVIDIA-Big-GSP-Firmware-Dump](https://www.phoronix.com/news/NVIDIA-Big-GSP-Firmware-Dump)

---

### Post by joepareti54 on 2024-07-12
yes I install from .run file. I have a lot of details in the log file

---

