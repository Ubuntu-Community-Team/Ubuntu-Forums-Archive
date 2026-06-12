---
title: "How to troubleshoot boot issue"
date: 2014-03-09
forum: General Help
---

### Post by darakus on 2014-03-09
Greetings,

I have been having this trouble since I switched to Ubuntu. I have a (seemingly random) boot problem in which my screen goes blank (as if computer is off) after grub and before the purple ubuntu splash screen. Here is a link to my previous post [http://ubuntuforums.org/showthread.php?t=2207624](http://ubuntuforums.org/showthread.php?t=2207624). I'm not so much looking for an answer to my problem, because if there was an easy one I would have found it by now (hopefully). When Ubuntu boots properly it works great.

When I get the blank screen my computer is powered on but completely  locked up, no video output at all, cant ping or ssh. I've tried mainline  kernels and ubuntu kernels. I have not tried very old kernels because  they would not support my graphics card so even if they fixed my boot  problem my computer would not be usable. I've tried the proprietary amd  drivers and the open source drivers. Everything I've tried the symptoms  are the same. Archlinux and Fedora and Windows boot properly so I think  this is unique to the way Ubuntu is booting.

I've tried all the obvious things like: [https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)
and: [https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)  (cannot do troubleshooting here, no ssh access)

What I am asking is help with how I can troubleshoot this issue. How can I debug this. Which logs could be helpful. Is there any way to step through boot so I can see every message before the screen blanks or log every boot message? I've removed quiet and splash from my kernel command line in grub, but as I said the monitor turns off a second or two after grub. I can see boot text whizzing by, but it does not stay on the screen long enough for me to read or take a picture of the messages.

Thanks for any help you can give.

---

### Post by oldfred on 2014-03-09
All the messages on screen are in /var/log/dmesg.
You can use Log File Viewer or just open file with editor.
I look for outright errors, warnings, long times between an entry or some task that keeps trying and fails and tries again later. Otherwise it is a long list of normal boot process.

---

### Post by darakus on 2014-03-09
Thanks for the reply,

It is my understanding that /var/log/dmesg gets overwritten at boot time. So what happens is my system will crash durring boot and then on the next (hopefully successful) boot dmesg gets written over with all the successful logs. If this is incorrect, please let me know. 

Also, what is the difference between dmesg and dmesg.0?

---

### Post by darakus on 2014-03-09
I feel silly for not noticing all the compressed dmesg's in /var/log 

Still, the only error or warning I see is:

ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20131115/tbfadt-603)

And it is not unique to the frozen/crashed boot. I'm doing more research into this Warning now.


UPDATE: This is a bios bug in my motherboard (Asus Sabertooth 990fx) and is being reported by the kernel on every boot. I dont think this is causing the issue because other flavors of linux boot properly every time.

---

### Post by Mark Phelps on 2014-03-09
> boot problem in which my screen goes blank (as if computer is off) after grub and before the purple ubuntu splash screen

This has been the standard behaviour on my Ubuntu installs as long as I can remember.  The screen going black indicates the boot process has transitioned to the next stage.  When it transitions again, the purple splash screen comes up.  The PC is unresponsive because it is in the middle of the boot process.

If you want to see what's happening (to show you that the boot process is continuing), go into the default GRUB config file and remove the "quiet" from the kernel command line.  You will then see the boot messages scrolling and stop (for quite a while) -- but they will pick up again.

---

### Post by darakus on 2014-03-09
> **Mark Phelps said:**
> This has been the standard behaviour on my Ubuntu installs as long as I can remember.

My post may have been somewhat unclear. My computer crashes/freezes at the point after grub but before splash screen. I must then do a hard reboot and cross my fingers that booting occurs normally the next time.

---

### Post by oldfred on 2014-03-09
There are several acpi boot options. But I have no idea which or if several may apply.

 [http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)

  acpi=off noapic nolapic noapci noirqpoll nosmp irqpoll

Have you updated BIOS to latest version, sometimes that helps.

---

### Post by darakus on 2014-03-09
> **oldfred said:**
> 
  acpi=off noapic nolapic noapci noirqpoll nosmp irqpoll



Thanks oldfred,

I have not solved the problem yet, but at least I now have a clue. Doing acpi=off does indeed allow me to boot correctly 100% of the time. Sadly it also allows me to see what my system would be like with only one cpu core. I'm going to read up and experiment with the other options for acpi.

> **oldfred said:**
> 
Have you updated BIOS to latest version, sometimes that helps. 


I'm using the most current version. However, ASUS released an R2 version of my motherboard so I'm wondering if there was something broken that they fixed in the new one. Sabertooth's have 5 year warranty so I'm going to try to contact them.

---

### Post by darakus on 2014-03-09
[FONT=arial]Ok, so after a long series of reboots to try various kernel parameters this is what I've found.

nosmp - Boots correctly every time but system is slowed to a crawl and unusable
apic=off - Boots correctly every time but system only detects one of eight processor cores.

noirqpoll - Seems to be the magical golden bullet that fixes my problem.

Thanks again to oldfred.

The question now is, what exactly does the noirqpoll option do.
In the documentation irqpoll is described as the following:[/FONT]

[FONT=courier new]When an interrupt is not handled search all handlers
for it. Also check all handlers each timer
interrupt. Intended to get systems with badly broken
firmware running.[/FONT]

[FONT=arial]But what about noirqpoll? Will I have any adverse effects from adding this to my kernel options?[/FONT] But I suppose that is a question for another time.

---

### Post by darakus on 2014-03-10
Not Solved, this actually broke my computer. It stopped booting at all. I guess I'll try ubuntu again when I get new hardware or when mir comes out.

---

### Post by newbie2244 on 2014-03-10
Which version of Ubuntu do you have? In one of my old Windows7-Lucid Lynx dual boot systems I experienced the same. And its a defect/ bug. I do not believe there is any way to correct it, except upgrade or change the version.

---

