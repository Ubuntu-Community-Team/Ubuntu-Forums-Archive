---
title: "Understanding System Monitor CPU Graph vs Process CPU Usage (overheating)"
date: 2024-11-28
forum: General Help
---

### Post by impracticaldogg on 2024-11-28
I have a 4 core 8 thread CPU in my laptop. The System Monitor shows one "CPU" (of 8) at 100%, with the others in the single digits. Under Processes there is one process constantly around 12.5%. And two Gnome processes around 1.5%.  Everything else is negligible. 
Am I interpreting this correctly: since 8 x 12.5 is 100, that one process at 12.5 is the one consuming all the output from a single core? 
If I set my power mode to Balanced or Performance that one process at 12.5% increases my CPU temperature to 95C according to PSensor. Under Power Saver the temp drops right down.
Thanks!

---

### Post by grahammechanical on 2024-11-28
I have a similar system to you. This is my experience with an 8 core CPU. The load is spread through all the 8 cores. Each core reaching 100% for a short time and then dropping to a much much lower rate as another core runs at 100%. I do not know if this method of working is called multi-tasking or multi-threading.

I am guessing that the multi core CPU make it possible for CPUs to be as powerful as the single core CPUs were without using as much electricity. This would mean longer battery life and less heat which in turn means that a fan is not needed or only a small fan that only switches on when the temperature rises above a certain level. This also prolongs battery life.

In the past when CPUs were single core there were two ways a CPU could be made more powerful. 

1) Increase the speed at which the CPU ran. This increased electricity usage as well as temperature output which in turn required a fan. On desktop machine this was not so much of a problem. Some enthusiasts even came up with a method of water cooling. Imagine that! But single core CPUs running faster were not so practical in laptops. Large size and low battery life being the things that held back sales. So, laptop were never as powerful as desktop machines. Unlike today.

2) Reduce the size of the millions of transistors that make up a CPU. This was successful until a limit was reached as to how small they could etech the transistors into a slice of silicon that became a CPU.

The leap from single to dual core and then to multi-core is an interesting story for those who find such things interesting. But that would be a story for personal research.

As for the difference between Performance, Balanced and Power Saver modes consider this: Imagine a CPU running at full Power. That is Performance mode. But it quickly uses up battery power. So, they put a limit on how fast the CPU runs and they call it Balanced mode. They limit the CPU even further and call it Power Saver mode.

So, there we are.

Regards

---

