---
title: "amdgpu proprietary driver for ubuntu LIMIT MY NUMBER OF CORES??"
date: 2023-09-11
forum: General Help
---

### Post by habernir on 2023-09-11
[COLOR=#000000][FONT=&quot]i have amd 5950x cpu that is 16 cores and 32 threads and 7900 xtx gpu[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]I have a very strange case that AFTER i install amdgpu proprietary driver for ubuntu its limit my cpu to 16 threads    [FONT=Verdana](i test it in some 3d software and all the same , all of them detect 16 threads)[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]and after i uninstall it its return to use 32 threads [FONT=Verdana](the 3d softwares detect 32 threads)[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]the installation command that i used its:[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]amdgpu-install --usecase=workstation,rocm --vulkan=amdvlk,pro --opencl=rocr,legacy[/FONT][/COLOR]
[COLOR=#000000]
Has anyone come across something like this?
[/COLOR]

---

### Post by MAFoElffen on 2023-09-11
My disclaimer, I do not have an AMD Ryzen CPU, nor AMD GPU.

With the Windows drivers:
[https://community.amd.com/t5/processors/5950x-with-8-cores-active-only-can-t-activate-all-cores/td-p/475457](https://community.amd.com/t5/processors/5950x-with-8-cores-active-only-can-t-activate-all-cores/td-p/475457)
[https://www.reddit.com/r/Amd/comments/vpgh2m/amd_radeon_driver_changes_cpu_clocks_power_limits/](https://www.reddit.com/r/Amd/comments/vpgh2m/amd_radeon_driver_changes_cpu_clocks_power_limits/)
[https://www.reddit.com/r/Amd/comments/txkbe8/heres_how_the_wattmanpbo_cpu_overclock_bug_works/](https://www.reddit.com/r/Amd/comments/txkbe8/heres_how_the_wattmanpbo_cpu_overclock_bug_works/)

But haven't heard anything on the Linux side of that...

I would say from the links about, that yes, there might be some connections between the two, and that the place to ask might be the AMD Forums, where there is a more likely a chance that people there have that hardware combination.

If you do find out, please post back what you find. I try to support people with Linux Graphics issues, am curious what might be going on, and the solutions to that.

---

### Post by #&amp;thj^% on 2023-09-11
> **MAFoElffen said:**
> My disclaimer, I do not have an AMD Ryzen CPU, nor AMD GPU.

I would say from the links about, that yes, there might be some connections between the two, and that the place to ask might be the AMD Forums, where there is a more likely a chance that people there have that hardware combination.

If you do find out, please post back what you find. I try to support people with Linux Graphics issues, am curious what might be going on, and the solutions to that.
+1 The forums (AMD)
And I had luck with,  I've added the following after the "quiet splash" radeon.cik_support=0 amdgpu.cik_support=1 amdgpu.dc=1" To Grub.
But mine is **"AMD Ryzen 5 4600H with Radeon Graphics**"

I'm assuming you know how, if not just ask.

---

### Post by habernir on 2023-09-12
> **1fallen said:**
> +1 The forums (AMD)
And I had luck with,  I've added the following after the "quiet splash" radeon.cik_support=0 amdgpu.cik_support=1 amdgpu.dc=1" To Grub.
But mine is **"AMD Ryzen 5 4600H with Radeon Graphics**"

I'm assuming you know how, if not just ask.

how its related to the cores problem? do you have the same issue and its solved your "number of cores" problem?

---

### Post by habernir on 2023-09-12
> **malisa00 said:**
> Check System Configuration: Ensure that the CPU configuration in your system's BIOS or UEFI settings is correctly set to utilize all available cores and threads. Verify that no settings limiting the CPU resources are enabled.

i already check BIOS and multithread  in ubuntu its enabled

---

### Post by #&amp;thj^% on 2023-09-12
> **habernir said:**
> how its related to the cores problem? do you have the same issue and its solved your "number of cores" problem?
??? What?
Of course it helped, but i also have the switchable nVidia chip, and that was used until I could figure out how to get all my cores online with the AMDgpu.
With nVidia:
```
sudo lshw -c video
  *-display                 
       description: VGA compatible controller
       product: TU117M [GeForce GTX 1650 Ti Mobile]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: iomemory:1fa0-1f9f iomemory:1fa0-1f9f irq:36 memory:d0000000-d0ffffff memory:1fa50000000-1fa5fffffff memory:1fa60000000-1fa61ffffff ioport:2000(size=128) memory:d1080000-d10fffff
  *-graphics
       product: EFI VGA
       physical id: 3
       logical name: /dev/fb0
       capabilities: fb
       configuration: depth=32 resolution=1920,1080

```
**Before the Driver is enabled**
```
lsmod | grep amd
snd_sof_amd_rembrandt    16384  0
snd_sof_amd_renoir     16384  0
snd_sof_amd_acp        57344  2 snd_sof_amd_rembrandt,snd_sof_amd_renoir
snd_sof_pci            24576  2 snd_sof_amd_rembrandt,snd_sof_amd_renoir
snd_sof_xtensa_dsp     16384  1 snd_sof_amd_acp
snd_sof               421888  2 snd_sof_amd_acp,snd_sof_pci
edac_mce_amd           53248  0
kvm_amd               204800  0
kvm                  1372160  1 kvm_amd
snd_acp_config         16384  7 snd_rn_pci_acp3x,snd_pci_acp6x,snd_pci_acp5x,snd_sof_amd_rembrandt,snd_acp_pci,snd_pci_ps,snd_sof_amd_renoir
snd_soc_acpi           12288  2 snd_sof_amd_acp,snd_acp_config
snd_pcm               204800  13 snd_sof_amd_acp,snd_hda_codec_hdmi,snd_pci_acp6x,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_sof,snd_compress,snd_soc_core,snd_sof_utils,snd_hda_core,snd_pci_ps,snd_pcm_dmaengine
ccp                   159744  1 kvm_amd

```
***Reboot to AMDGPU***
```
glxinfo -B
name of display: :0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: AMD (0x1002)
    Device: AMD Radeon Graphics (renoir, LLVM 16.0.6, DRM 3.54, 6.5.2-arch1-1) (0x1636)
    Version: 23.1.7
    Accelerated: yes
    Video memory: 512MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 4.6
    Max compat profile version: 4.6
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.2
Memory info (GL_ATI_meminfo):
    VBO free memory - total: 319 MB, largest block: 319 MB
    VBO free aux. memory - total: 7627 MB, largest block: 7627 MB
    Texture free memory - total: 319 MB, largest block: 319 MB
    Texture free aux. memory - total: 7627 MB, largest block: 7627 MB
    Renderbuffer free memory - total: 319 MB, largest block: 319 MB
    Renderbuffer free aux. memory - total: 7627 MB, largest block: 7627 MB
Memory info (GL_NVX_gpu_memory_info):
    Dedicated video memory: 512 MB
    Total available memory: 8191 MB
    Currently available dedicated video memory: 319 MB
OpenGL vendor string: AMD
OpenGL renderer string: AMD Radeon Graphics (renoir, LLVM 16.0.6, DRM 3.54, 6.5.2-arch1-1)
OpenGL core profile version string: 4.6 (Core Profile) Mesa 23.1.7-arch1.1
OpenGL core profile shading language version string: 4.60
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

OpenGL version string: 4.6 (Compatibility Profile) Mesa 23.1.7-arch1.1
OpenGL shading language version string: 4.60
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile

OpenGL ES profile version string: OpenGL ES 3.2 Mesa 23.1.7-arch1.1
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20


```
***Now check the Core's total***
```
lscpu
Architecture:            x86_64
  CPU op-mode(s):        32-bit, 64-bit
  Address sizes:         48 bits physical, 48 bits virtual
  Byte Order:            Little Endian
CPU(s):                  12
  On-line CPU(s) list:   0-11
Vendor ID:               AuthenticAMD
  Model name:            AMD Ryzen 5 4600H with Radeon Graphics
    CPU family:          23
    Model:               96
    Thread(s) per core:  2
    Core(s) per socket:  6
    Socket(s):           1
    Stepping:            1
    Frequency boost:     enabled
    CPU(s) scaling MHz:  46%
    CPU max MHz:         3000.0000
    CPU min MHz:         1400.0000
    BogoMIPS:            5991.74
    Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx f
                         xsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good no
                         pl nonstop_tsc cpuid extd_apicid aperfmperf rapl pni pclmulqdq monitor ssse3 fma cx16
                          sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic 
                         cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt tce topoext perfct
                         r_core perfctr_nb bpext perfctr_llc mwaitx cpb cat_l3 cdp_l3 hw_pstate ssbd mba ibrs 
                         ibpb stibp vmmcall fsgsbase bmi1 avx2 smep bmi2 cqm rdt_a rdseed adx smap clflushopt 
                         clwb sha_ni xsaveopt xsavec xgetbv1 cqm_llc cqm_occup_llc cqm_mbm_total cqm_mbm_local
                          clzero irperf xsaveerptr rdpru wbnoinvd cppc arat npt lbrv svm_lock nrip_save tsc_sc
                         ale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic v_vmsave_vmload
                          vgif v_spec_ctrl umip rdpid overflow_recov succor smca
Virtualization features: 
  Virtualization:        AMD-V
Caches (sum of all):     
  L1d:                   192 KiB (6 instances)
  L1i:                   192 KiB (6 instances)
  L2:                    3 MiB (6 instances)
  L3:                    8 MiB (2 instances)
NUMA:                    
  NUMA node(s):          1
  NUMA node0 CPU(s):     0-11
Vulnerabilities:         
  Gather data sampling:  Not affected
  Itlb multihit:         Not affected
  L1tf:                  Not affected
  Mds:                   Not affected
  Meltdown:              Not affected
  Mmio stale data:       Not affected
  Retbleed:              Mitigation; untrained return thunk; SMT enabled with STIBP protection
  Spec rstack overflow:  Mitigation; safe RET
  Spec store bypass:     Mitigation; Speculative Store Bypass disabled via prctl
  Spectre v1:            Mitigation; usercopy/swapgs barriers and __user pointer sanitization
  Spectre v2:            Mitigation; Retpolines, IBPB conditional, STIBP always-on, RSB filling, PBRSB-eIBRS N
                         ot affected
  Srbds:                 Not affected
  Tsx async abort:       Not affected

```
or a simple look:
```
getconf _NPROCESSORS_ONLN
12

```
So yes it helped on my system, I had to dump the earlier 5.15 kernels though
kernel 5.19 was acceptable, but best results on kernels 6.2 or newer.

I also have an advantage wiith a nVidia card, which I had and have no problems with that installed as well.
```
sudo dmesg | grep -i amdgpu
[sudo] password for me:               
[    0.000000] Command line: BOOT_IMAGE=/@/boot/vmlinuz-linux root=UUID=710f09be-a848-4c26-bc5b-e61b183ba942 rw rootflags=subvol=@ loglevel=3 lsm=landlock,lockdown,yama,integrity,apparmor,bpf quiet radeon.cik_support=0 amdgpu.cik_support=1 amdgpu.dc=1 nvidia_drm.modeset=1
[    0.036470] Kernel command line: BOOT_IMAGE=/@/boot/vmlinuz-linux root=UUID=710f09be-a848-4c26-bc5b-e61b183ba942 rw rootflags=subvol=@ loglevel=3 lsm=landlock,lockdown,yama,integrity,apparmor,bpf quiet radeon.cik_support=0 amdgpu.cik_support=1 amdgpu.dc=1 nvidia_drm.modeset=1
[   10.823716] [drm] amdgpu kernel modesetting enabled.
[   10.823743] amdgpu: vga_switcheroo: detected switching method \_SB_.PCI0.GP17.VGA_.ATPX handle
[   10.828671] amdgpu: CRAT table disabled by module option
[   10.828676] amdgpu: Virtual CRAT table created for CPU
[   10.828692] amdgpu: Topology: Add CPU node
[   10.828853] amdgpu 0000:05:00.0: enabling device (0006 -> 0007)
[   10.831298] amdgpu 0000:05:00.0: amdgpu: Fetched VBIOS from VFCT
[   10.831300] amdgpu: ATOM BIOS: 113-RENOIR-026
[   10.843044] amdgpu 0000:05:00.0: vgaarb: deactivate vga console
[   10.843048] amdgpu 0000:05:00.0: amdgpu: Trusted Memory Zone (TMZ) feature enabled
[   10.843058] amdgpu 0000:05:00.0: amdgpu: MODE2 reset
[   10.843295] amdgpu 0000:05:00.0: amdgpu: VRAM: 512M 0x000000F400000000 - 0x000000F41FFFFFFF (512M used)
[   10.843298] amdgpu 0000:05:00.0: amdgpu: GART: 1024M 0x0000000000000000 - 0x000000003FFFFFFF
[   10.843300] amdgpu 0000:05:00.0: amdgpu: AGP: 267419648M 0x000000F800000000 - 0x0000FFFFFFFFFFFF
[   10.843445] [drm] amdgpu: 512M of VRAM memory ready
[   10.843448] [drm] amdgpu: 7679M of GTT memory ready.
[   10.844461] amdgpu 0000:05:00.0: amdgpu: Will use PSP to load VCN firmware
[   11.523932] amdgpu 0000:05:00.0: amdgpu: RAS: optional ras ta ucode is not available
[   11.531469] amdgpu 0000:05:00.0: amdgpu: RAP: optional rap ta ucode is not available
[   11.535803] amdgpu 0000:05:00.0: amdgpu: Secure display: Generic Failure.
[   11.535807] amdgpu 0000:05:00.0: amdgpu: SECUREDISPLAY: query securedisplay TA failed. ret 0x0
[   11.536008] amdgpu 0000:05:00.0: amdgpu: SMU is initialized successfully!
[   11.750343] amdgpu: HMM registered 512MB device memory
[   11.751874] kfd kfd: amdgpu: Allocated 3969056 bytes on gart
[   11.751890] kfd kfd: amdgpu: Total number of KFD nodes to be created: 1
[   11.751993] amdgpu: Virtual CRAT table created for GPU
[   11.752083] amdgpu: Topology: Add dGPU node [0x1636:0x1002]
[   11.752085] kfd kfd: amdgpu: added device 1002:1636
[   11.752096] amdgpu 0000:05:00.0: amdgpu: SE 1, SH per SE 1, CU per SH 8, active_cu_number 6
[   11.752201] amdgpu 0000:05:00.0: amdgpu: ring gfx uses VM inv eng 0 on hub 0
[   11.752203] amdgpu 0000:05:00.0: amdgpu: ring gfx_low uses VM inv eng 1 on hub 0
[   11.752205] amdgpu 0000:05:00.0: amdgpu: ring gfx_high uses VM inv eng 4 on hub 0
[   11.752207] amdgpu 0000:05:00.0: amdgpu: ring comp_1.0.0 uses VM inv eng 5 on hub 0
[   11.752209] amdgpu 0000:05:00.0: amdgpu: ring comp_1.1.0 uses VM inv eng 6 on hub 0
[   11.752211] amdgpu 0000:05:00.0: amdgpu: ring comp_1.2.0 uses VM inv eng 7 on hub 0
[   11.752213] amdgpu 0000:05:00.0: amdgpu: ring comp_1.3.0 uses VM inv eng 8 on hub 0
[   11.752215] amdgpu 0000:05:00.0: amdgpu: ring comp_1.0.1 uses VM inv eng 9 on hub 0
[   11.752217] amdgpu 0000:05:00.0: amdgpu: ring comp_1.1.1 uses VM inv eng 10 on hub 0
[   11.752219] amdgpu 0000:05:00.0: amdgpu: ring comp_1.2.1 uses VM inv eng 11 on hub 0
[   11.752221] amdgpu 0000:05:00.0: amdgpu: ring comp_1.3.1 uses VM inv eng 12 on hub 0
[   11.752223] amdgpu 0000:05:00.0: amdgpu: ring kiq_0.2.1.0 uses VM inv eng 13 on hub 0
[   11.752225] amdgpu 0000:05:00.0: amdgpu: ring sdma0 uses VM inv eng 0 on hub 8
[   11.752227] amdgpu 0000:05:00.0: amdgpu: ring vcn_dec uses VM inv eng 1 on hub 8
[   11.752229] amdgpu 0000:05:00.0: amdgpu: ring vcn_enc0 uses VM inv eng 4 on hub 8
[   11.752231] amdgpu 0000:05:00.0: amdgpu: ring vcn_enc1 uses VM inv eng 5 on hub 8
[   11.752232] amdgpu 0000:05:00.0: amdgpu: ring jpeg_dec uses VM inv eng 6 on hub 8
[   11.753453] [drm] Initialized amdgpu 3.54.0 20150101 for 0000:05:00.0 on minor 1
[   11.759315] fbcon: amdgpudrmfb (fb0) is primary device
[   11.759325] amdgpu 0000:05:00.0: [drm] fb0: amdgpudrmfb frame buffer device

```
```
inxi -G | grep API
  API: OpenGL v: 4.6 Mesa 23.1.7-arch1.1 renderer: AMD Radeon Graphics
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> inxi -G 
Graphics:
  Device-1: NVIDIA TU117M [GeForce GTX 1650 Ti Mobile] driver: nvidia
    v: 535.104.05
  Device-2: AMD Renoir driver: amdgpu v: kernel
  Device-3: Generic Integrated Camera driver: uvcvideo type: USB
  Display: x11 server: X.Org v: 21.1.8 with: Xwayland v: 23.2.0 driver: X:
    loaded: modesetting,nvidia unloaded: vesa dri: radeonsi gpu: amdgpu
    resolution: 1920x1080~120Hz
  API: OpenGL v: 4.6 Mesa 23.1.7-arch1.1 renderer: AMD Radeon Graphics
    (renoir LLVM 16.0.6 DRM 3.54 6.5.2-arch1-1)

```

I've seen your chipset work very nicely on others machines, so hence the AMD forum might be the place for you get help.

---

### Post by MAFoElffen on 2023-09-12
Hmmm... Sorry, I got distracted looking at this: [https://gitlab.com/corectrl/corectrl](https://gitlab.com/corectrl/corectrl)

Breaking it down so understand what those options do: (From the Linux Kernel drm/amdgpu AMDgpu driver Documentation)
```

**dc (int)**
Disable/Enable Display Core driver for debugging (1 = enable, 0 = disable). The default is -1 (automatic for each asic).

**si_support (int)**
Set SI support driver. This parameter works after set config CONFIG_DRM_AMDGPU_SI. For SI asic, when radeon driver is enabled, set value 0 to use radeon driver, while set value 1 to use amdgpu driver. The default is using radeon driver when it available, otherwise using amdgpu driver.

**cik_support (int)**
Set CIK support driver. This parameter works after set config CONFIG_DRM_AMDGPU_CIK. For CIK asic, when radeon driver is enabled, set value 0 to use radeon driver, while set value 1 to use amdgpu driver. The default is using radeon driver when it available, otherwise using amdgpu driver.

```

---

### Post by habernir on 2023-09-13
thanks a lot everyone i will try it when i get home

---

### Post by #&amp;thj^% on 2023-09-13
I just tried it on Ubuntu 23.04, BTW 23.04 is not supported for AMDGPU-PRO
But this setting gives me some better function:
Again it is a kernel parameter "/etc/default/grub"
```
iommu=pt
```
So it has none of what I showed eariler ie:
```
GRUB_CMDLINE_LINUX_DEFAULT="loglevel=3 lsm=landlock,lockdown,yama,integrity,apparmor,bpf quiet  iommu=pt nvidia_drm.modeset=1"

```
Try both ways and let us know.
You do not want these there: (For Arch Linux only)
```
 [COLOR="#FF0000"]lsm=landlock,lockdown,yama,integrity,apparmor,bpf nvidia_drm.modeset=1[/COLOR]
```
EDIT: Current grubline 23.04
```
cat /etc/default/grub | grep GRUB_CMDLINE_LINUX_DEFAULT
GRUB_CMDLINE_LINUX_DEFAULT="quiet iommu=pt splash"

```
Sourced from:
```
Active apt repos in: /etc/apt/sources.list.d/amdgpu-pro-local.list
    1: deb [trusted=yes] file:/var/opt/amdgpu-pro-local/ ./
  No active apt repos in: /etc/apt/sources.list.d/amdgpu-proprietary.list
  Active apt repos in: /etc/apt/sources.list.d/amdgpu.list
    1: deb https://repo.radeon.com/amdgpu/23.20/amdgpu/ubuntu jammy main

```
```
apt policy amdgpu-pro-core
amdgpu-pro-core:
  Installed: 22.20-1438747~22.04
  Candidate: 22.20-1438747~22.04
  Version table:
 *** 22.20-1438747~22.04 600
        600 https://repo.radeon.com/amdgpu/22.20/ubuntu jammy/proprietary amd64 Packages
        600 https://repo.radeon.com/amdgpu/22.20/ubuntu jammy/proprietary i386 Packages
        100 /var/lib/dpkg/status

```

---

