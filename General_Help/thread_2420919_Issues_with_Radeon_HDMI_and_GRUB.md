---
title: "Issues with Radeon HDMI and GRUB"
date: 2019-06-13
forum: General Help
---

### Post by lemmy18 on 2019-06-13
I've Googled. I typed this description then clicked "check if already posted" with all the boxes unchecked. Still not getting it to work.

Did a PROPER shutdown. Everything was working before shutdown. Physically moved desktop to other side of same room. Did NOT drop machine or pass any EM field. Cannot think of any reason for corruption.

After reboot, using same cables, same external hardware, same everything, desktop would not send signal to LG TV as it did before. Did not display POST, BIOS, only the NO SIGNAL bouncy-box. Had to connect to 19" HNC TV/Monitor using same HDMI cable to see anything, and even then I had to hit the computer's reset button to get any signal to that monitor.
With HNC connected, Applications>System  Tools>Preferences>Settings for Devices>Displays shows Unknown  Display, resolution stuck at 1024x768 4:3 even though it used to identify the HNC and supported 720p on the HNC. Also used to identify the LG and supported 1080p.

Playing a video file with VLC gives no sound through HDMI but  VLC>Audio>Audio Device shows Cedar HDMI Audio ... as the selected  option. Selecting the built-in audio option doesn't produce any sound  either, not that I have anything connected to the mini-jacks anyway.
Only available option in Applications>System Tools>Preferences>Settings for audio is the onboard audio. The HDMI through my expansion video card is no longer an option.

Did a restart to use GRUB recovery mode. GRUB menu no longer shows by default. I have Win7 and Ubuntu 18.04 on separate drives and could select which OS I wanted to use from GRUB.
Did the SHIFT trick to access GRUB... Win7 no longer appears as an option. Selected latest Ubuntu kernel RECOVERY MODE, selected fsck, got the following echo:
/lib/recovery-mode/recovery-menu: line 80: /etc/default/reS: No such file or directory
flck from util-linux 2.31.1
/dev/sda5 is mounted
e2fsck: Cannot continue, aborting.

Proceeded to boot normal.
Used Terminal, sudo gedit /etc/default/grub and YES I also did sudo update-grub.
current config is as follows, STILL won't show me Win7 or even show up at all unless I hold the Shift key:
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash"
GRUB_CMDLINE_LINUX=""

Applications>System Tools>Preferences>Settings Details-About says
18.04.2 LTS (I'll add that the kernel images in GRUB are 4.15.0-51 and 4.15.0-50)
AMD PhenomII x4 955 processor (I'll add that the mobo is Asus M4A89TD)
Graphics: llvmpipe (LLVM 6.0, 128 bits) but I have ATI Radeon HD 5450 graphics card installed
GNOME 3.28.2 (btw, I have the system set to bypass the gdm3 login and directly open the desktop)
Software is up to date

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 400, current 1024 x 768, maximum 1024 x 768
default connected primary 1024x768+0+0 0mm x 0mm
   1024x768       0.00* 
   800x600        0.00  
   640x480        0.00  
   720x400        0.00

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Downloaded proprietary Radeon drivers then attempted to apt-get install through Terminal (even though they were for 14.04). This created dependency errors that cannot be resolved, so had to remove and autoremove. AMDGPU doesn't support this ancient card but I never had any need for it so that's likely not the answer either.

Can anyone help out a dinosaur?

---

### Post by lemmy18 on 2019-06-13
More Terminal Outputs

inxi -Fxz | grep -i display
           Display Server: x11 (X.Org 1.19.6 )

lspci | grep -i vga
05:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series]

sudo lshw     (redacted)

*-core
       description: Motherboard
       product: M4A89TD PRO
       vendor: ASUSTeK Computer INC.

*-firmware
          description: BIOS
          vendor: American Megatrends Inc.
capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     
*-cpu
          description: CPU
          product: AMD Phenom(tm) II X4 955 Processor
capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt hw_pstate vmmcall npt lbrv svm_lock nrip_save cpufreq
          configuration: cores=4 enabledcores=4
        
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Cedar [Radeon HD 5000/6000/7350/8350 Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list
                configuration: latency=0
                resources: memory:d0000000-dfffffff memory:fe9e0000-fe9fffff ioport:e000(size=256) memory:c0000-dffff

           *-multimedia
                description: Audio device
                product: Cedar HDMI Audio [Radeon HD 5400/6300/7300 Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:05:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:37 memory:fe9bc000-fe9bffff

---

### Post by lemmy18 on 2019-06-13
New GRUB config at least shows GRUB without having to play timing games with the shift-key.

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="video=0x122 gfxpayload=true"
GRUB_CMDLINE_LINUX="video=0x122 gfxpayload=true"
GRUB_GFXMODE=800x600x32
GRUB_GFXPAYLOAD=800x600x32
GRUB_GFXPAYLOAD_LINUX=800x600x32

Still can't get monitor to show 1360x768 resolution even though vbeinfo says this is the preferred mode (which is odd bc out of the 53 modes supported during boot, that mode isn't one of them).

Honestly ppl, I'm trying, but I feel like a sighted man in a dark room here.

---

### Post by lemmy18 on 2019-06-15
marking solved even though it isn't. downtime is lost money for me. i'm migrating. thanks for all the help.

---

