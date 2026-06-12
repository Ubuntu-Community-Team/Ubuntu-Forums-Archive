---
title: "Boot errors/issues with modprobe?"
date: 2014-02-11
forum: General Help
---

### Post by IPvFletch on 2014-02-11
So I just went through an order getting my Ubuntu 12.04 LTS x64 server booting again - reinstalling grub (the hard way) - here's a link for more details but Bashing_Om was a tremendous help and got me through it!

[http://ubuntuforums.org/showthread.php?t=2204826&page=4](http://ubuntuforums.org/showthread.php?t=2204826&page=4)

But now that's booting again, I did a whole bunch of boot/reboots on it, to make sure it keeps coming up. Well, wouldn't you know after maybe a dozen or so reboots, it actually failed to boot again. Just once (it came up again right after a hard reboot). but I see some things in the boot msgs which concern me, and I'm trying to do a full root-cause analysis on this.. Your help is appreciated!

Here's the boot msg when it didn't fully boot. Looks to me like it is having problems probing the HW. I found some other Ubuntu threads saying modprobe has bugs with some BIOSs and certain Broadcomm NICs (of which I don't have any)... Any ideas here?

```
                                                                          fsck from util-linux 2.20.1/dev/sda1: clean, 103270/30269440 files, 2886315/121048064 blocks


[    6.634342][COLOR=#ff0000] BUG: unable to handle kernel NULL pointer dereference at 0000000000000065[/COLOR]
[    6.636002] IP: [<ffffffffa014cfd5>] ReadVBIOSTablData+0x22/0x3d4 [xgifb]
[    6.636002] PGD 10fc8e067 PUD 10e4e2067 PMD 0
[    6.636002] Oops: 0000 [#1] SMP
[    6.636002] CPU 2
[    6.636002] Modules linked in: xgifb(C+) mac_hid i3000_edac serio_raw lp edac_core parport btrfs zlib_deflate libcrc32c e1000e igb dca
[    6.636002]
[    6.636002] Pid: 483, comm: [COLOR=#ff0000]modprobe Tainted[/COLOR]: G         C   3.2.0-58-generic #88-Ubuntu Juniper Networks SA 6500/PDSMP-JN1
[    6.636002] RIP: 0010:[<ffffffffa014cfd5>]  [<ffffffffa014cfd5>] ReadVBIOSTablData+0x22/0x3d4 [xgifb]
[    6.636002] RSP: 0018:ffff88010e967828  EFLAGS: 00010246
[    6.636002] RAX: 0000000000000000 RBX: ffff88011067c428 RCX: 000000000003ffff
[    6.636002] RDX: 0000000000000000 RSI: ffff88010e967848 RDI: 0000000000000031
[    6.636002] RBP: ffff88010e967828 R08: 000000000003ffff R09: 0000000000000000
[    6.636002] R10: 0000000000000000 R11: 0000000000000000 R12: ffff88011067c430
[    6.636002] R13: ffff880110016000 R14: ffff88011067c428 R15: 0000000000000000
[    6.636002] FS:  00007fcd65ac6700(0000) GS:ffff880117d00000(0000) knlGS:0000000000000000
[    6.636002] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[    6.636002] CR2: 0000000000000065 CR3: 000000010d2a6000 CR4: 00000000000006e0
[    6.636002] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[    6.636002] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[    6.636002] Process modprobe (pid: 483, threadinfo ffff88010e966000, task ffff88010ee99700)
[    6.636002] Stack:
[    6.636002]  ffff88010e967bf8 ffffffffa013f3cf 0000000000000010 0000000000000001
[    6.636002]  00000000ffffff00 0000000000007044 0000000000007054 0000000000007040
[    6.636002]  000000000000704e 0000000000007042 00000000000284d0 000000000000704a
[    6.636002] Call Trace:
[    6.636002]  [<ffffffffa013f3cf>] XGIInitNew+0x1ef/0xad0 [xgifb]
[    6.636002]  [<ffffffff81310000>] ? ida_get_new_above+0x2f0/0x310
[    6.636002]  [<ffffffff81318289>] ? put_dec+0x59/0x60
[    6.636002]  [<ffffffff8131a3ac>] ? vsnprintf+0x35c/0x600
[    6.636002]  [<ffffffff8103ec59>] ? default_spin_lock_flags+0x9/0x10
[    6.636002]  [<ffffffffa0150034>] xgifb_probe+0x531/0xf24 [xgifb]
[    6.636002]  [<ffffffff8103ec59>] ? default_spin_lock_flags+0x9/0x10
[    6.636002]  [<ffffffff8103ec59>] ? default_spin_lock_flags+0x9/0x10
[    6.636002]  [<ffffffff813386dc>] local_pci_probe+0x5c/0xd0
[    6.636002]  [<ffffffff81339fd9>] __pci_device_probe+0xf9/0x100
[    6.636002]  [<ffffffff81310efa>] ? kobject_get+0x1a/0x30
[    6.636002]  [<ffffffff8133a01a>] pci_device_probe+0x3a/0x60
[    6.636002]  [<ffffffff813fa3c8>] really_probe+0x68/0x190
[    6.636002]  [<ffffffff813fa655>] driver_probe_device+0x45/0x70
[    6.636002]  [<ffffffff813fa72b>] __driver_attach+0xab/0xb0
[    6.636002]  [<ffffffff813fa680>] ? driver_probe_device+0x70/0x70
[    6.636002]  [<ffffffff813fa680>] ? driver_probe_device+0x70/0x70
[    6.636002]  [<ffffffff813f94b4>] bus_for_each_dev+0x64/0xa0
[    6.636002]  [<ffffffff813fa18e>] driver_attach+0x1e/0x20
[    6.636002]  [<ffffffff813f9de0>] bus_add_driver+0x1a0/0x270
[    6.636002]  [<ffffffffa0160353>] ? XGIfb_setup+0x309/0x309 [xgifb]
[    6.636002]  [<ffffffff813fac96>] driver_register+0x76/0x140
[    6.636002]  [<ffffffffa0160353>] ? XGIfb_setup+0x309/0x309 [xgifb]
[    6.636002]  [<ffffffff81339cb6>] __pci_register_driver+0x56/0xd0
[    6.636002]  [<ffffffffa0160353>] ? XGIfb_setup+0x309/0x309 [xgifb]
[    6.636002]  [<ffffffffa016039f>] xgifb_init+0x4c/0xcad [xgifb]
[    6.636002]  [<ffffffff81002040>] do_one_initcall+0x40/0x180
[    6.636002]  [<ffffffff810a9d8e>] sys_init_module+0xbe/0x230
[    6.636002]  [<ffffffff8166a3c2>] system_call_fastpath+0x16/0x1b
[    6.636002] Code: 5c 41 5d 41 5e 41 5f 5d c3 55 48 89 e5 66 66 66 66 90 48 8b 96 e0 00 00 00 83 ff 31 0f 85 b9 03 00 00 66 c7 86 b8 00 00 00 00 00 <8a> 42 65 a8 01 0f 84 a5 03 00 00 66 c7 86 b8 00 00 00 01 00 8a
[    6.636002] RIP  [<ffffffffa014cfd5>] ReadVBIOSTablData+0x22/0x3d4 [xgifb]
[    6.636002]  RSP <ffff88010e967828>
[    6.636002] CR2: 0000000000000065
[   11.099306] sched: RT throttling activated
[   11.099417] ---[ end trace 4e829516194c0aff ]---
[COLOR=#ff0000]IT GOT STUCK HERE[/COLOR]

```

Here's the following boot msgs - note similar errors, but it DID boot up fully and it outputs these same logs every time it successfully boots up.. Are these real (HW?) problems or just noise?

```
                              fsck from util-linux 2.20.1                   ³/dev/sda1: clean, 103270/30269440 files, 2886315/121048064 blocks           ³
 ³                                                                          ³
[    6.689994] [COLOR=#ff0000]BUG: unable to handle kernel NULL pointer dereference at 0000000000000065[/COLOR]
[    6.719709] IP: [<ffffffffa014dfd5>] ReadVBIOSTablData+0x22/0x3d4 [xgifb]³
[    6.719709] PGD 10f823067 PUD 10c36b067 PMD 0                            ³
[    6.719709] Oops: 0000 [#1] SMP ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÙ
[    6.719709] CPU 1
[    6.719709] Modules linked in: xgifb(C+) mac_hid i3000_edac serio_raw lp parport edac_core btrfs zlib_deflate libcrc32c e1000e igb dcahe selected OS, 'e' to edit the commands
[    6.719709] oting or 'c' for a command-line.
[    6.719709] Pid: 478, comm: [COLOR=#ff0000]modprobe Tainted[/COLOR]: G         C   3.2.0-58-generic #88-Ubuntu Juniper Networks SA 6500/PDSMP-JN1
[    6.719709] RIP: 0010:[<ffffffffa014dfd5>]  [<ffffffffa014dfd5>] ReadVBIOSTablData+0x22/0x3d4 [xgifb]
[    6.719709] RSP: 0018:ffff88010f82d828  EFLAGS: 00010246
[    6.719709] RAX: 0000000000000000 RBX: ffff880110452428 RCX: 000000000003ffff
[    6.719709] RDX: 0000000000000000 RSI: ffff88010f82d848 RDI: 0000000000000031
[    6.719709] RBP: ffff88010f82d828 R08: 000000000003ffff R09: 0000000000000000
[    6.719709] R10: 0000000000000000 R11: 0000000000000000 R12: ffff880110452430
[    6.719709] R13: ffff880110015000 R14: ffff880110452428 R15: 0000000000000000
[    6.719709] FS:  00007f9672b7a700(0000) GS:ffff880117c80000(0000) knlGS:0000000000000000
[    6.719709] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[    6.719709] CR2: 0000000000000065 CR3: 000000010eab9000 CR4: 00000000000006e0
[    6.719709] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[    6.719709] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[    6.719709] Process modprobe (pid: 478, threadinfo ffff88010f82c000, task ffff88010d104500)
[    6.719709] Stack:
[    6.719709]  ffff88010f82dbf8 ffffffffa01403cf 0000000000000010 0000000000000001
[    6.719709]  00000000ffffff00 0000000000007044 0000000000007054 0000000000007040
[    6.719709]  000000000000704e 0000000000007042 00000000000284d0 000000000000704a
[    6.719709] Call Trace:
[    6.719709]  [<ffffffffa01403cf>] XGIInitNew+0x1ef/0xad0 [xgifb]
[    6.719709]  [<ffffffff810a3618>] ? smp_call_function_many+0x1f8/0x280
[    6.719709]  [<ffffffff81040000>] ? set_up_gart_resume+0x10/0x20
[    6.719709]  [<ffffffff81318289>] ? put_dec+0x59/0x60
[    6.719709]  [<ffffffff8131a3ac>] ? vsnprintf+0x35c/0x600
[    6.719709]  [<ffffffff8103ec59>] ? default_spin_lock_flags+0x9/0x10
[    6.719709]  [<ffffffffa0151034>] xgifb_probe+0x531/0xf24 [xgifb]
[    6.719709]  [<ffffffff8103ec59>] ? default_spin_lock_flags+0x9/0x10
[    6.719709]  [<ffffffff8103ec59>] ? default_spin_lock_flags+0x9/0x10
[    6.719709]  [<ffffffff813386dc>] local_pci_probe+0x5c/0xd0
[    6.719709]  [<ffffffff81339fd9>] __pci_device_probe+0xf9/0x100
[    6.719709]  [<ffffffff81310efa>] ? kobject_get+0x1a/0x30
[    6.719709]  [<ffffffff8133a01a>] pci_device_probe+0x3a/0x60
[    6.719709]  [<ffffffff813fa3c8>] really_probe+0x68/0x190
[    6.719709]  [<ffffffff813fa655>] driver_probe_device+0x45/0x70
[    6.719709]  [<ffffffff813fa72b>] __driver_attach+0xab/0xb0
[    6.719709]  [<ffffffff813fa680>] ? driver_probe_device+0x70/0x70
[    6.719709]  [<ffffffff813fa680>] ? driver_probe_device+0x70/0x70
[    6.719709]  [<ffffffff813f94b4>] bus_for_each_dev+0x64/0xa0
[    6.719709]  [<ffffffff813fa18e>] driver_attach+0x1e/0x20
[    6.719709]  [<ffffffff813f9de0>] bus_add_driver+0x1a0/0x270
[    6.719709]  [<ffffffffa0161353>] ? XGIfb_setup+0x309/0x309 [xgifb]
[    6.719709]  [<ffffffff813fac96>] driver_register+0x76/0x140
[    6.719709]  [<ffffffffa0161353>] ? XGIfb_setup+0x309/0x309 [xgifb]
[    6.719709]  [<ffffffff81339cb6>] __pci_register_driver+0x56/0xd0
[    6.719709]  [<ffffffffa0161353>] ? XGIfb_setup+0x309/0x309 [xgifb]
[    6.719709]  [<ffffffffa016139f>] xgifb_init+0x4c/0xcad [xgifb]
[    6.719709]  [<ffffffff81002040>] do_one_initcall+0x40/0x180
[    6.719709]  [<ffffffff810a9d8e>] sys_init_module+0xbe/0x230
[    6.719709]  [<ffffffff8166a3c2>] system_call_fastpath+0x16/0x1b
[    6.719709] Code: 5c 41 5d 41 5e 41 5f 5d c3 55 48 89 e5 66 66 66 66 90 48 8b 96 e0 00 00 00 83 ff 31 0f 85 b9 03 00 00 66 c7 86 b8 00 00 00 00 00 <8a> 42 65 a8 01 0f 84 a5 03 00 00 66 c7 86 b8 00 00 00 01 00 8a
[    6.719709] RIP  [<ffffffffa014dfd5>] ReadVBIOSTablData+0x22/0x3d4 [xgifb]
[    6.719709]  RSP <ffff88010f82d828>
[    6.719709] CR2: 0000000000000065
[   11.232059] sched: RT throttling activated
[   11.232152] ---[ end trace 8f85c102eea859db ]---
[   11.359533] leds_ss4200: no LED devices found
[   11.412329] device-mapper: multipath: version 1.3.1 loaded
[COLOR=#ff0000]udevd[415]: '/sbin/modprobe -bv pci:v000018CAd00000020sv000015D9sd0000AE80bc03sc00i00' [478] terminated by signal 9 (Killed)[/COLOR]


[   12.252855] type=1400 audit(1392147409.661:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=813 comm="apparmor_parser"
[   12.406249] type=1400 audit(1392147409.813:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=814 comm="apparmor_parser"
[   12.562506] type=1400 audit(1392147409.969:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=813 comm="apparmor_parser"
[   12.747858] type=1400 audit(1392147410.153:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=814 comm="apparmor_parser"
[   12.936318] type=1400 audit(1392147410.345:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=812 comm="apparmor_parser"
[   13.092527] type=1400 audit(1392147410.501:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=806 comm="apparmor_parser"
[   13.248725] type=1400 audit(1392147410.657:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=810 comm="apparmor_parser"
[   13.404924] type=1400 audit(1392147410.813:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=806 comm="apparmor_parser"
[   13.593413] type=1400 audit(1392147411.001:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=813 comm="apparmor_parser"
[   13.774580] type=1400 audit(1392147411.185:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=814 comm="apparmor_parser"
[   14.588250] e1000e 0000:11:00.0: irq 64 for MSI/MSI-X
[   14.704096] e1000e 0000:11:00.0: irq 64 for MSI/MSI-X
[   14.726631] init: udev-fallback-graphics main process (905) terminated with status 1
[   14.858345] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.780905] Loading iSCSI transport class v2.0-870.
[   15.917466] iscsi: registered transport (tcp)
[   16.226034] iscsi: registered transport (iser)
[   16.322140] iscsid (1001): /proc/1001/oom_adj is deprecated, please use /proc/1001/oom_score_adj instead.
[   16.713579] Bluetooth: Core ver 2.16
[   16.756433] NET: Registered protocol family 31
[   16.809654] Bluetooth: HCI device and connection manager initialized
[   16.885792] Bluetooth: HCI socket layer initialized
[   16.944232] Bluetooth: L2CAP socket layer initialized
[   17.004777] Bluetooth: SCO socket layer initialized
[   17.064159] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   17.154880] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.155386] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   17.287369] Bluetooth: BNEP filters: protocol multicast
[   17.287385] Bluetooth: RFCOMM TTY layer initialized
[   17.287389] Bluetooth: RFCOMM socket layer initialized
[   17.287391] Bluetooth: RFCOMM ver 1.11
[COLOR=#0000ff]FROM HERE MY NORMAL SERVICES START LOADING...[/COLOR]

```

---

### Post by IPvFletch on 2014-02-11
Trying to debug this further, just in case... I ran lspci -vkn and got a lot of PCI output. This is the only one which seems remotely close, so is the issue my VGA port?  Or are these alphanumeric ID chars just a total coincidence?

Error seen during boot:
```
[COLOR=#FF0000][FONT=Ubuntu Mono]udevd[415]: '/sbin/modprobe -bv pci:v0000**18CA**d0000**0020**sv0000**15D9**sd0000**AE80**bc03sc00i00' [478] terminated by signal 9 (Killed)[/FONT][/COLOR]
```

lspci output excerpt:
```

14:04.0 0300: **18ca:0020** (prog-if 00 [VGA controller])
        Subsystem: **15d9:ae80**
        Flags: 66MHz, medium devsel
        BIST result: 00
        Memory at ee000000 (32-bit, prefetchable) [size=32M]
        Memory at ec600000 (32-bit, non-prefetchable) [size=256K]
        I/O ports at 7000 [size=128]
        Capabilities: [40] Power Management version 2
        Kernel driver in use: xgifb
        Kernel modules: xgifb, sisfb

```

It resembles the ID in the error above, right??

If this IS a match, is this a problem or not?  Note: I'm not using the VGA port, but there is one (and it works). I'm using the Serial Console...

Thoughts???

Am I just shooting in the dark here?   :D

BTW, this is my Motherboard: [http://www.supermicro.com/products/motherboard/PD/E7230/PDSMP-i.cfm](http://www.supermicro.com/products/motherboard/PD/E7230/PDSMP-i.cfm)

---

### Post by IPvFletch on 2014-02-11
Any more ideas on this??  Just want to help thwart potential HW issues before they cause more pain..

---

### Post by Bashing-om on 2014-02-12
IPvFletch; Well;

I can try and see what I can do to help:
OK, what is the graphics situation ?

specs call for radeon or fglrx drivers for ATI cards:
> 
7. On board ATI RageXL Graphics


So I have to question where this comes from:
> 
Kernel driver in use: xgifb
        Kernel modules: xgifb, sisfb

 What in the world has "sisfb" got to do with the graphics ?
Let's take a look at what is:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
And maybe draw some conclusions ?

[INDENT]got to have an interface
[INDENT][INDENT]between the operating system and the hardware
[/INDENT][/INDENT][/INDENT]

---

### Post by IPvFletch on 2014-02-12
Hey there, and thanks for the help!

```
root@lnx6500:~#[COLOR=#0000ff] lspci -nnk | grep -iA3 vga[/COLOR]
14:04.0 VGA compatible controller [0300]: XGI Technology Inc. (eXtreme Graphics Innovation) Z7/Z9 (XG20 core) [18ca:0020]
        Subsystem: Super Micro Computer Inc Device [15d9:ae80]
        Kernel driver in use: xgifb
        Kernel modules: xgifb, sisfb
```

```
root@lnx6500:~#[COLOR=#0000ff] lshw -C display[/COLOR]
  *-display
       description: VGA compatible controller
       product: Z7/Z9 (XG20 core)
       vendor: XGI Technology Inc. (eXtreme Graphics Innovation)
       physical id: 4
       bus info: pci@0000:14:04.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm vga_controller cap_list
       configuration: driver=xgifb latency=0
       resources: irq:0 memory:ee000000-efffffff memory:ec600000-ec63ffff ioport:7000(size=128)
```


Like I was saying, I don't even USE the vga port (all serial console). This is a "headless server". No keyboard/mouse either. Just serial console and SSH. That said, I wouldn't be opposed to disabling it (if indeed it IS the HW throwing modprobe errors causing other problems) but I'm not even sure that's possible and I vaguely recall many programs rely on some kind of gtk or other video libraries being loaded.

---

### Post by Bashing-om on 2014-02-12
IPvFletch; Uhhmm,

Onboard ATI graphics disabled  and using a PCI card to interface with X-server -> ssh interface ? 
While I am looking and think'n this over, What does the system have to say ?
Post the output of :
```

cat /var/log/Xorg.0.log

```
see if we can correlate "[18ca:0020]".

Edit: Is it that gfx card anyway doesn't have a dedicated xorg video driver but relies only on fbdev xorg driver.
the Xorg.0.log may give us a hint.

Dazed and confused, but there is a chance ->
[INDENT][INDENT]we will get to the bottom of this
[/INDENT][/INDENT]

---

### Post by IPvFletch on 2014-02-12
I am not using X-windows. Just SSH'ing into the server pty shells. I don't have /var/log/Xorg or anything close.

Here's all I can find in the logs which is related:
```
dmesg:[    0.380573] pci 0000:14:04.0: [18ca:0020] type 0 class 0x000300boot.log:udevd[423]: '/sbin/modprobe -bv pci:v000018CAd00000020sv000015D9sd0000AE80bc03sc00i00' [533] terminated by signal 9 (Killed)
kern.log:Feb 11 23:38:37 localhost kernel: [    0.380573] pci 0000:14:04.0: [18ca:0020] type 0 class 0x000300

```

In udev log I found:
```
KERNEL[6.529998] add      /devices/pci0000:00/0000:00:1e.0/0000:14:04.0 (pci)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:14:04.0
MODALIAS=pci:v000018CAd00000020sv000015D9sd0000AE80bc03sc00i00
PCI_CLASS=30000
PCI_ID=18CA:0020
PCI_SLOT_NAME=0000:14:04.0
PCI_SUBSYS_ID=15D9:AE80
SEQNUM=1532
SUBSYSTEM=pci
UDEV_LOG=3

...

UDEV  [11.258255] add      /devices/pci0000:00/0000:00:1e.0/0000:14:04.0 (pci)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:14:04.0
MODALIAS=pci:v000018CAd00000020sv000015D9sd0000AE80bc03sc00i00
PCI_CLASS=30000
PCI_ID=18CA:0020
PCI_SLOT_NAME=0000:14:04.0
PCI_SUBSYS_ID=15D9:AE80
SEQNUM=1532
SUBSYSTEM=pci
UDEV_LOG=3
USEC_INITIALIZED=6597506

```

Not sure if this is just a rat hole or what though.. So far no more failed boot. I've rebooted it maybe 30 times now since we fixed Grub the other night. It rebooted a few times after then hung that one time, then has booted reliably since. I also enabled the grub menu to always show up and that whitespace I was talking about, shows up AFTER the grub menu (and before the fsck). So I have to wonder if it isn't due to an fsck check/failure. I was thinking maybe my controller takes a while to initialize, so I added "rootdelay=30" to the GRUB_CMDLINE_LINUX flags, just in case...  *shrug*

Don't want to waste too much of your time if you think this vga/modprobe failur is just a rat hole..

Thanks!

---

### Post by Bashing-om on 2014-02-12
IPvFletch; Welp, Like this:

If it concerns you, it concerns me, 'till what ever.

A 1 time glitch could, of course, be any thing. I do have one other thing that has popped into my mind we might look at.

Show me the current grub index file:
```

cat /etc/default/grub

```

In the meantime, I am still looking for a means to see the relationship (graphics driver).

[INDENT]ain't no quit in
[INDENT][INDENT]my nature
[/INDENT][/INDENT][/INDENT]

---

### Post by IPvFletch on 2014-02-12
```
kfletcher@lnx6500:~/images$ [COLOR=#0000ff]cat /etc/default/grub[/COLOR]
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=4
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="rootdelay=30 console=tty0 console=ttyS0,9600"


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console


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

Here's the generated boot grub.cfg file in case it helps:
```
kfletcher@lnx6500:~/images$ [COLOR=#0000ff]cat /boot/grub/grub.cfg
[/COLOR]#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#


### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi


function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}


function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}


function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}


terminal_input console
terminal_output console
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  set timeout=4
fi
### END /etc/grub.d/00_header ###


### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###


### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
        set gfxpayload="${1}"
        if [ "${1}" = "keep" ]; then
                set vt_handoff=vt.handoff=7
        else
                set vt_handoff=
        fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-58-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set=root d8f00bf3-5736-43bc-a4b3-e5fbb2cb7191
        linux   /boot/vmlinuz-3.2.0-58-generic root=UUID=d8f00bf3-5736-43bc-a4b3-e5fbb2cb7191 ro rootdelay=30 console=tty0 console=ttyS0,960
0  quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-58-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-58-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set=root d8f00bf3-5736-43bc-a4b3-e5fbb2cb7191
        echo    'Loading Linux 3.2.0-58-generic ...'
        linux   /boot/vmlinuz-3.2.0-58-generic root=UUID=d8f00bf3-5736-43bc-a4b3-e5fbb2cb7191 ro recovery nomodeset rootdelay=30 console=tty
0 console=ttyS0,9600
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-58-generic
}
### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set=root d8f00bf3-5736-43bc-a4b3-e5fbb2cb7191
        linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set=root d8f00bf3-5736-43bc-a4b3-e5fbb2cb7191
        linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###


### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###


### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

```

---

### Post by Bashing-om on 2014-02-12
IPvFletch; Hey;

/etc/default/grub looks good to me.

However, this;
This might take some thinking about:
> 
### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
        set gfxpayload="${1}"
        if [ "${1}" = "keep" ]; then
                set vt_handoff=vt.handoff=7
        else
                set vt_handoff=
        fi

Begs the question as to why you in your server environment would ever had off to virtual terminal number 7 ?
vt.handoff=7 causes the kernel to maintain the current contents of video memory on virtual terminal 7, which is a new "transparent" VT type.

Can it possibly do any harm if left alone ?

Hey
[INDENT][INDENT]it is just a thought
[/INDENT][/INDENT]

---

### Post by IPvFletch on 2014-02-12
No clue, I am totally lost on all of this gfx and handoff stuff. So you're saying it's trying to output video to vty7, but I have nothing hooked up to vty7 (right?) so what is the point?  If so, I would agree, why bother. Maybe it has to put it somewhere because I outputted console=ttyS0, and it didn't want to just drop VGA use. I mean I guess if I ever plug a monitor into the DB-15 VGA port (it's buried inside the case, not external like usual) then I would want to see the console on that monitor. But that is hopefully never going to happen, as this is a rackmounted server anyways. Not sure what to do from here, if anything..  ??

---

### Post by Bashing-om on 2014-02-12
IPvFletch; Hey;

To be honest, I also can not read that block of code. So, I do not know what is going on here or what it might do.
Let's wait and see if the smart people will see this thread and chime in for educational purposes.

[INDENT]sometimes I do not know
[INDENT][INDENT]this is one of them
[/INDENT][/INDENT][/INDENT]

---

### Post by IPvFletch on 2014-02-12
Well and nothing is really "broken" just that modprobe error.. so hopefully it's no big deal and I just move beyond this. It's just after our grub fiasco I'm really not trusting this box 100% yet, and I'm about to load a few OpenStack instance VMs on it, so trying to really count on this, but just not sure I can yet. Time will tell.. Thanks again for your help looking at this, and sometimes no special news is good news..  :)

---

### Post by Bashing-om on 2014-02-12
IPvFletch; Hey,

Like this, vt_handoff is conditional, I just do not know what the conditions are.

Presently we are awaiting wiser heads to prevail, and all you can do is use the system and see if it holds up. And, as you say, load her up.

Maybe yes
[INDENT][INDENT]probably moreso yes
[/INDENT][/INDENT]

---

