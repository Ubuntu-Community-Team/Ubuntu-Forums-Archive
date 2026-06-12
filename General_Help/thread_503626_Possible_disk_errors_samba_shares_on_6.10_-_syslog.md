---
title: "Possible disk errors samba shares on 6.10 - syslog help needed"
date: 2007-07-18
forum: General Help
---

### Post by DaiLaughing on 2007-07-18
6.10 server install used mainly to run samba for family PCs on LAN but also apache for playing.  All samba/apache data on a second drive (hdb1) mounted as one dir.  If I access lots of files (e.g. copy to local PC over network) I will often lose contact with the server and have to reboot it.  

This latest error I saw as it happened as I had a PUTTY session open while I did a full (/) backup with tar.  The backup went fine until it got part way through the samba shared directories and then I got the errors below.  The samba (and apache) data is on a separate drive which makes me think disk hardware problem.  fsck does find problems but I assume that could be caused by the problem.  I have just set up a mirrored raid on two other drives and will swap the data over.  Before I do is there another problem and would I be wasting my time.

I'll paste the lot as I have no idea what it means and what is important.  I am not experienced with this stuff so be gentle with me.  I have rtfmed but don't really know where to look next so point me to the answer:

___________________________________________________________________

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000] kernel BUG at fs/buffer.c:2793!

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000] invalid opcode: 0000 [#1]

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000] SMP

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000] CPU:    0

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000] EIP is at submit_bh+0x124/0x140

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000] eax: 00007d29   ebx: e5fd7e3c   ecx: 0000003                                  7   edx: e5fd7e3c

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000] esi: 00000001   edi: 00000000   ebp: ec57ba9                                  8   esp: ef527d74

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000] Process pdflush (pid: 108, threadinfo=ef5260                                  00 task=dff80050)

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000] Stack: 00000001 e5fd7e3c 00000001 00000000 e                                  c57ba98 c016d835 efe01014 e34943ec

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000]        00000000 00000003 f08fb520 c1590e20 0                                  0000000 00017289 00000000 e5fd7e3c

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000]        00001000 00000000 ec57ba98 c1590e20 0                                  0000000 c016dca8 ef527f4c 00000000

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000] Call Trace:

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000]  <c016d835> __block_write_full_page+0x1f5/0x                                  390  <f08fb520> ext3_get_block+0x0/0x100 [ext3]

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000]  <c016dca8> block_write_full_page+0xf8/0x100                                    <f08fb520> ext3_get_block+0x0/0x100 [ext3]

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000]  <f08fcf60> ext3_ordered_writepage+0x100/0x1                                  d0 [ext3]  <f08f9a10> bget_one+0x0/0x10 [ext3]

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000]  <f08fce60> ext3_ordered_writepage+0x0/0x1d0                                   [ext3]  <c018f3e7> mpage_writepages+0x1b7/0x3c0

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000]  <c018f371> mpage_writepages+0x141/0x3c0  <f                                  08fce60> ext3_ordered_writepage+0x0/0x1d0 [ext3]

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000]  <c0150a1b> do_writepages+0x4b/0x50  <c018d5                                  94> __writeback_single_inode+0x94/0x3c0

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000]  <c012ace7> try_to_del_timer_sync+0x47/0x50                                    <c012acfa> del_timer_sync+0xa/0x10

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000]  <c02d81c0> schedule_timeout+0x50/0xc0  <c01                                  8db05> sync_sb_inodes+0x185/0x250

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000]  <c018e11a> writeback_inodes+0x9a/0xcd  <c01                                  50d45> background_writeout+0x85/0xa0

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000]  <c0151410> pdflush+0x0/0x1c0  <c0151501> pd                                  flush+0xf1/0x1c0

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000]  <c0150cc0> background_writeout+0x0/0xa0  <c                                  0134e2b> kthread+0xab/0xe0

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000]  <c0134d80> kthread+0x0/0xe0  <c0101005> ker                                  nel_thread_helper+0x5/0x10

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000] Code: 5e 5f 5d c3 8d 76 00 90 0f ba 33 0b e9                                   57 ff ff ff 0f 0b eb 0a 97 66 2f c0 e9 14 ff ff ff 0f 0b ea 0a 97 66 2f c0 e9 f                                  c fe ff ff <0f> 0b e9 0a 97 66 2f c0 e9 e5 fe ff ff eb 0d 90 90 90 90 90 90

Message from syslogd@localhost at Wed Jul 18 07:51:42 2007 ...
localhost kernel: [43026852.690000] EIP: [submit_bh+292/320] submit_bh+0x124/0x1                                  40 SS:ESP 0068:ef527d74

_________________________________________________________________

fsck this time found no bad blocks but locked on Pass 1.  Trying to reboot from another PuTTY session sent the warning but no reboot happened.  Tried kill on fsck but wouldn't and still could not reboot.  After hardware reboot fsck found no errors.  Tried the backup again and the system just locked and died (not at same file - a bit later on).

TIA

Edit: was able to successfully copy all directories from hdb2 to new raid.  Then tried to backup from that raid and got same problem - system hang.  So not likely to be hard disk error then?  Might try to backup without compression next...

---

### Post by DaiLaughing on 2007-07-19
Replying to my own post just in case anyone else finds it useful.  

After trying many other things I increased the voltage (vcc) on my CPU and it all became wonderful.  It is/was not overclocked and had run in another motherboard at the recommended voltage for years but for some reason I thought I'd try it.  Upped from 1.75 to 1.8 and it became stable.

---

