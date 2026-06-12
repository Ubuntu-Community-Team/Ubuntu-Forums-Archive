---
title: "Acer won't shut down"
date: 2015-12-20
forum: General Help
---

### Post by kuckunniwi on 2015-12-20
Hi,

My Acer Aspire ES1-311 will not shut down, under any circumstance (Xubuntu Trusty amd64). It begins to shut down, then gets stuck either on the the Xubuntu logo, on three dots or on a black screen. When I bought the laptop over a year ago, this happened 2-3 of every 5 times. Now it's 5/5

***shutdown -h now*** and ***shutdown -P now*** don't seem to make a difference. 

I've also tried ***acpi=off*** and ***acpi=force*** in the appropriate line in etc/default/grub, blacklisting ***blacklist dw_dmac*** and ***dw_dmac_core*** (as suggested in one of he threads below), to no avail. 

Wondering whether it might be a Xubuntus-specific issue, I backed up my docs and tried a **fresh install** (not a live session) of **Ubuntu 15.04** (64-bit). No changes, same problem. So I got decided to go for a pro-active, no-BS approach and did fresh installs of **Kubuntu** (14.04, 14.10, 15.04, 15.10), **Mint 17** (MATE, KDE) and **Elementary** OS Freya. Same thing (with varying degrees of out-of-the-box hardware detection too; sometimes the trackpad wasn't recognized, sometimes the wireless adapter, sometimes both).

So I reckoned it might be an *buntu issue, and tried **Fedora**, **OpenSuse** and **Debian**,  (newest releases as of November '15). We're talking about at least 15 fresh installs using different distros. In some of these distros this error was present even in the live session; in others, live session was fine but issue appeared after a fresh install. 

Based on these *tests*, I'm guessing this is a **kernel**-related issue. Could that be the case? Another user had reported that things worked well in Fedora until he updated the kernel, then the issue reappeared.

When I first bought the laptop a year ago I also tried backporting kernels, but since then, I'm guessing current stable kernels would/should have fixed the issue. Might an older kernel be the solution to my problem?

I've been asking around and trying everything I've found on the forums ([http://ubuntuforums.org/showthread.php?t=2252074]("http://ubuntuforums.org/showthread.php?t=2252074") //  [http://ubuntuforums.org/showthread.php?t=2183391]("http://ubuntuforums.org/showthread.php?t=2183391")  //  [http://askubuntu.com/questions/524894/boot-and-shutdown-issues-on-aspire-e-11-model-e3-111-c0wa]("http://askubuntu.com/questions/524894/boot-and-shutdown-issues-on-aspire-e-11-model-e3-111-c0wa") //  [http://ubuntuforums.org/showthread.php?t=2121288 ]("http://ubuntuforums.org/showthread.php?t=2121288")) for a year now, to no avail...

Could this be an Ubuntu 64-bit issue? Might installing a 32-bit OS make a difference? (Laptop is 1 year old, so 64-bit architecture is supported, of course)

Any ideas...? **PLEASE...**! I've pretty much exhausted all the possibilities I've found in the forums, near-and-far, as well as the boundaries of my technical know-how, and am getting pretty desperate here. I really don't fancy having to go back to MS Windows as my main OS on this machine (no such issue in Windows), but daily forced power-offs can't be good for the hard drive (in fact, I've had kernel panic errors preventing OS boot twice now, forcing me to format)...

I could REALLY use the expertise of someone more savvy than myself and would be immensely appreciative for any help provided--at least to confirm my suspicions (OS architecture, kernel, etc.) and point me in the right direction. Thanks in advance and sorry for the soliloquy :D 

Edit: If I'm too vague in my description or more information is required to approach this particular issue, please don't hesitate to let me know and I'll be pleased to provide it; I don't expect someone else to solve this for me with no work on my behalf. Thanks!

---

### Post by kuckunniwi on 2015-12-21
Guys...I could really use some help...I've been literally asking around the forum for over a year....PLEASE, COMMUNITY, come to my rescue !!!

---

### Post by yoshii on 2015-12-21
My computer doesn't fully shut down either, but only AFTER I implemented anti-ACPI measures.  But I have to use them because I have a buggy BIOS.  I also disabled PNPBIOS, but I know from experience it's the ACPI stuff that relates to some of the hardware power.  Sorry I can't help much.  If I think of anything else I will come back and share it.

---

### Post by kuckunniwi on 2015-12-25
> **yoshi2 said:**
> My computer doesn't fully shut down either, but only AFTER I implemented anti-ACPI measures.  But I have to use them because I have a buggy BIOS.  I also disabled PNPBIOS, but I know from experience it's the ACPI stuff that relates to some of the hardware power.  Sorry I can't help much.  If I think of anything else I will come back and share it.

Thanks ! :D

---

### Post by kuckunniwi on 2016-01-04
Anyone out there...? PLEASE...?

---

### Post by kuckunniwi on 2016-02-02
Still no one?

---

### Post by qamelian on 2016-02-02
Aside from blacklisting dw_dmac, and dw_dmac_core, you might also need to add the following to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub:
```
intel_idle.max_cstate=1
```

That's what finally cleared up my issues with an Acer Aspire E5 E5-511.

---

### Post by kuckunniwi on 2016-02-02
> **qamelian said:**
> Aside from blacklisting dw_dmac, and dw_dmac_core, you might also need to add the following to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub:
```
intel_idle.max_cstate=1
```

That's what finally cleared up my issues with an Acer Aspire E5 E5-511.

Thanks for the suggestion. Just tried it (followed with update-grub, of course). Nothing has changed....any other ideas?

---

### Post by qamelian on 2016-02-02
Can't think of anything off the top of my head. Making that change and blacklisting dw__dmac and dw_dmac_core was all it took to fix the same problem for me.

---

### Post by kuckunniwi on 2016-02-03
Did a fresh install of Mint 17.3 Cinnamon. Installed wireless drivers and got touchpad to work (more or less) by adding *psmouse.proto=bare* to grub. **Blacklisted** ***dw_dmac*** and ***dw_dmac_core***, added the ***intel_idle.max_cstate=1*** to grub and no changes whatsoever.

**Upgraded kernel** to 4.2. No changes. **Downgraded** kernel to 3.13.0-45 > Now it shuts down correctly 1/2 of the time. Tried kernel 3.13.0-27, also 50/50. Might an older kerner be the solution to the problem?

---

### Post by kuckunniwi on 2017-01-15
Update: Fresh install of Mint 18.1, kernel 4.4.0-53. All updates applied. Same issue.

Tried blacklisting **blacklist wistron_btns**, as stated [here]("https://ubuntuforums.org/showthread.php?t=2220591&p=13012868#post13012868"), to no avail. Also tried all of the other options listed on this thread....NOTHING. What ON EARTH could be the problem?

System uses intel graphics. Installed intel-microcode 3.20151106.1. No changes...

This thread was opened in 2015 (and by then I'd already been having this problem for about a year). Since I opened the thread I've tried every distro since 14.04 Trusty to 16.04.1....Can anyone think of anything that hasn't been listed here???? I'm really running out of ideas and have swept the web, tried everything I've found and nothing has worked....Would be EXTREMELY grateful for any new insights into this issue...

---

### Post by kuckunniwi on 2017-01-15
Just tried, for the hell of it, adding this to grub GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=warm,cold,triple,kbd,acpi,efi,pci,force"

As expected, nothing...same thing...no results. Sigh...

---

### Post by venoty on 2017-09-16
[COLOR=#212121][FONT=arial]HelloIn BIOS, disable USB 3.0, it worked for me!!!

Good luck!![/FONT][/COLOR]

---

