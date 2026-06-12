---
title: "HP Folio 13 running hot on 12.10"
date: 2012-11-18
forum: General Help
---

### Post by LilLZ on 2012-11-18
Hello. I started talking about this on my previous thread, but since that wasn't on the same topic I decided to try here. I am running 12.10 on my HP folio 13 and it is running hot on idle. My two cores are at about 67-70C at idle.  The fan is running and its still fairly hot. I'v already customized my /etc/modprobe.d/i915.conf to look like this: options i915 i915_enable_rc6=0 lvds_downclock=1


I need rc6 off because it causes my laptop to not suspend correctly and lvds is supposed to lower heat of the cpu... What can I try now?

Current Info:
temp1 77C
Physical id 0 76C
Core 0 72C
Core 1 70C
and the cpu usage is at 1%

The max the top three have reached is 82C...

---

### Post by LilLZ on 2012-11-18
I know bumping is bad but its the only way I have ever received help on here so... This really needs to be fixed so please help..

---

### Post by idoitprone on 2012-11-18
> **LilLZ said:**
> I know bumping is bad but its the only way I have ever received help on here so... This really needs to be fixed so please help..

i think it is not working on /etc/modprobe.d

try to add it to 

/etc/default/grub


see this line

```
GRUB_CMDLINE_LINUX="quiet splash"
```change to
```
GRUB_CMDLINE_LINUX="quiet splash  i915.lvds_downclock=1 i915.i915_enable_fbc=1"
```add it there

then```
 sudo update-grub
``````
lspci -nnk
```i have to make sure you dont have a descrete graphic card

if that does not work then i wonder if forcing the apci will work

---

### Post by LilLZ on 2012-11-19
> **idoitprone said:**
> i think it is not working on /etc/modprobe.d

try to add it to 

/etc/default/grub


see this line

```
GRUB_CMDLINE_LINUX="quiet splash"
```change to
```
GRUB_CMDLINE_LINUX="quiet splash  i915.lvds_downclock=1 i915.i915_enable_fbc=1"
```add it there

then```
 sudo update-grub
``````
lspci -nnk
```i have to make sure you dont have a descrete graphic card

if that does not work then i wonder if forcing the apci will work

Ok I added it
Results of lspci:
```
tom@tom:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
	Subsystem: Hewlett-Packard Company Device [103c:1899]
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
	Subsystem: Hewlett-Packard Company Device [103c:1899]
	Kernel driver in use: i915
	Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:1899]
	Kernel driver in use: mei
	Kernel modules: mei
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:1899]
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:1899]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 [8086:1c18] (rev b4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:1899]
	Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:1899]
	Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:1899]
	Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:1899]
	Kernel modules: i2c-i801
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Hewlett-Packard Company Device [103c:1899]
	Kernel driver in use: r8169
	Kernel modules: r8169
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [8086:008b] (rev 34)
	Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN [8086:5315]
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:1899]
	Kernel driver in use: rts_pstor
	Kernel modules: rts_pstor
09:00.0 USB controller [0c03]: Fresco Logic Device [1b73:1009] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:1899]
	Kernel driver in use: xhci_hcd

```
 

I also installed Jupiter, which seems to be helping but the CPU is still running at around 68C which seems a bit hot. I'll let this run for awhile at idle and see if it helps.

Update: So I think it worked... its odd though.. It idles for awhile at about 63C then rises to 70C then drops back to like 60C and stays like that... Hmm

---

### Post by idoitprone on 2012-11-19
> **LilLZ said:**
> Ok I added it
Results of lspci:
```
tom@tom:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
    Subsystem: Hewlett-Packard Company Device [103c:1899]
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
    Subsystem: Hewlett-Packard Company Device [103c:1899]
    Kernel driver in use: i915
    Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:1899]
    Kernel driver in use: mei
    Kernel modules: mei
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:1899]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:1899]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 [8086:1c18] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:1899]
    Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:1899]
    Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:1899]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:1899]
    Kernel modules: i2c-i801
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:1899]
    Kernel driver in use: r8169
    Kernel modules: r8169
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [8086:008b] (rev 34)
    Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN [8086:5315]
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1899]
    Kernel driver in use: rts_pstor
    Kernel modules: rts_pstor
09:00.0 USB controller [0c03]: Fresco Logic Device [1b73:1009] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1899]
    Kernel driver in use: xhci_hcd

```I also installed Jupiter, which seems to be helping but the CPU is still running at around 68C which seems a bit hot. I'll let this run for awhile at idle and see if it helps.

Update: So I think it worked... its odd though.. It idles for awhile at about 63C then rises to 70C then drops back to like 60C and stays like that... Hmm


then i guess add 

```
acpi=force
``````
GRUB_CMDLINE_LINUX="quiet splash  i915.lvds_downclock=1 i915.i915_enable_fbc=1"
```change to
```
GRUB_CMDLINE_LINUX="quiet splash  i915.lvds_downclock=1 i915.i915_enable_fbc=1 acpi=force"
``````
sudo update-grub
```if that does not work then install the lastest kernel by ubuntu

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/)


use this to diagnosis powerusage 
```
sudo apt-get install powertop

sudo powertop
```

---

### Post by LilLZ on 2012-11-19
> **idoitprone said:**
> then i guess add 

```
acpi=force
``````
GRUB_CMDLINE_LINUX="quiet splash  i915.lvds_downclock=1 i915.i915_enable_fbc=1"
```change to
```
GRUB_CMDLINE_LINUX="quiet splash  i915.lvds_downclock=1 i915.i915_enable_fbc=1 acpi=force"
``````
sudo update-grub
```if that does not work then install the lastest kernel by ubuntu

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/)


use this to diagnosis powerusage 
```
sudo apt-get install powertop

sudo powertop
```

I actually just realized I put them on the wrong bit. I did it on GRUB_CMDLINE_LINUX_DEFAULT because thats where quiet splash is on my. I have acpi_backlight=vendor on the one you are talking about so I guess that replaced quiet splash. I'll add these to the correct line and see what happens..

Update: Well not sure if its working.. When running chrome it goes to about 65C and idle its at about 59-60C...
This is my grub:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_backlight=vendor i915.lvds_downclock=1 i915.i915_enable_fbc=1 acpi=force"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```


and this is the results of powertop
```
Summary: 706.6 wakeups/second,  84.4 GPU ops/seconds, 0.0 VFS ops/sec and 10.2%

                Usage       Events/s    Category       Description
             21.4 ms/s     166.8        Process        compiz
              6.2 ms/s     147.2        Process        /opt/google/chrome/chrome
            100.0%                      Device         Audio codec hwC0D0: IDT
            100.0%                      Device         Audio codec hwC0D3: Intel
             14.0 ms/s      62.8        Process        psensor
              1.0 ms/s      81.5        Interrupt      PS/2 Touchpad / Keyboard
              1.4 ms/s      62.8        Interrupt      [48] i915
              9.4 ms/s      55.9        Process        /opt/google/chrome/chrome
              5.2 ms/s      45.1        Process        gnome-terminal
             20.9 ms/s      22.6        Process        /usr/bin/X :0 -core -auth
              3.8 ms/s      19.6        Process        /usr/lib/unity/unity-pane
            331.2 µs/s      20.6        Timer          hrtimer_wakeup
             95.1 µs/s      17.7        kWork          intel_unpin_work_fn
            309.5 µs/s      14.7        Process        syndaemon -i 2.0 -K -R -t
            297.8 µs/s      12.8        Timer          tick_sched_timer
            396.0 µs/s      10.8        Interrupt      [6] tasklet(softirq)
            316.8 µs/s       8.8        Interrupt      [7] sched(softirq)


```

Also... Why are these forums so incredibly, mind numbingly slow?

---

### Post by idoitprone on 2012-11-19
> **LilLZ said:**
> Also... Why are these forums so incredibly, mind numbingly slow?
Did you update grub?

I  cant seem to figure out your problem. I will recommend updating the to the latest kernel for better support. I use cutting edge distros so I get the proper hardware support. 

Compiz and Chrome is waking your computer often
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1054088](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1054088)
[https://bugs.launchpad.net/ubuntu-power-consumption/+bug/917210](https://bugs.launchpad.net/ubuntu-power-consumption/+bug/917210)
Perhaps compiz is  the issue?
try and download a different environment such as xfce and to test it

These forums are slow because November is not exactly a month that people have free time to help people with their problems. Sometimes problems actually require some distinct experience. This mean less volunteers are able to give the proper advice.

It is difficult for me because sometimes I have to help debug hardware that I would never buy because of those issues. These days I buy amd because Intel quality is not really the greatest for linux anymore

---

### Post by LilLZ on 2012-11-20
Yeah I update grub... I'll try the new kernel and xfce. What I meant by slow is not the responses (although they are few currently) but 70% of the time the forums simply won't load at all. I really appreciate your help so far. Can you recommend a nice tutorial to update to that kernel? I tried to update to kernel 3.6.6 but it didn't support my screen so I reverted back...

---

### Post by idoitprone on 2012-11-21
> **LilLZ said:**
> Yeah I update grub... I'll try the new kernel and xfce. What I meant by slow is not the responses (although they are few currently) but 70% of the time the forums simply won't load at all. I really appreciate your help so far. Can you recommend a nice tutorial to update to that kernel? I tried to update to kernel 3.6.6 but it didn't support my screen so I reverted back...

ubuntu load instantly

I have 7 Mbps in America - this value inclues tcp/ip overhead


You have to use Ubuntu kernels

[http://packages.ubuntu.com/quantal/kernel/](http://packages.ubuntu.com/quantal/kernel/)

Configuring kernel is not easy.
If you want to compile to latest then
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
that is the guide

---

### Post by LilLZ on 2012-11-26
Ok I'll just stick with this kernel. Anyways, I haven't gotten to try xfce yet, but I'll do that soon. I'm also fairly certain its my graphics chip causing the heat, since the cpu isn't being used that much.

---

