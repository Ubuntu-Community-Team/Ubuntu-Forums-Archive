---
title: "After upgrade to 18.04 no GUI"
date: 2018-11-29
forum: General Help
---

### Post by DantePasquale on 2018-11-29
Hi, I just upgraded from 16.04 to 18.04 and the display manager doesn't startup

Console hangs on this line: Started Update UTMP about SystemRunlevel Changes.

I tried to start gdm3 in an alternate console but it says OK

```

root@inferno:~# lspci -v -s 85:00.0
85:00.0 VGA compatible controller: NVIDIA Corporation GP106 [GeForce GTX 1060 6GB] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: eVga.com. Corp. GP106 [GeForce GTX 1060 6GB]
	Flags: bus master, fast devsel, latency 0, IRQ 16, NUMA node 1
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at ce000000 (64-bit, prefetchable) [size=32M]
	I/O ports at ec00 [size=128]
	[virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [250] Latency Tolerance Reporting
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [420] Advanced Error Reporting
	Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia

```

Here's the dmesg re: NVidia

```

[   25.127476] nvidia: loading out-of-tree module taints kernel.
[   25.127487] nvidia: module license 'NVIDIA' taints kernel.
[   25.136599] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[   25.968399] nvidia-nvlink: Nvlink Core is being initialized, major device number 238
[   25.968939] nvidia 0000:85:00.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=none:owns=io+mem
[   25.969188] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  390.77  Tue Jul 10 18:28:52 PDT 2018 (using threaded interrupts)
[   26.305508] nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  390.77  Tue Jul 10 22:10:46 PDT 2018
[   26.722829] [drm] [nvidia-drm] [GPU ID 0x00008500] Loading driver
[   26.778065] [drm] Initialized nvidia-drm 0.0.0 20160202 for 0000:85:00.0 on minor 0
[  166.386341] nvidia-uvm: Loaded the UVM driver in 8 mode, major device number 237
[  167.109789] caller os_map_kernel_space.part.7+0xda/0x120 [nvidia] mapping multiple BARs
[  167.569498] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:80/0000:80:07.0/0000:85:00.1/sound/card1/input18
[  167.569618] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:80/0000:80:07.0/0000:85:00.1/sound/card1/input19
[  167.569732] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:80/0000:80:07.0/0000:85:00.1/sound/card1/input20
[  167.569803] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:80/0000:80:07.0/0000:85:00.1/sound/card1/input21

```

lsmod:

```
dante@inferno:~$ lsmod | grep -i nv
nvidia_uvm            757760  0
nvidia_drm             40960  0
nvidia_modeset       1110016  1 nvidia_drm
nvidia              14360576  2 nvidia_uvm,nvidia_modeset
drm_kms_helper        172032  1 nvidia_drm
drm                   401408  3 drm_kms_helper,nvidia_drm
ipmi_msghandler        53248  3 ipmi_devintf,ipmi_si,nvidia
```


```

root@inferno:~# systemctl status gdm3
[COLOR="#008000"]&#9679;[/COLOR] gdm.service - GNOME Display Manager
   Loaded: loaded (/lib/systemd/system/gdm.service; static; vendor preset: enabled)
  Drop-In: /lib/systemd/system/display-manager.service.d
           &#9492;&#9472;xdiagnose.conf
   Active: active (running) since Thu 2018-11-29 17:04:35 EST; 1min 37s ago
  Process: 2140 ExecStartPre=/usr/share/gdm/generate-config (code=exited, status=0/SUCCESS)
 Main PID: 2184 (gdm3)
    Tasks: 6 (limit: 4915)
   CGroup: /system.slice/gdm.service
           &#9500;&#9472;2184 /usr/sbin/gdm3
           &#9492;&#9472;2277 gdm-session-worker [pam/gdm-launch-environment]


```


modinfo nvidia

```
dante@inferno:~$ modinfo nvidia
filename:       /lib/modules/4.15.0-39-generic/updates/dkms/nvidia.ko
alias:          char-major-195-*
version:        390.77
supported:      external
license:        NVIDIA
srcversion:     209B1D0CB123DE466F700AD
alias:          pci:v000010DEd00000E00sv*sd*bc04sc80i00*
alias:          pci:v000010DEd*sv*sd*bc03sc02i00*
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
depends:        ipmi_msghandler
retpoline:      Y
name:           nvidia
vermagic:       4.15.0-39-generic SMP mod_unload 
parm:           NVreg_Mobile:int
parm:           NVreg_ResmanDebugLevel:int
parm:           NVreg_RmLogonRC:int
parm:           NVreg_ModifyDeviceFiles:int
parm:           NVreg_DeviceFileUID:int
parm:           NVreg_DeviceFileGID:int
parm:           NVreg_DeviceFileMode:int
parm:           NVreg_UpdateMemoryTypes:int
parm:           NVreg_InitializeSystemMemoryAllocations:int
parm:           NVreg_UsePageAttributeTable:int
parm:           NVreg_MapRegistersEarly:int
parm:           NVreg_RegisterForACPIEvents:int
parm:           NVreg_CheckPCIConfigSpace:int
parm:           NVreg_EnablePCIeGen3:int
parm:           NVreg_EnableMSI:int
parm:           NVreg_TCEBypassMode:int
parm:           NVreg_UseThreadedInterrupts:int
parm:           NVreg_EnableStreamMemOPs:int
parm:           NVreg_EnableBacklightHandler:int
parm:           NVreg_EnableUserNUMAManagement:int
parm:           NVreg_EnableIBMNPURelaxedOrderingMode:int
parm:           NVreg_MemoryPoolSize:int
parm:           NVreg_IgnoreMMIOCheck:int
parm:           NVreg_RegistryDwords:charp
parm:           NVreg_RegistryDwordsPerDevice:charp
parm:           NVreg_RmMsg:charp
parm:           NVreg_AssignGpus:charp

```

---

### Post by DantePasquale on 2018-11-30
Solved: re-installed desktop, lightdm, and nvidia drivers multiple times and now it's working -- no clue exactly why

---

