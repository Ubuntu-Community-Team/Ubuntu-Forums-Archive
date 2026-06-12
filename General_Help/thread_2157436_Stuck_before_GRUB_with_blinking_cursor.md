---
title: "Stuck before GRUB with blinking cursor"
date: 2013-06-25
forum: General Help
---

### Post by drgrateful on 2013-06-25
Hello, this is my first post here.

I am experiencing the following problem, and hope someone can suggest
what is going wrong.

I have been running Ubuntu (dual booting with Windows XP) in this
computer for years. In the last couple of days, often (*but not
always*) when I boot the computer, I get stuck after the RAM check,
just before the GRUB prompt. All I see is a blinking cursor on a black
screen. If I try to boot from a live Ubuntu CD, the boot fails and I
get the initramfs prompt.

When I try to boot again several times, I might eventually get the
GRUB prompt and start Ubuntu from HD as usual. All seems to be well
for a few hours (including booting from a live CD). Then, while running Ubuntu,
I may get a kernel panic message. If I try to restart, I am stuck again at the GRUB prompt.

I am running a 3.2.0-48 kernel in Ubuntu 12.04 on a (rather old) ASUS
A8V-E mobo equipped with an AMD K8 (Athlon64/Opteron) and 1GB RAM. The
VGA card is a GeForce 6600.

Thank you for any help.

Matteo

---

### Post by TheFu on 2013-06-25
Hi Matteo!

The issue you describe could be caused by hundreds of different items. Some are hardware and some software - or just "lazy bits" on the HDD.  Sadly, you'll need to watch the system logs carefully and I would highly recommend ensuring that your backup methodology is working perfectly and you can recover the complete system from yesterday, last week or last month - an ailing system is likely to be a dead system sooner than later.
 
In the meantime, the boot-repair tool might be able to correct any non-hardware issues with bootup. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) explains.

Many systems run in to the "lazy bits" issue if the OSes haven't been re-installed in a few years.  I'm a firm believer in bits on HDDs losing their magnetic strength, so using some software that reads and re-writes the bits can refresh the strength ... and give the HDD an opportunity to relocate failing sectors before something catastrophic happens.

To monitor the log files, there are many different ways. I like to have an automatic script that looks for issues and tells me about them - logwatch is 1 of those tools, but there are many others.  [http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files) offers other options.  Hopefully, any hardware issues will be seen in the logs when the system is working.  Reseat all the RAM, cables too. Can't hurt.

A failing GPU or failing PSU can cause all sorts of strange problems to a system. Sadly, the only real way to test for these issues is to replace each part, one at a time, until the problem stops.  For many people, it is less effort to just replace all the system internals for $200.  I've done that a few times after swapping GPUs, disk controllers, RAM, PSUs, cables and still never determining the cause. Swapping the motherboard entailed more changes - new CPU, new RAM, and a new PSU, to I was already almost there for a new system.  

Two of my workhorse systems are C2D still and working fine, but I expect that to end sometime. No issues today, but any 4-6 yr old PC that runs 24/7/365 is bound to have a failure.  Last fall, I replaced 6 HDDs that were almost 6 yrs old. None had failed, but I didn't want an unplanned failure to ruin my day or week. Best to be proactive, is my rule. Unexpected failures suck.

Almost forgot - the BIOS battery may need replacement.  While not a common issue, anytime a motherboard is 4+ yrs old, the battery that retains settings and the real-time clock might be failing. If you notice that hardware disappears in the BIOS or the clock is often wrong, change the BIOS battery.

---

### Post by drgrateful on 2013-06-27
Hi, thanks for all the suggestions. Fortunately, I have backups. In any case, I have no trouble accessing
my HD attaching it to a laptop with a SATA to USB adaptor.

Here's what I tried:

1) I have two memory sticks. I tried letting only one of them in turn.
2) I checked the BIOS battery: it is fully charged.
3) I updated the BIOS.
4) I tried a different graphics card.
5) I did a fsck on the HD.

None of this worked.

Now, often the BIOS gets stuck even before the memory test. Strangely, I see that when the computer stays off for a while,
it has many more chances to boot fine. I don't know if this gives any clue into what is going wrong.

I am about to give up, if I don't get any other suggestions.

In any case, thank you... I suppose I am in the market for a new computer.

Matteo

---

### Post by grahammechanical on 2013-06-27
I would put my money on the BIOS battery. You make two comments that point in that direction:

> [COLOR=#000000]I get stuck after the RAM check, [/COLOR][COLOR=#000000]just before the GRUB prompt.[/COLOR]
> [COLOR=#000000]often the BIOS gets stuck even before the memory test. [/COLOR]

Do you get a message telling you to reconfigure the BIOS settings.

I had a similar problem a few months ago with my five year old machine. Sometimes it would boot as normal. Sometimes I would get the message to reconfigure the BIOS settings or run with the default settings. I changed the BIOS battery and that solved it. The battery might be fully charged but it might not be holding the charge or recharging sufficiently while the machine is connected. The power switch on my motherboard does not switch of the power to the motherboard completely. That is done through a switch on the back of the power supply. So, my problem should not have happened. The battery should have always been fully charged. But changing the battery solved the problem.

A battery can show the correct voltage when it is not under load but the voltage will then drop when it is under load.

Regards.

---

### Post by TheFu on 2013-06-27
I've never heard of any motherboard actually "charging" any CMOS/BIOS battery.  That would be a new one on me.

Back to the OP - at this point, it could be anything still - a tiny short in any component that only occurs when it heats up a little. A cheap capacitor that is failing or a MB component that has just worn out.

The only things I've personally seen cause issues booting pre-MBR read are:
* CMOS battery
* dying video card
* dying PSU
* cracked motherboard
* blown cheap capacitors (don't think they've used then since the 1990s)
* loose RAM
* loose CPU

Sorry, but that's all I got. ;)

---

### Post by drgrateful on 2013-06-30
Thanks, I tried replacing the CMOS battery, even if it was fully charged, but to no avail.

I also tried reseating the RAM and checking the voltage coming from the PSU. As I said, I had already tried replacing the video card. Nothing seems to be evidently wrong.

Resetting the CMOS did not work either.

Thanks for the support anyway. Possibly, the CMOS itself is corrupt, or the mobo is broken. At this point, I have really no idea...

Best, Matteo

---

