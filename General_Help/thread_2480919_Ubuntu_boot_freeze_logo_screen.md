---
title: "Ubuntu boot freeze logo screen"
date: 2022-11-14
forum: General Help
---

### Post by iftik on 2022-11-14
[COLOR=#232629][FONT=-apple-system]Dynabook laptop: 

I had xubuntu 20 I did an apt-upgrade, at the end of the process it asked to reboot. After the reboot it freezes on the brand logo screen and won't boot.

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I formatted and installed ubuntu 22.4 again and still the same, when booting it freezes on the logo screen, after waiting a while if I reboot it CTRL+ALT+DEL when it restarts it boots correctly. I have installed windows and it does not give me this problem.

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]It is very strange, with windows boots correctly, with ubuntu/Linux it stays in the logo and sometimes it boots and sometimes not, but if I restart it CTRL+ALT+DEL it boots correctly.

I have run boot-repair, without success.[/FONT][/COLOR]

---

### Post by ActionParsnip on 2022-11-14
If you spam left SHIFT at boot, can you boot an older kernel and be OK?

"Ubuntu 20" doesn't exist. Are you using Ubuntu 20.04 (LTS release)  or 20.10 which is no longer supported?

---

### Post by iftik on 2022-11-14
[COLOR=#000000]If you spam left SHIFT at boot, can you boot an older kernel and be OK?
[/COLOR]same, stays in logo[COLOR=#000000]
[/COLOR]
[COLOR=#000000]"Ubuntu 20" doesn't exist. Are you using Ubuntu 20.04 (LTS release) or 20.10 which is no longer supported?[/COLOR]
Yeah , it was xubuntu 20.04 LTS.


It seems that the failure is in first boot, if I press F12 and in boot menu I choose "ubuntu" it boots. 


If I don't press F12 it stays in logo screen for a while, and if I reboot it boots fine.


It is as if it is not able to boot ubuntu by itself, as if something is wrong with the grub or something similar. Because if it's hardware, it shouldn't boot either by rebooting or by entering F12.


In boot order (Efibootmgr -V) ubuntu is first to boot.

---

### Post by tea for one on 2022-11-14
> **iftik said:**
> I have run boot-repair, without success.
If you run the boot-repair report again and pop the link in this thread, it may provide enough details to find a solution?

---

### Post by iftik on 2022-11-15
I have replied 2 times with the Pastebin link but after a while it is deleted.... How do I upload the report?

---

### Post by QIII on 2022-11-15
Your question about MINT has been moved [here]("https://ubuntuforums.org/showthread.php?t=2480953").

MINT is not an official flavor of Ubuntu.  Your original post is about Ubuntu, so MINT is off-topic.

---

