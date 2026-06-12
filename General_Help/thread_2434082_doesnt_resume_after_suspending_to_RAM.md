---
title: "doesnt resume after suspending to RAM"
date: 2019-12-30
forum: General Help
---

### Post by csowiec on 2019-12-30
Hi, i updated driver from [COLOR=#006400][FONT=Monaco]NVIDIA 390.116 to [/FONT][/COLOR]390.129 from ```
[COLOR=#333333][FONT=&amp]add-apt-repository ppa:graphics-drivers/ppa[/FONT][/COLOR]
```[COLOR=#333333][FONT=&amp] but problem still persists and i dont know where i should begin.
Thats [/FONT][/COLOR][IMG]https://i.ibb.co/hLw0Gxw/20191230-080522.jpg[/IMG][COLOR=#333333][FONT=&amp]the state after and nothing happening also i know it should blink during process. There is a booting process [/FONT][/COLOR]https://youtu.be/56BFauKNaQA . How to solve that problem?  with ```
[COLOR=#333333][FONT=Ubuntu][COLOR=#006400][FONT=Monaco]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"[/FONT][/COLOR]
[/FONT][/COLOR]

```
[COLOR=#333333][FONT=&amp]Window system doesnt load i stay under CLi.
Only 1 error which i found in xorg logging system was [/FONT][/COLOR]```
[COLOR=#006400][FONT=Monaco][    42.747] (EE) Failed to open authorization file "/var/run/sddm/{d528b25c-5377-4537-b22d-34e2cccd5490}": No such file or directory[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][FONT=inherit][FONT=Ubuntu][FONT=inherit]

[/FONT]
[/FONT]

[/FONT]
[/FONT][/COLOR]


```[COLOR=#333333][FONT=&amp] but im not even sure its colerated to that bug since im preschooler in linux things. 
Params: [/FONT][/COLOR][FONT=monospace][COLOR=#000000]Ubuntu 18.04.3 LTS \n \l[/COLOR]
[/FONT][COLOR=#333333][FONT=&amp]
[/FONT][/COLOR]```
[FONT=monospace][COLOR=#54FF54]**lsd@lsd-K56CB**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ inxi -Fxz[/COLOR]
[COLOR=#5454FF]**System:   **[/COLOR][COLOR=#5454FF]**Host:**[/COLOR][COLOR=#B2B2B2] lsd-K56CB [/COLOR][COLOR=#5454FF]**Kernel:**[/COLOR][COLOR=#B2B2B2] 5.0.0-37-generic x86_64 [/COLOR][COLOR=#5454FF]**bits:**[/COLOR][COLOR=#B2B2B2] 64 [/COLOR][COLOR=#5454FF]**gcc:**[/COLOR][COLOR=#B2B2B2] 7.4.0[/COLOR]
[COLOR=#5454FF]**Desktop:**[/COLOR][COLOR=#B2B2B2] KDE Plasma 5.12.9 (Qt 5.9.5) [/COLOR][COLOR=#5454FF]**Distro:**[/COLOR][COLOR=#B2B2B2] Ubuntu 18.04.3 LTS[/COLOR]
[COLOR=#5454FF]**Machine:  **[/COLOR][COLOR=#5454FF]**Device:**[/COLOR][COLOR=#B2B2B2] laptop [/COLOR][COLOR=#5454FF]**System:**[/COLOR][COLOR=#B2B2B2] ASUSTeK [/COLOR][COLOR=#5454FF]**product:**[/COLOR][COLOR=#B2B2B2] K56CB [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#B2B2B2] 1.0 [/COLOR][COLOR=#5454FF]**serial:**[/COLOR][COLOR=#B2B2B2] N/A[/COLOR]
[COLOR=#5454FF]**Mobo:**[/COLOR][COLOR=#B2B2B2] ASUSTeK [/COLOR][COLOR=#5454FF]**model:**[/COLOR][COLOR=#B2B2B2] K56CB [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#B2B2B2] 1.0 [/COLOR][COLOR=#5454FF]**serial:**[/COLOR][COLOR=#B2B2B2] N/A [/COLOR][COLOR=#5454FF]**UEFI:**[/COLOR][COLOR=#B2B2B2] American Megatrends [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#B2B2B2] K56CB.205 [/COLOR][COLOR=#5454FF]**date:**[/COLOR][COLOR=#B2B2B2] 03/13/2013[/COLOR]
[COLOR=#5454FF]**Battery   **[/COLOR][COLOR=#5454FF]**BAT0:**[/COLOR][COLOR=#5454FF]**charge:**[/COLOR][COLOR=#B2B2B2] 30.9 Wh 100.0% [/COLOR][COLOR=#5454FF]**condition:**[/COLOR][COLOR=#B2B2B2] 30.9/31.7 Wh (98%) [/COLOR][COLOR=#5454FF]**model:**[/COLOR][COLOR=#B2B2B2] ASUSTeK K56--30 [/COLOR][COLOR=#5454FF]**status:**[/COLOR][COLOR=#B2B2B2] Full[/COLOR]
[COLOR=#5454FF]**CPU:      **[/COLOR][COLOR=#5454FF]**Dual core**[/COLOR][COLOR=#B2B2B2] Intel Core i7-3537U (-MT-MCP-) [/COLOR][COLOR=#5454FF]**arch:**[/COLOR][COLOR=#B2B2B2] Ivy Bridge rev.9 [/COLOR][COLOR=#5454FF]**cache:**[/COLOR][COLOR=#B2B2B2] 4096 KB[/COLOR]
[COLOR=#5454FF]**flags:**[/COLOR][COLOR=#B2B2B2] (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) [/COLOR][COLOR=#5454FF]**bmips:**[/COLOR][COLOR=#B2B2B2] 9976[/COLOR]
[COLOR=#5454FF]**clock speeds:**[/COLOR][COLOR=#5454FF]**max:**[/COLOR][COLOR=#B2B2B2] 3100 MHz [/COLOR][COLOR=#5454FF]**1:**[/COLOR][COLOR=#B2B2B2] 1110 MHz [/COLOR][COLOR=#5454FF]**2:**[/COLOR][COLOR=#B2B2B2] 1185 MHz [/COLOR][COLOR=#5454FF]**3:**[/COLOR][COLOR=#B2B2B2] 1183 MHz [/COLOR][COLOR=#5454FF]**4:**[/COLOR][COLOR=#B2B2B2] 1166 MHz[/COLOR]
[COLOR=#5454FF]**Graphics: **[/COLOR][COLOR=#5454FF]**Card-1:**[/COLOR][COLOR=#B2B2B2] Intel 3rd Gen Core processor Graphics Controller [/COLOR][COLOR=#5454FF]**bus-ID:**[/COLOR][COLOR=#B2B2B2] 00:02.0[/COLOR]
[COLOR=#5454FF]**Card-2:**[/COLOR][COLOR=#B2B2B2] NVIDIA GK107M [GeForce GT 740M] [/COLOR][COLOR=#5454FF]**bus-ID:**[/COLOR][COLOR=#B2B2B2] 01:00.0[/COLOR]
[COLOR=#5454FF]**Display Server:**[/COLOR][COLOR=#B2B2B2] x11 (X.Org 1.20.4 ) [/COLOR][COLOR=#5454FF]**drivers:**[/COLOR][COLOR=#B2B2B2] modesetting,nvidia (unloaded: fbdev,vesa,nouveau)[/COLOR]
[COLOR=#5454FF]**Resolution:**[/COLOR][COLOR=#B2B2B2] 1366x768@60.11hz[/COLOR]
[COLOR=#5454FF]**OpenGL: renderer:**[/COLOR][COLOR=#B2B2B2] GeForce GT 740M/PCIe/SSE2 [/COLOR][COLOR=#5454FF]**version:**[/COLOR][COLOR=#B2B2B2] 4.6.0 NVIDIA 390.129 [/COLOR][COLOR=#5454FF]**Direct Render:**[/COLOR][COLOR=#B2B2B2] Yes[/COLOR]
[COLOR=#5454FF]**Audio:    **[/COLOR][COLOR=#5454FF]**Card-1**[/COLOR][COLOR=#B2B2B2] NVIDIA GK107 HDMI Audio Controller [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#B2B2B2] snd_hda_intel [/COLOR][COLOR=#5454FF]**bus-ID:**[/COLOR][COLOR=#B2B2B2] 01:00.1[/COLOR]
[COLOR=#5454FF]**Card-2**[/COLOR][COLOR=#B2B2B2] Intel 7 Series/C216 Family High Definition Audio Controller[/COLOR]
[COLOR=#5454FF]**driver:**[/COLOR][COLOR=#B2B2B2] snd_hda_intel [/COLOR][COLOR=#5454FF]**bus-ID:**[/COLOR][COLOR=#B2B2B2] 00:1b.0[/COLOR]
[COLOR=#5454FF]**Sound:**[/COLOR][COLOR=#B2B2B2] Advanced Linux Sound Architecture [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#B2B2B2] k5.0.0-37-generic[/COLOR]
[COLOR=#5454FF]**Network:  **[/COLOR][COLOR=#5454FF]**Card-1:**[/COLOR][COLOR=#B2B2B2] Intel Centrino Wireless-N 2230 [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#B2B2B2] iwlwifi [/COLOR][COLOR=#5454FF]**bus-ID:**[/COLOR][COLOR=#B2B2B2] 03:00.0[/COLOR]
[COLOR=#5454FF]**IF:**[/COLOR][COLOR=#B2B2B2] wlp3s0 [/COLOR][COLOR=#5454FF]**state:**[/COLOR][COLOR=#B2B2B2] up [/COLOR][COLOR=#5454FF]**mac:**[/COLOR][COLOR=#B2B2B2] <filter>[/COLOR]
[COLOR=#5454FF]**Card-2:**[/COLOR][COLOR=#B2B2B2] Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller[/COLOR]
[COLOR=#5454FF]**driver:**[/COLOR][COLOR=#B2B2B2] r8169 [/COLOR][COLOR=#5454FF]**port:**[/COLOR][COLOR=#B2B2B2] d000 [/COLOR][COLOR=#5454FF]**bus-ID:**[/COLOR][COLOR=#B2B2B2] 04:00.2[/COLOR]
[COLOR=#5454FF]**IF:**[/COLOR][COLOR=#B2B2B2] enp4s0f2 [/COLOR][COLOR=#5454FF]**state:**[/COLOR][COLOR=#B2B2B2] down [/COLOR][COLOR=#5454FF]**mac:**[/COLOR][COLOR=#B2B2B2] <filter>[/COLOR]
[COLOR=#5454FF]**Drives:   **[/COLOR][COLOR=#5454FF]**HDD Total Size:**[/COLOR][COLOR=#B2B2B2] 1000.2GB (1.5% used)[/COLOR]
[COLOR=#5454FF]**ID-1:**[/COLOR][COLOR=#B2B2B2] /dev/sda [/COLOR][COLOR=#5454FF]**model:**[/COLOR][COLOR=#B2B2B2] Samsung_SSD_860 [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#B2B2B2] 250.1GB[/COLOR]
[COLOR=#5454FF]**ID-2:**[/COLOR][COLOR=#B2B2B2] /dev/sdb [/COLOR][COLOR=#5454FF]**model:**[/COLOR][COLOR=#B2B2B2] TOSHIBA_MQ01ABD0 [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#B2B2B2] 750.2GB[/COLOR]
[COLOR=#5454FF]**Partition:**[/COLOR][COLOR=#5454FF]**ID-1:**[/COLOR][COLOR=#B2B2B2] / [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#B2B2B2] 49G [/COLOR][COLOR=#5454FF]**used:**[/COLOR][COLOR=#B2B2B2] 15G (31%) [/COLOR][COLOR=#5454FF]**fs:**[/COLOR][COLOR=#B2B2B2] ext4 [/COLOR][COLOR=#5454FF]**dev:**[/COLOR][COLOR=#B2B2B2] /dev/sdb6[/COLOR]
[COLOR=#5454FF]**RAID:     **[/COLOR][COLOR=#B2B2B2] No RAID devices: /proc/mdstat, md_mod kernel module present[/COLOR]
[COLOR=#5454FF]**Sensors:  **[/COLOR][COLOR=#5454FF]**System Temperatures: cpu:**[/COLOR][COLOR=#B2B2B2] 63.0C [/COLOR][COLOR=#5454FF]**mobo:**[/COLOR][COLOR=#B2B2B2] N/A [/COLOR][COLOR=#5454FF]**gpu:**[/COLOR][COLOR=#B2B2B2] 0.0:54C[/COLOR]
[COLOR=#5454FF]**Fan Speeds (in rpm): cpu:**[/COLOR][COLOR=#B2B2B2] 3300[/COLOR]
[COLOR=#5454FF]**Info:     **[/COLOR][COLOR=#5454FF]**Processes:**[/COLOR][COLOR=#B2B2B2] 227 [/COLOR][COLOR=#5454FF]**Uptime:**[/COLOR][COLOR=#B2B2B2] 18 min [/COLOR][COLOR=#5454FF]**Memory:**[/COLOR][COLOR=#B2B2B2] 1990.3/11892.0MB [/COLOR][COLOR=#5454FF]**Init:**[/COLOR][COLOR=#B2B2B2] systemd [/COLOR][COLOR=#5454FF]**runlevel:**[/COLOR][COLOR=#B2B2B2] 5 [/COLOR][COLOR=#5454FF]**Gcc sys:**[/COLOR][COLOR=#B2B2B2] 7.4.0[/COLOR]
[COLOR=#5454FF]**Client:**[/COLOR][COLOR=#B2B2B2] Shell (bash 4.4.201) [/COLOR][COLOR=#5454FF]**inxi:**[/COLOR][COLOR=#B2B2B2] 2.3.56 [/COLOR]

[/FONT]
```[COLOR=#333333][FONT=&amp]
[/FONT][/COLOR]

---

