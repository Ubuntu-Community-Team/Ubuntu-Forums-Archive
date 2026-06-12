---
title: "Intermittent Shutdown Syndrome"
date: 2006-11-03
forum: General Help
---

### Post by MaxBrains on 2006-11-03
I have Kubuntu 6.10 running on an eMachines T2042 with a 2GHz Celeron, 512MB DDR RAM, and an nVidia FX5200 video card.

Whenever I run the CPU at 100% for an extended time (with BOINC, FlightGear, compiling, even running the yes command), after about 10 minutes, all processes terminate and Kubuntu shuts down. If I don't tax the CPU, the computer is otherwise reliable.

My best guess is that Linux believes my CPU is overheating. On Wednesday, I installed a better copper heatsink and fan with Arctic Silver 5, yet the problem persists. I ran memtest Wednesday night, which successfully ran continuously into Thursday morning, and revealed nothing wrong with my memory.

I've only had this problem since I threw Microsoft out the window, so I imagine there must be a way to convince Linux that my CPU isn't about to become a fireball every time I do anything significant.

](*,)

---

### Post by neza.ics on 2006-11-10
Hey, I have the same problem same machine, and it seems that once you boot into the OS the fan stops working.  Thats why it overheats and shutts down.  It has to do with the new kernel (I think).  Any ways the only thing that i found suggest that you turn off acpi.  

Look [here]("http://ubuntuforums.org/showthread.php?t=293047&highlight=cpu+fan")

---

### Post by MaxBrains on 2006-11-16
Added "acpi=off" on the kernel lines in /boot/grub/menu.lst and it seems my problem has been solved.

Incidentally, I don't believe the fan was actually stopping. I checked ONCE during normal use and saw the fan spinning as it should.

---

