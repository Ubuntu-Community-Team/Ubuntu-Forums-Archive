---
title: "Problem mounting Large HFS+ drive [ 5.4 TB ]"
date: 2013-01-31
forum: General Help
---

### Post by zimbot on 2013-01-31
Friends,

I am happily able to mount read/write a HFS+ ( non-journaled ) mac drive on my ubuntu 12.4 64 bit machine.
The size was 1 TB or 2 TB

But when I tried to mount a 5.4 TB drive I have problems
( note same drive works on a ubuntu 10.4 32 bit system )

the err diag is.
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdc3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

if I look at dmesg
<snip>
[204213.746752] sd 15:0:0:0: [sdc] Very big device. Trying to use READ CAPACITY(16).
[204213.761752] sd 15:0:0:0: [sdc] Attached SCSI disk
[204214.116375] hfs: invalid secondary volume header
[204214.116380] hfs: unable to find HFS+ superblock
</snip>

so in some googling I see that there is a Bug
and maybe a patch -- so my Q
is there a patch that will allow my Ubuntu 12.4 64bit machine
to mount this Large HFS drive.
how to get and how to use the patch?

Thanks much!

---

