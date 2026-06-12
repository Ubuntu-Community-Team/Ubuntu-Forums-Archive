---
title: "Freezes on Ubuntu Gnome"
date: 2017-04-19
forum: General Help
---

### Post by oxedions on 2017-04-19
Hi,

I encounter a bug on the Ubuntu Gnome: sometime, randomly, my system hang and freeze. Sometime, I can keep the mouse few seconds, and then it freeze also. Ctrl + Alt + F? do nothing, so impossible to check what is going on (dmesg, ps, etc).
It seems to me that this happen every time I use some specific patterns:
- Load new page in Firefox (but randomly, I can open many pages before it happens)
- Use the "windows display" function of Gnome Shell (mouse on left up corner)
- Launch Factorio (a game, linux native binary)
So always seems to be "graphically hardware accelerated things", but not sure at 100%. Also, I never encounter the bug when I use one thing at at time. Maybe using 2 at the same time causes the issue.

System is ubuntu 17.04 x64, up to date.
Proc is i5-4200U (laptop)
Memory is 8Gb (tested with memtest, RAS), no swap

What I did recently: new sata disk, fresh ubuntu 17.04 install (was beta 2, now up to date). But disk seems fine also.

I thought it was related to memory limit, but when I use too much VM, system just hang few seconds and then kill the VM to free memory, so it seems able to handle that.

Some information:

```
~$ uname -a
Linux remiel 4.10.0-19-generic #21-Ubuntu SMP Thu Apr 6 17:04:57 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
~$ glxinfo 
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
[...]
~$ lspci
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I218-LM (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 1 (rev e4)
00:1c.3 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 4 (rev e4)
00:1c.5 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 6 (rev e4)
00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
02:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5227 PCI Express Card Reader (rev 01)
~$ sudo smartctl -a /dev/sda
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.10.0-19-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     ST1000LM035-1RK172
Serial Number:    WES0XVY8
LU WWN Device Id: 5 000c50 09ce09e26
Firmware Version: SDM1
User Capacity:    1 000 204 886 016 bytes [1,00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Form Factor:      2.5 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-3 T13/2161-D revision 3b
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Wed Apr 19 16:40:45 2017 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (    0) seconds.
Offline data collection
capabilities:              (0x79) SMART execute Offline immediate.
                    No Auto Offline data collection support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      ( 163) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x3035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   084   064   006    Pre-fail  Always       -       240962056
  3 Spin_Up_Time            0x0003   099   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       26
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   071   060   045    Pre-fail  Always       -       12147781
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       113 (67 65 0)
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       25
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   061   056   040    Old_age   Always       -       39 (Min/Max 38/40)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       7
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       469
194 Temperature_Celsius     0x0022   039   044   000    Old_age   Always       -       39 (0 17 0 0 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       111 (146 212 0)
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       1797941164
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       397767541
254 Free_Fall_Sensor        0x0032   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]

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

I am out of ideas. Does any of you have a new way to explore ?

With my best regards

Ox

---

### Post by jaarvidsen on 2017-04-19
im having similar problems on ubuntu gnome 17.04, just random freezing/crashing    

so far ive tried getting an updated libmozjs via zesty-proposed as described here [https://bugs.launchpad.net/ubuntu/+source/mozjs38/+bug/1682631](https://bugs.launchpad.net/ubuntu/+source/mozjs38/+bug/1682631) - but that did not fix the problem

in the 17.04 release notes it says: GNOME Shell 3.24 uses the SpiderMonkey (mozjs) 38 engine which requires stricter JavaScript syntax. **Some GNOME Shell extensions will need to be fixed by their developers before they can be used with GNOME Shell 3.24.    **

so im in the process of disabling some extension to see if the crashes still occur using the eliminaition method, but too early to tell yet. 

got any extensions installed?

---

### Post by dragonfly41 on 2017-04-19
> [COLOR=#000000]So always seems to be "graphically hardware accelerated things", but not sure at 100%. 

I would start by disabling hardware acceleration as a first experiment.[/COLOR]

---

### Post by JoelParke on 2017-04-20
I too am seeing freezes... 
although looking at syslog, it isn't clear why at all!

But today I lost 2 or 3 hours of work... so 
I am ready to revert back to 16.10 where I  never had these issues.

There was a suggesting to disable hardware acceleration.
? Of what the graphics ? 
If so, how can I do that ? 

Looking at the graphics I see acceleration:
```
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV117
OpenGL version string:  3.0 Mesa 17.0.3


Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes


```
Looking at smartctrl, etc.  things look fine also.

Thanks,
Joel Parke

PS
If I end up needing to switch back, and given the death of Unity,  Do you have another distro you recommend as very stable?

---

### Post by wildmanne39 on 2017-04-20
>  If I end up needing to switch back, and given the death of Unity, Do you have another distro you recommend as very stable? 
Unity 7 is still going to be supported for a long time to come because 16.04 still has I believe four years left for support.

Unity 8 is going to be developed by another developer so no need to worry about it.

---

### Post by JoelParke on 2017-04-20
It's good to know that unity will be supported for a LONG time and be developed more.

I looked at my kern.log before I had to reboot from the last freeze.  
What I see is a ton of repeated errors from evolution-calen, but I don't know enough to understand what they are a symptom of:

```
Apr 19 20:24:27 parke evolution-calen[2642]: caldav_setup_bearer_auth: assertion 'E_IS_SOUP_AUTH_BEARER (bearer)' failed
Apr 19 20:24:27 parke evolution-calen[2642]: invalid cast from 'SoupAuthBasic' to 'ESoupAuthBearer'
Apr 19 20:24:27 parke evolution-calen[2642]: caldav_setup_bearer_auth: assertion 'E_IS_SOUP_AUTH_BEARER (bearer)' failed
Apr 19 20:24:27 parke evolution-calen[2642]: invalid cast from 'SoupAuthBasic' to 'ESoupAuthBearer'
Apr 19 20:24:27 parke evolution-calen[2642]: caldav_setup_bearer_auth: assertion 'E_IS_SOUP_AUTH_BEARER (bearer)' failed
Apr 19 20:24:28 parke evolution-calen[2642]: invalid cast from 'SoupAuthBasic' to 'ESoupAuthBearer'
Apr 19 20:24:28 parke evolution-calen[2642]: caldav_setup_bearer_auth: assertion 'E_IS_SOUP_AUTH_BEARER (bearer)' failed
Apr 19 20:24:28 parke evolution-calen[2642]: invalid cast from 'SoupAuthBasic' to 'ESoupAuthBearer'
Apr 19 20:24:28 parke evolution-calen[2642]: caldav_setup_bearer_auth: assertion 'E_IS_SOUP_AUTH_BEARER (bearer)' failed
Apr 19 20:24:28 parke evolution-calen[2642]: invalid cast from 'SoupAuthBasic' to 'ESoupAuthBearer'
Apr 19 20:24:28 parke evolution-calen[2642]: caldav_setup_bearer_auth: assertion 'E_IS_SOUP_AUTH_BEARER (bearer)' failed
Apr 19 20:24:28 parke evolution-calen[2642]: invalid cast from 'SoupAuthBasic' to 'ESoupAuthBearer'
Apr 19 20:24:28 parke evolution-calen[2642]: caldav_setup_bearer_auth: assertion 'E_IS_SOUP_AUTH_BEARER (bearer)' failed
Apr 19 20:24:28 parke evolution-calen[2642]: invalid cast from 'SoupAuthBasic' to 'ESoupAuthBearer'
Apr 19 20:24:28 parke evolution-calen[2642]: caldav_setup_bearer_auth: assertion 'E_IS_SOUP_AUTH_BEARER (bearer)' failed
Apr 19 20:24:29 parke evolution-calen[2642]: invalid cast from 'SoupAuthBasic' to 'ESoupAuthBearer'
Apr 19 20:24:29 parke evolution-calen[2642]: caldav_setup_bearer_auth: assertion 'E_IS_SOUP_AUTH_BEARER (bearer)' failed
Apr 19 20:24:29 parke evolution-calen[2642]: invalid cast from 'SoupAuthBasic' to 'ESoupAuthBearer'
Apr 19 20:24:29 parke evolution-calen[2642]: caldav_setup_bearer_auth: assertion 'E_IS_SOUP_AUTH_BEARER (bearer)' failed
Apr 19 20:24:29 parke evolution-calen[2642]: invalid cast from 'SoupAuthBasic' to 'ESoupAuthBearer'
Apr 19 20:24:29 parke evolution-calen[2642]: caldav_setup_bearer_auth: assertion 'E_IS_SOUP_AUTH_BEARER (bearer)' failed
Apr 19 20:24:30 parke evolution-calen[2642]: invalid cast from 'SoupAuthBasic' to 'ESoupAuthBearer'
Apr 19 20:24:30 parke evolution-calen[2642]: caldav_setup_bearer_auth: assertion 'E_IS_SOUP_AUTH_BEARER (bearer)' failed
```

---

### Post by wildmanne39 on 2017-04-20
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by oxedions on 2017-04-20
Thank you for your answers.

> **jaarvidsen said:**
> got any extensions installed?

Yes, but none are activated. In gnome tweak tool, in extensions, Extension main switch is ON, but all extensions are OFF. Because I am not used to Gnome Shell, I did not install anything more than what is delivered to better know this interface first.

> **dragonfly41 said:**
> I would start by disabling hardware acceleration as a first experiment.[/COLOR]

Yes, sounds a good idea. It will be laggy, but if it can solve this issue (I lost many hours of shell history because of that), it worth it.
Do you know how to do that ? I know many things in linux, but I am not very used to interfaces... :oops:

For the time being, I disabled all "animation effects" in gnome shell:
dconf-editor > org > gnome > desktop > interface
enable-animations set to False

Is there a specific log where I can search after a crash and reboot ?

Edit: had a crash again. Disabling animations did not change this issue.
Logs just before the crash (found nothing else)
```
Apr 20 10:15:44 remiel gnome-terminal-[3822]: Allocating size to GtkBox 0x55eb050ab880 without calling gtk_widget_get_preferred_width/height(). How does the code know the size to allocate?
Apr 20 10:15:45 remiel gnome-terminal-[3822]: message repeated 2 times: [ Allocating size to GtkBox 0x55eb050ab880 without calling gtk_widget_get_preferred_width/height(). How does the code know the size to allocate?]
Apr 20 10:16:47 remiel gnome-shell[1755]: pushModal: invocation of begin_modal failed
Apr 20 10:18:56 remiel gnome-shell[1755]: pushModal: invocation of begin_modal failed
```

---

### Post by dragonfly41 on 2017-04-20
re: disabling hardware acceleration (for troubleshooting the problem) ...

I have not used Firefox for some time, but this discussion I found explains ... go to url .. about:support

[https://www.quora.com/How-do-I-check-if-Firefox-and-Chrome-are-really-using-hardware-acceleration](https://www.quora.com/How-do-I-check-if-Firefox-and-Chrome-are-really-using-hardware-acceleration)

---

### Post by oxedions on 2017-04-20
Thank you. here are the results:

Graphics
Features
Compositing    Basic
Asynchronous Pan/Zoom    wheel input enabled; touch input enabled
WebGL Renderer    Intel Open Source Technology Center -- Mesa DRI Intel(R) Haswell Mobile
WebGL2 Renderer    Intel Open Source Technology Center -- Mesa DRI Intel(R) Haswell Mobile
Hardware H264 Decoding    No
Audio Backend    pulse
GPU #1
Active    Yes
Description    Intel Open Source Technology Center -- Mesa DRI Intel(R) Haswell Mobile
Vendor ID    Intel Open Source Technology Center
Device ID    Mesa DRI Intel(R) Haswell Mobile
Driver Version    3.0 Mesa 17.0.3
Diagnostics
AzureCanvasAccelerated    0
AzureCanvasBackend    skia
AzureContentBackend    skia
AzureFallbackCanvasBackend    none
CairoUseXRender    0
Decision Log
HW_COMPOSITING    
blocked by default: Acceleration blocked by platform
OPENGL_COMPOSITING    
unavailable by default: Hardware compositing is disabled

So it is enabled. I will try to isolate firefox. I have a VM with a GUI, I will use firefox from here.
I am also wondering if it is not the VMs that cause crash, Gnome Shell react with a strange animation when you start an instance (double popup + flash).

Let's see what happens when firefox is not playing around ;)

---

### Post by JoelParke on 2017-04-20
In my case, I have switched back to Ubuntu Unity away from Gnome Classic.  Now I will know within a day, if the freezes are tied to Gnome.
In my case, I could not access the shell through the network either after the freeze (which seems to be related to the UI). 
Lets see what this change does.

---

### Post by jaarvidsen on 2017-04-20
i found my crashes were almost certainly related to the system-monitor extension paradoxxx version (from github). been running 24h or something now without the extension and without any crashes. wont help the original poster but might help someone searching the forum for gnome shell crashes

---

### Post by JoelParke on 2017-04-21
I have determined that it is definitely an issue with Gnome.  After switching back (desktop only - no other changes) I have had no issues.  With Gnome it only took hours  before a freeze.  
Tomorrow I will switch to Wayland with Gnome and see it things are stable or not. But for anyone using Gnome, I would be very CAREFUL.  There is definitely some fatal issue.

---

### Post by jaarvidsen on 2017-04-21
beh, started crashing again
sigh
i notice gnome 3.24.1 is available in the proposed repository, same with mutter and other things
3.24.1 is a new bugfix release in the stable 3.24 series

havent tried..yet

---

### Post by JoelParke on 2017-04-21
I will be very curious to know how 3.24.1.  This evening I will try Wayland this evening and see if it lasts overnight.

---

### Post by JoelParke on 2017-04-22
When I switched Wayland, It ran all night.  So the issue is definately with Gnome and Gnome Classic.  For now I will switch back to Unity and try again after there is a change.

---

### Post by oxedions on 2017-04-27
I tried all combinaison possible, it always end with a freeze. Sometime it appends instantly, sometime, some parts freeze, but I can still act with the mouse one some others windows, and then after few seconds it crashs.
I reinstalled the whole system from scratch, on another disk, this time with swap, same issues.

I am installing LXDE alongside gnome, and will work on LXDE to check if it is also related to gnome.

Ox

---

### Post by dragonfly41 on 2017-04-27
If you are willing to try out ideas ...

Although you have done memtest .. 
Take out half of your memory cards (8GB split into two sets of 4GB).
Test PC running with each set of 4GB cards.
There is a slim possibility that there is a faulty card connection not picked up by memtest.

When removing/replacing each set of memory cards, carefully clean connection edges with a clean rubber eraser to ensure good
connection. Handle cards carefully to avoid static (wearing an anti-static jumper lead on wrist connected to earth would be safest).

Rationale. In searching around to solve my own spate of freezes in an old laptop I have read reports
of poor memory card connection(s) causing freezes.

---

### Post by jaarvidsen on 2017-04-27
i know ive blamed extensions before but this time im 99% certain

freon - both the versions that are available
without it, no crash for 3 days
with, crashes every few hours

---

### Post by oxedions on 2017-04-27
[HR][/HR]Found it !!

```
Apr 27 17:24:30 remiel kernel: [19729.706196] ------------[ cut here ]------------
Apr 27 17:24:30 remiel kernel: [19729.706228] kernel BUG at /build/linux-2NWldV/linux-4.10.0/include/linux/swapops.h:129!
Apr 27 17:24:30 remiel kernel: [19729.706255] invalid opcode: 0000 [#1] SMP
Apr 27 17:24:30 remiel kernel: [19729.706270] Modules linked in: dm_crypt pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) ccm rfcomm bnep hp_wmi sparse_keymap uvcvideo videobuf2_vmalloc arc4 videobuf2_memops videobuf2_v4l2 videobuf2_core videodev btusb btrtl media btbcm snd_usb_audio snd_usbmidi_lib btintel bluetooth snd_hda_codec_hdmi intel_rapl snd_hda_codec_idt x86_pkg_temp_thermal snd_hda_codec_generic intel_powerclamp coretemp kvm_intel snd_hda_intel snd_hda_codec kvm snd_hda_core snd_hwdep snd_pcm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_seq_midi pcbc snd_seq_midi_event snd_rawmidi iwlmvm snd_seq aesni_intel mac80211 aes_x86_64 crypto_simd glue_helper cryptd snd_seq_device intel_cstate snd_timer iwlwifi intel_rapl_perf cfg80211 input_leds joydev serio_raw rtsx_pci_ms snd memstick lpc_ich
Apr 27 17:24:30 remiel kernel: [19729.706506]  shpchp mei_me mei soundcore hp_accel lis3lv02d intel_smartconnect input_polldev hp_wireless tpm_infineon mac_hid ip6t_REJECT nf_reject_ipv6 nf_log_ipv6 xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT nf_reject_ipv4 nf_log_ipv4 nf_log_common xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat libcrc32c nf_conntrack_ftp nf_conntrack parport_pc ppdev iptable_filter lp parport ip_tables x_tables autofs4 hid_logitech_hidpp hid_logitech_dj hid_generic usbhid hid rtsx_pci_sdmmc i915 i2c_algo_bit drm_kms_helper syscopyarea sysfillrect ahci libahci rtsx_pci psmouse sysimgblt e1000e fb_sys_fops drm ptp pps_core wmi video fjes
Apr 27 17:24:30 remiel kernel: [19729.706732] CPU: 3 PID: 2953 Comm: firefox Tainted: G           OE   4.10.0-20-generic #22-Ubuntu
Apr 27 17:24:30 remiel kernel: [19729.706761] Hardware name: Hewlett-Packard HP EliteBook 840 G1/198F, BIOS L71 Ver. 01.10 03/25/2014
Apr 27 17:24:30 remiel kernel: [19729.706791] task: ffff92932d6d5a00 task.stack: ffffac6781dec000
Apr 27 17:24:30 remiel kernel: [19729.706815] RIP: 0010:__migration_entry_wait+0x16a/0x180
Apr 27 17:24:30 remiel kernel: [19729.706833] RSP: 0000:ffffac6781defd68 EFLAGS: 00010246
Apr 27 17:24:30 remiel kernel: [19729.706852] RAX: 0017ffffc0048078 RBX: ffffeacbc8d46070 RCX: ffffeacbc8d46070
Apr 27 17:24:30 remiel kernel: [19729.706875] RDX: 0000000000000001 RSI: ffff929335181858 RDI: ffffeacbc7f4c2c0
Apr 27 17:24:30 remiel kernel: [19729.706899] RBP: ffffac6781defd80 R08: ffff92932e04b640 R09: ffff92932e04b640
Apr 27 17:24:30 remiel kernel: [19729.706923] R10: 000000000000daf6 R11: 00007fe614100000 R12: ffffeacbc7f4c2c0
Apr 27 17:24:30 remiel kernel: [19729.706946] R13: 3e000000001fd30b R14: ffffac6781defe30 R15: ffff92932f078ed8
Apr 27 17:24:30 remiel kernel: [19729.706969] FS:  00007fe69bb94740(0000) GS:ffff92933eac0000(0000) knlGS:0000000000000000
Apr 27 17:24:30 remiel kernel: [19729.706996] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Apr 27 17:24:30 remiel kernel: [19729.707016] CR2: 00007fe67990bea4 CR3: 000000022bb1d000 CR4: 00000000001426e0
Apr 27 17:24:30 remiel kernel: [19729.707040] Call Trace:
Apr 27 17:24:30 remiel kernel: [19729.707052]  migration_entry_wait+0x74/0x80
Apr 27 17:24:30 remiel kernel: [19729.707071]  do_swap_page+0x5b3/0x770
Apr 27 17:24:30 remiel kernel: [19729.707087]  handle_mm_fault+0x873/0x1360
Apr 27 17:24:30 remiel kernel: [19729.707104]  __do_page_fault+0x23e/0x4e0
Apr 27 17:24:30 remiel kernel: [19729.707121]  do_page_fault+0x22/0x30
Apr 27 17:24:30 remiel kernel: [19729.707136]  page_fault+0x28/0x30
Apr 27 17:24:30 remiel kernel: [19729.707149] RIP: 0033:0x7fe68cb88c4a
Apr 27 17:24:30 remiel kernel: [19729.707162] RSP: 002b:00007ffccbbf0310 EFLAGS: 00010246
Apr 27 17:24:30 remiel kernel: [19729.707180] RAX: 000000001b5ec024 RBX: 00007fe685790000 RCX: 000000000000000d
Apr 27 17:24:30 remiel kernel: [19729.707203] RDX: 0000000000000000 RSI: 00000000157f4344 RDI: 00007fe67990bea0
Apr 27 17:24:30 remiel kernel: [19729.707227] RBP: 00007fe6141daf60 R08: 00007ffccbbf0370 R09: 0000000000000000
Apr 27 17:24:30 remiel kernel: [19729.707249] R10: 000000000000daf6 R11: 00007fe614100000 R12: 00007fe685790200
Apr 27 17:24:30 remiel kernel: [19729.707273] R13: 000000001b5ec024 R14: 000000000000000d R15: 00007fe606738792
Apr 27 17:24:30 remiel kernel: [19729.707297] Code: ff ff ff 4c 89 e7 e8 96 a2 f8 ff e9 3c ff ff ff 85 d2 0f 84 2a ff ff ff 8d 4a 01 89 d0 f0 41 0f b1 4d 00 39 d0 74 81 89 c2 eb e5 <0f> 0b 4c 89 e7 e8 0c fb f9 ff eb b8 4c 8d 60 ff 4c 8d 68 1b eb 
Apr 27 17:24:30 remiel kernel: [19729.707378] RIP: __migration_entry_wait+0x16a/0x180 RSP: ffffac6781defd68
Apr 27 17:24:30 remiel kernel: [19729.711609] ---[ end trace 3cebfd383ca42f28 ]---
Apr 27 17:25:29 remiel gnome-terminal-[3418]: Allocating size to GtkBox 0x5619a039c2e0 without calling gtk_widget_get_preferred_width/height(). How does the code know the size to allocate?


```

It also appends on LXDE, so it is not related to Gnome.
Firefox goes weird (freeze, cannot do anything), then I killed it (killall firefox does not the job, so a dangerous xkill), but it was still here as Zl (zombie ?) in ps -ax. And when I kill -9 this process, my terminal scrolled indefinitely, CPU went at 100% (interface still working, so I could see it in the small graph in the panel of LXDE), but no more mouse or keyboard.
And freeze.

Any idea how to solve this ??

dragonfly41: I only have one 8gb sodim, so I cannot remove it. But I will check it's clean ;-)

---

### Post by jaarvidsen on 2017-05-03
gnome-shell 3.24.1 just landed in the regular repos. ive updated and not noticed anything different.
however after about a week without running the freon extension ive still had no crash, so i guess that must have been the problem on my machine

---

