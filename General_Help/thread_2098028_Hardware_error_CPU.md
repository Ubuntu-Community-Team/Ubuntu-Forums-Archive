---
title: "Hardware error CPU"
date: 2012-12-25
forum: General Help
---

### Post by Axio on 2012-12-25
Hi,

My computer randomly crashed so I have investigated the problem. As I couldn't have any crashlog or traceback I had to use netconsole. Here is the result: [http://paste.ubuntu.com/1464622/](http://paste.ubuntu.com/1464622/)

My CPU is E-350. I have tried several kernels (3.2, 3.4, 3.7). I have updated my bios. I have tried to deactivate one of the two cores. It didn't solve the problem.

The bug appears randomly, but it appears quickly after I start an intensive task (in my case it was a ffmpeg conversion). If I don't start such task it could pass days or weeks before the bug occurs.

Bug with 3.7
```
[  765.772789] i2c /dev entries driver
[ 1327.785334] mce: [Hardware Error]: CPU 1: Machine Check Exception: 4 Bank 0: f600000000010015
[ 1327.789344] mce: [Hardware Error]: TSC 1f357ac28c4 ADDR b1be8000 
[ 1327.793361] mce: [Hardware Error]: PROCESSOR 2:500f10 TIME 1356277176 SOCKET 0 APIC 1 microcode 5000026
[ 1327.797362] mce: [Hardware Error]: Run the above through 'mcelog --ascii'
[ 1327.801339] mce: [Hardware Error]: Machine check: Invalid
[ 1327.805255] Kernel panic - not syncing: Fatal machine check on current CPU
```

Bug with 3.2, ffmpeg and one core deactivated:
```
[    7.250095] SP5100 TCO timer: mmio address 0xbafe00 already in use
[   23.216775] SP5100 TCO timer: mmio address 0xbafe00 already in use
[   21.184130] SP5100 TCO timer: mmio address 0xbafe00 already in use
[ 1583.874892] [Hardware Error]: CPU 0: Machine Check Exception: 4 Bank 0: b600000000010015
[ 1583.876014] [Hardware Error]: TSC 252f65ae0c8 ADDR b671d000 
[ 1583.876014] [Hardware Error]: PROCESSOR 2:500f10 TIME 1356285230 SOCKET 0 APIC 0 microcode 5000028
[ 1583.876014] [Hardware Error]: Run the above through 'mcelog --ascii'
[ 1583.876014] [Hardware Error]: Machine check: Processor context corrupt
[ 1583.876014] Kernel panic - not syncing: Fatal machine check on current CPU
[ 1583.876014] Pid: 3234, comm: ffmpeg Tainted: G   M       O 3.2.0-35-generic #55-Ubuntu
[ 1583.876014] Call Trace:
[ 1583.876014]  [<c1560f2c>] ? printk+0x2d/0x2f
[ 1583.876014]  [<c1560dfa>] panic+0x5c/0x161
[ 1583.876014]  [<c1015a0f>] mce_panic.part.14+0x13f/0x170
[ 1583.876014]  [<c1015a92>] mce_panic+0x52/0x90
[ 1583.876014]  [<c1016526>] do_machine_check+0x356/0x4f0
[ 1583.876014]  [<c10161d0>] ? mce_log+0x120/0x120
[ 1583.876014]  [<c15769a7>] error_code+0x67/0x6c
[   24.773952] SP5100 TCO timer: mmio address 0xbafe00 already in use
[   24.118978] SP5100 TCO timer: mmio address 0xbafe00 already in use
```

Before coming here I have asked on irc and I was told that my cpu was buggy and that there wasn't much I could do about it (except change it). Well I hope the guy was wrong, you tell me...

---

### Post by dino99 on 2012-12-25
this is mostly a bad bios irq setting, resulting in irq conflict, not a kernel problem.

[https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems)
[http://askubuntu.com/questions/182365/irq-conflicts-causing-video-card-and-boot-problems](http://askubuntu.com/questions/182365/irq-conflicts-causing-video-card-and-boot-problems)

if you cant change/test irq setting into your bios, then use the irqpoll boot parameter inside /etc/default/grub (set it before "quiet splash") then update grub to care of it (sudo update-grub)

note: removing "quiet splash" from the boot line, let you see the verbose booting comments to identify the possible warnings/errors.

note2: actual kernel use pae enabled (even they are called "generic" now, as pure generic kernel have been dropped now). So check that your proc is able to use pae

cat /proc/cpuinfo

if you does not see pae in the list, then your proc is not able to run recent kernel like 3.7

---

### Post by Pjotr123 on 2012-12-25
Installing the newest microcode may help (and certainly won't hurt):
[https://sites.google.com/site/easylinuxtipsproject/microcode](https://sites.google.com/site/easylinuxtipsproject/microcode)

---

### Post by Axio on 2012-12-25
> **dino99 said:**
> this is mostly a bad bios irq setting, resulting in irq conflict, not a kernel problem.

[https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems)
[http://askubuntu.com/questions/182365/irq-conflicts-causing-video-card-and-boot-problems](http://askubuntu.com/questions/182365/irq-conflicts-causing-video-card-and-boot-problems)

if you cant change/test irq setting into your bios, then use the irqpoll boot parameter inside /etc/default/grub (**set it before "quiet splash"**) then update grub to care of it (sudo update-grub)

note: removing "quiet splash" from the boot line, let you see the verbose booting comments to identify the possible warnings/errors.

I wasn't aware of what I put in bold, maybe that explains why it didn't change a thing.

Thank you both, I will try what you told me.

---

### Post by Axio on 2012-12-25
I have checked the bios: no irq option.

I have put irqpoll before quiet/splash.

I have installed the newest microcode.

Now I am waiting.

---

### Post by Axio on 2012-12-31
I have tried everything there was on the page, it didn't work. I have opened a bug on launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1094904](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1094904)

---

### Post by SirWeazel on 2012-12-31
Just browsing forums from my phone, so i apologize if I'm a little of track. But when you say "start an intensive task" my first thought is overheating issues. Have you checked temps, fans, cleaned out the dust, possibly new thermal paste?

Ffmpeg conversion will quickly drive up temps. Try prime95, or narrow down an os problem by booting to a live distro (ubuntu or even try another), and stress the cpu.  This would quickly help narrow down your issue.

---

### Post by dcstar on 2013-01-01
> **SirWeazel said:**
> Just browsing forums from my phone, so i apologize if I'm a little of track. But when you say "start an intensive task" my first thought is overheating issues. Have you checked temps, fans, cleaned out the dust, possibly new thermal paste?

Ffmpeg conversion will quickly drive up temps. Try prime95, or narrow down an os problem by booting to a live distro (ubuntu or even try another), and stress the cpu.  This would quickly help narrow down your issue.

+1

Too many people blame software when their hardware cooks or is unreliable.

---

