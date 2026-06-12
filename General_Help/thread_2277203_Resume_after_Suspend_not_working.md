---
title: "Resume after Suspend not working"
date: 2015-05-07
forum: General Help
---

### Post by aknjusa on 2015-05-07
I installed Ubuntu 14.04 LTS 32 bit on a Dell Vostro 200 machine. I believe I have an accessory display adapter card and not using the on board video.
The machine works fine except when I resume after a suspend, the display shows large graphic shapes and patterns, not the expected graphics.
I have to shut the power off to be able to restart as I can't see anything useful on the display.

This is what the System Settings show for graphics.

Gallium 0.4 on AMD RV710

What do I need to do to be able to resume?

---

### Post by pme 72 on 2015-05-10
Hi aknjusa, there is a bug report on Launchpad regarding resume from suspend issues with an [AMD/ATI] RV710/M92 [Mobility Radeon HD 4530/4570/545v].

[https://bugs.launchpad.net/dri/+bug/1319589](https://bugs.launchpad.net/dri/+bug/1319589)

To see the name of your active graphics adapter run:

lspci -nn | grep VGA

in a terminal window.

Do you know if you have a workable desktop with your on board video?

My HD4550 video card has some issues with resume from suspend but since a motherboard failure/replacement I have been using the graphics chip on the new motherboard.

---

### Post by aknjusa on 2015-05-10
On resume, I get a black screen on a Dell Latitude  D620 laptop, too.
The command indicated above shows
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)

I have the native VGA adapter on the desktop and it may work but I am not going to switch to that.

Thanks

---

### Post by aknjusa on 2015-06-04
Here is the lspci output.

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV710 [Radeon HD 4350/4550] (prog-if 00 [VGA controller])
	Subsystem: Micro-Star International Co., Ltd. [MSI] R4350 MD512H (MS-V161)
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fdde0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at ce00 [size=256]
	[virtual] Expansion ROM at fdd00000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Kernel driver in use: radeon

---

### Post by webmanoffesto on 2015-06-04
I'm having the same problem. I've been struggling with this one for a while. I have my ASUS K55A Laptop set to "no hibernate" only "suspend". However, after I close the laptop lid, I still get a black screen. The weird thing is sometimes, after a hard reboot, on the first resume-after-lid-close it DOES resume, however on the second resume-after-lid-close I get a black screen. Also, there are times when I have a YouTube movie playing, and on a resume-after-lid-close which gives me a black screen I can hear the YouTube video playing ("behind" the black screen).

Asus K55A Laptop
Ubuntu 14.04.2 LTS Gnome
.---------------.

When did CTRL + ALT + F1 I got a login prompt. I entered username and password, and then received the appropriate user prompt. Then I did CTRL + ALT + F7 and was presented with the Black Screen.

It's a Black Screen with a Glow, and if I press Fn-F7 (screen off) the glow shuts off.
This is the same as when I Reboot and Login, I then see that glowing-black-screen, and then the purplish Gnome Desktop appears.

Since it's a glowing-black-screen that tells me the screen is not off, it is on and "showing me" a black or blank image.
.---------------.

tom@Toms-Laptop-K55A:~$ uname -a
Linux Toms-Laptop-K55A 3.13.0-53-generic #89-Ubuntu SMP Wed May 20 10:34:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
tom@Toms-Laptop-K55A:~$ 


tom@Toms-Laptop-K55A:~$ sudo systool -m i915 -av
Module = "i915"

  Attributes:
    coresize            = "784123"
    initsize            = "0"
    initstate           = "live"
    refcnt              = "3"
    srcversion          = "EAE574025ED8FCDDFFC9401"
    taint               = ""
    uevent              = <store method only>

  Parameters:
    disable_power_well  = "1"
    enable_hangcheck    = "Y"
    enable_ips          = "1"
    enable_pc8          = "1"
    enable_psr          = "0"
    fastboot            = "N"
    fbpercrtc           = "0"
    i915_enable_fbc     = "-1"
    i915_enable_ppgtt   = "-1"
    i915_enable_rc6     = "-1"
    invert_brightness   = "0"
    lvds_channel_mode   = "0"
    lvds_downclock      = "0"
    lvds_use_ssc        = "-1"
    modeset             = "-1"
    panel_ignore_lid    = "1"
    pc8_timeout         = "5000"
    powersave           = "1"
    prefault_disable    = "N"
    preliminary_hw_support= "1"
    reset               = "Y"
    semaphores          = "-1"
    vbt_sdvo_panel_type = "-1"

  Sections:
    .altinstr_replacement= "0xffffffffa0155d41"
    .altinstructions    = "0xffffffffa017902c"
    .bss                = "0xffffffffa017db40"
    .data               = "0xffffffffa017a000"
    .data..read_mostly  = "0xffffffffa017bfc0"
    .data.unlikely      = "0xffffffffa017c8e0"
    .exit.text          = "0xffffffffa0154beb"
    .fixup              = "0xffffffffa0155e3f"
    .gnu.linkonce.this_module= "0xffffffffa017d8e0"
    .init.text          = "0xffffffffa019b000"
    .note.gnu.build-id  = "0xffffffffa0156000"
    .parainstructions   = "0xffffffffa01780b8"
    .ref.data           = "0xffffffffa017c9c0"
    .rodata             = "0xffffffffa0156100"
    .rodata.str1.1      = "0xffffffffa016f560"
    .rodata.str1.8      = "0xffffffffa0164de8"
    .smp_locks          = "0xffffffffa0178df0"
    .strtab             = "0xffffffffa01ae780"
    .symtab             = "0xffffffffa019c000"
    .text               = "0xffffffffa00da000"
    .text.unlikely      = "0xffffffffa0154c04"
    __bug_table         = "0xffffffffa01787b4"
    __ex_table          = "0xffffffffa01793a8"
    __jump_table        = "0xffffffffa017c010"
    __kcrctab_gpl       = "0xffffffffa01560b0"
    __ksymtab_gpl       = "0xffffffffa0156030"
    __ksymtab_strings   = "0xffffffffa0179857"
    __mcount_loc        = "0xffffffffa01756b8"
    __param             = "0xffffffffa01753d8"
    __tracepoints_ptrs  = "0xffffffffa0179490"
    __tracepoints_strings= "0xffffffffa0179560"
    __tracepoints       = "0xffffffffa017d200"
    __verbose           = "0xffffffffa017d878"
    _ftrace_events      = "0xffffffffa017c8f0"
.---------------.



tom@Toms-Laptop-K55A:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3839       3733        105        138        170        913
-/+ buffers/cache:       2649       1189
Swap:         3909          0       3909
tom@Toms-Laptop-K55A:~$ 

.---------------.

Graphics Card
lspci | http VGA
VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
.---------------.

tom@Toms-Laptop-K55A:~$ /usr/lib/nux/unity_support_test --print
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile
OpenGL version string:  3.0 Mesa 10.1.3
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
.---------------.

tom@Toms-Laptop-K55A:~$ sudo lshw -C video
[sudo] password for tom:
*-display               
description: VGA compatible controller
product: 3rd Gen Core processor Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 09
width: 64 bits
clock: 33MHz
capabilities: msi pm vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:47 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
.---------------.

Pastebin Diagnostic Files:

1. X.org log file pasted here
[http://pastebin.com/Yze9P1Rt](http://pastebin.com/Yze9P1Rt)

2. pm-suspend.log. pasted here [http://pastebin.com/w20SZ3N2](http://pastebin.com/w20SZ3N2)

3. Output of: sudo systool -m i915 -av
[http://pastebin.com/X3YKB7zW](http://pastebin.com/X3YKB7zW) y
.---------------.

Is it significant that it's a Black Screen with a Glow, and if I press Fn-F7 (screen off) the glow shuts off?

.---------------.

Output of: sudo systool -m i915 -av
[http://pastebin.com/X3YKB7zW](http://pastebin.com/X3YKB7zW)

.---------------.

---

### Post by aknjusa on 2015-06-04
On a Dell Latitude 620 laptop, closing and opening the lcd gets a black screen but there is the Fn key and the blue screen like icon key (#6 or #7) and its combination restores the screen.

---

### Post by webmanoffesto on 2015-06-04
> **aknjusa said:**
> On a Dell Latitude 620 laptop, closing and opening the lcd gets a black screen but there is the Fn key and the blue screen like icon key (#6 or #7) and its combination restores the screen.

When I did CTRL + ALT + F1 I got a login prompt. I entered username and password, and then received the appropriate user prompt. Then I did CTRL + ALT + F7 and was presented with the Black Screen.

It's a Black Screen with a Glow, and if I press Fn-F7 (screen off) the glow shuts off.
This is the same as when I Reboot and Login, I then see that glowing-black-screen, and then the purplish Gnome Desktop appears.

Since it's a glowing-black-screen that tells me the screen is not off, it is on and "showing me" a black or blank image.

---

### Post by webmanoffesto on 2015-06-07
Do you think this could fix the problem?

Workaround A: Non-graphical Boot
You can disable the graphical bootscreen via:
    set gfxpayload=text 
[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)

How would I do that?
Does that make a non-graphical boot, or a non-graphical session (like without the Ubuntu Gnome graphical user interace)?

---

