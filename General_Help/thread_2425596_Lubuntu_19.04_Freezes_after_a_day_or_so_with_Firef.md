---
title: "Lubuntu 19.04 Freezes after a day or so with Firefox left open"
date: 2019-08-27
forum: General Help
---

### Post by fozziebear on 2019-08-27
I am beginning to wonder if this is a hardware issue rather than the OS but would appreciate some thoughts or suggestions. 
I have installed Lubuntu 19.04 on an HP Pavilion tower with an Intel Core Duo 2.4Ghz processor and 2Gb ram. Graphics is onboard.

On boot the system is really snappy and works well,however after a day or two the system freezes. On most occasions I can still move the mouse but when I click on anything it takes up to 10 minutes to change focus. On occasions the system clock remains static. Its as if something is hogging all resources. I am using get_iplayer web PVR which relies on three tabs of Firefox being left open permanently. Could this be a reason for memory leakage? I know Chrome can be a problem with memory leakage but don't know about Firefox.
I am not sure if relevant but even on initial boot Discover is so slow to load. It will eventually display featured apps but I cant scroll and cannot search as the search box cannot be captured by the mouse.
The only solution when this happens is a hard reboot with the power button. I'm really disappointed as I hoped Lubuntu would be lighter on resources than Xubuntu which I really liked as an OS.
Is there an easy way to check memory usage? Would a dedicated graphics card help with load on memory/CPU

---

### Post by crip720 on 2019-08-27
Might be hardware issue has in not enough ram.  You can use the 'top' command in terminal and see how much cpu/memory the different programs are using.  One program might be acting up.  Would google the make and model of your machine to see how much memory can be added. Can be a cheap worth while upgrade. Do you have much free space on your hard drive or is it almost full?  Should have at least 20 to 25% free(in lubuntu's partition).

---

### Post by fozziebear on 2019-08-28
> **crip720 said:**
> Might be hardware issue has in not enough ram.  You can use the 'top' command in terminal and see how much cpu/memory the different programs are using.  One program might be acting up.  Would google the make and model of your machine to see how much memory can be added. Can be a cheap worth while upgrade. Do you have much free space on your hard drive or is it almost full?  Should have at least 20 to 25% free(in lubuntu's partition).
Unfortunately system can only accommodate 2Gb ram which is what is currently installed. I have a 500gb hard drive and that is 60% free.
I had a similar issue with Xubuntu so thought a move to Lubuntu which can supposedly run on 256Mb ram that it would be OK. What is strange is that the system on boot is really snappy and fast. Its just that over time it deteriorates to the point of being unusable. This is normally an indication of memory leakage but I don't know how to check that. In windows there are applications that will free up ram but dont know if similar tools are available in Linux. 
As an aside please could you expand on ***Top*** command and how you run that in terminal assuming a frozen system will let me bring up terminal? Is there an equivalent of ctrl+alt+del in linux to get out of a locked desktop?

---

