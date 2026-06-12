---
title: "Possible missing firmware."
date: 2021-06-05
forum: General Help
---

### Post by Hewjr100 on 2021-06-05
This is what I get after a fresh install of Ubuntu 21.04 with ZFS.  Does not matter if I install Nvidia GTX 1650 or not.  System is running fine, but I wonder why I get this error message.   I assume the GPU is not that new, more likely old.  So why is this happening.  BTW this does not occur with EXT4 install, but I have problems with brightness and boot, reboot and shutdown with EXT4 setup.  Any explanation would help me to under what this is all about.

```
[COLOR=#000000][FONT=Calibri]W: Possible missing firmware /lib/firmware/amdgpu/vangogh_gpu_info.bin for module amdgpu[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/arcturus_gpu_info.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/dimgrey_cavefish_ta.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/dimgrey_cavefish_sos.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/vangogh_toc.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/vangogh_asd.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/arcturus_ta.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/arcturus_asd.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/arcturus_sos.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/arcturus_rlc.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/arcturus_mec2.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/arcturus_mec.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/dimgrey_cavefish_rlc.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/dimgrey_cavefish_mec2.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/dimgrey_cavefish_mec.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/dimgrey_cavefish_me.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/dimgrey_cavefish_pfp.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/dimgrey_cavefish_ce.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/vangogh_rlc.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/vangogh_mec2.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/vangogh_mec.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/vangogh_me.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/vangogh_pfp.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/vangogh_ce.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/arcturus_sdma.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/vangogh_sdma.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/dimgrey_cavefish_sdma.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/sienna_cichlid_mes.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/navi10_mes.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/dimgrey_cavefish_vcn.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/vangogh_vcn.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/arcturus_vcn.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/dimgrey_cavefish_smc.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/arcturus_smc.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/dimgrey_cavefish_dmcub.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]W: Possible missing firmware /lib/firmware/amdgpu/vangogh_dmcub.bin for module amdgpu[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]I: The initramfs will attempt to resume from /dev/nvme0n1p2[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][LEFT]I: (UUID=d992e5ff-97b2-40b0-97ac-0d68a6e1bdd1)[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri]I: Set the RESUME variable to override this.[/FONT][/COLOR]
```

Henry

---

### Post by ActionParsnip on 2021-06-05
[https://community.amd.com/t5/drivers-software/can-t-install-amdgpu-drivers-on-ubuntu-20-04-1-5-4-0-56-generic/td-p/426676/page/19](https://community.amd.com/t5/drivers-software/can-t-install-amdgpu-drivers-on-ubuntu-20-04-1-5-4-0-56-generic/td-p/426676/page/19)

---

### Post by Yellow Pasque on 2021-06-05
[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1922350](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1922350)

The bottom line is that you don't need to worry about it unless you have a Radeon RX6000-series card.

---

### Post by Hewjr100 on 2021-06-05
Thanks, now I have an idea to work with.

Henry

---

