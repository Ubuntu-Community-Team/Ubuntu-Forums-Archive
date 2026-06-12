---
title: "Sudden shutdown when my Secondrary display unplugged"
date: 2016-02-13
forum: General Help
---

### Post by sudosu2 on 2016-02-13
Hey, as you see from the topic title, my Kubuntu  (And every other Linux installation/live cd) suddenly shutdowns after few minutes, when my secondary veteran CRT monitor is unplugged (Of course when it's plugged I'm using the laptop screen too with extended mode!). It's really interesting problem, I didn't find this kind of problem on the net. Everything is works fine with my Windows 10.

I experince this problem both on battery and AC power. There shouldn't be problem with my battery or power cable, as I said everything works fine with Windows.
There's no overheating. 
I'm running on the newest BIOS.
I've updated all system components after installation and installed Intel and NVIDIA driver (Optimus)
I've unplugged everything from my notebook, the crash still came. (When the CRT monitor connected everything worked fine, what the heck?) 
I ran  memtest for a night, there's no problem with my memory.

I don't know what kind of log files should I put here for the problem solving, so please ask for it!  

My Hardware specs: 
**Notebook name: **Asus X55VD-SX029D
**CPU: **Intel(R) Core(TM) i3-2350M
**RAM: **8192 MB 
**Storage: **KINGSTON SV300S37A (120 GB, SSD) 
**Secondrary storage: **Toshiba 5400MQ01ABD100 SATA3 (MQ01ABD100) 1TB (I'm using it from USB)
**GPU: **Intel HD3000 and NVIDIA Geforce 610M (1GB VRAM)
**OS:  **Kubuntu 15.10 (I also tried the newest Fedora, Debian, Ubuntu)  and Windows 10

Please somehow help me to solve the problem! 
Have a good day! 

P.S.: Sorry for my horrible English! :)

---

### Post by branau on 2016-02-13
A couple of things might be useful here:

```
lspci | grep VGA
```

That should give us info about which type of display you have. 

```
lsmod
```

That will tell you what drivers you have installed. 

```
cat /var/log/Xorg.0.log
``` 
That ought to tell us if there's any errors being logged by the X server.  

Please post the contents of these commands

---

### Post by sudosu2 on 2016-02-13
Here you go: 

> 
[FONT=monospace][COLOR=#000000]sudosu@sudosu-X55VDR:~$ lspci | grep VGA[/COLOR]
00:02.0 [COLOR=#FF5454]**VGA**[/COLOR][COLOR=#000000] compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Control[/COLOR]
ler (rev 09)
01:00.0 [COLOR=#FF5454]**VGA**[/COLOR][COLOR=#000000] compatible controller: NVIDIA Corporation GF119M [GeForce 610M] (rev ff)[/COLOR]
[/FONT]

[LSMOD Output]("http://1drv.ms/1Kh1kcc")

[/var/log/Xorg.0.log]("http://1drv.ms/1Kh1Abl")

---

