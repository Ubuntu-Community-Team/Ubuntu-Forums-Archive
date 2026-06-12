---
title: "Ubuntu only seeing 3.2Gb of memory?"
date: 2006-08-02
forum: General Help
---

### Post by Grizzly_Adams on 2006-08-02
G'day all,

I have 2 new Dell PowerEdge 2950's.

On one I have installed Ubuntu server SMP, and on the other Redhat ES 4 Update 3.

The Redhat box can see the full amount of memory installed, but the Ubuntu installation doesn't seem to want to.

Lets look at what dmesg reports.

Redhat:
[root@pmx ~]# dmesg | more
Linux version 2.6.9-34.0.2.ELsmp (bhcompile@hs20-bc1-6.build.redhat.com) (gcc ve
rsion 3.4.6 20060404 (Red Hat 3.4.6-2)) #1 SMP Fri Jun 30 10:33:58 EDT 2006
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
 BIOS-e820: 0000000000100000 - 00000000cffa8000 (usable)
 BIOS-e820: 00000000cffa8000 - 00000000cffb7c00 (ACPI data)
 BIOS-e820: 00000000cffb7c00 - 00000000d0000000 (reserved)
 BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
 BIOS-e820: 00000000fe000000 - 0000000100000000 (reserved)
 BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
3968MB HIGHMEM available.
896MB LOWMEM available.
found SMP MP-table at 000fe710

Ubuntu:
[17179569.184000] Linux version 2.6.15-26-686 (buildd@terranova) (gcc version 4.
0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Mon Jul 17 20:14:14 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[17179569.184000]  BIOS-e820: 0000000000100000 - 00000000cffa8000 (usable)
[17179569.184000]  BIOS-e820: 00000000cffa8000 - 00000000cffb7c00 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000cffb7c00 - 00000000d0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fe000000 - 0000000100000000 (reserved)
[17179569.184000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[17179569.184000] Warning only 4GB will be used.
[17179569.184000] Use a PAE enabled kernel.
[17179569.184000] 3200MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000fe710

Now if we look at the first few lines in the /proc/meminfo file we see differences also.

Redhat:
[root@pmx ~]# cat /proc/meminfo
MemTotal:      4149156 kB
MemFree:       4084052 kB

Ubuntu:
rccadmin@mizar:~$ cat /proc/meminfo
MemTotal:      3365944 kB
MemFree:        126440 kB

Can someone please point me in the direction of why Ubuntu doesn't want to see the full 4Gb of RAM?  Or indeed if Redhat is seeing something it shouldn't...

Both boxes are identical, ordered at the same time with the same  spec.

Please help!  ](*,)

---

### Post by Grizzly_Adams on 2006-08-02
It appears that Ubuntu wants me to enable PAE in the kernel:

[17179569.184000] Use a PAE enabled kernel.

However I'm not sure how to do this.  Can anyone lead me in the right direction?

---

### Post by Grizzly_Adams on 2006-08-02
It appears that Ubuntu wants me to enable PAE in the kernel:

[17179569.184000] Use a PAE enabled kernel.

However I'm not sure how to do this.  Can anyone lead me in the right direction?

---

### Post by perler on 2006-08-04
the same problem here, mys system even sees just 2,8 gb of 4gb installed on an AMD64X2 system.

suse sees 4gb on other systems to, as a friend told me..

PAT

---

### Post by HAARP on 2006-08-04
Use a kernel that can handle that much RAM (i686, k7, not i386)
That should solve that problem. You can install them with synaptic, using linux-i686/k7

edit: I'm stupid. You are already using it :-( 
Sorry, can't help you then :/

---

