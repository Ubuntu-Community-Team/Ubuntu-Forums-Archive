---
title: "&quot;Call Trace&quot; indication of an issue ??"
date: 2013-03-26
forum: General Help
---

### Post by clubbing80s on 2013-03-26
Hi. 

I'm seeing the the Call Traces below what do they mean , should I be concerned ?

[    1.707448] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[    1.707565] cpuidle: using governor ladder
[    1.707727] cpuidle: using governor menu
[    1.707728] EFI Variables Facility v0.08 2004-May-17
[    1.719132] ------------[ cut here ]------------
[    1.719137] WARNING: at /build/buildd/linux-3.2.0/fs/sysfs/dir.c:481 sysfs_add_one+0xc8/0x100()
[    1.719138] Hardware name: HP Compaq 8200 Elite SFF PC
[    1.719139] sysfs: cannot create duplicate filename '/firmware/efi/vars/SlotPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9'
[    1.719140] Modules linked in:
[    1.719142] Pid: 1, comm: swapper/0 Not tainted 3.2.0-38-generic #61-Ubuntu
[    1.719143] Call Trace:
[    1.719147]  [<ffffffff81067e3f>] warn_slowpath_common+0x7f/0xc0
[    1.719149]  [<ffffffff81067f36>] warn_slowpath_fmt+0x46/0x50
[    1.719153]  [<ffffffff81315fd0>] ? strlcat+0x60/0x80
[    1.719155]  [<ffffffff811ef5b8>] sysfs_add_one+0xc8/0x100
[    1.719156]  [<ffffffff811ef667>] create_dir+0x77/0xd0
[    1.719158]  [<ffffffff811ef76d>] sysfs_create_dir+0x7d/0xc0
[    1.719160]  [<ffffffff8130f111>] kobject_add_internal+0xb1/0x200
[    1.719162]  [<ffffffff8130f543>] kobject_init_and_add+0x63/0x90
[    1.719165]  [<ffffffff8151a240>] ? efivar_create_sysfs_entry+0x130/0x1c0
[    1.719167]  [<ffffffff8151a22a>] efivar_create_sysfs_entry+0x11a/0x1c0
[    1.719170]  [<ffffffff8151aa32>] register_efivars+0xc2/0x290
[    1.719172]  [<ffffffff81d37ab9>] ? edd_init+0x1a3/0x1a3
[    1.719174]  [<ffffffff81d37b5f>] efivars_init+0xa6/0xf3
[    1.719177]  [<ffffffff81002040>] do_one_initcall+0x40/0x180
[    1.719179]  [<ffffffff81cfccf5>] kernel_init+0xe5/0x164
[    1.719182]  [<ffffffff81667af4>] kernel_thread_helper+0x4/0x10
[    1.719184]  [<ffffffff81cfcc10>] ? start_kernel+0x3bd/0x3bd
[    1.719186]  [<ffffffff81667af0>] ? gs_change+0x13/0x13
[    1.719189] ---[ end trace c630880989f0c2f2 ]---
[    1.719191] kobject_add_internal failed for SlotPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9 with -EEXIST, don't try to register things with the same name in the same directory.
[    1.719193] Pid: 1, comm: swapper/0 Tainted: G        W    3.2.0-38-generic #61-Ubuntu
[    1.719194] Call Trace:
[    1.719196]  [<ffffffff8130f1b5>] kobject_add_internal+0x155/0x200
[    1.719197]  [<ffffffff8130f543>] kobject_init_and_add+0x63/0x90
[    1.719199]  [<ffffffff8151a240>] ? efivar_create_sysfs_entry+0x130/0x1c0
[    1.719202]  [<ffffffff8151a22a>] efivar_create_sysfs_entry+0x11a/0x1c0
[    1.719204]  [<ffffffff8151aa32>] register_efivars+0xc2/0x290
[    1.719206]  [<ffffffff81d37ab9>] ? edd_init+0x1a3/0x1a3
[    1.719207]  [<ffffffff81d37b5f>] efivars_init+0xa6/0xf3
[    1.719209]  [<ffffffff81002040>] do_one_initcall+0x40/0x180
[    1.719211]  [<ffffffff81cfccf5>] kernel_init+0xe5/0x164
[    1.719213]  [<ffffffff81667af4>] kernel_thread_helper+0x4/0x10
[    1.719214]  [<ffffffff81cfcc10>] ? start_kernel+0x3bd/0x3bd
[    1.719216]  [<ffffffff81667af0>] ? gs_change+0x13/0x13
[    1.719336] ------------[ cut here ]------------
[    1.719338] WARNING: at /build/buildd/linux-3.2.0/fs/sysfs/dir.c:481 sysfs_add_one+0xc8/0x100()
[    1.719339] Hardware name: HP Compaq 8200 Elite SFF PC
[    1.719340] sysfs: cannot create duplicate filename '/firmware/efi/vars/FrontUsbPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9'
[    1.719341] Modules linked in:
[    1.719342] Pid: 1, comm: swapper/0 Tainted: G        W    3.2.0-38-generic #61-Ubuntu
[    1.719343] Call Trace:
[    1.719345]  [<ffffffff81067e3f>] warn_slowpath_common+0x7f/0xc0
[    1.719347]  [<ffffffff81067f36>] warn_slowpath_fmt+0x46/0x50
[    1.719349]  [<ffffffff81315fd0>] ? strlcat+0x60/0x80
[    1.719350]  [<ffffffff811ef5b8>] sysfs_add_one+0xc8/0x100
[    1.719352]  [<ffffffff811ef667>] create_dir+0x77/0xd0
[    1.719354]  [<ffffffff811ef76d>] sysfs_create_dir+0x7d/0xc0
[    1.719356]  [<ffffffff8130f111>] kobject_add_internal+0xb1/0x200
[    1.719357]  [<ffffffff8130f543>] kobject_init_and_add+0x63/0x90
[    1.719359]  [<ffffffff8151a240>] ? efivar_create_sysfs_entry+0x130/0x1c0
[    1.719361]  [<ffffffff8151a22a>] efivar_create_sysfs_entry+0x11a/0x1c0
[    1.719363]  [<ffffffff8151aa32>] register_efivars+0xc2/0x290
[    1.719365]  [<ffffffff81d37ab9>] ? edd_init+0x1a3/0x1a3
[    1.719367]  [<ffffffff81d37b5f>] efivars_init+0xa6/0xf3
[    1.719369]  [<ffffffff81002040>] do_one_initcall+0x40/0x180
[    1.719370]  [<ffffffff81cfccf5>] kernel_init+0xe5/0x164
[    1.719372]  [<ffffffff81667af4>] kernel_thread_helper+0x4/0x10
[    1.719374]  [<ffffffff81cfcc10>] ? start_kernel+0x3bd/0x3bd
[    1.719376]  [<ffffffff81667af0>] ? gs_change+0x13/0x13
[    1.719376] ---[ end trace c630880989f0c2f3 ]---
[    1.719378] kobject_add_internal failed for FrontUsbPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9 with -EEXIST, don't try to register things with the same name in the same directory.
[    1.719380] Pid: 1, comm: swapper/0 Tainted: G        W    3.2.0-38-generic #61-Ubuntu
[    1.719381] Call Trace:
[    1.719382]  [<ffffffff8130f1b5>] kobject_add_internal+0x155/0x200
[    1.719383]  [<ffffffff8130f543>] kobject_init_and_add+0x63/0x90
[    1.719386]  [<ffffffff8151a240>] ? efivar_create_sysfs_entry+0x130/0x1c0
[    1.719388]  [<ffffffff8151a22a>] efivar_create_sysfs_entry+0x11a/0x1c0
[    1.719390]  [<ffffffff8151aa32>] register_efivars+0xc2/0x290
[    1.719391]  [<ffffffff81d37ab9>] ? edd_init+0x1a3/0x1a3
[    1.719393]  [<ffffffff81d37b5f>] efivars_init+0xa6/0xf3
[    1.719395]  [<ffffffff81002040>] do_one_initcall+0x40/0x180
[    1.719396]  [<ffffffff81cfccf5>] kernel_init+0xe5/0x164
[    1.719398]  [<ffffffff81667af4>] kernel_thread_helper+0x4/0x10
[    1.719400]  [<ffffffff81cfcc10>] ? start_kernel+0x3bd/0x3bd
[    1.719402]  [<ffffffff81667af0>] ? gs_change+0x13/0x13
[    1.719533] ------------[ cut here ]------------
[    1.719535] WARNING: at /build/buildd/linux-3.2.0/fs/sysfs/dir.c:481 sysfs_add_one+0xc8/0x100()
[    1.719536] Hardware name: HP Compaq 8200 Elite SFF PC
[    1.719537] sysfs: cannot create duplicate filename '/firmware/efi/vars/RearUsbPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9'
[    1.719538] Modules linked in:
[    1.719539] Pid: 1, comm: swapper/0 Tainted: G        W    3.2.0-38-generic #61-Ubuntu
[    1.719540] Call Trace:
[    1.719542]  [<ffffffff81067e3f>] warn_slowpath_common+0x7f/0xc0
[    1.719544]  [<ffffffff81067f36>] warn_slowpath_fmt+0x46/0x50
[    1.719546]  [<ffffffff81315fd0>] ? strlcat+0x60/0x80
[    1.719547]  [<ffffffff811ef5b8>] sysfs_add_one+0xc8/0x100
[    1.719549]  [<ffffffff811ef667>] create_dir+0x77/0xd0
[    1.719551]  [<ffffffff811ef76d>] sysfs_create_dir+0x7d/0xc0
[    1.719553]  [<ffffffff8130f111>] kobject_add_internal+0xb1/0x200
[    1.719554]  [<ffffffff8130f543>] kobject_init_and_add+0x63/0x90
[    1.719556]  [<ffffffff8151a240>] ? efivar_create_sysfs_entry+0x130/0x1c0
[    1.719558]  [<ffffffff8151a22a>] efivar_create_sysfs_entry+0x11a/0x1c0
[    1.719561]  [<ffffffff8151aa32>] register_efivars+0xc2/0x290
[    1.719562]  [<ffffffff81d37ab9>] ? edd_init+0x1a3/0x1a3
[    1.719564]  [<ffffffff81d37b5f>] efivars_init+0xa6/0xf3
[    1.719566]  [<ffffffff81002040>] do_one_initcall+0x40/0x180
[    1.719567]  [<ffffffff81cfccf5>] kernel_init+0xe5/0x164
[    1.719569]  [<ffffffff81667af4>] kernel_thread_helper+0x4/0x10
[    1.719571]  [<ffffffff81cfcc10>] ? start_kernel+0x3bd/0x3bd
[    1.719573]  [<ffffffff81667af0>] ? gs_change+0x13/0x13
[    1.719573] ---[ end trace c630880989f0c2f4 ]---
[    1.719575] kobject_add_internal failed for RearUsbPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9 with -EEXIST, don't try to register things with the same name in the same directory.
[    1.719577] Pid: 1, comm: swapper/0 Tainted: G        W    3.2.0-38-generic #61-Ubuntu
[    1.719577] Call Trace:
[    1.719579]  [<ffffffff8130f1b5>] kobject_add_internal+0x155/0x200
[    1.719580]  [<ffffffff8130f543>] kobject_init_and_add+0x63/0x90
[    1.719582]  [<ffffffff8151a240>] ? efivar_create_sysfs_entry+0x130/0x1c0
[    1.719585]  [<ffffffff8151a22a>] efivar_create_sysfs_entry+0x11a/0x1c0
[    1.719587]  [<ffffffff8151aa32>] register_efivars+0xc2/0x290
[    1.719588]  [<ffffffff81d37ab9>] ? edd_init+0x1a3/0x1a3
[    1.719590]  [<ffffffff81d37b5f>] efivars_init+0xa6/0xf3
[    1.719592]  [<ffffffff81002040>] do_one_initcall+0x40/0x180
[    1.719593]  [<ffffffff81cfccf5>] kernel_init+0xe5/0x164
[    1.719595]  [<ffffffff81667af4>] kernel_thread_helper+0x4/0x10
[    1.719597]  [<ffffffff81cfcc10>] ? start_kernel+0x3bd/0x3bd
[    1.719599]  [<ffffffff81667af0>] ? gs_change+0x13/0x13
[    1.719714] ------------[ cut here ]------------
[    1.719717] WARNING: at /build/buildd/linux-3.2.0/fs/sysfs/dir.c:481 sysfs_add_one+0xc8/0x100()
[    1.719718] Hardware name: HP Compaq 8200 Elite SFF PC
[    1.719719] sysfs: cannot create duplicate filename '/firmware/efi/vars/InternalUsbPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9'
[    1.719720] Modules linked in:
[    1.719721] Pid: 1, comm: swapper/0 Tainted: G        W    3.2.0-38-generic #61-Ubuntu
[    1.719722] Call Trace:
[    1.719724]  [<ffffffff81067e3f>] warn_slowpath_common+0x7f/0xc0
[    1.719725]  [<ffffffff81067f36>] warn_slowpath_fmt+0x46/0x50
[    1.719727]  [<ffffffff81315fd0>] ? strlcat+0x60/0x80
[    1.719729]  [<ffffffff811ef5b8>] sysfs_add_one+0xc8/0x100
[    1.719731]  [<ffffffff811ef667>] create_dir+0x77/0xd0
[    1.719733]  [<ffffffff811ef76d>] sysfs_create_dir+0x7d/0xc0
[    1.719734]  [<ffffffff8130f111>] kobject_add_internal+0xb1/0x200
[    1.719736]  [<ffffffff8130f543>] kobject_init_and_add+0x63/0x90
[    1.719738]  [<ffffffff8151a240>] ? efivar_create_sysfs_entry+0x130/0x1c0
[    1.719740]  [<ffffffff8151a22a>] efivar_create_sysfs_entry+0x11a/0x1c0
[    1.719742]  [<ffffffff8151aa32>] register_efivars+0xc2/0x290
[    1.719744]  [<ffffffff81d37ab9>] ? edd_init+0x1a3/0x1a3
[    1.719745]  [<ffffffff81d37b5f>] efivars_init+0xa6/0xf3
[    1.719747]  [<ffffffff81002040>] do_one_initcall+0x40/0x180
[    1.719749]  [<ffffffff81cfccf5>] kernel_init+0xe5/0x164
[    1.719751]  [<ffffffff81667af4>] kernel_thread_helper+0x4/0x10
[    1.719752]  [<ffffffff81cfcc10>] ? start_kernel+0x3bd/0x3bd
[    1.719754]  [<ffffffff81667af0>] ? gs_change+0x13/0x13
[    1.719755] ---[ end trace c630880989f0c2f5 ]---
[    1.719756] kobject_add_internal failed for InternalUsbPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9 with -EEXIST, don't try to register things with the same name in the same directory.
[    1.719758] Pid: 1, comm: swapper/0 Tainted: G        W    3.2.0-38-generic #61-Ubuntu
[    1.719759] Call Trace:
[    1.719760]  [<ffffffff8130f1b5>] kobject_add_internal+0x155/0x200
[    1.719762]  [<ffffffff8130f543>] kobject_init_and_add+0x63/0x90
[    1.719764]  [<ffffffff8151a240>] ? efivar_create_sysfs_entry+0x130/0x1c0
[    1.719766]  [<ffffffff8151a22a>] efivar_create_sysfs_entry+0x11a/0x1c0
[    1.719768]  [<ffffffff8151aa32>] register_efivars+0xc2/0x290
[    1.719770]  [<ffffffff81d37ab9>] ? edd_init+0x1a3/0x1a3
[    1.719772]  [<ffffffff81d37b5f>] efivars_init+0xa6/0xf3
[    1.719774]  [<ffffffff81002040>] do_one_initcall+0x40/0x180
[    1.719775]  [<ffffffff81cfccf5>] kernel_init+0xe5/0x164
[    1.719777]  [<ffffffff81667af4>] kernel_thread_helper+0x4/0x10
[    1.719779]  [<ffffffff81cfcc10>] ? start_kernel+0x3bd/0x3bd
[    1.719780]  [<ffffffff81667af0>] ? gs_change+0x13/0x13
[    1.722307] TCP cubic registered


Thanks

G

---

