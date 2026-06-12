---
title: "adding system snapshots to ubuntu standard install"
date: 2006-08-18
forum: General Help
---

### Post by nijhawank on 2006-08-18
hello friends,

im trying to add a kind of system snapshot feature in my standard desktop install of ubuntu dapper.

basically what i intend to do is that i freeze my system state at some point in time. after this whatever i do to the system is recorded as a delta somewhere else.
this is something like vmware snapshot feature but off the real hardware without using vmware.

its actually working and now when im typing this post, all the changes are being recorded in the delta. i can install new packages, change configuration blah blah and it will go in the delta. but im observing some errors which irritates me

so first of all, how im doing it. im using unionfs to enable this snapshot feature. here is what i have done...

1. i have ubuntu dapper installed on /dev/hda1 (ext3)

2. i have another ext3 partition on /dev/hda2. this is the one im using to store all the delta, so my original install in /dev/hda1 wont be touched at all

3. i modified the default initrd to mount this extra partition (/dev/hda2) on /extra_root

4. the default scripts in init have already mounted my actual root (/dev/hda1) on /root

5. i then create a unionfs on /virtual_root by combining /extra_root and /root, making /root as a readonly branch and /extra_root as writable branch

6. after this i just use /virtual_root to call the real init _and the system boots on top of my union, and hence recording all the changes in /dev/hda2

my unionfs is configured like this
/dev/hda1 on /root (in initrd)
/dev/hda2 on /extra_root (in initrd, done by me)
command line for mounting unionfs is
mount -t unionfs -o dirs=/extra_root=rw:/root:ro unionfs /virtual_root

so one of the error that im getting is just after the real init is called, here it is... i have googled a bit and its in unionfs but the thing is that its working even with message but then why and whats the reason for this message... i was earlier getting this error when the branches of my unionfs were overlapping but it is not the case anymore...

[4294705.764000] Unable to handle kernel NULL pointer dereference at virtual address 00000050
[4294705.764000]  printing eip:
[4294705.764000] c01651d4
[4294705.764000] *pde = 00000000
[4294705.764000] Oops: 0000 [#1]
[4294705.764000] PREEMPT 
[4294705.764000] Modules linked in: ext3 jbd ide_generic ehci_hcd uhci_hcd usbcore ide_cd cdrom ide_disk piix generic thermal processor fan unionfs fbcon tileblit font bitblit softcursor capability commoncap
[4294705.764000] CPU:    0
[4294705.764000] EIP:    0060:[<c01651d4>]    Not tainted VLI
[4294705.764000] EFLAGS: 00010246   (2.6.15-23-386) 
[4294705.764000] EIP is at bio_get_nr_vecs+0x4/0x60
[4294705.764000] eax: 00000000   ebx: 00000000   ecx: 00000001   edx: 00000000
[4294705.764000] esi: c13ea9a0   edi: dfca2c3c   ebp: 00000001   esp: dfb77d84
[4294705.764000] ds: 007b   es: 007b   ss: 0068
[4294705.764000] Process readahead-list (pid: 2102, threadinfo=dfb76000 task=dfabd550)
[4294705.764000] Stack: c0185b0b 00000000 dfcb2900 ded28424 dfb77dc8 0000000c dfca2cd4 00000001 
[4294705.764000]        00000001 00000000 00000001 00000000 00000001 00000000 00000001 dfca2c3c 
[4294705.764000]        00000000 dfb77e3c 0000000d dffac940 dfb76000 def8005c 00000046 00000000 
[4294705.764000] Call Trace:
[4294705.764000]  [<c0185b0b>] do_mpage_readpage+0x40b/0x4c0
[4294705.764000]  [<c0149001>] kmem_cache_alloc+0x31/0x40
[4294705.764000]  [<c01dafd5>] radix_tree_node_alloc+0x15/0x60
[4294705.764000]  [<c01db29f>] radix_tree_insert+0xff/0x140
[4294705.764000]  [<c013fa26>] add_to_page_cache+0x46/0xb0
[4294705.764000]  [<c0185c5a>] mpage_readpages+0x9a/0x130
[4294705.764000]  [<e090f610>] ext3_get_block+0x0/0xc0 [ext3]
[4294705.764000]  [<e085fbb2>] unionfs_permission+0x72/0xd0 [unionfs]
[4294705.764000]  [<c0143f78>] prep_new_page+0x68/0x80
[4294705.764000]  [<c0144537>] buffered_rmqueue+0xc7/0x250
[4294705.764000]  [<c0147117>] read_pages+0x27/0x130
[4294705.764000]  [<e090f610>] ext3_get_block+0x0/0xc0 [ext3]
[4294705.764000]  [<c014489e>] __alloc_pages+0x4e/0x2e0
[4294705.764000]  [<c0147391>] __do_page_cache_readahead+0x171/0x1d0
[4294705.764000]  [<c0147433>] force_page_cache_readahead+0x43/0xa0
[4294705.764000]  [<c0140ab9>] do_readahead+0x39/0x40
[4294705.764000]  [<c0140b36>] sys_readahead+0x76/0x90
[4294705.764000]  [<c010302b>] sysenter_past_esp+0x54/0x79
[4294705.764000] Code: 5a 5b 5e 5f 5d c3 53 8b 44 24 04 50 e8 f6 69 06 00 5d 58 8b 53 10 eb e1 53 8b 7c 24 04 57 e8 e4 69 06 00 59 5e eb d7 8b 44 24 04 <8b> 40 50 8b 48 34 8b 81 3c 01 00 00 25 ff ff 00 00 c1 e0 09 8d 

the good thing is that its working even with this error, but i dont like errors..

the other problem is that how should i unmount all the filesystems at shutdown.

thanks in advance.

regards,
- kamal n

---

