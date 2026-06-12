---
title: "can't enable fast writes and SBA for nvidia card"
date: 2008-02-15
forum: General Help
---

### Post by miatawnt2b on 2008-02-15
OK, so I am trying to enable fast writes and SBA on my Nvidia card.  Problem is that I see the NVdriver NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1 options in the nvidia-kernel-nkc file but things still aren't enabled.

xxx@xxx: cat /proc/driver/nvidia/agp/card
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       4x 2x 1x 
Registers:       0x1f000217:0x1f000104

xxx@xxx:  cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled


and the nvidia-kernel-nkc file looks like this.

alias char-major-195* nvidia

options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1 NVreg_NvAGP=3 NVreg_Devi
ceFileMode=0666 NVreg_DeviceFileUID=0 NVreg_DeviceFileGID=44 NVreg_ModifyDeviceF
iles=1 NVreg_ReqAGPRate=4


Anyone have any idea why FastWrites and SBA are still disabled?
-J

---

### Post by UnRkiSt on 2008-02-16
What does host-bridge tell you?  Are fast writes supported?

---

### Post by miatawnt2b on 2008-02-17
> **miatawnt2b said:**
> OK, so I am trying to enable fast writes and SBA on my Nvidia card.  Problem is that I see the NVdriver NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1 options in the nvidia-kernel-nkc file but things still aren't enabled.

xxx@xxx: cat /proc/driver/nvidia/agp/card
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       4x 2x 1x 
Registers:       0x1f000217:0x1f000104

xxx@xxx:  cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled


and the nvidia-kernel-nkc file looks like this.

alias char-major-195* nvidia

options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1 NVreg_NvAGP=3 NVreg_Devi
ceFileMode=0666 NVreg_DeviceFileUID=0 NVreg_DeviceFileGID=44 NVreg_ModifyDeviceF
iles=1 NVreg_ReqAGPRate=4


Anyone have any idea why FastWrites and SBA are still disabled?
-J

I figured it out.  in the nvidia-kernel-nkc, the 'options nvidia' should instead be 'options nvidia_new'
-J

---

