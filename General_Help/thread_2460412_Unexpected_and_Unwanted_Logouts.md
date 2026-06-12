---
title: "Unexpected and Unwanted Logouts"
date: 2021-04-09
forum: General Help
---

### Post by raccoonstrait on 2021-04-09
Good Morning Everyone,

Xubuntu 20.04.2 with the XFCE desktop, updated every weekday. This is on a System76 Bonobo laptop that has has several versions of Xubuntu installed, but the issue has only been with the 20.04 LTS version.

I have been experiencing this phenomena for a while now, I will click on something (a program in the Whisker Menu or a launcher on the panel, or something on the desktop) and the system logs me out. Today, I didn't even click on something and the logout happened. I have a report error message when I login and was hoping that the two were related, but no fix has come through yet. Nothing came up searching for logout on the forum.

Not sure what to look for, or where to look. Let me know what you might need to help.

Thanks

Raccoon Strait

---

### Post by CatKiller on 2021-04-09
I can't help with the particulars of your issue, but you might find it easier to find a solution if you know that you aren't being logged out.

For whatever reason, your graphical session is crashing. The login screen is just the first thing that gets shown when it restarts.

---

### Post by ajgreeny on 2021-04-09
We really need more info to ba able to help so for a start let's see the output of terminal command (assuming you can get a terminal up and running) ```
inxi -Fzx
```
I can't remember if inxi is installed as default but if not install it first, as you'll be told to do with ```
sudo apt install inxi
```
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted.
See my signature below for a **How-to**

---

### Post by raccoonstrait on 2021-04-09
agreeny

Thanks for the reply, here is the output:

```

[FONT=monospace][COLOR=#000000]$ inxi -Fzx[/COLOR]
[COLOR=#5454FF]**System:    Kernel:**[/COLOR][COLOR=#000000] 5.11.0-7612-generic x86_64 [/COLOR][COLOR=#5454FF]**bits:**[/COLOR][COLOR=#000000] 64 [/COLOR][COLOR=#5454FF]**compiler:**[/COLOR][COLOR=#000000] N/A [/COLOR][COLOR=#5454FF]**Desktop:**[/COLOR][COLOR=#000000] Xfce 4.14.2  [/COLOR]
           [COLOR=#5454FF]**Distro:**[/COLOR][COLOR=#000000] Ubuntu 20.04.2 LTS (Focal Fossa)  [/COLOR]
[COLOR=#5454FF]**Machine:   Type:**[/COLOR][COLOR=#000000] Laptop [/COLOR][COLOR=#5454FF]**System:**[/COLOR][COLOR=#000000] System76 [/COLOR][COLOR=#5454FF]**product:**[/COLOR][COLOR=#000000] Bonobo WS [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] bonw10 [/COLOR][COLOR=#5454FF]**serial:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
           [COLOR=#5454FF]**Mobo:**[/COLOR][COLOR=#000000] System76 [/COLOR][COLOR=#5454FF]**model:**[/COLOR][COLOR=#000000] Bonobo WS [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] bonw10 [/COLOR][COLOR=#5454FF]**serial:**[/COLOR][COLOR=#000000] <filter> [/COLOR][COLOR=#5454FF]**UEFI:**[/COLOR][COLOR=#000000] American Megatrends [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] 1.05.02RS76  [/COLOR]
           [COLOR=#5454FF]**date:**[/COLOR][COLOR=#000000] 11/25/2015  [/COLOR]
[COLOR=#5454FF]**Battery:   ID-1:**[/COLOR][COLOR=#000000] BAT0 [/COLOR][COLOR=#5454FF]**charge:**[/COLOR][COLOR=#000000] 59.1 Wh [/COLOR][COLOR=#5454FF]**condition:**[/COLOR][COLOR=#000000] 59.1/89.1 Wh (66%) [/COLOR][COLOR=#5454FF]**model:**[/COLOR][COLOR=#000000] Notebook BAT [/COLOR][COLOR=#5454FF]**status:**[/COLOR][COLOR=#000000] Full  [/COLOR]
[COLOR=#5454FF]**CPU:       Topology:**[/COLOR][COLOR=#000000] Quad Core [/COLOR][COLOR=#5454FF]**model:**[/COLOR][COLOR=#000000] Intel Core i7-6700K [/COLOR][COLOR=#5454FF]**bits:**[/COLOR][COLOR=#000000] 64 [/COLOR][COLOR=#5454FF]**type:**[/COLOR][COLOR=#000000] MT MCP [/COLOR][COLOR=#5454FF]**arch:**[/COLOR][COLOR=#000000] Skylake-S [/COLOR][COLOR=#5454FF]**rev:**[/COLOR][COLOR=#000000] 3 [/COLOR][COLOR=#5454FF]**L2 cache:**[/COLOR][COLOR=#000000] 8192 KiB  [/COLOR]
           [COLOR=#5454FF]**flags:**[/COLOR][COLOR=#000000] avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx [/COLOR][COLOR=#5454FF]**bogomips:**[/COLOR][COLOR=#000000] 63999  [/COLOR]
           [COLOR=#5454FF]**Speed:**[/COLOR][COLOR=#000000] 953 MHz [/COLOR][COLOR=#5454FF]**min/max:**[/COLOR][COLOR=#000000] 800/4200 MHz [/COLOR][COLOR=#5454FF]**Core speeds (MHz):**[/COLOR][COLOR=#5454FF]**1:**[/COLOR][COLOR=#000000] 999 [/COLOR][COLOR=#5454FF]**2:**[/COLOR][COLOR=#000000] 1000 [/COLOR][COLOR=#5454FF]**3:**[/COLOR][COLOR=#000000] 942 [/COLOR][COLOR=#5454FF]**4:**[/COLOR][COLOR=#000000] 1799 [/COLOR][COLOR=#5454FF]**5:**[/COLOR][COLOR=#000000] 900 [/COLOR][COLOR=#5454FF]**6:**[/COLOR][COLOR=#000000] 900 [/COLOR][COLOR=#5454FF]**7:**[/COLOR][COLOR=#000000] 967 [/COLOR][COLOR=#5454FF]**8:**[/COLOR][COLOR=#000000] 899  [/COLOR]
[COLOR=#5454FF]**Graphics:  Device-1:**[/COLOR][COLOR=#000000] NVIDIA GM204M [GeForce GTX 970M] [/COLOR][COLOR=#5454FF]**vendor:**[/COLOR][COLOR=#000000] CLEVO/KAPOK [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] nouveau [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] kernel [/COLOR][COLOR=#5454FF]**bus ID:**[/COLOR][COLOR=#000000] 01:00.0  [/COLOR]
           [COLOR=#5454FF]**Device-2:**[/COLOR][COLOR=#000000] NVIDIA GM204M [GeForce GTX 970M] [/COLOR][COLOR=#5454FF]**vendor:**[/COLOR][COLOR=#000000] CLEVO/KAPOK [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] nouveau [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] kernel [/COLOR][COLOR=#5454FF]**bus ID:**[/COLOR][COLOR=#000000] 02:00.0  [/COLOR]
           [COLOR=#5454FF]**Display:**[/COLOR][COLOR=#000000] x11 [/COLOR][COLOR=#5454FF]**server:**[/COLOR][COLOR=#000000] X.Org 1.20.9 [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] modesetting [/COLOR][COLOR=#5454FF]**unloaded:**[/COLOR][COLOR=#000000] fbdev,vesa [/COLOR][COLOR=#5454FF]**resolution:**[/COLOR][COLOR=#000000] 1920x1080~60Hz  [/COLOR]
           [COLOR=#5454FF]**OpenGL:**[/COLOR][COLOR=#5454FF]**renderer:**[/COLOR][COLOR=#000000] NV124 [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] 4.3 Mesa 21.0.0 [/COLOR][COLOR=#5454FF]**direct render:**[/COLOR][COLOR=#000000] Yes  [/COLOR]
[COLOR=#5454FF]**Audio:     Device-1:**[/COLOR][COLOR=#000000] Intel 100 Series/C230 Series Family HD Audio [/COLOR][COLOR=#5454FF]**vendor:**[/COLOR][COLOR=#000000] CLEVO/KAPOK [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] snd_hda_intel [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] kernel  [/COLOR]
           [COLOR=#5454FF]**bus ID:**[/COLOR][COLOR=#000000] 00:1f.3  [/COLOR]
           [COLOR=#5454FF]**Device-2:**[/COLOR][COLOR=#000000] NVIDIA GM204 High Definition Audio [/COLOR][COLOR=#5454FF]**vendor:**[/COLOR][COLOR=#000000] CLEVO/KAPOK [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] snd_hda_intel [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] kernel [/COLOR][COLOR=#5454FF]**bus ID:**[/COLOR][COLOR=#000000] 01:00.1  [/COLOR]
           [COLOR=#5454FF]**Device-3:**[/COLOR][COLOR=#000000] NVIDIA GM204 High Definition Audio [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] snd_hda_intel [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] kernel [/COLOR][COLOR=#5454FF]**bus ID:**[/COLOR][COLOR=#000000] 02:00.1  [/COLOR]
           [COLOR=#5454FF]**Sound Server:**[/COLOR][COLOR=#000000] ALSA [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] k5.11.0-7612-generic  [/COLOR]
[COLOR=#5454FF]**Network:   Device-1:**[/COLOR][COLOR=#000000] Qualcomm Atheros Killer E2400 Gigabit Ethernet [/COLOR][COLOR=#5454FF]**vendor:**[/COLOR][COLOR=#000000] CLEVO/KAPOK [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] alx [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] kernel [/COLOR][COLOR=#5454FF]**port:**[/COLOR][COLOR=#000000] c000  [/COLOR]
           [COLOR=#5454FF]**bus ID:**[/COLOR][COLOR=#000000] 03:00.0  [/COLOR]
           [COLOR=#5454FF]**IF:**[/COLOR][COLOR=#000000] enp3s0 [/COLOR][COLOR=#5454FF]**state:**[/COLOR][COLOR=#000000] down [/COLOR][COLOR=#5454FF]**mac:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
           [COLOR=#5454FF]**Device-2:**[/COLOR][COLOR=#000000] Qualcomm Atheros Killer E2400 Gigabit Ethernet [/COLOR][COLOR=#5454FF]**vendor:**[/COLOR][COLOR=#000000] CLEVO/KAPOK [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] alx [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] kernel [/COLOR][COLOR=#5454FF]**port:**[/COLOR][COLOR=#000000] b000  [/COLOR]
           [COLOR=#5454FF]**bus ID:**[/COLOR][COLOR=#000000] 04:00.0  [/COLOR]
           [COLOR=#5454FF]**IF:**[/COLOR][COLOR=#000000] enp4s0 [/COLOR][COLOR=#5454FF]**state:**[/COLOR][COLOR=#000000] up [/COLOR][COLOR=#5454FF]**speed:**[/COLOR][COLOR=#000000] 1000 Mbps [/COLOR][COLOR=#5454FF]**duplex:**[/COLOR][COLOR=#000000] full [/COLOR][COLOR=#5454FF]**mac:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
           [COLOR=#5454FF]**Device-3:**[/COLOR][COLOR=#000000] Intel Wireless 8260 [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] iwlwifi [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] kernel [/COLOR][COLOR=#5454FF]**port:**[/COLOR][COLOR=#000000] b000 [/COLOR][COLOR=#5454FF]**bus ID:**[/COLOR][COLOR=#000000] 05:00.0  [/COLOR]
           [COLOR=#5454FF]**IF:**[/COLOR][COLOR=#000000] wlp5s0 [/COLOR][COLOR=#5454FF]**state:**[/COLOR][COLOR=#000000] down [/COLOR][COLOR=#5454FF]**mac:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
[COLOR=#5454FF]**Drives:    Local Storage:**[/COLOR][COLOR=#5454FF]**total:**[/COLOR][COLOR=#000000] 1.13 TiB [/COLOR][COLOR=#5454FF]**used:**[/COLOR][COLOR=#000000] 379.40 GiB (32.8%)  [/COLOR]
           [COLOR=#5454FF]**ID-1:**[/COLOR][COLOR=#000000] /dev/sda [/COLOR][COLOR=#5454FF]**vendor:**[/COLOR][COLOR=#000000] Samsung [/COLOR][COLOR=#5454FF]**model:**[/COLOR][COLOR=#000000] SSD 850 EVO M.2 120GB [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#000000] 111.79 GiB  [/COLOR]
           [COLOR=#5454FF]**ID-2:**[/COLOR][COLOR=#000000] /dev/sdb [/COLOR][COLOR=#5454FF]**vendor:**[/COLOR][COLOR=#000000] Samsung [/COLOR][COLOR=#5454FF]**model:**[/COLOR][COLOR=#000000] SSD 850 EVO M.2 120GB [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#000000] 111.79 GiB  [/COLOR]
           [COLOR=#5454FF]**ID-3:**[/COLOR][COLOR=#000000] /dev/sdc [/COLOR][COLOR=#5454FF]**vendor:**[/COLOR][COLOR=#000000] HGST (Hitachi) [/COLOR][COLOR=#5454FF]**model:**[/COLOR][COLOR=#000000] HTS721010A9E630 [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#000000] 931.51 GiB  [/COLOR]
[COLOR=#5454FF]**Partition: ID-1:**[/COLOR][COLOR=#000000] / [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#000000] 45.55 GiB [/COLOR][COLOR=#5454FF]**used:**[/COLOR][COLOR=#000000] 14.04 GiB (30.8%) [/COLOR][COLOR=#5454FF]**fs:**[/COLOR][COLOR=#000000] ext4 [/COLOR][COLOR=#5454FF]**dev:**[/COLOR][COLOR=#000000] /dev/sda2  [/COLOR]
           [COLOR=#5454FF]**ID-2:**[/COLOR][COLOR=#000000] /home [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#000000] 47.66 GiB [/COLOR][COLOR=#5454FF]**used:**[/COLOR][COLOR=#000000] 34.47 GiB (72.3%) [/COLOR][COLOR=#5454FF]**fs:**[/COLOR][COLOR=#000000] ext4 [/COLOR][COLOR=#5454FF]**dev:**[/COLOR][COLOR=#000000] /dev/sda4  [/COLOR]
           [COLOR=#5454FF]**ID-3:**[/COLOR][COLOR=#000000] swap-1 [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#000000] 15.96 GiB [/COLOR][COLOR=#5454FF]**used:**[/COLOR][COLOR=#000000] 3.0 MiB (0.0%) [/COLOR][COLOR=#5454FF]**fs:**[/COLOR][COLOR=#000000] swap [/COLOR][COLOR=#5454FF]**dev:**[/COLOR][COLOR=#000000] /dev/sda3  [/COLOR]
[COLOR=#5454FF]**Sensors:   System Temperatures:**[/COLOR][COLOR=#5454FF]**cpu:**[/COLOR][COLOR=#000000] 68.5 C [/COLOR][COLOR=#5454FF]**mobo:**[/COLOR][COLOR=#000000] N/A  [/COLOR]
           [COLOR=#5454FF]**Fan Speeds (RPM):**[/COLOR][COLOR=#000000] N/A  [/COLOR]
           [COLOR=#5454FF]**GPU:**[/COLOR][COLOR=#5454FF]**device:**[/COLOR][COLOR=#000000] nouveau [/COLOR][COLOR=#5454FF]**temp:**[/COLOR][COLOR=#000000] 55 C [/COLOR][COLOR=#5454FF]**device:**[/COLOR][COLOR=#000000] nouveau [/COLOR][COLOR=#5454FF]**temp:**[/COLOR][COLOR=#000000] 67 C  [/COLOR]
[COLOR=#5454FF]**Info:      Processes:**[/COLOR][COLOR=#000000] 308 [/COLOR][COLOR=#5454FF]**Uptime:**[/COLOR][COLOR=#000000] 19h 59m [/COLOR][COLOR=#5454FF]**Memory:**[/COLOR][COLOR=#000000] 15.59 GiB [/COLOR][COLOR=#5454FF]**used:**[/COLOR][COLOR=#000000] 3.09 GiB (19.8%) [/COLOR][COLOR=#5454FF]**Init:**[/COLOR][COLOR=#000000] systemd [/COLOR][COLOR=#5454FF]**runlevel:**[/COLOR][COLOR=#000000] 5 [/COLOR][COLOR=#5454FF]**Compilers:**[/COLOR]
           [COLOR=#5454FF]**gcc:**[/COLOR][COLOR=#000000] 9.3.0 [/COLOR][COLOR=#5454FF]**Shell:**[/COLOR][COLOR=#000000] bash [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] 5.0.17 [/COLOR][COLOR=#5454FF]**inxi:**[/COLOR][COLOR=#000000] 3.0.38

 [/COLOR][/FONT]
```[FONT=monospace]

Please let me know if you need anything else.

Raccoon Strait

[/FONT]

---

### Post by ajgreeny on 2021-04-09
Two questions arise from your inxi output.
[LIST=1]
[*]Where did that **5.11.0-7612-generic** kernel come from as it is not part of the standard focal repo?
[*]Have you searched for a driver for the nvidia graphics card using the Additional Drivers utility?  If not do so now as ot may be all that's needed as it looks as if you are currently using the nouveau (open source) driver not an nvidia driver from those offered by Ubuntu.
[/LIST]

---

### Post by raccoonstrait on 2021-04-09
ajgreeny

The kernel and drivers come from System76 who specialize in Linux machines. I have had this machine for around  5 years now and have not had a problem like this.

But I did update to an Nvidia driver, and will now have to watch and see if that took care of the problem. I have no way to force the 'logout' so waiting and using the system will have to do.

Thanks for your input.

Raccoon Strait

---

### Post by ajgreeny on 2021-04-09
I hope it was the recommended diver from the Ubuntu system and not one downloaded direct from Nvidia?

---

### Post by raccoonstrait on 2021-04-09
The original driver was what Xubuntu installs. Then, after re-adding the System76 PPA I got whatever apt sends. This time I used the Additional Drivers app from the whisker menu and chose the latest Nvidia driver there. I presume that is the correct one. It seems to be working, and I have not, as of yet, had any logouts.

Raccoon Strait

---

### Post by raccoonstrait on 2021-04-12
Good Morning Everybody,

I haven't had this issue for several days now, with normal use. I am therefore presuming that the solution implemented resolved the problem. Marking this solved.

Thanks for the assistance.

Raccoon Strait

---

