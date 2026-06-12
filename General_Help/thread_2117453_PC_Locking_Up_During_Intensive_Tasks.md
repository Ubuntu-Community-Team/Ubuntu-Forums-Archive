---
title: "PC Locking Up During Intensive Tasks"
date: 2013-02-18
forum: General Help
---

### Post by writhziden on 2013-02-18
I have some experiments running for my PhD research, and the experiments utilize all 8 logical cores of my Intel® Core&#8482; i7-3630QM CPU @ 2.40GHz. 

So far, the system has locked up on three occasions. I have left it running overnight and had it lock up twice where the screen would not turn back on when I moved the mouse or pressed keys. ALT+SYSRQ+R+S+E+I+U+O/B also had no effect. 

I also had it lock up when clicking on the Inbox link in Firefox for my work webmail account. All lock ups have occurred while running experiments for my research. The application for my research is a computer vision, feature matching application that requires 6-12 GB of RAM at a time and uses all 8 logical processors as already stated.


System Specs:[INDENT]OS: Ubuntu 12.04 64-bit
[/INDENT][INDENT]Model: Toshiba QOSMIO X875-Q7380

Processor: Intel® Core&#8482; i7-3630QM CPU @ 2.40GHz (3.40 GHz Turbo)

RAM: 12 GB DDR3 (1600 MHz)

Display Card: NVIDIA GeForce GTX 670M Graphics (3 GB DDR5 dedicated RAM)

OnBoard Display: Intel HD 4000

Hard Disk Drive(s): 2x512GB drives, both 7200 RPM, Toshiba drives.

Max Screen Resolution: 1600x900

[/INDENT]I have not upgraded any hardware, nor do I overclock beyond the TurboBoost technology. Let me know if there are logs I can provide to help determine the cause of the lock-ups.

---

### Post by Ceiber Boy on 2013-02-18
> **writhziden said:**
> I have some experiments running for my PhD research, and the experiments utilize all 8 logical cores of my Intel® Core&#8482; i7-3630QM CPU @ 2.40GHz. 

So far, the system has locked up on three occasions. I have left it running overnight and had it lock up twice where the screen would not turn back on when I moved the mouse or pressed keys. ALT+SYSRQ+R+S+E+I+U+O/B also had no effect. 

I also had it lock up when clicking on the Inbox link in Firefox for my work webmail account. All lock ups have occurred while running experiments for my research. The application for my research is a computer vision, feature matching application that requires 6-12 GB of RAM at a time and uses all 8 logical processors as already stated.


System Specs:[INDENT]OS: Ubuntu 12.04 64-bit
[/INDENT][INDENT]Model: Toshiba QOSMIO X875-Q7380

Processor: Intel® Core&#8482; i7-3630QM CPU @ 2.40GHz (3.40 GHz Turbo)

RAM: 12 GB DDR3 (1600 MHz)

Display Card: NVIDIA GeForce GTX 670M Graphics (3 GB DDR5 dedicated RAM)

OnBoard Display: Intel HD 4000

Hard Disk Drive(s): 2x512GB drives, both 7200 RPM, Toshiba drives.

Max Screen Resolution: 1600x900

[/INDENT]I have not upgraded any hardware, nor do I overclock beyond the TurboBoost technology. Let me know if there are logs I can provide to help determine the cause of the lock-ups.

Is their a configuration on your experimenting software to reduce the number of  cpu's assigned to it by 1 so at least the system has some resource available to it?

If it is locking up when using firefox it sounds like more than a resource issue, how much of a head ach would it be to reinstall the OS, or perhaps install another instance of ubuntu? Then run your experiment to see if a clean install has the same problem.

Im just thinking aloud, hopefully it is helpfull to you, good luck with your PHD.:)

---

### Post by writhziden on 2013-02-18
Thanks for the well wishes on my PhD. 

I will backup my current installation and re-install. And yes, I can choose how many processors I want to utilize. The reason I use the maximum is it takes 94 hours for one experiment set to run with one core and 12 hours if I use all four + the i7 threading technology (8 logical cores).

---

### Post by rnerwein on 2013-02-18
> **writhziden said:**
> Thanks for the well wishes on my PhD. 

I will backup my current installation and re-install. And yes, I can choose how many processors I want to utilize. The reason I use the maximum is it takes 94 hours for one experiment set to run with one core and 12 hours if I use all four + the i7 threading technology (8 logical cores).
hi
in that situation i'll do this 
1. before start your tests - run in a terminal: top
2. bind the top process to a core e.g.: taskset -p 0x00000001 pid_of_topprocess.
     (top will be bound to core 0 )
3. give the task highest realtime e.g.: chrt -p 99 pid_of_topprocess
4. start your tests
5. if the system totaly freeze you can see in the "top" terminal (i hope so) interesting values like mem/cache using ......
if the system is frozen notice the values of the first, lets say, 15 lines and post them.
have fun
ciao

---

### Post by writhziden on 2013-02-19
A re-install seems to have fixed it. I have a new problem with Ubuntu killing my research process when the Swap gets full (24 GB), but I will start a new thread if advised to do so. My original problem seems to be solved, so I will mark it so for now. 

Thanks for the help Ceiber Boy and rnerwein.

---

### Post by Ceiber Boy on 2013-02-19
> **writhziden said:**
> A re-install seems to have fixed it. I have a new problem with Ubuntu killing my research process when the Swap gets full (24 GB), but I will start a new thread if advised to do so. My original problem seems to be solved, so I will mark it so for now. 

Thanks for the help Ceiber Boy and rnerwein.

Use the alternate ISO and manualy make the SWAP any size you wish.

---

### Post by Ceiber Boy on 2013-02-19
> **Ceiber Boy said:**
> Use the alternate ISO and manualy make the SWAP any size you wish.

This might be helpfull:
 [http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/)

Its not using the alternate ISO as i first segested but by the looks of it will achive the same result.

---

