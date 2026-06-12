---
title: "Ubuntu 20.04 screen freezes after ~5 minutes of uptime?"
date: 2020-05-07
forum: General Help
---

### Post by bulwe on 2020-05-07
[COLOR=#242729][FONT=Arial]I dual boot Ubuntu and Windows and am trying to use a dual-monitor setup, with a monitor being connected to a HDMI port in my laptop.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]To use the second monitor, I am trying to use Nvidia's proprietary drivers, since that is the only way my second monitor gets recognized.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Now, every time I install ANY Nvidia driver (tried 440, 435, 430, 390), through any means (Software & Updates -> Additional drivers; as well as manually - adding the graphics ppa repository) in Ubuntu, **the system's view completely freezes** after a few minutes of being booted, requiring a hard-restart.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]**If any music is currently playing, it continues playing.** I just cannot move my mouse or interact with the system, since the view of the system is completely frozen. This happens consistently after every boot.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The way I counteract this this is I boot up and quickly go to Software & Updates -> Additional drivers and revert back to default Nouveau graphics drivers. When reverted and rebooted, the system does not freeze anymore, but I cannot use my second monitor this way, because Nouveau does not seem to recognize the second monitor.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Also, I had to do "nomodeset" in GRUB settings, otherwise the system gets stuck on the login screen.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]This used to happen with Ubuntu 18.04 as well, that is why upgraded to 20.04, thinking it might solve this problem.[/FONT][/COLOR]
[HR][/HR][COLOR=#242729][FONT=Arial]System specs:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]+Laptop: HP Zbook Studio G5 x360[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]+Video card: Nvidia Quadro P1000[/FONT][/COLOR]
[HR][/HR][COLOR=#242729][FONT=Arial]I am looking for a way to get the second monitor working without the system freezing. I am not sure whether this is possible only with Nvidia drivers, or maybe there is some other way.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Any and all help is appreciated, since I've been stuck on this problem for quite some time. Also, please tell me if I can provide any more information about this issue.[/FONT][/COLOR]

---

### Post by bulwe on 2020-06-30
Answered by generix on Nvidia forums: 


Known bios issue of that notebook. Please use kernel parameter
intel_idle.max_cstate=1


Adding this kernel parameter in grub `GRUB_CMDLINE_LINUX_DEFAULT="intel_idle.max_cstate=1"` solved the freezing issue.

---

### Post by a-j-beaumont on 2021-01-19
Did adding this kernel parameter fix your freeze problem?  I have had serious problems with this and I also have a HP Zbook.

---

