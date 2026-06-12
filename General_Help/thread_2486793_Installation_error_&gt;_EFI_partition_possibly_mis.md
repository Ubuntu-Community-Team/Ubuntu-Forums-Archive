---
title: "Installation error &gt; EFI partition possibly missing &gt;"
date: 2023-05-10
forum: General Help
---

### Post by noobtechninja on 2023-05-10
Hi there guys

I was hoping that you could help me with a tricky little issue that I've
just encountered.


**Background:**
I have a (new to me) PC, lets call it PC-2
ATM, It has NO GFX capeabilites at all, -
(I'm awaitng a GFX card to be delivered).

In the meantime I thought I'd get ahead of the game, and install Ubuntu to
the SSD via an external interface (connected to my main PC = PC-1)

All seemed to be going well, but I came across an error message when I was
trying to install Ubuntu to the SSD


On PC-1, I have done the following -

1. Mounted the SSD

2. Used Gparted to delete **(all)** of the old, original partitions on the SSD
This included the Windows installation that the PC came with, the recovery
partition and.................

3. As I've now found out, it appears that I have also deleted any FAT
partition that may have included the EFI / boot partition.

4. Repartitioned the SSD to my preferred set-up =
4.1. A 180 GB = /(root)
4.2. A 320 GB = /home


**Issue:**
I was running Ubuntu from a live USB stick (22.04.02)
When I got to the HD partitioning, I chose manual, then opted to use the
partitioning scheme that I had alrady configured (outlined above in points 4)

As I was doing this, the installation wizard, complained that it couldn't find
any EFI partitions, and that the install, and subsequent boots may not work
or boot properly.

I realised my mistake, and cancelled the installation of the new OS
on the SSD


**Questions:**


1. Do I actually need a EFI partition to allow me to boot Ubuntu on my new
PC-2 ?


2. (If so) can I recover the old EFI partition and code ?
(unlikeley I know)


3. Can I create a new EFI boot partition ?
3.1. If so how ?


4. Do I need a EFI / "registration code" that is tied to the physical ID of the SSD ?
4.1. If so, how can I generate it / a new version ?


**Useful information for PC-2:**

Motherboard = Sabertooth 990FX
SSD = Samsung SSD 850 EVO 500G


TIA for any help or advice

---

### Post by oldfred on 2023-05-10
Duplicate post, closed.
See:
[https://ubuntuforums.org/showthread.php?t=2486758](https://ubuntuforums.org/showthread.php?t=2486758)

We all are volunteers here & need to know what has already been suggested to avoid duplicate effort.

---

