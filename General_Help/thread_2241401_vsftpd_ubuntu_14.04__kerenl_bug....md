---
title: "vsftpd ubuntu 14.04  kerenl bug..."
date: 2014-08-25
forum: General Help
---

### Post by bawoowow on 2014-08-25
1. my linux version 
# uname -a
Linux ip-192-168-10-156 3.13.0-29-generic #53-Ubuntu SMP Wed Jun 4 21:00:20 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

# cat /etc/issue
Ubuntu 14.04 LTS \n \l


2. vsftpd version 3.0.2

I did source install vsftpd.


[COLOR=#303030][FONT=Helvetica]Then, when the run , the following error may occur .

[/FONT][/COLOR]#/usr/local/sbin/vsftpd &
[1] 14262
~/vsftpd-3.0.2# 500 OOPS: munmap


[1]+  Exit 2                  /usr/local/sbin/vsftpd


(/var/log/syslog/ )
Aug 26 03:12:56 ip-192-168-10-156 kernel: [40194034.505153] BUG: Bad page map in process vsftpd  pte:8000000000000965 pmd:03167067
Aug 26 03:12:56 ip-192-168-10-156 kernel: [40194034.505177] page:ffffea0000000000 count:-79 mapcount:-79 mapping:          (null) index:0x0
Aug 26 03:12:56 ip-192-168-10-156 kernel: [40194034.505187] page flags: 0x10(dirty)
Aug 26 03:12:56 ip-192-168-10-156 kernel: [40194034.505195] addr:00007f533d28a000 vm_flags:08100071 anon_vma:ffff8800233a2300 mapping:          (null) index:7f533d28a
Aug 26 03:12:56 ip-192-168-10-156 kernel: [40194034.505205] CPU: 0 PID: 14262 Comm: vsftpd Tainted: G    B        3.13.0-29-generic #53-Ubuntu
Aug 26 03:12:56 ip-192-168-10-156 kernel: [40194034.505208]  ffff88000af42f00 ffff88000aeadc70 ffffffff8171a214 00007f533d28a000
Aug 26 03:12:56 ip-192-168-10-156 kernel: [40194034.505212]  ffff88000aeadcb8 ffffffff81174653 8000000ba6572965 00000007f533d28a
Aug 26 03:12:56 ip-192-168-10-156 kernel: [40194034.505214]  ffff880003167450 ffffea0000000000 00007f533d28a000 00007f533d28b000
Aug 26 03:12:56 ip-192-168-10-156 kernel: [40194034.505217] Call Trace:
Aug 26 03:12:56 ip-192-168-10-156 kernel: [40194034.505229]  [<ffffffff8171a214>] dump_stack+0x45/0x56
Aug 26 03:12:56 ip-192-168-10-156 kernel: [40194034.505235]  [<ffffffff81174653>] print_bad_pte+0x1a3/0x250
Aug 26 03:12:56 ip-192-168-10-156 kernel: [40194034.505238]  [<ffffffff81176037>] unmap_page_range+0x717/0x7f0
Aug 26 03:12:56 ip-192-168-10-156 kernel: [40194034.505242]  [<ffffffff81176191>] unmap_single_vma+0x81/0xf0
Aug 26 03:12:56 ip-192-168-10-156 kernel: [40194034.505245]  [<ffffffff81177209>] unmap_vmas+0x49/0x90
Aug 26 03:12:56 ip-192-168-10-156 kernel: [40194034.505249]  [<ffffffff811803bc>] exit_mmap+0x9c/0x170
Aug 26 03:12:56 ip-192-168-10-156 kernel: [40194034.505253]  [<ffffffff8106482c>] mmput+0x5c/0x120
Aug 26 03:12:56 ip-192-168-10-156 kernel: [40194034.505257]  [<ffffffff81069bbc>] do_exit+0x26c/0xa50
Aug 26 03:12:56 ip-192-168-10-156 kernel: [40194034.505262]  [<ffffffff8109dd94>] ? vtime_account_user+0x54/0x60
Aug 26 03:12:56 ip-192-168-10-156 kernel: [40194034.505268]  [<ffffffff8114d62f>] ? context_tracking_user_exit+0x4f/0xc0
Aug 26 03:12:56 ip-192-168-10-156 kernel: [40194034.505271]  [<ffffffff8106a41f>] do_group_exit+0x3f/0xa0
Aug 26 03:12:56 ip-192-168-10-156 kernel: [40194034.505274]  [<ffffffff8106a494>] SyS_exit_group+0x14/0x20
Aug 26 03:12:56 ip-192-168-10-156 kernel: [40194034.505279]  [<ffffffff8172adff>] tracesys+0xe1/0xe6
Aug 26 03:12:56 ip-192-168-10-156 kernel: [40194034.505351] BUG: Bad rss-counter state mm:ffff88000aedae00 idx:0 val:-1
Aug 26 03:12:56 ip-192-168-10-156 kernel: [40194034.505363] BUG: Bad rss-counter state mm:ffff88000aedae00 idx:1 val:1





But ubuntu12.04 lts version (kernel  3.2.0-54) normally running ok..

It was not see the link below ,  is bug in the ubuntu kernel?
[https://bugs.archlinux.org/task/38596](https://bugs.archlinux.org/task/38596)

---

