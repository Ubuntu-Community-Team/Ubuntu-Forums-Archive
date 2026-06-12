---
title: "Computer won't suspend after upgrade to 24.04"
date: 2024-08-29
forum: General Help
---

### Post by bbutler3 on 2024-08-29
I upgraded from 22.04 to 24.04 today, and my computer will no longer fully suspend. Before, it would send everything to RAM (I presume) and the fans and things would stop. Now, it only does a "lighter sleep" when I select suspend: display turns off, system is locked, but everything keeps running. Basically I think the system used to enter the S3 state, and now it seems like just S1. How can I get suspend to go back to S3? (note: I don't want S4/hibernate)

I've tried both the power GUI and [FONT=courier new]systemctl suspend[/FONT] methods, in case there was a difference, but there wasn't. I installed [FONT=courier new]pm-utils[/FONT] and tried [FONT=courier new]sudo pm-suspend[/FONT], but that resulted in an even lighter sleep. I also tried [FONT=courier new]sudo pm-suspend-hybrid[/FONT], but that didn't seem to enter S3, and worse, I wasn't able to get my system to wake back up without hard shutting down using the power button.

I learned through some searching that this could have to do with graphics drivers, but according to Ubuntu, I've got the latest Nvidia driver. There seem to be some more recent versions in production on Nvidia's website, but after starting the install process, it seemed like I should probably stick with the one I currently have based on the warnings shown.

I also checked the logs using [FONT=courier new]sudo journalctl -b | grep -i suspend[/FONT] after a standard suspend attempt, but didn't see any errors or anything. But I'm far from an expert in [FONT=courier new]journalctl[/FONT].

I'd appreciate any help anyone can give! I'll attach some system specs below in case they're relevant.

---

Ubuntu 24.04.1 LTS x86_64
6.8.0-41-generic kernel

Dell Precision 3660 (work machine but untouched by IT)
Dell SafeBIOS (unchanged by me)
NVIDIA RTX 3070 Lite Hash Rate
Intel i7-13700
32 GB memory (further specs unclear; probably just some Dell OEM)

---

### Post by currentshaft on 2024-08-30
S3 sleep state hasn't been around since like Tiger Lake.

Use this tool to debug your problem: [https://gitlab.freedesktop.org/drm/amd/-/blob/master/scripts/amd_s2idle.py](https://gitlab.freedesktop.org/drm/amd/-/blob/master/scripts/amd_s2idle.py)

---

### Post by bbutler3 on 2024-08-30
Thanks for your response. This tool is for AMD systems. Also, this computer successfully entered a state at least similar to S3 in 22.04. The only change has been the upgrade to 24.04. Additionally, my Raptor Lake machine at home enters such a state from Windows.

---

### Post by currentshaft on 2024-08-30
> **bbutler3 said:**
> Thanks for your response. This tool is for AMD systems. Also, this computer successfully entered a state at least similar to S3 in 22.04. The only change has been the upgrade to 24.04. Additionally, my Raptor Lake machine at home enters such a state from Windows.

Sorry, for Intel use [https://github.com/intel/S0ixSelftestTool](https://github.com/intel/S0ixSelftestTool)

---

### Post by jvcdk2 on 2024-09-06
Same for me. My system won't suspend after upgrading to 24.04. I ran the S0ix self test tool mentioned above, it stated:

[COLOR=#696969][FONT=courier new]---Check S2idle path S0ix Residency---:

The system OS Kernel version is:
Linux xps 6.8.0-41-generic #41-Ubuntu SMP PREEMPT_DYNAMIC Fri Aug  2 20:41:06 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux

---Check whether your system supports S0ix or not---:

Low Power S0 Idle is:0
Your system does not support low power S0 idle capability.     
Isolation suggestion:     
Please check BIOS low power S0 idle capability setting.
[/FONT][/COLOR]
I did not mess with my BIOS during the upgrade. Still I checked the BIOS and found no suspicious settings.

Any advice on how to mitigate this?

~Jørn

---

### Post by jvcdk2 on 2024-09-06
Ps.: Also on a Dell machine: Dell XPS 15 9560 with Nvidia GeForce GTX 1050 Mobile.

---

### Post by jvcdk2 on 2024-09-06
I got it to work again.

I had two stale symlinks in each of the folders [FONT=courier new]/etc/systemd/system/systemd-suspend.service.requires/[/FONT] and [FONT=courier new]/etc/systemd/system/systemd-hibernate.service.requires[/FONT].  Something related to nvidia suspend/hibernate/resume services.

It seems that since the symlinks are dead, the system refuses go into suspend. No logs (that I could find). The diagnostic tool above sending me on a wild goose chase.  Great :-(

But removing those 4 dead links made my system work again :)

I hope that this finding may help somebody else as well :)

~Jørn

---

### Post by bbutler3 on 2024-09-16
Thanks for your reply, Jørn! I was excited to try this when I got to work, but unfortunately it won't work for me. I don't even have folders in those [FONT=courier new]system[/FONT] directories with [FONT=courier new]requires[/FONT] in the name; only [FONT=courier new]wants[/FONT]. And in the wants folders corresponding to the ones you list, the symlinks are alive and well. 

If anyone else has any further ideas, I'd love to hear them!

---

