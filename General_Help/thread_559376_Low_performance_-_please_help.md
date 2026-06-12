---
title: "Low performance - please help"
date: 2007-09-25
forum: General Help
---

### Post by bsh on 2007-09-25
Ok i'm a linux n00b so treat me like that :)
I have the following pc specs: some old noname motherboard with via kt133a chipset, an amd duron 1200mhz cpu, 2x128mb sdram (133mhz), a 80gb maxtor 7200rpm ide hard disk, and some agp graphics card (tried with nvidia geforce 2 ti and geforce 4 mx440) but the problem is not grapchics related.
the disk is partitioned as follows:
5gb primary ntfs for windows xp
10gb extended, in which 5gb logical ext3 for root and 5gb logical for home
1gb for swap
~60gb primary ntfs to store data and to share this on my home network
i use ubuntu linux 7.04. tried it with gnome and xfce, now using xfce. the pc is headless (no monitor, keyboard or mouse). in grub, ubuntu is set to boot up automatically. after which, i can vnc into it from my main pc.
i have ntfs-3g installed and set up, the large partition is read/write accessible
i have samba set up, the large partition is shared with it, so i can access it from my other (windows) pc if needed.
i have vnc server set up.
i use azureus to download and seed torrents 24/7. it auto-downloads everything to this big partition and seeds from there. java doesn't use up all memory, there's some 40-50mb free usually.

the problem is following:
when i open a torrent and azureus allocates the free space, it takes some 20 seconds or more for a 100mb file. similarly, when it checks integrity, it takes similarly long. when creating new torrents, it takes long to hash files. when i copy something to this shared drive from my win pc, the speed is like 2-3mb/s, even if the hard drive itself could do 40-50mb/s with ease. and it's blazing fast on windows too.
but generally, the hard disk delivers only 3-5mb/s speed. :(
and most importatnly: all disk activities use 100%cpu
so my first guess was, the drive isn't running in udma mode, but it does run in udma5 (checked with hdstat -I) (hdstat -Tt reports 29.8mb/s)
i'm not sure why is this?
maybe ntfs-3g or samba is that slow and cpu intensive? i tried it, unmounted ntfs partitions, disabled samba sharing, and tried the speeds on the ext3 partitions - with the same low speed and 100%cpu usage, so maybe the problem is not with ntfs3g nor with samba.

so any ideas why i'm getting such low performance and 100% cpu usage in this setup?
thanks in advance.

---

### Post by overdrank on 2007-09-26
Well in my opinion AMD 1200 duron and only 256 mb ram that is it. I believe if you get that system to do what you are asking of it is pretty darn good. :)

---

### Post by bsh on 2007-09-26
a duron1200 should be enough, many users have even slower cpu's. and as said, the memory isn't full with java and other stuff, the resource monitor says there's still 40-50mb free physical memory.
i don't think a low cpu speed or even low amount of memory (and i believe both the cpu and the memory is sufficient) should cause 100% cpu usage on disk i/o, we are not talking about compressed filesystems or similar cpu intensive tasks...

---

### Post by dabl on 2007-09-26
Couple of notions:

1. Is swap being used to full advantage?  You could watch it with your system monitor while exercising the disk/CPU with file-transferring tasks.  You can change the vmswappiness value if you come to a belief that it could help speed things up.

2. Root filesystem congestion -- 5GB is kind of "just" enough, in my experience watching it during the past year.  I've seen it grow to 4.6GB in between apt cache cleanups and such, and sometimes (with Audacity, for example) the /tmp directory will grow dynamically even over the reported filesystem size.  I've been going with 6GB root partitions to stay safe.

3. The "top" command in a console window always provides an interesting view of what's going on with the CPU, while you stress the system, since it keeps the busiest processes on top of the list.

4. You might want to put the "noatime" option in your /etc/fstab line for "/" and "/home" -- it should provide a marginal improvement on that drive.

HTH ...  :)

---

