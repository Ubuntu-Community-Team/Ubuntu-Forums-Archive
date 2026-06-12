---
title: "Loads BusyBox instead of Ubuntu"
date: 2008-04-26
forum: General Help
---

### Post by Stonebot on 2008-04-26
When I start up my computer the Wubi screen comes up and I select Ubuntu then it loads up to the splash screen loads for a tiny bit then it goes into a BusyBox thing.

I tried this but it didn't work:
> The Ubuntu splash screen loads for awhile then exits to a BusyBox/(unutramfs) prompt

Reboot and hit Esc when prompted to enter the boot menu Hit 'e' to edit the first line. Next select the second line and hit 'e' again. Input 'irqpoll' towards the end of the bootline. Then hit 'enter' and then 'b' to boot.

So from there I had no idea what else to do so I came here. does anyone know the problem and how to solve it?

Stonebot...

---

### Post by Stonebot on 2008-04-26
I Just tried reinstalling but when it reboots and you select Ubuntu so it can install, before it even installs, the BusyBox comes up again, so how do I solve this?

---

### Post by ago on 2008-04-26
At the busybox look in /casper.log for relevant error messages.

cat /casper.log

Use shift+pgup to scroll

There might be mont errors. Also

grep err /casper.log -A 3 -B 3
grep mount /casper.log -A 3 -B 3

---

### Post by Stonebot on 2008-04-26
> **ago said:**
> At the busybox look in /casper.log for relevant error messages.

cat /casper.log

Use shift+pgup to scroll

There might be mont errors. Also

grep err /casper.log -A 3 -B 3
grep mount /casper.log -A 3 -B 3

what does all this mean, i am new with linux, and never heard of busybox

---

### Post by ago on 2008-04-26
Those are commands to read the relevant log file so that you can look for error messages. The error messages will give me some hint to understand why you are having problems.

---

### Post by Stonebot on 2008-04-26
Ok, I did that and i took pictures of the screen:
[IMG]http://i154.photobucket.com/albums/s275/stonebot/DSC09447.jpg[/IMG]
[IMG]http://i154.photobucket.com/albums/s275/stonebot/DSC09448.jpg[/IMG]
What do they mean

---

### Post by shedokan on 2008-04-26
I have the same problem.

---

### Post by Stonebot on 2008-04-26
Thanks, I fixed it by shutting down windows properly then booting Ubuntu and it worked :D

Thanks

Stonebot...

---

### Post by shedokan on 2008-04-27
how do you shut down windows properly?

---

### Post by ago on 2008-04-27
Open a dos box
Go to the drive where you installed wubi and run

chkdsk /r

Then shutdown using the Windows menu, not the power button.

---

### Post by Trustpt on 2008-04-27
> **shedokan said:**
> how do you shut down windows properly?

Yeah, I wonder the same thing since I also get the BusyBox instead of Ubuntu instalation.

I tried to edit some line, adding irqpoll to the end of that line. But I got the same screen. After I removed all my USB devices (even my mouse) and again, nothing seemed to change.

---

### Post by ago on 2008-04-27
If you are in the BusyBox, please try to get error messages from the log file /casper.log

See my post above on how to do that. If you can tell me what are the errors in there, I can probably tell you what to do next ;)

---

### Post by shedokan on 2008-04-27
here are my errors from casper log(each of them shows about 5 times):
> /scripts/casper-premount/20isoscan: /scripts/casper-premount/20isoscan: 33: cannot open /dev/scd0: No medium found
> /scripts/casper-premount/30custon_installation: /scripts/casper-premount/30custon_installation: 91 :cannot open /dev/scd0: No medium found
> /init: init 1: cannot open /dev/scd0: No medium found
> unable to find a medium containing a live file system

and when I used chkdsk /r ,  it didn't move on 73%

thanks.

---

### Post by ago on 2008-04-27
can you post the content of: 

cat /proc/partitions

---

### Post by shedokan on 2008-04-27
cat /proc/partitions:
> magor minor #blocks name

after that there is nothing, just this line.

---

### Post by ago on 2008-04-27
Your hard disk/controller might not be supported what is your make and model?
You can use lspci -v for more info

---

### Post by shedokan on 2008-04-28
when I used ubuntu gutsy it did support my disk/controller, when I use the command it says:
> /bin/sh/: lspci: not found

---

### Post by ago on 2008-04-28
Can you run that as well as cat /proc/partitions after booting from Live CD?

---

### Post by shedokan on 2008-04-28
ubuntu gutsy live cd:
```
ubuntu@ubuntu:~$ cat /proc/partitions
major minor  #blocks  name

  22     0  156290904 hdc
  22     1   97281576 hdc1
  22     2   57641220 hdc2
   7     0     657224 loop0

```
```
ubuntu@ubuntu:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
        Subsystem: VIA Technologies, Inc. P4M890 Host Bridge
        Flags: bus master, medium devsel, latency 8
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
        Subsystem: VIA Technologies, Inc. P4M890 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
        Subsystem: VIA Technologies, Inc. P4M890 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
        Subsystem: VIA Technologies, Inc. P4M890 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller (prog-if 20 [IO(X)-APIC])
        Flags: bus master, fast devsel, latency 0

00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
        Flags: bus master, fast devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Capabilities: <access denied>

00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: fa900000-fe9fffff
        Prefetchable memory behind bridge: 00000000bff00000-00000000dfefffff
        Capabilities: <access denied>

00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>

00:0f.0 RAID bus controller: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at ec00 [size=8]
        I/O ports at e880 [size=4]
        I/O ports at e800 [size=8]
        I/O ports at e480 [size=4]
        I/O ports at e400 [size=16]
        I/O ports at e000 [size=256]
        Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07) (prog-if 8a [Master SecP PriP])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
        Flags: bus master, medium devsel, latency 32
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at fc00 [size=16]
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
        Flags: bus master, medium devsel, latency 64, IRQ 20
        I/O ports at dc00 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
        Flags: bus master, medium devsel, latency 64, IRQ 21
        I/O ports at d880 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at d800 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
        Flags: bus master, medium devsel, latency 64, IRQ 19
        I/O ports at d480 [size=32]
        Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at febffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
        Subsystem: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
        Flags: medium devsel
        Capabilities: <access denied>

00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
        Subsystem: VIA Technologies, Inc. Unknown device 337e
        Flags: bus master, medium devsel, latency 128
        Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
        Flags: bus master, medium devsel, latency 64, IRQ 19
        I/O ports at d000 [size=256]
        Memory at febff800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Memory behind bridge: fea00000-feafffff
        Capabilities: <access denied>

00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Capabilities: <access denied>

02:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1) (prog-if 00 [VGA])
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
        Expansion ROM at fe9e0000 [disabled] [size=128K]
        Capabilities: <access denied>

04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at feafc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

---

### Post by ago on 2008-04-28
And can you do the same with Hardy Live CD?

---

### Post by shedokan on 2008-04-28
sure, just took time to load:
> ubuntu@ubuntu:~$ cat /proc/partitions
major minor  #blocks  name

   7     0     690060 loop0

> ubuntu@ubuntu:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
	Subsystem: VIA Technologies, Inc. P4M890 Host Bridge
	Flags: bus master, medium devsel, latency 8
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>

00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
	Subsystem: VIA Technologies, Inc. P4M890 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
	Subsystem: VIA Technologies, Inc. P4M890 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
	Subsystem: VIA Technologies, Inc. P4M890 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller (prog-if 20 [IO(X)-APIC])
	Flags: bus master, fast devsel, latency 0

00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
	Flags: bus master, fast devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: <access denied>

00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: fa900000-fe9fffff
	Prefetchable memory behind bridge: 00000000bff00000-00000000dfefffff
	Capabilities: <access denied>

00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>

00:0f.0 RAID bus controller: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
	Flags: bus master, medium devsel, latency 64, IRQ 20
	I/O ports at ec00 [size=8]
	I/O ports at e880 [size=4]
	I/O ports at e800 [size=8]
	I/O ports at e480 [size=4]
	I/O ports at e400 [size=16]
	I/O ports at e000 [size=256]
	Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07) (prog-if 8a [Master SecP PriP])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
	Flags: bus master, medium devsel, latency 32
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at fc00 [size=16]
	Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at dc00 [size=32]
	Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
	Flags: bus master, medium devsel, latency 64, IRQ 19
	I/O ports at d880 [size=32]
	Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
	Flags: bus master, medium devsel, latency 64, IRQ 20
	I/O ports at d800 [size=32]
	Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at d480 [size=32]
	Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at febffc00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
	Subsystem: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
	Flags: medium devsel
	Capabilities: <access denied>

00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
	Subsystem: VIA Technologies, Inc. Unknown device 337e
	Flags: bus master, medium devsel, latency 128
	Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at d000 [size=256]
	Memory at febff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: fea00000-feafffff
	Capabilities: <access denied>

00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Capabilities: <access denied>

02:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1) (prog-if 00 [VGA controller])
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
	Expansion ROM at fe9e0000 [disabled] [size=128K]
	Capabilities: <access denied>

04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at feafc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>


---

### Post by ago on 2008-04-28
Well it seems there is a general issue with 8.04 then, since that cannot access your disks! That is nothing to do with Wubi, you might want to open a bug in launchpad!

---

### Post by shedokan on 2008-04-28
ok, but what info should I give them?

---

### Post by ago on 2008-04-28
The above is a good start!

---

### Post by shedokan on 2008-04-29
thanks for all your help, too bad my problem isn't solved.

---

### Post by ago on 2008-04-29
That is a kernel issue or a missing module in initramfs, in either case it is out of my domain and the resolution might take a bit longer, but if you file a bug in launchpad and mention it here I'll keep an eye on it.

---

### Post by Delenir on 2008-04-29
Thanks to the help in this thread, Ubuntu lives on in my home. :)  Thank you all!!

---

### Post by ago on 2008-04-29
Do you use a raid? Which one? Sotware raids (aka fakeraid) are not supported.

---

### Post by shedokan on 2008-04-29
what kernel should I choose?
there are a lot of them.
[https://bugs.launchpad.net/ubuntu/+bug/223819](https://bugs.launchpad.net/ubuntu/+bug/223819)

---

### Post by ago on 2008-04-29
Shedokan I can you use a raid

00:0f.0 RAID bus controller: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
Flags: bus master, medium devsel, latency 64, IRQ 20
I/O ports at ec00 [size=8]
I/O ports at e880 [size=4]
I/O ports at e800 [size=8]
I/O ports at e480 [size=4]
I/O ports at e400 [size=16]
I/O ports at e000 [size=256]

That is likely a software raid, and if all your hard disk are in a raid array 0 or 1, they will not be accessible. This is a known issue, as mentioned in the WubiGuide and FAQ, software raid arrays are not supported.

---

### Post by shedokan on 2008-04-29
is there a way to change it?

---

### Post by ago on 2008-04-29
Monitor dmraid/fakeraid. Wubi 7.04 or 7.10 may work. For 8.04 you would need to do a CD installation, then install dmraid and customize your initrd with it.

---

### Post by shedokan on 2008-04-29
maybe I'll use wubi7.04?
if I can't so can you tell me or give me a tutoiral to "install dmraid and customize your initrd with it"?

---

### Post by ago on 2008-04-29
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by shedokan on 2008-04-29
what I don't understand is: how have I used gutsy?

---

### Post by ago on 2008-04-29
That depends on whether the initrd contains the required modules by default or not.

---

### Post by shedokan on 2008-04-29
whta if I'll use wubi7.04 and upgrade to 8.04?

---

### Post by ago on 2008-04-29
7.04 had a custom initrd with dmraid built in

---

### Post by shedokan on 2008-04-29
I will try it for now and will wait for 8.10

---

