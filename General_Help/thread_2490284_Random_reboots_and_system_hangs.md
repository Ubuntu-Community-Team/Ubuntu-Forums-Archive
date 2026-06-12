---
title: "Random reboots and system hangs"
date: 2023-08-29
forum: General Help
---

### Post by shaneee922 on 2023-08-29
Hello.

I have a system that runs Ubuntu 23.04 using kernel 6.2.0-27. It mainly runs Plex for my network, I'll list the specs below. Every so often the system will either reboot randomly or fully hang. I'm unsure what's causing this. I was originally running TrueNAS Scale and didn't have these issues.
I originally thought it was a memory issue as I'm using ZFS for my drives but I've added more memory and it still happens. Running "last reboot" doesn't really show anything. I'm not sure where else to look for any crash dumps on Linux.

I've disabled Precision Boost on the CPU for now as a test. Not sure if it'll help though but thought I'd make this post just in case I still need the help.

CPU: Ryzen 1600X
Motherboard: Gigabyte B450 Aorus Elite
RAM: Originally 16GB now 24GB
GPU: GTX 1070Ti
PSU: Corsair VS 450 ( I think this is enough )

Thanks.

---

### Post by ajgreeny on 2023-08-29
Have you checked temperatures as if too hot, that can cause sudden reboots.

Desktop or laptop machine, I suspect a desktop but would be good to know?

---

### Post by shaneee922 on 2023-08-30
Yes it's a desktop. Tctl will spike to high 70s sometimes low 80s but Tdie only goes to mid/high 50s.

Even with Precision Boost disabled in the BIOS.

---

### Post by Autodave on 2023-08-30
Sounds like a RAM problem.  Run the memory test for a good long while.  Or, take out your old RAM sticks and just move the new one to the first slot and try for awhile.

---

### Post by shaneee922 on 2023-09-15
> **Autodave said:**
> Sounds like a RAM problem.  Run the memory test for a good long while.  Or, take out your old RAM sticks and just move the new one to the first slot and try for awhile.

Memtest reports no errors with the RAM. Still getting random reboots and full system hangs.

---

