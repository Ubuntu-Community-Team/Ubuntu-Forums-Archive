---
title: "start problem"
date: 2012-12-25
forum: General Help
---

### Post by gramsyn on 2012-12-25
Hello everyone and merry Christmass,

I have a major problem and I need some help.

I was using Ubuntu and Windows at different partitions of the same disk. I installed a new disk and split it as well. At one partition installed Windows as a second Windows system (I plan to delete the first later). After some effort, I managed to meke every 3 of them working.

Then, I made a partition at the second disk from gnome-didk-utility with Ext4 filesystem. I labeled it but the utility didn't accept the label. I mounted it from the same utility and saw that the exlorer recognises its label. I also moved some files there and worked properly.

When I restarted the system, there was a message for NTLDR missing, and didn't reach to Grub. I restarted and the bios screen stayed for longer than usual but then loaded Grub and I chose Ubuntu. After 20 minutes Ubuntu loaded, but was like running at a PC of the 80's. Restarted again. Now no matter how many times I restart there is the following case:

The BIOS screen stays for 5 minutes! Then appears one of the following messages: ```
Disk boot failure, insert system disk and press enter
``` or ```
NTLDR missing. Restart your system
```
It doesn't accept any starting disk though (CD or USB).

Any thoughts?

---

### Post by gramsyn on 2012-12-25
I unplugged the second disk and everything is working. But I suppose, if I try to plug it again, the same will happen. Can I plug a SATA III disk to an operating system? If yes, I can fix the problem from Ubuntu. But I am afraid there will be a hardware damage.

Can you give me an advice on that? I cannot find something relevant to the web

---

### Post by Kirk Schnable on 2012-12-25
> **gramsyn said:**
> I unplugged the second disk and everything is working. But I suppose, if I try to plug it again, the same will happen. Can I plug a SATA III disk to an operating system? If yes, I can fix the problem from Ubuntu. But I am afraid there will be a hardware damage.

Can you give me an advice on that? I cannot find something relevant to the web

If unplugging a hard drive solves all your boot problems, check your BIOS boot order. You should be able to set it to boot to the "good" hard drive first automatically, thus ignoring the second drive. 

To do this, you want to press the button to launch Setup, at your boot splash screen. It's usually F2 or Delete.  Then, go to the Startup/Boot tab, or equivalent. 

If this doesn't resolve all your problems, I would be happy to try to assist further.

---

