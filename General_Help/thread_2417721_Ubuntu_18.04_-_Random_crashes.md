---
title: "Ubuntu 18.04 - Random crashes"
date: 2019-04-26
forum: General Help
---

### Post by scpsc on 2019-04-26
Hi everyone,

I just experienced a crash with a 1-week-fresh installation of Ubuntu 18.04. Here is what I found in syslog at the time of the crash:

```
Apr 26 13:19:37 pcarthur org.gnome.Shell.desktop[2798]: [Parent 3353, Gecko_IOThread] WARNING: pipe error (268): Connexion ré-initialisée par le correspondant: file /build/firefox-6m4fHv/firefox-66.0.3+build1/ipc/chromium/src/chrome/common/ipc_channel_posix.cc, line 357
Apr 26 13:19:37 pcarthur org.gnome.Shell.desktop[2798]: [Parent 3353, Gecko_IOThread] WARNING: pipe error (159): Connexion ré-initialisée par le correspondant: file /build/firefox-6m4fHv/firefox-66.0.3+build1/ipc/chromium/src/chrome/common/ipc_channel_posix.cc, line 357
Apr 26 13:19:37 pcarthur kernel: [ 9752.989260] DMAR: DRHD: handling fault status reg 2
Apr 26 13:19:37 pcarthur kernel: [ 9752.989272] DMAR: [INTR-REMAP] Request device [00:00.0] fault index 28 [fault reason 38] Blocked an interrupt request due to source-id verification failure
```

The 2 "DMAR" lines seem to be the same issue I had with Ubuntu 16.04, same computer. [Here]("https://ubuntuforums.org/showthread.php?t=2362492") is a thread I opened a while ago about this, which is closed now.

So updating to a "modern" version of Ubuntu, as wisely suggested by mörgæs in the old thread doesn't seem to fix the problem :(

This is my configuration:

2 Intel Xeon E5-2620
256G SSD M.2
+ 2T HD
32G RAM
AMD FirePro W4100

Thanks for your help!

---

### Post by cruzer001 on 2019-04-26
RedHat had a similar issue. Have you seen this?

> add kernel parameter 
```
intremap=no_x2apic_optout
```

[https://support.hpe.com/hpsc/doc/public/display?docId=emr_na-a00019143en_us](https://support.hpe.com/hpsc/doc/public/display?docId=emr_na-a00019143en_us)

[https://wiki.ubuntu.com/Kernel/KernelBootParameters#Temporarily_Add_a_Kernel_Boot_Parameter_for_Testing](https://wiki.ubuntu.com/Kernel/KernelBootParameters#Temporarily_Add_a_Kernel_Boot_Parameter_for_Testing)

---

### Post by scpsc on 2019-04-29
Thanks for your input, I added the parameter. As the crash is random, I don't know yet if it fixed it but I will post here the result soon.

---

### Post by scpsc on 2019-05-02
I had 2 crashes since that change, so the issue is still here. Here is the syslog for last crash:
```
May  2 10:08:55 pcarthur systemd[1]: Starting Network Manager Script Dispatcher Service...
May  2 10:08:55 pcarthur systemd[1]: Started Network Manager Script Dispatcher Service.
May  2 10:09:11 pcarthur org.gnome.Shell.desktop[2786]: [Parent 7809, Gecko_IOThread] WARNING: pipe error (182): Connexion ré-initialisée par le correspondant: file /build/firefox-6m4fHv/firefox-66.0.3+build1/ipc/chromium/src/chrome/common/ipc_channel_posix.cc, line 357
May  2 10:10:00 pcarthur kernel: [ 1466.171347] DMAR: DRHD: handling fault status reg 2
May  2 10:10:00 pcarthur kernel: [ 1466.171360] DMAR: [INTR-REMAP] Request device [00:00.0] fault index 28 [fault reason 38] Blocked an interrupt request due to source-id verification failure
```
Before the 2 DMAR lines, there is the same warning for chromium than in the first crash report. I don't know if it is related though (and the time is not the time of the crash in this second report).

I don't know if I should remove the suggested change in kernel parameters. I think my computer is starting faster since that change. Is that possible? Anyway, it might be a better idea to put things like they were, what do you think?

So I'm still looking for a solution, if any of you have an idea.

Thanks!

---

### Post by scpsc on 2019-05-29
A friend of mine found a solution to my issue: enter the BIOS, go to Virtualization Support and siwtch "VT for Direct I/O" off. No freeze/crash since I made this change!

---

