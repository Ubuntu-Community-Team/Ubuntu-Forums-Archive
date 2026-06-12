---
title: "Ubuntu Reboots/Freezes constantly"
date: 2007-04-08
forum: General Help
---

### Post by Draek on 2007-04-08
Ubuntu refuses to work for very long. It will just freeze, or reboot on its own after a certain amount of time, random.

I have checked /var/log/dmesg and /var/log/syslog and just about every other log file in there. There is not one single error, panic, or warning that seems would cause this problem.

I have removed NVIDIA drivers for the ones that come with ubuntu. Still the same problem. I don't have any special devices installed, its pretty much a clean Ubuntu install.

I also have a windows HD, i boot up in there, and I can stay in indefinitely. Not that I think windows is better, but right now, its the only thing that works. At least it confirms that my hardware is working fine. I can even play 3D games in windows, so I know that i can heat up the CPU/GPU and it still works fine.

Anyone have ANY ideas before I just simply give up on using Linux?

---

### Post by ihavenoname on 2007-04-08
> **Draek said:**
> Ubuntu refuses to work for very long. It will just freeze, or reboot on its own after a certain amount of time, random.

I have checked /var/log/dmesg and /var/log/syslog and just about every other log file in there. There is not one single error, panic, or warning that seems would cause this problem.

I have removed NVIDIA drivers for the ones that come with ubuntu. Still the same problem. I don't have any special devices installed, its pretty much a clean Ubuntu install.

I also have a windows HD, i boot up in there, and I can stay in indefinitely. Not that I think windows is better, but right now, its the only thing that works. At least it confirms that my hardware is working fine. I can even play 3D games in windows, so I know that i can heat up the CPU/GPU and it still works fine.

Do you have any wireless cards? What are your system specifications? Is it a laptop, or desktop, what processor are you using. How much ram do you have. What brand is it? etc. 

> **Draek said:**
> 
Anyone have ANY ideas before I just simply give up on using Linux?
You realize that Ubuntu is not the only linux operating system out there right? You should try Mandriva or Opensuse, or maybe even Fedora. Better yet you can try Debian itself. (Similar to Ubuntu but it tends to be more stable.) Debian Etch is a very nice operating system. 

Although if Windows is the best thing for you, theres nothing wrong with using it. You can still use many open source applications on windows. (Openoffice, firefox, gimp, blender etc.)

---

### Post by Draek on 2007-04-08
The goal is ubuntu, so using another distro is not an option. Neither is windows, as this is not my goal. Thats like saying, "I'm having a problem with my car" and the answer the mechanic says is "why don't you fly a plane instead?"

Now that we got past that, my comp is using:

- Intel Pentium 4 3.2Ghz HT on a Gigabyte motherboard
- 2GB of DDR 400 ram (checked with memtest86)
- 200GB SATA hard drive
- IDE DVD-RW Drive
- Onboard 5.1 audio
- GeForce 4 ti4400 (using nv driver)
- Onboard Ethernet

No other devices, nothing special, no peripherals. Ubuntu worked fine before. Now it just reboots constantly, never can stay in longer than 15 minutes. Windows works fine (used another HD to test my hardware) can stay in indefinitely, and can play 3D games (Stress test).

I get the following summarized error SOMETIMES, depends on how the OS crashes. Sometimes its a clean reboot, sometimes its a freeze, sometimes i get this kernel panic message on screen in text mode. The following is just the key words, i didn't write down all the memory addresses and time/date stuff

EIP: local_bh_enable SS:ESP
Kernel Panic - Not syncing: fatal exception in interrupt.
BUG: at arch/i386/kernel/smp.c: 549 smp_call_function()
smp_call_function
printk
smp_send_stop
panic,
die
do_page_fault
do_softirq
smp_apic_time_intterupt
cpu_idle

I tried 2 different kernel versions from the official repositories. If I log in single user (safe mode) i can stay at the command prompt indefinitely. Not sure what is happening.

Anyone have any constructive suggestions towards fixing my problem? Anything I should be looking at?

---

### Post by heimo on 2007-04-08
Is it possible to disable hyper threading in BIOS? I'd try that. Or install non-SMP kernel, just to test if the problem lies in HT/SMP.

---

### Post by ihavenoname on 2007-04-08
> **Draek said:**
> The goal is ubuntu, so using another distro is not an option. Neither is windows, as this is not my goal. Thats like saying, "I'm having a problem with my car" and the answer the mechanic says is "why don't you fly a plane instead?"

 It is absolutely NOT the same thing. There is a HUGE difference between the interface of a plane and a car (not to mention usage cases and costs) Debian and Ubuntu are almost the same thing. The main difference is in the fact that Ubuntu has a lot of pre-configured options. While debian is more like a blank slate that let's you choose. (Though it's gotten very user friendly with etch.) I told you to try other distros/ stick with windows because the last sentence of your original post said 
> 
Anyone have ANY ideas before I just simply give up on using Linux?This implies that you see Ubuntu not working as a problem with LINUX. Not the case. Ubuntu has bugs that are Ubuntu specific. Debian IS more stable than Ubuntu as it has a more rigorous testing cycle and  has no closed source drivers which could cause strange problems. If all you want to use is Ubuntu, then your last sentence of your original post was useless. I told you that using windows was ok because it seems to work for you and my goal is not to have you waste your time. (Assuming we could not fix this).


> **Draek said:**
> 

Now that we got past that, my comp is using:

- Intel Pentium 4 3.2Ghz HT on a Gigabyte motherboard
- 2GB of DDR 400 ram (checked with memtest86)
- 200GB SATA hard drive
- IDE DVD-RW Drive
- Onboard 5.1 audio
- GeForce 4 ti4400 (using nv driver)
- Onboard Ethernet

No other devices, nothing special, no peripherals. Ubuntu worked fine before. Now it just reboots constantly, never can stay in longer than 15 minutes. Windows works fine (used another HD to test my hardware) can stay in indefinitely, and can play 3D games (Stress test).

I get the following summarized error SOMETIMES, depends on how the OS crashes. Sometimes its a clean reboot, sometimes its a freeze, sometimes i get this kernel panic message on screen in text mode. The following is just the key words, i didn't write down all the memory addresses and time/date stuff

EIP: local_bh_enable SS:ESP
Kernel Panic - Not syncing: fatal exception in interrupt.
BUG: at arch/i386/kernel/smp.c: 549 smp_call_function()
smp_call_function
printk
smp_send_stop
panic,
die
do_page_fault
do_softirq
smp_apic_time_intterupt
cpu_idle

I tried 2 different kernel versions from the official repositories. If I log in single user (safe mode) i can stay at the command prompt indefinitely. Not sure what is happening.

Anyone have any constructive suggestions towards fixing my problem? Anything I should be looking at?


The information you provided in your second post is much more useful. 

It does seem to be an smp issue. Try adding irqpoll to your boot parameters as I have heard that can help with some smp issues.

IF you want to remove smp support try looking at this thread [http://www.linuxquestions.org/questions/showthread.php?t=7816](http://www.linuxquestions.org/questions/showthread.php?t=7816)
There is a wiki entry in the ubuntu wiki for the ubuntu way to recompile a kernel. [https://wiki.ubuntu.com/KernelCustomBuild?highlight=%28CategoryKernel%29](https://wiki.ubuntu.com/KernelCustomBuild?highlight=%28CategoryKernel%29)
 Don't worry it's not as bad as it sounds. (The only problem might be getting through the compile without having your computer reboot.)

Does this happen when the computer is in heavy use, or is that not a main factor?  Also which kernel are you using? uname -r will tell you if your not sure. 

The part of the kernel that the error is referring to is here
[http://www.gelato.unsw.edu.au/lxr/source/arch/i386/kernel/smp.c](http://www.gelato.unsw.edu.au/lxr/source/arch/i386/kernel/smp.c)

If none of what has been suggested to you seems to fix the problem then you should file a bug report. I hope this helps you somehow.

---

### Post by Draek on 2007-04-10
I'm using 2.6.20-14-generic right now, but i don't see any difference between between Edgy and Fiesty.

I'll try some of your suggestions, I wanted to install a non-SMP kernel, i figured one would be provided in the repos, like it used to be. I'll see about that kernel option, but i dont see any way to turn off HT in the bios.

After the last reboot i checked the CPU temp and it was 60C so i think thats a bit hot. Although I've read anything under 70 is fine. It went down to 50C while in BIOS so it went down basically 10 degrees. I wonder if my CPU is busted. or my Mobo. Although that doesn't explain why windows doesn't crash, if the CPU was getting hot, it should crash in both OSes. Somehow this is specific to Ubuntu so far, and it used to work fine, and it doesn't anymore... which is weird.

I guess this is a good reason to get a Core 2 Duo.

---

### Post by ihavenoname on 2007-04-10
> **Draek said:**
> I'm using 2.6.20-14-generic right now, but i don't see any difference between between Edgy and Fiesty.

I'll try some of your suggestions, I wanted to install a non-SMP kernel, i figured one would be provided in the repos, like it used to be. I'll see about that kernel option, but i dont see any way to turn off HT in the bios.
The kernel now is set to detect whether you are running a dual-core/threaded processor or a single processor and runs that.  Try adding the nosmp option to your kernel line in grub. I am not sure if that will have an affect but it's worth a try. 


> **Draek said:**
> 
After the last reboot i checked the CPU temp and it was 60C so i think thats a bit hot. Although I've read anything under 70 is fine. It went down to 50C while in BIOS so it went down basically 10 degrees. I wonder if my CPU is busted. or my Mobo. Although that doesn't explain why windows doesn't crash, if the CPU was getting hot, it should crash in both OSes. Somehow this is specific to Ubuntu so far, and it used to work fine, and it doesn't anymore... which is weird.

I guess this is a good reason to get a Core 2 Duo.

See if you can find an app that checks the temperature on Windows. You say that it runs well in Windows doing heavy work. So I don't know if that is the issue. Maybe it's something in the way linux tries to optimize your processor. So it trys to run some smp function which crashes. The kernel (2.6.20) your runing is one that has given a lot of people problems. If you can find a different one that would be better. 

You are having the same problems with both feisty and edgy? What is kernel on edgy?

---

### Post by Draek on 2007-04-10
The kernel was 2.6.14 in Edgy, I believe there was an update to 2.6.17 as well, but i never tried it.

Today a update came out for Fiesty for the kernel 2.6.20-14 but it didn't change the version number. Must have been a minor change. It didn't fix the problem anyway.

I've been compiling the kernel without SMP, just took forever this morning (about 2 hours to compile the darn modules) so I haven't had a chance to try it out yet. I was late for work too. This has really been driving me insane, my awesome computer now has been lowered to a useless piece of junk. Quite frustrating.

I'm going home for lunch to boot the new kernel without SMP to see if it works. I tried the IRQPOLL option as suggested, but didn't make any change.
The thing that really bothers me, again, is that I've been using Ubuntu for Years. I used Edgy since its release, on the same computer. So for this to be happening now, is a bit odd.

---

### Post by ihavenoname on 2007-04-10
> **Draek said:**
> The kernel was 2.6.14 in Edgy, I believe there was an update to 2.6.17 as well, but i never tried it.

Today a update came out for Fiesty for the kernel 2.6.20-14 but it didn't change the version number. Must have been a minor change. It didn't fix the problem anyway.

I've been compiling the kernel without SMP, just took forever this morning (about 2 hours to compile the darn modules) so I haven't had a chance to try it out yet. I was late for work too. This has really been driving me insane, my awesome computer now has been lowered to a useless piece of junk. Quite frustrating.

I'm going home for lunch to boot the new kernel without SMP to see if it works. I tried the IRQPOLL option as suggested, but didn't make any change.
The thing that really bothers me, again, is that I've been using Ubuntu for Years. I used Edgy since its release, on the same computer. So for this to be happening now, is a bit odd.

This is a very odd issue indeed. Just out of curiosity did you compile a vanilla kernel or did you recompile the Ubuntu kernel? 

Also do you have an extra hard drive or partition? I ask this because maybe if you could re-install Ubuntu and see if the problem persists. You say it's on both feisty and edgy.  So I am trying to find out if it's Linux, Ubuntu specs. , or a hardware problem. I feel your pain, don't worry though I'm sure we can find SOME way to fix this. Hopefully your new kernel will work though. (Well, it might mean that you would have to live w/o HT for a while. Not sure if that is acceptable to you though.) 

Hang in there :guitar:!

---

