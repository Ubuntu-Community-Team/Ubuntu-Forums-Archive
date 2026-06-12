---
title: "ACPI Bios Error"
date: 2021-08-24
forum: General Help
---

### Post by libertasinvictus on 2021-08-24
I keep getting this error whenever I try to launch Ubuntu. I’ve been using Ubuntu alongside windows via dual boot for almost a year now, and all of a sudden this starts happening.

ACPI BIOS Error (bug): Failure creating names object.
AE_ALREADY_EXISTS, During name lookup/catalog
Call trace: 
dump_stack+0x6d/0x8b
panic+0x101/0x2e3
mount_block_root+0x23f/0x2e8
mount_root+0x38/0x3a
prepare_namespace+0x13f/0x194
kernel_init_freeable+0x23f/0x263
? rest_init+0xb0/0xb0
kernel_init+0xe/0x110
rest_from_fork+0x35/0x40
Kernel Offset: 0x2f200000 from 0xffffffff81000000 (relocation range: 0xffffffff80000000-0xffffffffbffffffff
—-[ end Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0) ]—-

---

### Post by T.J. on 2021-08-24
Hi! 

Have you updated your firmware recently?  ACPI implementations in firmware are famous for being buggy.  An update may fix the problem.  You could either disable disable ACPI in your firmware or add "acpi=off" to your Linux boot options in order to get the system to start up.

---

