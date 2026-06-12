---
title: "Having issues with AMD RX 570 cards in mining rig"
date: 2023-03-04
forum: General Help
---

### Post by radiah on 2023-03-04
Folks, I could really use some advice here!  I'm not that good in Linux/Ubuntu, but I have a mining rig with mixed cards (NVidia and AMD) and prior to Ubuntu updates this week, they all worked well together.

Suddenly, the AMD cards will no longer initialize, however, the rig runs fine with the NVidia cards.  In the GRUB entries, I see no mention of NOMODESET, however I get the dreaded "VGACON disables amdgpu kernel modesetting" warning in the boot process, and then things lock up.

There are some peculiar entries for AMD cards, like: amdgpu.vm_fragment_size=9 amdgpu.ppfeaturemask=0xffffffff nogpumanager

The core is 5.0.0-31 and the version is 18.04 LTS.  The mining software in PiMP, which recently went belly up, yet continues to function well for my purposes up until this current issue.

Can someone please walk me through how to fix this?  I've tried various solutions in the forums that I've found to deal with the VGACON disables amdgpu kernel modesetting issue, however nothing has worked.

Grateful for any help I can get!  Thanks!
radiah

---

### Post by MAFoElffen on 2023-03-04
The only thing I see recently, is people using "amdgpu.dc=0" as a boot parameter to remedy that error...

I would post the results of 
```

lshw -C video

```
To check if the AMD cards have drivers assigned to all the cards...

---

### Post by radiah on 2023-03-04
Thanks for the response MAFoElffen!
Here is the output from lshw -C video as you requested.
All the AMD devices are UNCLAIMED, as is the on-board Intel video, which is disabled
I'd appreciate any further advice you may have.
Thanks!

```
 *-display                 
       description: VGA compatible controller
       product: TU116 [GeForce GTX 1660]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:137 memory:f3000000-f3ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:e000(size=128) memory:f4000000-f407ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: HD Graphics 510
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: iomemory:2f0-2ef iomemory:2e0-2df memory:2ffe000000-2ffeffffff memory:2e90000000-2e9fffffff ioport:f000(size=64) memory:c0000-dffff
  *-display
       description: 3D controller
       product: GP106 [P106-090]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: iomemory:2e0-2df iomemory:2e0-2df irq:138 memory:eb000000-ebffffff memory:2ee0000000-2eefffffff memory:2ef0000000-2ef1ffffff
  *-display
       description: VGA compatible controller
       product: GP106 [GeForce GTX 1060 6GB]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: iomemory:2e0-2df iomemory:2e0-2df irq:139 memory:e9000000-e9ffffff memory:2ec0000000-2ecfffffff memory:2ed0000000-2ed1ffffff ioport:8000(size=128) memory:ea000000-ea07ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: Ellesmere [Radeon RX 470/480/570/570X/580/580X/590]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:07:00.0
       version: ef
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: iomemory:2f0-2ef iomemory:2f0-2ef memory:2f00000000-2f0fffffff memory:2f10000000-2f101fffff ioport:7000(size=256) memory:ec000000-ec03ffff memory:ec040000-ec05ffff
  *-display
       description: VGA compatible controller
       product: TU116 [GeForce GTX 1660]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: iomemory:2e0-2df iomemory:2e0-2df irq:140 memory:e7000000-e7ffffff memory:2ea0000000-2eafffffff memory:2eb0000000-2eb1ffffff ioport:6000(size=128) memory:e8000000-e807ffff
  *-display
       description: 3D controller
       product: GP106 [P106-100]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: iomemory:2f0-2ef iomemory:2f0-2ef irq:141 memory:f6000000-f6ffffff memory:2fa0000000-2fafffffff memory:2fb0000000-2fb1ffffff
  *-display
       description: VGA compatible controller
       product: TU116 [GeForce GTX 1660]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: iomemory:2f0-2ef iomemory:2f0-2ef irq:142 memory:f1000000-f1ffffff memory:2f60000000-2f6fffffff memory:2f70000000-2f71ffffff ioport:d000(size=128) memory:f2000000-f207ffff
  *-display
       description: VGA compatible controller
       product: TU116 [GeForce GTX 1660]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: iomemory:2f0-2ef iomemory:2f0-2ef irq:143 memory:ef000000-efffffff memory:2f40000000-2f4fffffff memory:2f50000000-2f51ffffff ioport:c000(size=128) memory:f0000000-f007ffff
  *-display
       description: VGA compatible controller
       product: TU116 [GeForce GTX 1660]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: iomemory:2f0-2ef iomemory:2f0-2ef irq:144 memory:ed000000-edffffff memory:2f20000000-2f2fffffff memory:2f30000000-2f31ffffff ioport:b000(size=128) memory:ee000000-ee07ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: Ellesmere [Radeon RX 470/480/570/570X/580/580X/590]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:0f:00.0
       version: ef
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: iomemory:2f0-2ef iomemory:2f0-2ef memory:2fe0000000-2fefffffff memory:2ff0000000-2ff01fffff ioport:a000(size=256) memory:f7100000-f713ffff memory:f7140000-f715ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: Ellesmere [Radeon RX 470/480/570/570X/580/580X/590]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:10:00.0
       version: ef
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: iomemory:2f0-2ef iomemory:2f0-2ef memory:2fc0000000-2fcfffffff memory:2fd0000000-2fd01fffff ioport:9000(size=256) memory:f7000000-f703ffff memory:f7040000-f705ffff
  *-display
       description: 3D controller
       product: GP106 [P106-100]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:11:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: iomemory:2f0-2ef iomemory:2f0-2ef irq:145 memory:f5000000-f5ffffff memory:2f80000000-2f8fffffff memory:2f90000000-2f91ffffff
```

---

### Post by MAFoElffen on 2023-03-05
Please remember to wrap raw output and commands with CODE Tags like this: [noparse]```
Put raw output here...
```[/noparse]

Looking at it now... Hmmm. 

Could you please post the content of this?
```

grep . /etc/modprobe.d/amdgpu.conf
grep . /proc/cmdline

```
Was looking at "amdgpu.ppfeaturemask=0xffffffff" What I see with that parameter is not really an error, but rather How AMD unlocks access to adjust their GPU clocks and voltages in sysfs.

---

### Post by radiah on 2023-03-05
Sorry for the CODE issue.  Was just so happy that someone took and interest, and I forgot.

Well, this is interesting....

```
 grep: /etc/modprobe/amdgpu.conf: No such file or directory 
```

and

```
 grep - /proc/cmdline:  BOOT_IMAGE=/boot/vmlinuz-5.0.0-31-generic root=UUID=a0df558f-82fd-4001-9417-27596e382377 ro single nomodeset dis_ucode_ldr quiet iommu=soft net.ifnames=0 biosdevname=0 usbcore.autosuspend=-1 amdgpu.vm_fragment_size=9 amdgpu.ppfeaturemask=0xffffffff nogpumanager 
```

I don't like the looks of the last one. What do you think?
Thanks!

---

### Post by MAFoElffen on 2023-03-05
+1 -- The last output is troubling. Remove 'nomodeset' from the boot line in /etc/default/grub... That is what is causing your "VGACON disables amdgpu kernel modesetting" issue... This boot parameter is also probably stopping amdgpu from trying to load.

'dis_code_ldr' ... That was a boot parameter that disables kernel microcode updates for kernels running 5.0.x. Well, Ubuntu 18 LTS, up until releases 20.04 & 22.04. In 20.04, they have 'fwupdate' as default and can then update the microcode firmware. For BIONIC (18.04) you can install the package (optional). If you did that, 
```

sudo apt install fwupdate
sudo fwupdate -update

```
Then you would not need that.

Along the line of the first, having no output...I think that needs more investigation. You are running a multi-GPU rig and utilizing their 'GPU acceleration features'. It would make since that you are seeing "amdgpu.ppfeaturemask=0xffffffff" in the logs, as that would be saying that something is unlocking the full addressable space of the GPU card to Overclock the GPU... That boot parameter, when set is usually via either the kernel boot line in passed via Grub. or in the override file at "/etc/modprobe.d/amdgpu.conf"...

Sort of looking something like this sample output:
```

# cat /etc/modprobe.d/amdgpu.conf 
blacklist radeon
blacklist fglrx
options amdgpu si_support=1 cik_support=1 vm_fragment_size=9 audio=0 dc=0 aspm=0 ppfeaturemask=0xffffffff

```
But your doesn't have that parameter set in /etc/default/grub, and it says /etc/modprobe.d/amdgpu.conf doesn't exist... So where is it getting that parameter? That is not a default. It has to get passed that from "somewhere"??? Oh

Oh... There was a typo... It should be 
```

grep . /etc/modprobe.d/amdgpu.conf

```

---

### Post by radiah on 2023-03-05
I've gone through several times now, and I do not know from where /proc/cmdline is getting these values!  They do not exist in the default grub file!  In this particular mining software we have /root/gpu-config.json .  This allows me to enter any tweaking values for the GPU, but this has none of those commands either!.  I will have to check through and find from where these values are being pulled.

---

### Post by MAFoElffen on 2023-03-05
+1... Agreed. They are coming from "somewhere", but not from the "usual suspects"... LOL I am very curious where they are getting injected from...

EDIT: 18.04 is EOS in a matter of weeks now. Do you have a plan to upgrade releases yet? There are newer version of amdgu in the kernels of 20.04 and 22.04.

---

### Post by radiah on 2023-03-05
This is what the GRUB shows:

```

  # If you change this file, run 'update-grub' afterwards to update
 2 # /boot/grub/grub.cfg.
 3 # For full documentation of the options in this file, see:
 4 #   info -f grub -n 'Simple configuration'
 5
 6 GRUB_DEFAULT=0
 7 # GRUB_HIDDEN_TIMEOUT=0
 8 # GRUB_HIDDEN_TIMEOUT_QUIET=true
 9 GRUB_TIMEOUT=2
10 GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
11 GRUB_CMDLINE_LINUX_DEFAULT=""
12 GRUB_CMDLINE_LINUX="quiet iommu=soft net.ifnames=0 biosdevname=0 usbcore.autosuspend=-1 amdgpu.dc=0 amdgpu.vm_fragment_size=9 amdgpu.ppfeaturemask=0xffffffff nogpumanager"
13
14 GRUB_THEME=/boot/grub/themes/pimp/pimptheme.txt
15
16 # Uncomment to enable BadRAM filtering, modify to suit your needs
17 # This works with Linux (no patch required) and with any kernel that obtains
18 # the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
19 #GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
20
21 # Uncomment to disable graphical terminal (grub-pc only)
22 #GRUB_TERMINAL=console
23
24 # The resolution used on graphical terminal
25 # note that you can use only modes which your graphic card supports via VBE
26 # you can see them in real GRUB with the command `vbeinfo'
27 #GRUB_GFXMODE=640x480
28
29 # Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
30 #GRUB_DISABLE_LINUX_UUID=true
31
32 # Uncomment to disable generation of recovery mode menu entries
33 #GRUB_DISABLE_RECOVERY="true"
34
35 # Uncomment to get a beep at grub start
36 #GRUB_INIT_TUNE="480 440 1"
37 

```

---

### Post by #&amp;thj^% on 2023-03-05
I've not seen this work in grub for a very long time now:
```
nogpumanager
```
try without, unless MAFoElffen told you to add it.

---

### Post by radiah on 2023-03-05
I am going to attempt a command-line upgrade on the thing.  This should be fun! :lolflag:

Well, that died like a fart in a thunderstorm.  Guess I'll have to do it from a uSB drive.

Thanks, guys for the help.  I will continue to try to fix this, so I may be posting again in due course.

---

### Post by MAFoElffen on 2023-03-05
'nogpumanager' was a workaround from 14.04 LTS that stopped custom xorg.conf files from getting overwritten/overridden at boot time (RE: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1310489](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1310489)).... I have not seen it since then. I thought the code for that has been changed since then for that. Yes. It was Init based and got changed with systemd to gpu-manager.service

Do you have a custom /etc/X11/xorg.conf file? If so, save a copy of that first, just for the 'might-happens' kinds of things. 

My service for 22.04 is
```

mafoelffen@Mikes-ThinkPad-T520:~$ grep . /lib/systemd/system/gpu-manager.service
[Unit]
Description=Detect the available GPUs and deal with any system changes
Before=display-manager.service/etc/modprobe.d/r
Before=oem-config.service
[Service]
Type=oneshot
ExecStart=/usr/bin/gpu-manager --log /var/log/gpu-manager.log
StandardOutput=null
StandardError=null
[Install]
WantedBy=display-manager.service
WantedBy=oem-config.service

```

Not sure what it was for 18.04... Please look first, then try without 'nogpumanager'. 

The others, I would expect in a GPU forward and tweaked machine.

Still not seeing where 'nomodeset' is getting injected from...

Maybe post 
```

ls /etc/modprobe.d/*.conf 
grep -r 'nomodeset\|modeset=' /etc/modprobe.d/*.conf

```
For ideas of any possible overrides being applied there...

---

### Post by radiah on 2023-03-06
Hi,  here is my /etc/X11/xorg.conf file:

```

  1 # nvidia-xconfig: X configuration file generated by nvidia-xconfig
  2 # nvidia-xconfig:  version 470.161.03
  3
  4
  5 Section "ServerLayout"
  6     Identifier     "Layout0"
  7     Screen      0  "Screen0"
  8     Screen      1  "Screen1" RightOf "Screen0"
  9     Screen      2  "Screen2" RightOf "Screen1"
 10     Screen      3  "Screen3" RightOf "Screen2"
 11     Screen      4  "Screen4" RightOf "Screen3"
 12     Screen      5  "Screen5" RightOf "Screen4"
 13     Screen      6  "Screen6" RightOf "Screen5"
 14     Screen      7  "Screen7" RightOf "Screen6"
 15     Screen      8  "Screen8" RightOf "Screen7"
 16     InputDevice    "Keyboard0" "CoreKeyboard"
 17     InputDevice    "Mouse0" "CorePointer"
 18 EndSection
 19
 20 Section "Files"
 21 EndSection
 22
 23 Section "InputDevice"
 24
 25     # generated from default
 26     Identifier     "Mouse0"
 27     Driver         "mouse"
 28     Option         "Protocol" "auto"
 29     Option         "Device" "/dev/psaux"
 30     Option         "Emulate3Buttons" "no"
 31     Option         "ZAxisMapping" "4 5"
 32 EndSection
 33
 34 Section "InputDevice"
 35
 36     # generated from default
 37     Identifier     "Keyboard0"
 38     Driver         "kbd"
 39 EndSection
 40
 41 Section "Monitor"
 42     Identifier     "Monitor0"
 43     VendorName     "Unknown"
 44     ModelName      "Unknown"
 45     Option         "DPMS"
 46 EndSection
 47
 48 Section "Monitor"
 49     Identifier     "Monitor1"
 50     VendorName     "Unknown"
 51     ModelName      "Unknown"
 52     Option         "DPMS"
 53 EndSection
 54
 55 Section "Monitor"
 56     Identifier     "Monitor2"
 57     VendorName     "Unknown"
 58     ModelName      "Unknown"
 59     Option         "DPMS"
 60 EndSection
 61
 62 Section "Monitor"
 63     Identifier     "Monitor3"
 64     VendorName     "Unknown"
 65     ModelName      "Unknown"
 66     Option         "DPMS"
 67 EndSection
 68
 69 Section "Monitor"
 70     Identifier     "Monitor4"
 71     VendorName     "Unknown"
72     ModelName      "Unknown"
 73     Option         "DPMS"
 74 EndSection
 75
 76 Section "Monitor"
 77     Identifier     "Monitor5"
 78     VendorName     "Unknown"
 79     ModelName      "Unknown"
 80     Option         "DPMS"
 81 EndSection
 82
 83 Section "Monitor"
 84     Identifier     "Monitor6"
 85     VendorName     "Unknown"
 86     ModelName      "Unknown"
 87     Option         "DPMS"
 88 EndSection
 89
 90 Section "Monitor"
 91     Identifier     "Monitor7"
 92     VendorName     "Unknown"
 93     ModelName      "Unknown"
 94     Option         "DPMS"
 95 EndSection
 96
 97 Section "Monitor"
 98     Identifier     "Monitor8"
 99     VendorName     "Unknown"
100     ModelName      "Unknown"
101     Option         "DPMS"
102 EndSection
103
104 Section "Device"
105     Identifier     "Device0"
106     Driver         "nvidia"
107     VendorName     "NVIDIA Corporation"
108     BoardName      "NVIDIA GeForce GTX 1660"
109     BusID          "PCI:1:0:0"
110 EndSection
111
112 Section "Device"
113     Identifier     "Device1"
114     Driver         "nvidia"
115     VendorName     "NVIDIA Corporation"
116     BoardName      "NVIDIA P106-090"
117     BusID          "PCI:4:0:0"
118 EndSection
119
120 Section "Device"
121     Identifier     "Device2"
122     Driver         "nvidia"
123     VendorName     "NVIDIA Corporation"
124     BoardName      "NVIDIA GeForce GTX 1060 6GB"
125     BusID          "PCI:6:0:0"
126 EndSection
127
128 Section "Device"
129     Identifier     "Device3"
130     Driver         "nvidia"
131     VendorName     "NVIDIA Corporation"
132     BoardName      "NVIDIA GeForce GTX 1660"
133     BusID          "PCI:9:0:0"
134 EndSection
135
136 Section "Device"
137     Identifier     "Device4"
138     Driver         "nvidia"
139     VendorName     "NVIDIA Corporation"
140     BoardName      "NVIDIA P106-100"
141     BusID          "PCI:11:0:0"
142 EndSection
143
144 Section "Device"
145     Identifier     "Device5"
146     Driver         "nvidia"
147     VendorName     "NVIDIA Corporation"
148     BoardName      "NVIDIA GeForce GTX 1660"
149     BusID          "PCI:12:0:0"
150 EndSection
151
152 Section "Device"
153     Identifier     "Device6"
154     Driver         "nvidia"
155     VendorName     "NVIDIA Corporation"
156     BoardName      "NVIDIA GeForce GTX 1660"
157     BusID          "PCI:13:0:0"
158 EndSection
159
160 Section "Device"
161     Identifier     "Device7"
162     Driver         "nvidia"
163     VendorName     "NVIDIA Corporation"
164     BoardName      "NVIDIA GeForce GTX 1660"
165     BusID          "PCI:14:0:0"
166 EndSection
167
168 Section "Device"
169     Identifier     "Device8"
170     Driver         "nvidia"
171     VendorName     "NVIDIA Corporation"
172     BoardName      "NVIDIA P106-100"
173     BusID          "PCI:17:0:0"
174 EndSection
175
176 Section "Screen"
177     Identifier     "Screen0"
178     Device         "Device0"
179     Monitor        "Monitor0"
180     DefaultDepth    24
181     Option         "AllowEmptyInitialConfiguration" "True"
182     Option         "Coolbits" "28"
183     SubSection     "Display"
184         Depth       24
185     EndSubSection
186 EndSection
187
188 Section "Screen"
189     Identifier     "Screen1"
190     Device         "Device1"
191     Monitor        "Monitor1"
192     DefaultDepth    24
193     Option         "AllowEmptyInitialConfiguration" "True"
194     Option         "Coolbits" "28"
195     SubSection     "Display"
196         Depth       24
197     EndSubSection
198 EndSection
199
200 Section "Screen"
201     Identifier     "Screen2"
202     Device         "Device2"
203     Monitor        "Monitor2"
204     DefaultDepth    24
205     Option         "AllowEmptyInitialConfiguration" "True"
206     Option         "Coolbits" "28"
207     SubSection     "Display"
208         Depth       24
209     EndSubSection
210 EndSection
211
212 Section "Screen"
213     Identifier     "Screen3"
214     Device         "Device3"
215     Monitor        "Monitor3"
216     DefaultDepth    24
217     Option         "AllowEmptyInitialConfiguration" "True"
218     Option         "Coolbits" "28"
219     SubSection     "Display"
220         Depth       24
221     EndSubSection
222 EndSection
223
224 Section "Screen"
225     Identifier     "Screen4"
226     Device         "Device4"
227     Monitor        "Monitor4"
228     DefaultDepth    24
229     Option         "AllowEmptyInitialConfiguration" "True"
230     Option         "Coolbits" "28"
231     SubSection     "Display"
232         Depth       24
233     EndSubSection
234 EndSection
235
236 Section "Screen"
237     Identifier     "Screen5"
238     Device         "Device5"
239     Monitor        "Monitor5"
240     DefaultDepth    24
241     Option         "AllowEmptyInitialConfiguration" "True"
242     Option         "Coolbits" "28"
243     SubSection     "Display"
244         Depth       24
245     EndSubSection
246 EndSection
247
248 Section "Screen"
249     Identifier     "Screen6"
250     Device         "Device6"
251     Monitor        "Monitor6"
252     DefaultDepth    24
253     Option         "AllowEmptyInitialConfiguration" "True"
254     Option         "Coolbits" "28"
255     SubSection     "Display"
256         Depth       24
257     EndSubSection
258 EndSection
259
260 Section "Screen"
261     Identifier     "Screen7"
262     Device         "Device7"
263     Monitor        "Monitor7"
264     DefaultDepth    24
265     Option         "AllowEmptyInitialConfiguration" "True"
266     Option         "Coolbits" "28"
267     SubSection     "Display"
268         Depth       24
269     EndSubSection
270 EndSection
271
272 Section "Screen"
273     Identifier     "Screen8"
274     Device         "Device8"
275     Monitor        "Monitor8"
276     DefaultDepth    24
277     Option         "AllowEmptyInitialConfiguration" "True"
278     Option         "Coolbits" "28"
279     SubSection     "Display"
280         Depth       24
281     EndSubSection
282 EndSection
283

```

Output from ls /etc/modprobe.d/*.conf  :

```

/etc/modprobe.d/alsa-base.conf           /etc/modprobe.d/blacklist-framebuffer.conf  /etc/modprobe.d/blacklist-rare-network.conf     /etc/modprobe.d/libpisock9.conf
/etc/modprobe.d/blacklist-ath_pci.conf   /etc/modprobe.d/blacklist-modem.conf        /etc/modprobe.d/dkms.conf                       /etc/modprobe.d/nvidia-installer-disable-nouveau.conf
/etc/modprobe.d/blacklist.conf           /etc/modprobe.d/blacklist-oss.conf          /etc/modprobe.d/intel-microcode-blacklist.conf
/etc/modprobe.d/blacklist-firewire.conf  /etc/modprobe.d/blacklist-radeon.conf       /etc/modprobe.d/iwlwifi.conf

```

Output from grep -r 'nomodeset\|modeset=' /etc/modprobe.d/*.conf :

```

/etc/modprobe.d/nvidia-installer-disable-nouveau.conf:options nouveau modeset=0

```

Does this help?

---

### Post by MAFoElffen on 2023-03-06
> **radiah said:**
> 
Output from grep -r 'nomodeset\|modeset=' /etc/modprobe.d/*.conf :

```

/etc/modprobe.d/nvidia-installer-disable-[COLOR=#ff0000]nouveau.conf:options nouveau modeset=0[/COLOR]

```

Does this help?
Edit nouveau.conf and remove "options nouveau modeset=0" then do
```

sudo update-initramfs -c -k all

```
Then reboot and recheck /proc/cmdline

Is there anything in radeon.conf of interest?

Looking at the xorg.conf file now...

EDIT: Your xorg.conf file is incomplete / wrong. It only has 9 GPU's  (0-8) in it and they are all listed as NVidia. It does not include any of the 3 AMD GPU's...

---

### Post by #&amp;thj^% on 2023-03-06
It's just me but I'd for sure copy xorg.conf to "/etc/X11/xorg.conf.bk"
wait till you lay eye's on it>>>quite a set-up

---

### Post by MAFoElffen on 2023-03-06
+1... But the file is incomplete (see EDIT in my last post). It doesn't include any of your 3 AMD GPU's.

Let's dig a little deeper...
```

sudo dmesg | grep -i 'amdgpu'

```

---

### Post by radiah on 2023-03-06
Guys, none of this changed /proc/cmdline.  Nothing has changed.
I'm about ready to throw the whole thing out.
Thanks for all your help and advice, but I think this is a lost cause.

---

### Post by radiah on 2023-03-06
```

[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-5.0.0-31-generic root=UUID=a0df558f-82fd-4001-9417-27596e382377 ro single nomodeset dis_ucode_ldr quiet iommu=soft net.ifnames=0 biosdevname=0 usbcore.autosuspend=-1 amdgpu.dc=0 amdgpu.vm_fragment_size=9 amdgpu.ppfeaturemask=0xffffffff
[    0.055920] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.0.0-31-generic root=UUID=a0df558f-82fd-4001-9417-27596e382377 ro single nomodeset dis_ucode_ldr quiet iommu=soft net.ifnames=0 biosdevname=0 usbcore.autosuspend=-1 amdgpu.dc=0 amdgpu.vm_fragment_size=9 amdgpu.ppfeaturemask=0xffffffff
[    4.470851] [drm:amdgpu_init [amdgpu]] *ERROR* VGACON disables amdgpu kernel modesetting.
[    4.991661] [drm:amdgpu_init [amdgpu]] *ERROR* VGACON disables amdgpu kernel modesetting.
[    5.037729] [drm:amdgpu_init [amdgpu]] *ERROR* VGACON disables amdgpu kernel modesetting.

```

This is the output of sudo dmesg | grep -i 'amdgpu'

---

### Post by MAFoElffen on 2023-03-06
I'm trying to reconcile your xorg.conf file with your lshw results...

You are good for Device's 
```

Device0 BusID "PCI:1:0:0"
Device1 BusID "PCI:4:0:0"
Device2 BusID "PCI:6:0:0"
Device3 BusID "PCI:9:0:0"
Device4 BusID "PCI:11:0:0"

```
The following devices have the wrong busid's:
```

Device5 BusID "PCI:12:0:0" # Driver nvidia
Device6 BusID "PCI:13:0:0" # Driver nvidia
Device7 BusID "PCI:14:0:0" # Driver nvidia
Device8 BusID "PCI:17:0:0" # Driver nvidia

```
The following are not there:
```

       product: Ellesmere [Radeon RX 470/480/570/570X/580/580X/590]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       bus info: pci@0000:07:00.0

      product: GP106 [P106-100]
       vendor: NVIDIA Corporation
       bus info: pci@0000:0b:00.0

       product: TU116 [GeForce GTX 1660]
       vendor: NVIDIA Corporation
       bus info: pci@0000:0c:00.0

       product: TU116 [GeForce GTX 1660]
       vendor: NVIDIA Corporation
       bus info: pci@0000:0d:00.0

       product: TU116 [GeForce GTX 1660]
       vendor: NVIDIA Corporation
       bus info: pci@0000:0e:00.0

       product: Ellesmere [Radeon RX 470/480/570/570X/580/580X/590]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       bus info: pci@0000:0f:00.0

       product: Ellesmere [Radeon RX 470/480/570/570X/580/580X/590]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       bus info: pci@0000:10:00.0

```
Though, if you check your xorg.0.log, they might be getting coverage for amdgpu from some override (named_file).conf file from /etc/X11/xorg.conf.d or /usr/share/X11/xorg.conf.d

---

### Post by radiah on 2023-03-06
Physically, they all in place and functioning with the exception of the AMD units.

---

### Post by MAFoElffen on 2023-03-06
What does the dmesg search above, your /var/log/Xorg.0.log, and /var/log/gpu-manager.log files say?

---

### Post by radiah on 2023-03-06
Had to use the Ubuntu paste bins since the one log was way too long.
See [https://paste.ubuntu.com/p/sy24KHQz6G/](https://paste.ubuntu.com/p/sy24KHQz6G/)  and [https://paste.ubuntu.com/p/TtPBkWyQ29/](https://paste.ubuntu.com/p/TtPBkWyQ29/)
this has the output of both, with Xorg.0.log being the extremely long one.
Cheers!
Radiah

---

### Post by MAFoElffen on 2023-03-07
Thank you. Reviewing those two... And bringing this up after I got off work, saw the output of the dmesg search. That doesn't make sense now at all. Where is nomodeset coming from?

---

### Post by MAFoElffen on 2023-03-07
The Xorg.0.log doesn't even mention AMD... Not once. But the gpumanager.log did...
```

  4 can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
 15 Is amdgpu loaded? no
 16 Is amdgpu blacklisted? no
 17 Is amdgpu versioned? yes
 18 Is amdgpu pro stack? yes
153 Has amd? yes

```
If it were me...

1.) I would install this driver: [https://repo.radeon.com/amdgpu-install/22.40.3/ubuntu/focal/amdgpu-install_5.4.50403-1_all.deb](https://repo.radeon.com/amdgpu-install/22.40.3/ubuntu/focal/amdgpu-install_5.4.50403-1_all.deb)

2.) Then I would add 3 device  sections in your xorg.conf file, with the 3 AMD card BusID's, with a format similar to this:
```

Section "Device"
    Identifier             "Screen0"
    Driver                 "amdgpu"
    VendorName             "Advanced Micro Devices, Inc. [AMD/ATI]"
    BusID                  "PCI:3:0:0"
EndSection

```
Then lets look at those two log files again after that...

---

### Post by radiah on 2023-03-07
Oh boy, did that cause a mess, lol.  Trying to install radeon drivers produced this:

```

Hit:1 http://us.archive.ubuntu.com/ubuntu bionic InRelease
Err:1 http://us.archive.ubuntu.com/ubuntu bionic InRelease                                                                                                                                          
  Splitting up /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_bionic_InRelease into data and signature failed
Get:2 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7  kB]                                                                                                                       
Err:2 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease                                                                                                                                  
  Error writing to output file - write (28: No space left on device) [IP: 91.189.91.39 80]
Get:3 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease  [83.3 kB]                                                                                                                     
Err:3 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease                                                                                                                                
  Error writing to output file - write (28: No space left on device) [IP: 91.189.91.38 80]
Get:4 https://repo.radeon.com/amdgpu/5.4.3/ubuntu focal InRelease [5,457  B]                                                                                                                    
Err:4 https://repo.radeon.com/amdgpu/5.4.3/ubuntu focal InRelease                                                                                                  
  Error writing to output file - write (28: No space left on device) [IP: 13.82.220.49 443]
Get:5 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7  kB]                                                                     
Err:5 http://security.ubuntu.com/ubuntu bionic-security InRelease                                                  
  Error writing to output file - write (28: No space left on device) [IP: 185.125.190.36 80]
Get:6 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu bionic  InRelease [20.8 kB]                                                     
Err:6 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu bionic  InRelease                                                               
  Error writing to output file - write (28: No space left on device) [IP: 185.125.190.52 80]
Hit:7 http://archive.canonical.com/ubuntu bionic InRelease                                                                                   
Err:7 http://archive.canonical.com/ubuntu bionic InRelease                                                                
  Splitting up /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_bionic_InRelease into data and signature failed
Get:8 https://repo.radeon.com/rocm/apt/5.4.3 focal InRelease [2,603 B]                                                    
Err:8 https://repo.radeon.com/rocm/apt/5.4.3 focal InRelease                                   
  Error writing to output file - write (28: No space left on device) [IP: 13.82.220.49 443]
Get:9 https://esm.ubuntu.com/apps/ubuntu bionic-apps-security InRelease [7,636 B]
Err:9 https://esm.ubuntu.com/apps/ubuntu bionic-apps-security InRelease
  Error writing to output file - write (28: No space left on device) [IP: 185.125.190.24 443]
Get:10 https://esm.ubuntu.com/apps/ubuntu bionic-apps-updates InRelease [7,524 B]
Err:10 https://esm.ubuntu.com/apps/ubuntu bionic-apps-updates InRelease
  Error writing to output file - write (28: No space left on device) [IP: 185.125.190.24 443]
Get:11 https://esm.ubuntu.com/infra/ubuntu bionic-infra-security InRelease [7,512 B]
Err:11 https://esm.ubuntu.com/infra/ubuntu bionic-infra-security InRelease
  Error writing to output file - write (28: No space left on device) [IP: 185.125.190.24 443]
Get:12 https://esm.ubuntu.com/infra/ubuntu bionic-infra-updates InRelease [7,511 B]
Err:12 https://esm.ubuntu.com/infra/ubuntu bionic-infra-updates InRelease
  Error writing to output file - write (28: No space left on device) [IP: 185.125.190.24 443]
Reading package lists... Done   
W: An error occurred during the signature verification. The repository  is not updated and the previous index files will be used. GPG error:  http://us.archive.ubuntu.com/ubuntu bionic InRelease: Splitting up  /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_bionic_InRelease  into data and signature failed
W: An error occurred during the signature verification. The repository  is not updated and the previous index files will be used. GPG error:  http://archive.canonical.com/ubuntu bionic InRelease: Splitting up  /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_bionic_InRelease  into data and signature failed
W: Failed to fetch  http://us.archive.ubuntu.com/ubuntu/dists/bionic/InRelease  Splitting up  /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_bionic_InRelease  into data and signature failed
W: Failed to fetch  http://us.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease   Error writing to output file - write (28: No space left on device) [IP:  91.189.91.39 80]
W: Failed to fetch  http://us.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease   Error writing to output file - write (28: No space left on device) [IP:  91.189.91.38 80]
W: Failed to fetch  http://archive.canonical.com/ubuntu/dists/bionic/InRelease  Splitting up  /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_bionic_InRelease  into data and signature failed
W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease  Error  writing to output file - write (28: No space left on device) [IP:  185.125.190.36 80]
W: Failed to fetch  https://repo.radeon.com/amdgpu/5.4.3/ubuntu/dists/focal/InRelease  Error  writing to output file - write (28: No space left on device) [IP:  13.82.220.49 443]
W: Failed to fetch  http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu/dists/bionic/InRelease   Error writing to output file - write (28: No space left on device)  [IP: 185.125.190.52 80]
W: Failed to fetch  https://repo.radeon.com/rocm/apt/5.4.3/dists/focal/InRelease  Error  writing to output file - write (28: No space left on device) [IP:  13.82.220.49 443]
W: Failed to fetch  https://esm.ubuntu.com/apps/ubuntu/dists/bionic-apps-security/InRelease   Error writing to output file - write (28: No space left on device) [IP:  185.125.190.24 443]
W: Failed to fetch  https://esm.ubuntu.com/apps/ubuntu/dists/bionic-apps-updates/InRelease   Error writing to output file - write (28: No space left on device) [IP:  185.125.190.24 443]
W: Failed to fetch  https://esm.ubuntu.com/infra/ubuntu/dists/bionic-infra-security/InRelease   Error writing to output file - write (28: No space left on device)  [IP: 185.125.190.24 443]
W: Failed to fetch  https://esm.ubuntu.com/infra/ubuntu/dists/bionic-infra-updates/InRelease   Error writing to output file - write (28: No space left on device)  [IP: 185.125.190.24 443]
W: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package amdgpu-lib
E: Unable to locate package amdgpu-lib32
E: Unable to locate package rocm-opencl-runtime
E: Unable to locate package rocm-hip-runtime
E: Unable to locate package amdgpu-dkms

```

Maybe all of this is where the issue is coming from?  I don't know why  it says no space left on device.  There is plenty of space left on the  120GB SSD.
Thoughts?

---

### Post by radiah on 2023-03-07
I made the modifications to the xorg.conf file you suggested, naming them consecutively screen0, 1, 2.  I then re-booted.
Here is the new xorg.0.log:  [https://paste.ubuntu.com/p/sWfnF7nRtt/](https://paste.ubuntu.com/p/sWfnF7nRtt/)
Here is the latest gpumanager.log:

```

1 log_file: /var/log/gpu-manager.log
  2 last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
  3 new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
  4 can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
  5 Looking for nvidia modules in /lib/modules/5.0.0-31-generic/updates/dkms
  6 Found nvidia module: nvidia-modeset.ko
  7 Looking for amdgpu modules in /lib/modules/5.0.0-31-generic/updates/dkms
  8 Found amdgpu module: amdgpu.ko
  9 Is nvidia loaded? yes
 10 Was nvidia unloaded? no
 11 Is nvidia blacklisted? no
 12 Is intel loaded? yes
 13 Is radeon loaded? no
 14 Is radeon blacklisted? yes
 15 Is amdgpu loaded? no
 16 Is amdgpu blacklisted? no
 17 Is amdgpu versioned? yes
 18 Is amdgpu pro stack? yes
 19 Is nouveau loaded? no
 20 Is nouveau blacklisted? yes
 21 Is nvidia kernel module available? yes
 22 Is amdgpu kernel module available? yes
 23 Vendor/Device Id: 8086:1902
 24 BusID "PCI:0@0:2:0"
 25 Is boot vga? yes
 26 Error: can't access /sys/bus/pci/devices/0000:00:02.0/driver
 27 The device is not bound to any driver.
 28 Vendor/Device Id: 10de:2184
 29 BusID "PCI:13@0:0:0"
 30 Is boot vga? no
 31 can't access /etc/u-d-c-nvidia-runtimepm-override file
 32 Found json file: /usr/share/doc/nvidia-driver-470-server/supported-gpus.json
 33 File /usr/share/doc/nvidia-driver-470-server/supported-gpus.json not found
 34 Is nvidia runtime pm supported for "0x2184"? yes
 35 Trying to create new file: /run/nvidia_runtimepm_supported
 36 Checking power status in /proc/driver/nvidia/gpus/0000:0d:00.0/power
 37 Runtime D3 status:          ?
 38 Is nvidia runtime pm enabled for "0x2184"? no
 39 Vendor/Device Id: 10de:1c09
 40 BusID "PCI:4@0:0:0"
 41 can't open /sys/bus/pci/devices/0000:04:00.0/boot_vga
 42 Is boot vga? no
 43 can't open /sys/bus/pci/devices/0000:04:00.0/boot_vga
 44 can't access /etc/u-d-c-nvidia-runtimepm-override file
 45 Found json file: /usr/share/doc/nvidia-driver-470-server/supported-gpus.json
 46 File /usr/share/doc/nvidia-driver-470-server/supported-gpus.json not found
 47 Is nvidia runtime pm supported for "0x1c09"? no
 48 Checking power status in /proc/driver/nvidia/gpus/0000:04:00.0/power
 49 Runtime D3 status:          ?
 50 Is nvidia runtime pm enabled for "0x1c09"? no
 51 Vendor/Device Id: 1002:67df
 52 BusID "PCI:16@0:0:0"
 53 Is boot vga? no
 54 Error: can't access /sys/bus/pci/devices/0000:10:00.0/driver
 55 The device is not bound to any driver.
 56 Vendor/Device Id: 10de:2184
 57 BusID "PCI:14@0:0:0"
 58 Is boot vga? no
 59 can't access /etc/u-d-c-nvidia-runtimepm-override file
 60 Found json file: /usr/share/doc/nvidia-driver-470-server/supported-gpus.json
 61 File /usr/share/doc/nvidia-driver-470-server/supported-gpus.json not found
 62 Is nvidia runtime pm supported for "0x2184"? yes
 63 Trying to create new file: /run/nvidia_runtimepm_supported
 64 Checking power status in /proc/driver/nvidia/gpus/0000:0e:00.0/power
 65 Runtime D3 status:          ?
 66 Is nvidia runtime pm enabled for "0x2184"? no
 67 Vendor/Device Id: 10de:1c07
 68 BusID "PCI:17@0:0:0"
 69 can't open /sys/bus/pci/devices/0000:11:00.0/boot_vga
 70 Is boot vga? no
 71 can't open /sys/bus/pci/devices/0000:11:00.0/boot_vga
72 can't access /etc/u-d-c-nvidia-runtimepm-override file
 73 Found json file: /usr/share/doc/nvidia-driver-470-server/supported-gpus.json
 74 File /usr/share/doc/nvidia-driver-470-server/supported-gpus.json not found
 75 Is nvidia runtime pm supported for "0x1c07"? no
 76 Checking power status in /proc/driver/nvidia/gpus/0000:11:00.0/power
 77 Runtime D3 status:          ?
 78 Is nvidia runtime pm enabled for "0x1c07"? no
 79 Vendor/Device Id: 1002:67df
 80 BusID "PCI:15@0:0:0"
 81 Is boot vga? no
 82 Error: can't access /sys/bus/pci/devices/0000:0f:00.0/driver
 83 The device is not bound to any driver.
 84 Vendor/Device Id: 10de:1c03
 85 BusID "PCI:6@0:0:0"
 86 Is boot vga? no
 87 can't access /etc/u-d-c-nvidia-runtimepm-override file
 88 Found json file: /usr/share/doc/nvidia-driver-470-server/supported-gpus.json
 89 File /usr/share/doc/nvidia-driver-470-server/supported-gpus.json not found
 90 Is nvidia runtime pm supported for "0x1c03"? no
 91 Checking power status in /proc/driver/nvidia/gpus/0000:06:00.0/power
 92 Runtime D3 status:          ?
 93 Is nvidia runtime pm enabled for "0x1c03"? no
 94 Vendor/Device Id: 1002:67df
 95 BusID "PCI:7@0:0:0"
 96 Is boot vga? no
 97 Error: can't access /sys/bus/pci/devices/0000:07:00.0/driver
 98 The device is not bound to any driver.
 99 Vendor/Device Id: 10de:2184
100 BusID "PCI:1@0:0:0"
101 Is boot vga? no
102 can't access /etc/u-d-c-nvidia-runtimepm-override file
103 Found json file: /usr/share/doc/nvidia-driver-470-server/supported-gpus.json
104 File /usr/share/doc/nvidia-driver-470-server/supported-gpus.json not found
105 Is nvidia runtime pm supported for "0x2184"? yes
106 Trying to create new file: /run/nvidia_runtimepm_supported
107 Checking power status in /proc/driver/nvidia/gpus/0000:01:00.0/power
108 Runtime D3 status:          ?
109 Is nvidia runtime pm enabled for "0x2184"? no
110 Vendor/Device Id: 10de:1c07
111 BusID "PCI:11@0:0:0"
112 can't open /sys/bus/pci/devices/0000:0b:00.0/boot_vga
113 Is boot vga? no
114 Warning: too many devices 10. Max supported 10. Ignoring the rest.
115 Skipping "/dev/dri/card8", driven by "nvidia-drm"
116 Skipping "/dev/dri/card7", driven by "nvidia-drm"
117 Skipping "/dev/dri/card6", driven by "nvidia-drm"
118 Skipping "/dev/dri/card5", driven by "nvidia-drm"
119 Skipping "/dev/dri/card4", driven by "nvidia-drm"
120 Skipping "/dev/dri/card3", driven by "nvidia-drm"
121 Skipping "/dev/dri/card2", driven by "nvidia-drm"
122 Skipping "/dev/dri/card1", driven by "nvidia-drm"
123 Skipping "/dev/dri/card0", driven by "nvidia-drm"
124 Skipping "/dev/dri/card8", driven by "nvidia-drm"
125 Skipping "/dev/dri/card7", driven by "nvidia-drm"
126 Skipping "/dev/dri/card6", driven by "nvidia-drm"
127 Skipping "/dev/dri/card5", driven by "nvidia-drm"
128 Skipping "/dev/dri/card4", driven by "nvidia-drm"
129 Skipping "/dev/dri/card3", driven by "nvidia-drm"
130 Skipping "/dev/dri/card2", driven by "nvidia-drm"
131 Skipping "/dev/dri/card1", driven by "nvidia-drm"
132 Skipping "/dev/dri/card0", driven by "nvidia-drm"
133 Skipping "/dev/dri/card8", driven by "nvidia-drm"
134 Skipping "/dev/dri/card7", driven by "nvidia-drm"
135 Skipping "/dev/dri/card6", driven by "nvidia-drm"
136 Skipping "/dev/dri/card5", driven by "nvidia-drm"
137 Skipping "/dev/dri/card4", driven by "nvidia-drm"
138 Skipping "/dev/dri/card3", driven by "nvidia-drm"
139 Skipping "/dev/dri/card2", driven by "nvidia-drm"
140 Skipping "/dev/dri/card1", driven by "nvidia-drm"
141 Skipping "/dev/dri/card0", driven by "nvidia-drm"
142 Skipping "/dev/dri/card8", driven by "nvidia-drm"
143 Skipping "/dev/dri/card7", driven by "nvidia-drm"
144 Skipping "/dev/dri/card6", driven by "nvidia-drm"
145 Skipping "/dev/dri/card5", driven by "nvidia-drm"
146 Skipping "/dev/dri/card4", driven by "nvidia-drm"
147 Skipping "/dev/dri/card3", driven by "nvidia-drm"
148 Skipping "/dev/dri/card2", driven by "nvidia-drm"
149 Skipping "/dev/dri/card1", driven by "nvidia-drm"
150 Skipping "/dev/dri/card0", driven by "nvidia-drm"
151 Does it require offloading? no
152 last cards number = 10
153 Has amd? yes
154 Has intel? yes
155 Has nvidia? yes
156 How many cards? 10
157 Has the system changed? No
158 Intel IGP detected
159 NVIDIA hybrid system
160 Creating /usr/share/X11/xorg.conf.d/11-nvidia-prime.conf
161 Setting power control to "on" in /sys/bus/pci/devices/0000:0d:00.0/power/control

```

xorg.0.log still does not seem to mention any AMD devices....

---

### Post by MAFoElffen on 2023-03-07
Dang. But now it is not loading the nvidia drivers either??? Is it still in a state where that install of the AMD drivers is failed? And where is the out-of-space error coming from?
```

df -h

```

---

### Post by radiah on 2023-03-07
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  6.3M  1.6G   1% /run
/dev/sda1        15G   14G     0 100% /
tmpfs           7.8G     0  7.8G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/sda2       148M  8.8M  139M   6% /boot/efi
/dev/loop0      117M  117M     0 100% /snap/core/14784
/dev/loop1      9.0M  9.0M     0 100% /snap/canonical-livepatch/164
tmpfs           1.6G   16K  1.6G   1% /run/user/0
/dev/sdb2       477M  2.3M  445M   1% /media/root/DATA
/dev/sdb1      1022M  446M  577M  44% /media/root/MINING_OS

---

### Post by MAFoElffen on 2023-03-07
What is here?
```

/dev/sda1 15G 14G 0 100% /

```
Says your root drive is full. That will cause big problems...

Anyway to give it room?

---

### Post by radiah on 2023-03-07
-bash: /dev/sda1: Permission denied  :-O

---

### Post by #&amp;thj^% on 2023-03-07
use this:
```
ls  /dev/sda1
```

---

### Post by MAFoElffen on 2023-03-07
if you can do above, then
```

sudo du -h / 2> /dev/null | grep -v 'run\|proc\|snap\|root\|sys' | sort -r

```

---

### Post by radiah on 2023-03-07
I've cleaned out logs, and old installations, etc.  I'm beginning to wonder if perhaps the drive is not damaged or corrupt?

---

### Post by MAFoElffen on 2023-03-07
You could check it for errors:
```

sudo smartctl -a /dev/sda | less
sudo fsck -n /dev/sda1

```

---

### Post by radiah on 2023-03-08
sudo smartctl -a /dev/sda | less:
```

smartctl 6.6 2016-05-31 r4324 [x86_64-linux-5.0.0-31-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     SandForce Driven SSDs
Device Model:     SanDisk SDSSDA120G
Serial Number:    154067405679
LU WWN Device Id: 5 001b44 eeab7076f
Firmware Version: Z22000RL
User Capacity:    120,034,123,776 bytes [120 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Form Factor:      1.8 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2 T13/2015-D revision 3
SATA Version is:  SATA 3.2, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Wed Mar  8 09:37:29 2023 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x02) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (    0) seconds.
Offline data collection
capabilities:                    (0x71) SMART execute Offline immediate.
                                        No Auto Offline data collection support.
                                        Suspend Offline collection upon new
                                        command.
                                        No Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0002) Does not save SMART data before
                                        entering power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  10) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.

SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Retired_Block_Count     0x0032   100   100   000    Old_age   Always       -       0
  9 Power_On_Hours_and_Msec 0x0032   225   100   000    Old_age   Always       -       993h+00m+00.000s
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       432
166 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       303
167 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
168 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       355
169 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       36
170 Reserve_Block_Count     0x0032   100   100   000    Old_age   Always       -       0
171 Program_Fail_Count      0x0032   100   100   000    Old_age   Always       -       0
172 Erase_Fail_Count        0x0032   100   100   000    Old_age   Always       -       0
173 Unknown_SandForce_Attr  0x0032   100   100   ---    Old_age   Always       -       338
174 Unexpect_Power_Loss_Ct  0x0032   100   100   000    Old_age   Always       -       255
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0022   076   100   000    Old_age   Always       -       24 (Min/Max 0/44)
199 SATA_CRC_Error_Count    0x0032   100   100   000    Old_age   Always       -       2
230 Life_Curve_Status       0x0032   100   100   000    Old_age   Always       -       11
232 Available_Reservd_Space 0x0033   100   100   004    Pre-fail  Always       -       100
233 SandForce_Internal      0x0032   100   100   000    Old_age   Always       -       28134
241 Lifetime_Writes_GiB     0x0030   253   253   000    Old_age   Offline      -       11754
242 Lifetime_Reads_GiB      0x0030   253   253   000    Old_age   Offline      -       4648

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%        56         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

sudo fsck -n /dev/sda1:

fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
Warning!  /dev/sda1 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
/dev/sda1: clean, 263591/966656 files, 3704329/3866134 blocks

So much for that idea.  May have to boot into "Try Ubuntu" from a flash drive and use partition magic to expand that partition?  What do you think of that idea?

Thanks for your continued help!

---

### Post by radiah on 2023-03-08
I have just found this monster in /usr/bin

-rwxr-xr-x  1 root root    10265096 Dec 15  2016  pedump

and these huge core dumps.

[/var/lib/apport/coredump]:# ls -al
total 649920
drwxr-xr-x 2 root root      4096 Feb 24 04:25 .
drwxr-xr-x 3 root root      4096 Jun 15  2022 ..
-r-------- 1 root root 133099520 Feb 23 19:45 core._usr_lib_xorg_Xorg.0.0b99fa71-6b0c-4e3a-86b6-178489a65468.723.603
-r-------- 1 root root 133095424 Feb 22 07:32 core._usr_lib_xorg_Xorg.0.4aff6006-b372-4fa3-8b03-5ad9c306450a.754.597
-r-------- 1 root root 133095424 Feb 24 00:01 core._usr_lib_xorg_Xorg.0.9c7063e8-7208-4f56-b984-51f11a9f89f6.729.593
-r-------- 1 root root 133103616 Feb 24 04:25 core._usr_lib_xorg_Xorg.0.ae556614-122b-4fa6-9ee8-7353a6abcfa8.778.597
-r-------- 1 root root 133095424 Feb 23 05:51 core._usr_lib_xorg_Xorg.0.c3d9ecc7-0771-49d1-810f-feeeda44f8f8.853.654

Can any of these core dumps or the pedump file be safely deleted?  Might free up a lot of space for me.

OK core dumps deleted.  Found a post saying they could be safely remove. ;-)

But wait!  There's more!

Gained 500MB  

```

[/root]:# df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  6.3M  1.6G   1% /run
/dev/sda1        15G   14G  499M  97% /
tmpfs           7.8G     0  7.8G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/sda2       148M  8.8M  139M   6% /boot/efi
/dev/loop0      117M  117M     0 100% /snap/core/14784
/dev/loop1      9.0M  9.0M     0 100% /snap/canonical-livepatch/164
tmpfs           1.6G   12K  1.6G   1% /run/user/0

```

---

### Post by #&amp;thj^% on 2023-03-08
If you don&#8217;t plan on investigating your core dumps any further, you can delete the contents of the directory.

---

### Post by radiah on 2023-03-08
Did that already.  Any idea what /usr/bin/pedump file is?

---

### Post by #&amp;thj^% on 2023-03-08
No.. where did you see that?
Or did you mean "utmpdump"
I see it:
```
cd /usr/bin/ && ls | grep *pedump
pedump

```
If I remember right it is a part of rubygems...
EDIT: I just had to be sure, now I am
```
gem install pedump 
Fetching pedump-0.6.5.gem
Fetching zhexdump-0.0.2.gem
Fetching rainbow-3.1.1.gem
Fetching multipart-post-2.3.0.gem
Fetching iostruct-0.0.5.gem
Fetching awesome_print-1.9.2.gem
ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions for the /var/lib/gems/3.1.0 directory.

```
I did the install anyway:
```
pedump -h
Usage: pedump [options]
        --version                    Print version information and exit
    -v, --verbose                    Run verbosely
                                     (can be used multiple times)
    -q, --quiet                      Silent any warnings
                                     (can be used multiple times)
    -F, --force                      Try to dump by all means
                                     (can cause exceptions & heavy wounds)
    -f, --format FORMAT              Output format: bin,c,dump,hex,inspect,json,table,yaml
                                     (default: table)
        --mz
        --dos-stub
        --rich
        --pe
        --ne
        --te
        --data-directory
    -S, --sections
        --tls
        --security
    -s, --strings
    -R, --resources
        --resource-directory
    -I, --imports
    -E, --exports
    -V, --version-info
        --packer
        --deep                       packer deep scan, significantly slower
    -P, --packer-only                packer/compiler detect only,
                                     mimics 'file' command output
    -r, --recursive                  recurse dirs in packer detect
        --all                        Dump all but resource-directory (default)

        --extract ID                 Extract a resource/section/data_dir
                                     ID: datadir:EXPORT     - datadir by type
                                     ID: resource:0x98478   - resource by offset
                                     ID: resource:ICON/#1   - resource by type & name
                                     ID: section:.text      - section by name
                                     ID: section:rva/0x1000 - section by RVA
                                     ID: section:raw/0x400  - section by RAW_PTR
        --va2file VA                 Convert RVA to file offset

    -W, --web                        Uploads files to a https://pedump.me
                                     for a nice HTML tables with image previews,
                                     candies & stuff
    -C, --console                    opens IRB console with specified file loaded


```

---

