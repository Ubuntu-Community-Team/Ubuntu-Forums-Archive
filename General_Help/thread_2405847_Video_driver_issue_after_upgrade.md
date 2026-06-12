---
title: "Video driver issue after upgrade"
date: 2018-11-12
forum: General Help
---

### Post by benlyboy on 2018-11-12
Hi I originally posted this problem in the upgrades and installs . but have now moved over here as I now think its a video driver issues.

My problems started after deciding to upgrade my system to 18.04 and finding it wouldn't boot after woulds.
Hi I originally posted this problem in the upgrades and installs . but have now moved over here as I now think its a video driver issues.

My problems started after deciding to upgrade my system to 18.04 and finding it wouldn't boot after woul
The computer is an old Dell that we have had for quite some time I actually know very little about its specs, so I ran lshw. This is some of the resulting information.
I did notice two things my self from this info, first you can't see on here but the listings for the video were the only ones in red.
The second is as you can see there are two of them.

I should probably add there is no additional video card installed, only the motherboards on board video.

id: thereHi I originally posted this problem in the upgrades and installs . but have now moved over here as I now think its a video driver issues.

My problems started after deciding to upgrade my system to 18.04 and finding it wouldn't boot after woul
graham-optiplex-755
description: Desktop Computerinstalled
product: OptiPlex 755
vendor: Dell Inc.
serial: JYRN1J1i
width: 64 bitsyes

id:
display:0
description: VGA compatible controller
product: 82Q35 Express Integrated GrapHi I originally posted this problem in the upgrades and installs . but have now moved over here as I now think its a video driver issues.Hi I originally posted this problem in the upgrades and installs . but have now moved over here as I now think its a video driver issues.

My problems started after deciding to upgrade my system to 18.04 and finding it wouldn't boot after woul

My problems started after deciding to upgrade my system to 18.04 and finding it wouldn't boot after woulhics Controller
vendor: Intel Corporation
physical id:
2
bus info:
pci@0000:00:02.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: msi pm vga_controller cap_list
configuration:Hi I originally posted this problem in the upgrades and installs . but have now moved over here as I now think its a video driver issues.

My problems started after deciding to upgrade my system to 18.04 and finding it wouldn't boot after woul
latency = 0
resources:
memory : fea00000-fea7ffff
ioport : ec90(size=8)
memory : d0000000-dfffffff
memory : feb00000-febfffffHi I originally posted this problem in the upgrades and installs . but have now moved over here as I now think its a video driver issues.

My problems started after deciding to upgrade my system to 18.04 and finding it wouldn't boot after woul
memory : c0000-dffff

id:
display:1Hi I originally posted this problem in the upgrades and installs . but have now moved over here as I now think its a video driver issues.

My problems started after deciding to upgrade my system to 18.04 and finding it wouldn't boot after woul
description: Display controller
product: 82Q35 Express Integrated Graphics Controller
vendor: Intel Corporation
physical id:
2.1
bus info:
pci@0000:00:02.1
version: 02
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cHi I originally posted this problem in the upgrades and installs . but have now moved over here as I now think its a video driver issues.

My problems started after deciding to upgrade my system to 18.04 and finding it wouldn't boot after woulap_list
configuration:
latency = 0
resources:
memory : fea80000-feafffff


So I did some research on line and it seems that 18.04 has an issue with older intel video chips.

The funny thing is that if I boot into recovery mode then from there go ahead and select boot normally I get a warning that says something like "some video drivers require full boot if the system fails to boot go ahead and restart your computer" something along those lines.

The fact that its working great when I boot this way make me wonder if a selected driver isn't loading when I boot this way, and the system is then falling back on a backup driver.
The graphics are perfectly fine in this mode. so I'm wondering if maybe the answer is to deselect that main driver and let the backup take over?

is this a possibility?

---

### Post by oldos2er on 2018-11-12
Near duplicate of [https://ubuntuforums.org/showthread.php?t=2405767&p=13815402#post13815402](https://ubuntuforums.org/showthread.php?t=2405767&p=13815402#post13815402) closed. Please don't create duplicate threads, see [https://ubuntuforums.org/showthread.php?t=2158945](https://ubuntuforums.org/showthread.php?t=2158945)

If you wish a member of staff to move your original thread, use the Report Post icon to ask that it be moved. Thanks.

---

