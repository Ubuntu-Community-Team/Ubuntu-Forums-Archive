---
title: "xorg freezes and causes dual core CPU 100%, reboot fix only"
date: 2012-12-21
forum: General Help
---

### Post by diskmaster23 on 2012-12-21
I've been searching the forums for a solution to this problem. By looking at the bug reports and other forums, I know there folks out there that haven't found a solution to the typical xorg freezing randomly and causing it to max out the CPU on multiple cores. I've tried every solution in the that was recommended in the many forums, but have yet to find a solution. Here are the solutions I've tried.
[LIST]
[*]Put "Option "UseEvents" "false"" into my xorg.conf under the device section.
[*]Turned down my AGP port speed from 8x to 4x by adding this to my /etc/modules/ "nvidia NVreg_ReqAGPRate=4" *(I am running a AGP GeForce 6200(?) nvidia card.)
[*]Upgraded from Mythbuntu 10.04 to Xbmcbuntu 12.10 (Kinda was looking to try something different for a media center, also thought that a kernel upgrade would fix my problem)
[*]Used various versions of nvidia drivers, now currently on 304.51.
[*]set my nvidia card to persistence mode by adding this to my rc.local, nvidia-smi -pm 1 (I think this probably is what helped prolong a crash the best)
[*]Removed AGPGart from the kernel and recompiled the kernel without it. I am running an NForce3 chipset, so I figured it might help to run NvAGP instead of AGPGart, but it didn't work.
[/LIST]

This bug has been affecting hundreds, possibly thousands, of users with a very similar problem with no real solution.

I am willing to provide any logs, specifications, or anything else related to solving this problem.

The problem typically happens with:
[LIST]
[*]The screen freezing
[*]followed by broken sound and non-responsiveness to any input other than SSH
[*]After SSHing in, TOP reveals that Xorg is consuming multiple cores at high usage. Xorg cannot be killed. GUI cannot be reinstated, even when init levels are changed. Reboot is the only cure.
[/LIST]

Dmesg shows the following errors before you finally decide to do a safe reboot from SSH.
[http://pastebin.com/0Ey7AZXe](http://pastebin.com/0Ey7AZXe)

Here is my Xorg log. You'll see the typical NVIDIA(0): WAIT error.
[http://pastebin.com/0TMxXY1r](http://pastebin.com/0TMxXY1r)

kernal.log
[http://pastebin.com/EpujC3iW](http://pastebin.com/EpujC3iW)
Typical error, NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
NVRM: Xid (0000:01:00): 8, Channel 00000020

Any help would be greatly appreciated.

---

### Post by diskmaster23 on 2012-12-27
The only fix this whole thing was to add in a new video card that had either VDPAU or VAAPI. Once I added the new video card to offload the CPU then my problem went away.

---

