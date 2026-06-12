---
title: "MySQL slow on ubuntu server 22.04"
date: 2023-01-27
forum: General Help
---

### Post by patdundee on 2023-01-27
Hi Guys
I have 2 servers 
Server A ) Ubuntu 22.04 (Clean Install) running on Intel(R) Xeon(R) CPU E3-1220 v3 @ 3.10GHz, 4 cores with 32GB Ram MySql Server version:                8.0.32
Server B ) Ubuntu 20.o4 (Clean Install) running on Intel(R) Xeon(R) CPU           E5420  @ 2.50GHz, 8 cores with 32GB Ram Server MySql Server version:                8.0.32

Not much difference in the CPU's

Identical setup in mysql files

My Question is why would the MySQL server on Ubuntu Server 22.04 run extremely slow but the MySQL server on Ubuntu Server 20.04 is lightning fast

Any odeas would be greatly appreciated

Many thanks

---

### Post by TheFu on 2023-01-27
What sort of server monitoring do you have setup?  Munin, sysusage are pretty easy.  Those are the easier ones, but there's cacti and Zabbix too.

When you have monitoring setup, you'll be able to see what is causing the slowdowns.
Generally, it comes down to
* wrong configs / incorrect access
* slow networking (needs correct drivers all along the path)
* slow disk subsystem (needs tuning)
* not sufficient RAM
* software bug

Performance monitoring is something every server should have anyways, so I'd start there.  Blame the DBA first, then the Server Admin, then work your way out, AFTER the internal issues have all been researched.  It is almost never the networking, so if you get to that point, assume you are still wrong and be nice asking for the network guys to help.  Sometimes is it the networking ... a recent change like closing open connections every 24 hrs has caught my projects before.  That pesky security vs convenience issue strikes once in a while too.

Are these virtual machines?  There is tuning for those too.
Some of Intel's CPU bug fixes drastically impact performance, especially for DBMS loads.  Check into those.

Anyway, that should be plenty to research for now.

---

### Post by ActionParsnip on 2023-01-27
How did you deploy the SQL configs? Are they the same? What storage is in both? Are they using SSDs or are there some platter based drives somewhere here....? SQL hammers storage so simply stating the CPU and RAM isn't sufficient.

---

