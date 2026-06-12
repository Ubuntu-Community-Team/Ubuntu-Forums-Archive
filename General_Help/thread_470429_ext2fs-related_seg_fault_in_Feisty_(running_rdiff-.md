---
title: "ext2fs-related seg fault in Feisty (running rdiff-backup)"
date: 2007-06-11
forum: General Help
---

### Post by mattengland on 2007-06-11
I'm experiencing this seg fault (quoted below) with a pretty consistent error message when running rdiff-backup's.  Note I've run these backups for a few years now without problem, and now when doing it with the same basic data set on a freshly-installed Feisty install causes this problem.  I plan on installing back down to 6.06 to see if it still happens.

I have already tried downrevving the e2fslibs and e2fsprogs packages to 1.39 (the Edgy flavor) with Feisty loaded, with no luck.

Any other thoughts?

```

mengland@matts-laptop:~$ rdiff-backup -v6 /data /datab2/data.rdiff-backup/
Unable to import module xattr.
Extended attributes not supported on filesystem at /data
Unable to import module posix1e from pylibacl package.
ACLs not supported on filesystem at /data
-----------------------------------------------------------------
Detected abilities for source (read only) file system:
  Access control lists                         Off
  Extended attributes                          Off
  Case sensitivity                             On
  Mac OS X style resource forks                Off
  Mac OS X Finder information                  Off
-----------------------------------------------------------------
Making directory /datab2/data.rdiff-backup/rdiff-backup-data/rdiff-backup.tmp.1
Making directory /datab2/data.rdiff-backup/rdiff-backup-data/rdiff-backup.tmp.1/hl
Hard linking /datab2/data.rdiff-backup/rdiff-backup-data/rdiff-backup.tmp.1/hl/hardlinked_file2 to /datab2/data.rdiff-backup/rdiff-backup-data/rdiff-backup.tmp.1/hardlinked_file1
Unable to import module xattr.
Extended attributes not supported on filesystem at /datab2/data.rdiff-backup/rdiff-backup-data/rdiff-backup.tmp.1
Unable to import module posix1e from pylibacl package.
ACLs not supported on filesystem at /datab2/data.rdiff-backup/rdiff-backup-data/rdiff-backup.tmp.1
Removing directory /datab2/data.rdiff-backup/rdiff-backup-data/rdiff-backup.tmp.1
-----------------------------------------------------------------
Detected abilities for destination (read/write) file system:
  Ownership changing                           Off
  Hard linking                                 On
  fsync() directories                          On
  Directory inc permissions                    On
  High-bit permissions                         On
  Extended filenames                           On
  Access control lists                         Off
  Extended attributes                          Off
  Case sensitivity                             On
  Mac OS X style resource forks                Off
  Mac OS X Finder information                  Off
-----------------------------------------------------------------
Writing mirror marker /datab2/data.rdiff-backup/rdiff-backup-data/current_mirror.2007-06-10T23:23:09-05:00.data
Starting increment operation /data to /datab2/data.rdiff-backup
Processing changed file .
Incrementing mirror file /datab2/data.rdiff-backup
Processing changed file data.personal
Incrementing mirror file /datab2/data.rdiff-backup/data.personal
Processing changed file data.personal/email.eudora.personal
Incrementing mirror file /datab2/data.rdiff-backup/data.personal/email.eudora.personal
Segmentation fault

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000] Assertion failure in dx_probe() at fs/ext3/namei.c:384: "dx_get_limit(entries) == dx_root_limit(dir, root->info.info_length)"

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000] ------------[ cut here ]------------

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000] invalid opcode: 0000 [#1]

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000] SMP 

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000] CPU:    0

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000] EIP:    0060:[<f89d0b51>]    Tainted: P      VLI

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000] EFLAGS: 00210286   (2.6.20-16-generic #2)

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000] EIP is at dx_probe+0x1e1/0x320 [ext3]

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000] eax: 00000090   ebx: f4193000   ecx: 00200082   edx: 00000000

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000] esi: f4193018   edi: f4160358   ebp: f4151e50   esp: f7e99e40

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000] Process rdiff-backup (pid: 5511, ti=f7e98000 task=f6d10030 task.ti=f7e98000)
mengland@matts-laptop:~$ 
Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000] Stack: f89dcf28 f89dc26b f89ded6d 00000180 f89dd078 f7e99ea8 00000000 00000007 

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000]        00000000 f6d1fb40 00000000 00000000 f4151e50 f89d1edd f7e99e90 f7e99ebc 

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000]        f6fc2140 00000000 00000000 f6058e00 00000000 f6058e00 f6fc2144 00000000 

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000] Call Trace:

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000]  [<f89d1edd>] ext3_htree_fill_tree+0xad/0x200 [ext3]

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000]  [<f89db610>] ext3_permission+0x0/0x10 [ext3]

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000]  [<f89ca062>] ext3_readdir+0x112/0x640 [ext3]

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000]  [copy_to_user+41/80] copy_to_user+0x29/0x50

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000]  [cp_new_stat64+249/272] cp_new_stat64+0xf9/0x110

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000]  [filldir64+0/224] filldir64+0x0/0xe0

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000]  [sys_fstat64+30/48] sys_fstat64+0x1e/0x30

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000]  [filldir64+0/224] filldir64+0x0/0xe0

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000]  [vfs_readdir+148/176] vfs_readdir+0x94/0xb0

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000]  [sys_getdents64+111/192] sys_getdents64+0x6f/0xc0

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000]  =======================

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000] Code: 44 24 10 78 d0 9d f8 c7 44 24 0c 80 01 00 00 c7 44 24 08 6d ed 9d f8 c7 44 24 04 6b c2 9d f8 c7 04 24 28 cf 9d f8 e8 bf 60 75 c7 <0f> 0b eb fe 89 44 24 0c c7 44 24 08 50 d0 9d f8 c7 44 24 04 6b 

Message from syslogd@matts-laptop at Sun Jun 10 23:23:31 2007 ...
matts-laptop kernel: [  319.632000] EIP: [<f89d0b51>] dx_probe+0x1e1/0x320 [ext3] SS:ESP 0068:f7e99e40
mengland@matts-laptop:~$ 
mengland@matts-laptop:~$ 
mengland@matts-laptop:~$ 
mengland@matts-laptop:~$ 
mengland@matts-laptop:~$ date
Sun Jun 10 23:25:56 CDT 2007
mengland@matts-laptop:~$ uname -a
Linux matts-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux
mengland@matts-laptop:~$ cat /etc/issue
Ubuntu 7.04 \n \l

mengland@matts-laptop:~$ 

```

---

### Post by reidms on 2007-06-11
I would run memtest of the live cd to make sure your memory is not corrupted
Also make sure your system is cooling properly

---

### Post by mattengland on 2007-06-11
> **reidms said:**
> I would run memtest of the live cd to make sure your memory is not corrupted
Also make sure your system is cooling properly

Ok, I'm doing that and am basically in the process of investigating hardware problems in general (as per implied by your comments and as a general debugging rule on my part).

Is there anything in the data above that leads you to make these specific recommendations?

---

### Post by mattengland on 2007-06-23
Ok, I've run a variety of tests in 2 different categories:  1) testing my laptop's hardware, and 2) executing the same scenarios in Dapper that caused the above problems for Feisty.  I found no hardware problems (after memory tests and smartmon hard-drive tests).  I found that Feisty experiences the above fault and Dapper does not, for almost an identical data set.  I have immediately discontinued use of Feisty.

This would seem to me like a significant red flag for Feisty and concern for any Feisty certifiers/testers.  What's the best way/place to "shoot this up the flag pole"?  If I remember correctly, the Ubuntu team uses launchpad.net for bug management?

Note that I often boot this laptop to windows and mount said data set, which lives on an ext3 fs, in Windows using the Ext2 Installable File System rev 1.10c (a windows ext2/ext3 driver), found here: [http://www.fs-driver.org/](http://www.fs-driver.org/) .  Lots of Windows apps (namely Eudora) access this ext3-based data set.  I have no data to suggest that this is a contributing factor, but I note it because it may make my test scenario unique.

---

### Post by mattengland on 2007-06-25
Bump.  I'm curious how I should followup this issue (bug, etc)?  I would like to be able to one day run Feisty, even though this might take a while to investigate and/or fix.

---

### Post by mattengland on 2007-06-26
fyi, I've created this bug per this issue:

[https://bugs.launchpad.net/ubuntu/+bug/122369](https://bugs.launchpad.net/ubuntu/+bug/122369)

---

