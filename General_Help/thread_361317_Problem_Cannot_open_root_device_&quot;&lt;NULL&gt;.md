---
title: "Problem :Cannot open root device &quot;&lt;NULL&gt;&quot; or unknown-block(8,3)"
date: 2007-02-14
forum: General Help
---

### Post by yobikap on 2007-02-14
I have a problem with my server, everytime when I restart my server I get this error:

Please append a correct "root=" boot option
Kernelpanic - not syncing: VFS: Unable to mount root on unknown-block(8,3)
VFS: Cannot open root device "<NULL>" or unknown-block(8,3)

And then the server stuck, it doesn't respond.

If someone could help me I would appreciate it, because I need the files that's on the harddisk.

I have also tried to boot from the commandline at startup, I get the same error.

The kernel what I am using is: 2.6.15-26-386
The computer spec's are: pentium 2 500mhz, 196 MB ram and 10 GB harddisk.

I haven't reinstalled the system, one week ago everythig worked fine untill yesterday, I had rebooted the system because of some problem with php server (I hadn't change things on the system.

---

### Post by pks_loss on 2008-05-08
I had this issue when I was installing slackware onto my machine. Here's what I did to fix it.

 Reformat the partition that your linux machine is booting off of, make sure that you do a slow, complete format. Then make sure that your bootloader is configured correctly to boot the right partition from the correct drive. 

 Good luck,

     -- pk

---

