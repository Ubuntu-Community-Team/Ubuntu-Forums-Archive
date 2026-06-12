---
title: "ext2 filesystem corrupted?"
date: 2007-08-05
forum: General Help
---

### Post by davidsiegel on 2007-08-05
I was using an ext2/3 filesystem driver while booted in Windows XP to save some data in my ~/Music directory on my Ubuntu ext2 partition. Now ~/Music is not accessible

```

$ ls ~/Music
Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000] Assertion failure in dx_probe() at fs/ext3/namei.c:384: "dx_get_limit(entries) == dx_root_limit(dir, root->info.info_length)"

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000] ------------[ cut here ]------------

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000] invalid opcode: 0000 [#1]

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000] SMP 

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000] CPU:    0

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000] EIP:    0060:[<f8a50b51>]    Not tainted VLI

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000] EIP is at dx_probe+0x1e1/0x320 [ext3]

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000] eax: 00000090   ebx: dcc03000   ecx: 00200082   edx: 00000000

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000] esi: dcc03018   edi: e3394390   ebp: dd2f34dc   esp: e6b93e40

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000] Process ls (pid: 6482, ti=e6b92000 task=ed524030 task.ti=e6b92000)

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000] Stack: f8a5cf28 f8a5c26b f8a5ed6d 00000180 f8a5d078 e6b93ea8 00000000 00000003 

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000]        00000000 f77efee0 00000000 00000000 dd2f34dc f8a51edd e6b93e90 e6b93ebc 

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000]        dff4cfc0 00000000 00000000 e10d2440 00000000 e10d2440 c0177adf 00000000 

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000] Call Trace:

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000]  [<f8a51edd>] ext3_htree_fill_tree+0xad/0x200 [ext3]

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000] EFLAGS: 00210286   (2.6.20-16-generic #2)

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000]  [get_empty_filp+111/336] get_empty_filp+0x6f/0x150

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000]  [<f8a5b610>] ext3_permission+0x0/0x10 [ext3]

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000]  [<f8a4a062>] ext3_readdir+0x112/0x640 [ext3]

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000]  [filldir64+0/224] filldir64+0x0/0xe0

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000]  [filldir64+0/224] filldir64+0x0/0xe0

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000]  [vfs_readdir+148/176] vfs_readdir+0x94/0xb0

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000]  [sys_getdents64+111/192] sys_getdents64+0x6f/0xc0

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000]  =======================

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000] Code: 44 24 10 78 d0 a5 f8 c7 44 24 0c 80 01 00 00 c7 44 24 08 6d ed a5 f8 c7 44 24 04 6b c2 a5 f8 c7 04 24 28 cf a5 f8 e8 bf 60 6d c7 <0f> 0b eb fe 89 44 24 0c c7 44 24 08 50 d0 a5 f8 c7 44 24 04 6b 

Message from syslogd@aesop at Sun Aug  5 17:27:13 2007 ...
aesop kernel: [  152.560000] EIP: [<f8a50b51>] dx_probe+0x1e1/0x320 [ext3] SS:ESP 0068:e6b93e40

```I tried running fdisk, but that didn't detect or correct any errors. What happened? What can I do?

---

### Post by Bachstelze on 2007-08-05
Boot from a live CD and do (as root) :

```
e2fsck -fy /dev/hda1
```

(of course replace hda1 with the correct name of your partition)

---

