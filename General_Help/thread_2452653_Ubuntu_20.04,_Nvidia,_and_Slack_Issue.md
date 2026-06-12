---
title: "Ubuntu 20.04, Nvidia, and Slack Issue"
date: 2020-10-26
forum: General Help
---

### Post by sdsurfer on 2020-10-26
**The problem: **Recently upgraded from 18.04 to 20.04, **mostly** without issue except one.After a screen lock, returning to Slack  displays many of the panes (sidebar, some channels) black. Exiting Slack  and restarting appears to solve it, but it's annoying .... Slack was fine  before upgrading to 20.04. Purged and reinstalled both Nvidia drivers and Slack, no love. I believe this to be an Nvidia driver issue  but cannot confirm. 

**Environment:** The issue is primarily with Slack desktop after upgrading to Ubuntu  20.04, but I've seen it in Chrome as well. As below, all packages latest  versions. All other applications seem to be fine.

**System Info:**
20.04 LTS, added a bunch of software updates this morning per the software updates prompt, should be latest.
System76 Gazelle version gaze14
BIOS INSYDE Corp. version 1.07.09f-1
CPU 4 cores  Intel(R) Core(TM) i7-9750H CPU @ 2.60GHz
RAM 16GB SODIMM DDR4 Synchronous 2667 MHz
GPU GeForce GTX 1660 Ti Mobile version a1 (also has onboard Intel, disabled)
uname -r = 5.4.0-52-generic

```

ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00002191sv00001558sd00008550bc03sc00i00
vendor   : NVIDIA Corporation
model    : TU116M [GeForce GTX 1660 Ti Mobile]
driver   : nvidia-driver-450-server - distro non-free
driver   : nvidia-driver-450 - distro non-free recommended
driver   : nvidia-driver-418-server - distro non-free
driver   : nvidia-driver-435 - distro non-free
driver   : nvidia-driver-440-server - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

```

Initially the "recommended," V 450 was enabled, I then rolled back to 440 which didn't fix the issue.

**Slack version** Production 4.10.3 64-bit
[COLOR=#5F6368][FONT=Roboto]**Chrom(ium) Version** 86.0.4240.111 64 bit
[/FONT][/COLOR]
I've done due diligence, been on it a week or so not finding any relevant articles out there, anyone got any ideas?

---

### Post by sdsurfer on 2020-10-26
Apparently after chat with Slack, it is not a driver issue, there have been reports. Their suggested fix:

- At first go to Preferences, disable hardware acceleration.
- Go to Help->Troubleshooting->Clear Cache and Restart. This will reset your current windows but no big deal.
- **This will log you out of Slack. **Go to Help->Troubleshooting->Reset App Data

Try the first two first, see if it goes away. Then re-enable hardware acceleration, see if it returns. If it persists, do 1 and 3, see if it goes away. If it does, re-enable hardware acceleration.

Agreed, it's a hit/miss and they don't really know why it's broken, but if it works, it works. In my case I have to leave the machine in a locked screen/sleep state for extended periods of time to reproduce the issue. If I get through a couple of those and it goes away, will return to mark thread as solved.

---

### Post by sdsurfer on 2020-10-27
After all of the above: It's hardware acceleration. Official response from Slack:> [COLOR=#2B2E2F][FONT=&quot]In the meantime, it sounds like you've already found the suggested workaround which is to disable hardware acceleration in the app.

They are working on a fix. I do notice without hardware acceleration the panels/channels seem to load a bit slower, but it's workable.
[/FONT][/COLOR]

---

