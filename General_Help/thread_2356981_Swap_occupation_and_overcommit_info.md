---
title: "Swap occupation and overcommit info"
date: 2017-03-28
forum: General Help
---

### Post by suaro on 2017-03-28
Hi Everyone,

I have an Ubuntu 16.04 system with 56GB of ram and 8 cores. The swap file that's setup on the system is only 7GB.
Very little of the swap file is being used at all.  Its almost negligible .
When I use atop I see vmlim is **13.8G** and the vmcom is **19.1G**.

The man page shows the following definitions for vmlim and vmcom

       SWP  Swap occupation and overcommit info.
            This line contains the total amount of swap space on disk (`tot') and the amount of free swap space (`free').
            Furthermore  the committed virtual memory space (`**vmcom'**) and the maximum limit of the committed space (`**vmlim'**, which is by default swap size
            plus 50% of memory size) is shown.  The committed space is the reserved virtual space for all allocations of private  memory  space  for  pro&#8208;
            cesses. The kernel only verifies whether the committed space exceeds the limit if strict overcommit handling is configured (vm.overcommit_mem&#8208;
            ory is 2).

My overcommit is set to 0:

   cat /proc/sys/vm/overcommit_memory
    0


The Answer section here ([http://serverfault.com/questions/606185/how-does-vm-overcommit-memory-work](http://serverfault.com/questions/606185/how-does-vm-overcommit-memory-work) ) seems to explain what the values represent:

(from link above)

This file contains the kernel virtual memory accounting mode.  Values are:
0: heuristic overcommit (this is the default)
1: always overcommit, never check
2: always check, never overcommit
In  mode  0, calls of mmap(2) with MAP_NORESERVE are not checked, and the default check is very weak, leading to the risk of get-ting a process "OOM-killed".  Under Linux 2.4 any non-zero value implies mode 1.  In mode 2  (available  since  Linux   2.6),  the total  virtual  address  space on the system is limited to (SS + RAM*(r/100)), where SS is the size of the swap space, and RAM is the size of the physical memory, and r is the contents of the file /proc/sys/vm/overcommit_ratio.


My question is :  With overcommit_memory set to 0 should there be any concern the limit space (vmcom ) is way higher than the limit ?  Are there any performance implications because of this ?

Yes, I can increase the size of the swap file to get vmlim higher than vmcom, but was mostly concerned if vmcom which is higher than vmlim is bad ?   Atop flags this in red. 

Thank in advance

---

