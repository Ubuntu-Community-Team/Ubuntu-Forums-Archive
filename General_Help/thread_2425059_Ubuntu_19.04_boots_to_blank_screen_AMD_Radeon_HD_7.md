---
title: "Ubuntu 19.04 boots to blank screen AMD Radeon HD 7730"
date: 2019-08-19
forum: General Help
---

### Post by MrRubik on 2019-08-19
[COLOR=#000000]I just loaded Ubuntu 19.04 onto my Dell XPS 8500 desktop last week. I am using an AMD Radeon HD 7730 with dual monitors (1 HDMI, 1 DisplayPort). Most of the time when I reboot my system, it will boot to a completely blank login screen. It shows nothing at all, just a blank screen. I have tried the things below and nothing is working. Deleting the raven_dmcu.bin file seemed to work but now I'm having the problem again. If anyone could please tell me how to fix this, I would very much appreciate it. I don't want to have to buy a new video card but I'm going to have to if I can't get this fixed. I have got all other issues on my system worked out except this one. Thanks.[/COLOR]

[COLOR=#000000]1 - Tried with only one monitor and the same issue occurs.[/COLOR]
[COLOR=#000000]2 - Tried switching monitor 1 and 2 cables and adjusting the display settings to put their left/right orientation back.[/COLOR]
[COLOR=#000000]3 - I read someones post that said this would work and it did for a while but I'm having the issue again now. Delete the file /lib/firmware/amdgpu/raven_dmcu.bin and then run [/COLOR][COLOR=#242729][FONT=Consolas]sudo update-initramfs -u -k all[/FONT][/COLOR]

---

### Post by QIII on 2019-08-19
Hello!

Did your installation work initially and then stop working when you installed a driver?

---

### Post by Yellow Pasque on 2019-08-20
> Deleting the raven_dmcu.bin file seemed to work but now I'm having the problem again. 
Your card is not a Raven Ridge APU, and it uses the older 'radeon' kernel module by default (not 'amdgpu'). I am very skeptical of this "solution". Link?

Speaking of amdgpu, you may want try forcing that to be used instead of radeon to see if the issue persists with it: You'll have to boot with these 4 arguments added to the kernel line:
```
radeon.si_support=0 radeon.cik_support=0 amdgpu.si_support=1 amdgpu.cik_support=1
```

---

### Post by MrRubik on 2019-08-20
[FONT=arial]Everything worked fine for the initial install and the first boot. Then when I try to reboot it happens. I've tried a fresh install and it didn't help. As of now, the problem is happening about half of the time. Sometimes it will boot up okay and the other times I get stuck at a completely blank login screen. I didn't install any driver as I read that Ubuntu 19.04 already had all the drivers I needed. However, I did try to install the amdgpu drivers straight from AMD's website, but every time I try to install them (the open and pro variant) I get an error "[COLOR=#242729]E: Sub-process /usr/bin/dpkg returned an error code (1)". I have just been trying things to fix it and then using Timeshift to roll back if it doesn't work. Another thing I tried last night that didn't work is to set it to boot [/COLOR]radeon.modeset=0 and that didn't work either. Also, I tried that raven fix before I knew my card wasn't raven ridge. Now I know I just got lucky and deleting the file had no effect on my problem since it's still occurring. But the link to the suggested "fix" is below. I'm about t[/FONT][FONT=arial]o try what Yellow Pasque suggested. I'm hoping I'm not going to have to buy a new video card but I guess I will if I have to.[/FONT][FONT=arial][COLOR=#242729]
[/COLOR]
[https://askubuntu.com/questions/1135590/amdgpu-driver-refuses-to-load-on-19-04](https://askubuntu.com/questions/1135590/amdgpu-driver-refuses-to-load-on-19-04)[/FONT]

---

### Post by MrRubik on 2019-08-20
> **Yellow Pasque said:**
> Your card is not a Raven Ridge APU, and it uses the older 'radeon' kernel module by default (not 'amdgpu'). I am very skeptical of this "solution". Link?

Speaking of amdgpu, you may want try forcing that to be used instead of radeon to see if the issue persists with it: You'll have to boot with these 4 arguments added to the kernel line:
```
radeon.si_support=0 radeon.cik_support=0 amdgpu.si_support=1 amdgpu.cik_support=1
```

So I just add those 4 lines to GRUB_CMDLINE_LINUX_DEFAULT="quiet spash" and then update GRUB like I did when trying the modeset and try it again? It will look like this below, right? Sorry if this is a dumb question but I'm very new to Ubuntu and Linux.
[FONT=arial]
GRUB_CMDLINE_LINUX_DEFAULT="quiet spash [COLOR=#000000]radeon.si_support=0 radeon.cik_support=0 amdgpu.si_support=1 amdgpu.cik_support=1"[/COLOR][/FONT]

---

### Post by QIII on 2019-08-20
Don't mess with AMDGPU.  Your card is a first gen GCN, or GCN 1.0 (Graphics Core Next) unit.  When it debuted, AMDGPU was supported only by GCN 1.1 or greater.

I am not sure if it has been developed backwards to support 1.0 yet.

When Ubuntu is installed initially, the AMDGPU module is activated if the correct hardware is present.  Otherwise, radeon is used.

They are not the same and you should let it be after installation.

---

### Post by MrRubik on 2019-08-20
The problem has been solved by hooking one of my monitors up with DVI instead of DisplayPort. My video card has 1 x HDMI, 1 x DVI, 1 x DisplayPort. I am now using HDMI and DVI instead of HDMI and DisplayPort. I can now properly see the bootsplash screen and I can see the login screen properly. When I tried with a single monitor, I tried it with DisplayPort instead of HDMI. I read somewhere that Ubuntu is known to have issues with DisplayPort. Is this true? I'd just like to know in case I ever get a new graphics card. Thanks for the help everybody.

---

### Post by Yellow Pasque on 2019-08-21
> **QIII said:**
> Don't mess with AMDGPU. I am not sure if it has been developed backwards to support (GCN) 1.0 yet.

The support is officially "experimental" and probably will remain that way, but I feel it is okay to try amdgpu on GCN 1.0/1.1 to troubleshoot an issue (and some users may even want to run it all of the time if they really want Vulkan support): [https://www.phoronix.com/scan.php?page=article&item=amdgpu-radeon-linux50&num=1](https://www.phoronix.com/scan.php?page=article&item=amdgpu-radeon-linux50&num=1)

---

### Post by QIII on 2019-08-23
> **MrRubik said:**
> I read somewhere that Ubuntu is known to have issues with DisplayPort. Is this true?

If that were true, then I would be having trouble x3 with my monitors.

Not sure where you read that.

---

