---
title: "mouting a UDF CD"
date: 2007-11-12
forum: General Help
---

### Post by bashveank on 2007-11-12
My friend gave my a CD burned using UDF and I can't figure out how to mount it.

This is what I get from mount /dev/cdrom1 /media/cdrom 
mount: block device /dev/scd1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Same thing if I -t udf it
here's the dmesg | tail

[174772.610297] Unable to identify CD-ROM format.
[174945.706097] UDF-fs: No fileset found
[174945.843038] Unable to identify CD-ROM format.
[175114.388459] FAT: bogus number of reserved sectors
[175114.388470] VFS: Can't find a valid FAT filesystem on dev sr1.
[175119.663565] UDF-fs: No fileset found
[175154.579053] UDF-fs: No fileset found
[175259.204889] UDF-fs: No fileset found
[175316.995780] UDF-fs: No fileset found
[175431.620722] UDF-fs: No fileset found


If someone could help me that'd be great.

---

### Post by Fibonacci on 2008-02-07
I'm having exactly the same problem here.

---

### Post by paranoid_humanoid on 2008-04-03
me too

---

### Post by Speels on 2008-04-27
*bump*

Me too

I found a patch: [http://groups.google.com/group/linux.kernel/browse_thread/thread/0645fc915322343c]("http://groups.google.com/group/linux.kernel/browse_thread/thread/0645fc915322343c"), but I don't know how to apply it. Seems I need the code of my kernel, and then applying the patch.

-edit- retried it with libudf0 installed. No result :-(

---

### Post by Scoubidou on 2008-05-28
Bump

Same here :(

---

