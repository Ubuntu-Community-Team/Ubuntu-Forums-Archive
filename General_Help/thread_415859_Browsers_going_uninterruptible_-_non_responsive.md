---
title: "Browsers going uninterruptible - non responsive"
date: 2007-04-20
forum: General Help
---

### Post by | MM | on 2007-04-20
HI,

Both Opera and Firefox are going uninterpretable and non responsive.

In the case of opera the first time i try to open it, it fails to display and in system monitor you see it appear then disappear.  When you try to reopen it, it just stays in the system monitor list as uninterpretable... but never opens and i could not kill it.

Firefox at least opens i can view a few pages then it goes uninterpretable and non-responsive.  I can force quit, but then on reopen firefox and firefox-bin are uninterpretable and i cannot kill them from system monitor.

Everything was working fine yesterday... as far as i know there were no major updates, i have not made any changes, and my windows XP install is running fine.  So i am baffled.

---

### Post by | MM | on 2007-04-20
Here is what the console spews in the case of Opera (firefox does not produce anything in the console when it goes unresponsive):

NB:  The first section emboldened is normal Opera console output from my expierience. Tthe rest of the output is not, as you can see a seg fault occurs and the kernel delivers numerous error messages of which i have no comprehension.

Any help much appreciated!

Regards 
Matthew


[I][B]matthew@matthew-desktop:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device[/B]
Segmentation fault
matthew@matthew-desktop:~$ 
Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000] Assertion failure in dx_probe() at fs/ext3/namei.c:384: "dx_get_limit(entries) == dx_root_limit(dir, root->info.info_length)"

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000] ------------[ cut here ]------------

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000] invalid opcode: 0000 [#1]

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000] SMP 

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000] CPU:    0

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000] EIP:    0060:[<f8a23b51>]    Tainted: P      VLI

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000] EFLAGS: 00010292   (2.6.20-15-generic #2)

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000] EIP is at dx_probe+0x1e1/0x320 [ext3]

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000] eax: 00000090   ebx: ea870000   ecx: 00000096   edx: 00000000

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000] esi: ea870018   edi: ea8a2978   ebp: ea87d114   esp: ef9dbca8

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000] Process opera (pid: 5577, ti=ef9da000 task=f27ee560 task.ti=ef9da000)

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000] Stack: f8a2ff28 f8a2f26b f8a31d6d 00000180 f8a30078 ef9dbd94 00000000 f7ce0390 

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000]        ce23bf1c dfc2a600 ef9dbda4 ef9dbd7c ef9dbe38 f8a2474b ef9dbd7c ef9dbda4 

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000]        00000049 00248024 dfc2a600 c01976bc 00001000 f7ceb000 c0197d20 ea8a29b0 

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000] Call Trace:

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000]  [<f8a2474b>] ext3_find_entry+0x28b/0x640 [ext3]

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000]  [__getblk+44/688] __getblk+0x2c/0x2b0

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000]  [sync_buffer+0/64] sync_buffer+0x0/0x40

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000]  [<f8a1ef0e>] __ext3_get_inode_loc+0x11e/0x340 [ext3]

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000]  [cache_alloc_refill+113/1360] cache_alloc_refill+0x71/0x550

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000]  [<f8a2620c>] ext3_lookup+0x3c/0x100 [ext3]

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000]  [d_alloc+263/400] d_alloc+0x107/0x190

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000]  [do_lookup+328/400] do_lookup+0x148/0x190

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000]  [__link_path_walk+309/3696] __link_path_walk+0x135/0xe70

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000]  [do_lookup+101/400] do_lookup+0x65/0x190

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000]  [link_path_walk+69/192] link_path_walk+0x45/0xc0

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000]  [do_path_lookup+131/448] do_path_lookup+0x83/0x1c0

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000]  [getname+167/208] getname+0xa7/0xd0

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000]  [__user_walk_fd+59/96] __user_walk_fd+0x3b/0x60

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000]  [vfs_stat_fd+34/96] vfs_stat_fd+0x22/0x60

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000]  [sys_stat64+15/48] sys_stat64+0xf/0x30

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000]  =======================

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000] Code: 44 24 10 78 00 a3 f8 c7 44 24 0c 80 01 00 00 c7 44 24 08 6d 1d a3 f8 c7 44 24 04 6b f2 a2 f8 c7 04 24 28 ff a2 f8 e8 bf 30 70 c7 <0f> 0b eb fe 89 44 24 0c c7 44 24 08 50 00 a3 f8 c7 44 24 04 6b 

Message from syslogd@localhost at Sat Apr 21 10:15:36 2007 ...
localhost kernel: [  159.160000] EIP: [<f8a23b51>] dx_probe+0x1e1/0x320 [ext3] SS:ESP 0068:ef9dbca8
[/I]

---

### Post by Colonel Kilkenny on 2007-04-21
> **| MM | said:**
> 
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device[/B]
Segmentation fault


First two rows say that Opera cannot find Java. Nothing to worry, you can fix it after you get it going.
X errors are also nothing to worry about. They are because xorg.conf has configured input devices which you don't have (Wacom paint tablets or whatever their name is...), you can remove all the traces of them from xorg.conf if you know how to do it. But be careful if you decide to do it..
And segmentation fault is the major problem here. It is caused by X libraries which were upgraded a while ago. That can be fixed by upgrading Opera. The last version is 9.20 and it is available from opera.com. Just fetch the ubuntu .deb-package to desktop and install it with doubleclicking on it.

I have no idea about those kernel errors. They look quite scary / important to me..

---

