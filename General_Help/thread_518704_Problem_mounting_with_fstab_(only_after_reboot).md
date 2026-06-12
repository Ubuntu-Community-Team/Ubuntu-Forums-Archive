---
title: "Problem mounting with fstab (only after reboot)"
date: 2007-08-06
forum: General Help
---

### Post by forgeuk on 2007-08-06
Having a bit of a problem with automatic mounting, I've reinstalled Ubuntu a few times overs the past year or so, and thought I'd got the hang on mounting using fstab, but this time around, its just not working right.

Heres the two important lines in my fstab:

```
/dev/sda5 /media/Stuff auto user,auto 1 1
/dev/hdb1 /media/WinXP ntfs-3g defaults,locale=en_GB.UTF-8 0 0
```

So sda5 (Stuff) is an ext3 partition with all my stuff in it
and hdb1 (WinXP) is the XP partition (NTFS configuration tool put the 2nd line in for me)

When booting up, it seems to stick when mounting them both, if I double click them, nothing happens, if I navigate to /media it locks up nautilus and eventually displays the Stuff and WinXP as blank files rather than folders for mount points.

Now, heres the weird bit, if I # out those two lines, restart, everything is fine, I add them back in and do a sudo mount -a and I can access both mounts! if I then restart again, I'm back to not being able to access them.

any help?

p.s. using feisty.

---

### Post by forgeuk on 2007-08-06
UPDATE : just been playing around with it, and when doing a sudo mount -a it came up with all the techy-gibberish, anyone translate it into english?

```
Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.603315] Assertion failure in dx_probe() at fs/ext3/namei.c:384: "dx_get_limit(entries) == dx_root_limit(dir, root->info.info_length)"

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.603369] ------------[ cut here ]------------

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.603377] invalid opcode: 0000 [#1]

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.603379] SMP 

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.603496] CPU:    1

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.603498] EIP:    0060:[<f8a86b51>]    Tainted: P      VLI

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.603500] EFLAGS: 00210292   (2.6.20-16-generic #2)

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.603520] EIP is at dx_probe+0x1e1/0x320 [ext3]

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.603524] eax: 00000090   ebx: f5026000   ecx: 00200096   edx: 00000000

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.603529] esi: f5026018   edi: f5613d30   ebp: f57fcc2c   esp: f50b5ca8

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.603533] ds: 007b   es: 007b   ss: 0068

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.603537] Process trashapplet (pid: 5662, ti=f50b4000 task=dfe3b030 task.ti=f50b4000)

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.603541] Stack: f8a92f28 f8a9226b f8a94d6d 00000180 f8a93078 f50b5d94 00000000 00000000 

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.603552]        6f947d78 dfc6ec00 f50b5da4 f50b5d7c f50b5e38 f8a8774b f50b5d7c f50b5da4 

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.603564]        00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000 

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.603573] Call Trace:

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.603625]  [<f8a8774b>] ext3_find_entry+0x28b/0x640 [ext3]

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.603834]  [<f8a8920c>] ext3_lookup+0x3c/0x100 [ext3]

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.603857]  [d_alloc+263/400] d_alloc+0x107/0x190

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.603887]  [do_lookup+328/400] do_lookup+0x148/0x190

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.603923]  [__link_path_walk+2151/3696] __link_path_walk+0x867/0xe70

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.604004]  [link_path_walk+69/192] link_path_walk+0x45/0xc0

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.604098]  [do_path_lookup+131/448] do_path_lookup+0x83/0x1c0

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.604113]  [getname+167/208] getname+0xa7/0xd0

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.604133]  [__user_walk_fd+59/96] __user_walk_fd+0x3b/0x60

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.604158]  [vfs_lstat_fd+31/80] vfs_lstat_fd+0x1f/0x50

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.604248]  [sys_lstat64+15/48] sys_lstat64+0xf/0x30

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.604265]  [copy_process+861/4576] copy_process+0x35d/0x11e0

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.604326]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.604395]  =======================

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.604397] Code: 44 24 10 78 30 a9 f8 c7 44 24 0c 80 01 00 00 c7 44 24 08 6d 4d a9 f8 c7 44 24 04 6b 22 a9 f8 c7 04 24 28 2f a9 f8 e8 bf 00 6a c7 <0f> 0b eb fe 89 44 24 0c c7 44 24 08 50 30 a9 f8 c7 44 24 04 6b 

Message from syslogd@linux at Mon Aug  6 13:33:16 2007 ...
linux kernel: [ 2881.604456] EIP: [<f8a86b51>] dx_probe+0x1e1/0x320 [ext3] SS:ESP 0068:f50b5ca8

```

---

### Post by Steve1961 on 2007-08-06
> **forgeuk said:**
> Having a bit of a problem with automatic mounting, I've reinstalled Ubuntu a few times overs the past year or so, and thought I'd got the hang on mounting using fstab, but this time around, its just not working right.

Heres the two important lines in my fstab:

```
/dev/sda5 /media/Stuff auto user,auto 1 1
/dev/hdb1 /media/WinXP ntfs-3g defaults,locale=en_GB.UTF-8 0 0
```

So sda5 (Stuff) is an ext3 partition with all my stuff in it
and hdb1 (WinXP) is the XP partition (NTFS configuration tool put the 2nd line in for me)

When booting up, it seems to stick when mounting them both, if I double click them, nothing happens, if I navigate to /media it locks up nautilus and eventually displays the Stuff and WinXP as blank files rather than folders for mount points.

Now, heres the weird bit, if I # out those two lines, restart, everything is fine, I add them back in and do a sudo mount -a and I can access both mounts! if I then restart again, I'm back to not being able to access them.

any help?

p.s. using feisty.

Try 

/dev/sda5 /media/Stuff ext3 defaults 1 1

---

### Post by forgeuk on 2007-08-07
Found the problem. I've been dual booting, and this time I put "IFS.." on so I can read/write to my linux partitions from Windows. This is the problem, the driver is a bit buggy, in that it corrupts ext3 partitions.

Didn't loose any data, as fsck repaired the partition and now it mounts fine. 

So, avoid putting this on [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by merlinus on 2007-08-07
I have not had this problem.

-merlin

---

### Post by forgeuk on 2007-08-07
Do you Write to the linux partition from XP ?
I think its OK if you read only from linux.

---

