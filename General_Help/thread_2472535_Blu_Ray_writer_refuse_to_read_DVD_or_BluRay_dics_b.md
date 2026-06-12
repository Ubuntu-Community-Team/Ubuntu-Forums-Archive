---
title: "Blu Ray writer refuse to read DVD or BluRay dics but is fine for audio CDs"
date: 2022-03-02
forum: General Help
---

### Post by georgesgiralt on 2022-03-02
Hello Guys !
The culprit is a laptop running Ubuntu 20.04.4 LTS. This morning I wanted to look a a DVD (rented) before I return it to the store. (I missed the end, yesterday night falling asleep...) 
The DVD icon did not show on the launcher and VLC refused to open it. Even after half an hour... 
The eject command did not work either. (from a terminal : eject /dev/sr0) 
As the BD writer is an external device bought second hand, I thought it was dead.I tried it on a Windows 11 computer and it worked fine, reading DVD and BD discs. 
So I tried on the laptop using different USB-C port and USB3 ports. Same behavior. 
The last time I used it was to look at a rented DVD my DVD reader attached to the TV set refused to open. It was Feb. 14th. So during this last fortnight something changed and killed DVD and BD reading. 
To be sure the problem was not hardware related, I played a couple of audio CDs (same LED used to read a CD and a DVD, if I'm not mistaken) and they read fine. 
I tried to install the 1.4.3 libdvdcss because I had only 1.4.1 installed but to no avail. 
So I would be very grateful to get your help and advice on this matter. 
Many thanks in advance for you help. 
Have a nice and bright day.
Edit : I just saw that the log has some errors related to the DVD drive : 
```

[ 5558.882929] INFO: task scsi_eh_2:9410 blocked for more than 120 seconds.
[ 5558.882942]       Tainted: P           O      5.13.0-30-generic #33~20.04.1-Ubuntu
[ 5558.882946] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 5558.882948] task:scsi_eh_2       state:D stack:    0 pid: 9410 ppid:     2 flags:0x00004000
[ 5558.882956] Call Trace:
[ 5558.882959]  <TASK>
[ 5558.882964]  __schedule+0x2ee/0x900
[ 5558.882975]  ? load_balance+0x98e/0xc60
[ 5558.882981]  schedule+0x4f/0xc0
[ 5558.882987]  schedule_preempt_disabled+0xe/0x10
[ 5558.882993]  __mutex_lock.isra.0+0x183/0x4d0
[ 5558.882996]  ? dequeue_entity+0xdb/0x410
[ 5558.883003]  ? blk_mq_find_and_get_req+0x4f/0x90
[ 5558.883009]  __mutex_lock_slowpath+0x13/0x20
[ 5558.883012]  mutex_lock+0x32/0x40
[ 5558.883018]  device_reset+0x22/0x50 [usb_storage]
[ 5558.883026]  scsi_eh_ready_devs+0x57d/0xa50
[ 5558.883033]  ? __pm_runtime_resume+0x60/0x80
[ 5558.883042]  scsi_error_handler+0x446/0x520
[ 5558.883048]  ? scsi_eh_get_sense+0x230/0x230
[ 5558.883053]  kthread+0x128/0x150
[ 5558.883058]  ? set_kthread_struct+0x40/0x40
[ 5558.883062]  ret_from_fork+0x1f/0x30
[ 5558.883070]  </TASK>
[ 5558.883073] INFO: task usb-storage:9412 blocked for more than 120 seconds.
[ 5558.883077]       Tainted: P           O      5.13.0-30-generic #33~20.04.1-Ubuntu
[ 5558.883080] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 5558.883082] task:usb-storage     state:D stack:    0 pid: 9412 ppid:     2 flags:0x00004000
[ 5558.883086] Call Trace:
[ 5558.883088]  <TASK>
[ 5558.883090]  __schedule+0x2ee/0x900
[ 5558.883096]  ? usleep_range+0x90/0x90
[ 5558.883101]  schedule+0x4f/0xc0
[ 5558.883106]  schedule_timeout+0x202/0x290
[ 5558.883110]  ? xhci_urb_enqueue+0x1e6/0x530
[ 5558.883118]  ? usleep_range+0x90/0x90
[ 5558.883121]  __wait_for_common+0xba/0x160
[ 5558.883125]  wait_for_completion+0x24/0x30
[ 5558.883128]  usb_sg_wait+0xea/0x170
[ 5558.883134]  usb_stor_bulk_transfer_sglist+0x97/0xe0 [usb_storage]
[ 5558.883143]  usb_stor_bulk_srb+0x3d/0x70 [usb_storage]
[ 5558.883151]  usb_stor_Bulk_transport+0x177/0x410 [usb_storage]
[ 5558.883158]  ? schedule_timeout+0x202/0x290
[ 5558.883162]  usb_stor_invoke_transport+0x3e/0x520 [usb_storage]
[ 5558.883170]  ? usleep_range+0x90/0x90
[ 5558.883173]  ? __wait_for_common+0xfb/0x160
[ 5558.883177]  ? __raw_callee_save___native_queued_spin_unlock+0x15/0x23
[ 5558.883183]  usb_stor_transparent_scsi_command+0xe/0x10 [usb_storage]
[ 5558.883189]  usb_stor_control_thread+0x19b/0x2a0 [usb_storage]
[ 5558.883198]  ? storage_probe+0x2b0/0x2b0 [usb_storage]
[ 5558.883205]  kthread+0x128/0x150
[ 5558.883209]  ? set_kthread_struct+0x40/0x40
[ 5558.883213]  ret_from_fork+0x1f/0x30
[ 5558.883220]  </TASK>
[ 5679.721093] INFO: task udisksd:1141 blocked for more than 120 seconds.
[ 5679.721099]       Tainted: P           O      5.13.0-30-generic #33~20.04.1-Ubuntu
[ 5679.721101] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 5679.721102] task:udisksd         state:D stack:    0 pid: 1141 ppid:     1 flags:0x00000000
[ 5679.721105] Call Trace:
[ 5679.721106]  <TASK>
[ 5679.721109]  __schedule+0x2ee/0x900
[ 5679.721113]  ? __enqueue_entity+0x96/0xa0
[ 5679.721116]  ? usleep_range+0x90/0x90
[ 5679.721118]  schedule+0x4f/0xc0
[ 5679.721119]  schedule_timeout+0x202/0x290
[ 5679.721121]  ? ttwu_do_wakeup+0x1c/0x150
[ 5679.721122]  ? ttwu_do_activate+0xb7/0x490
[ 5679.721123]  ? usleep_range+0x90/0x90
[ 5679.721124]  __wait_for_common+0xba/0x160
[ 5679.721125]  wait_for_completion+0x24/0x30
[ 5679.721126]  __flush_work+0x12a/0x1e0
[ 5679.721128]  ? worker_detach_from_pool+0xc0/0xc0
[ 5679.721130]  __cancel_work_timer+0x11d/0x1a0
[ 5679.721131]  ? find_inode_fast.isra.0+0x59/0xc0
[ 5679.721134]  cancel_delayed_work_sync+0x13/0x20
[ 5679.721135]  disk_block_events+0x78/0x80
[ 5679.721138]  blkdev_get_by_dev+0xfd/0x230
[ 5679.721139]  ? blkdev_get_by_dev+0x230/0x230
[ 5679.721140]  blkdev_open+0x50/0x90
[ 5679.721141]  do_dentry_open+0x154/0x370
[ 5679.721144]  vfs_open+0x2d/0x30
[ 5679.721145]  do_open.isra.0+0x205/0x3e0
[ 5679.721147]  path_openat+0x18e/0xc80
[ 5679.721148]  ? copyout+0x20/0x30
[ 5679.721150]  ? _copy_to_iter+0xb3/0x7b0
[ 5679.721152]  do_filp_open+0xa2/0x110
[ 5679.721153]  ? __check_object_size+0x13f/0x150
[ 5679.721155]  ? alloc_fd+0x58/0x190
[ 5679.721156]  do_sys_openat2+0x245/0x310
[ 5679.721157]  do_sys_open+0x46/0x80
[ 5679.721159]  __x64_sys_openat+0x20/0x30
[ 5679.721160]  do_syscall_64+0x61/0xb0
[ 5679.721163]  ? exit_to_user_mode_prepare+0x3d/0x1c0
[ 5679.721165]  ? syscall_exit_to_user_mode+0x27/0x50
[ 5679.721166]  ? __x64_sys_close+0x12/0x40
[ 5679.721167]  ? do_syscall_64+0x6e/0xb0
[ 5679.721169]  ? syscall_exit_to_user_mode+0x27/0x50
[ 5679.721170]  ? __x64_sys_close+0x12/0x40
[ 5679.721171]  ? do_syscall_64+0x6e/0xb0
[ 5679.721173]  ? __x64_sys_openat+0x20/0x30
[ 5679.721175]  ? do_syscall_64+0x6e/0xb0
[ 5679.721176]  ? do_syscall_64+0x6e/0xb0
[ 5679.721178]  entry_SYSCALL_64_after_hwframe+0x44/0xae
[ 5679.721179] RIP: 0033:0x7fb97eaf3ad4
[ 5679.721181] RSP: 002b:00007ffd1e2f3400 EFLAGS: 00000293 ORIG_RAX: 0000000000000101
[ 5679.721183] RAX: ffffffffffffffda RBX: 00007ffd1e2f352c RCX: 00007fb97eaf3ad4
[ 5679.721184] RDX: 0000000000000000 RSI: 000055adfede3cb0 RDI: 00000000ffffff9c
[ 5679.721184] RBP: 000055adfede3cb0 R08: 0000000000000000 R09: 0000000000000007
[ 5679.721185] R10: 0000000000000000 R11: 0000000000000293 R12: 0000000000000000
[ 5679.721185] R13: 0000000000000000 R14: 000055adfede3cb0 R15: 000055adfec71430
[ 5679.721187]  </TASK>
[ 5679.721379] INFO: task scsi_eh_2:9410 blocked for more than 241 seconds.
[ 5679.721380]       Tainted: P           O      5.13.0-30-generic #33~20.04.1-Ubuntu
[ 5679.721381] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 5679.721381] task:scsi_eh_2       state:D stack:    0 pid: 9410 ppid:     2 flags:0x00004000
[ 5679.721383] Call Trace:
[ 5679.721383]  <TASK>
[ 5679.721384]  __schedule+0x2ee/0x900
[ 5679.721386]  ? load_balance+0x98e/0xc60
[ 5679.721387]  schedule+0x4f/0xc0
[ 5679.721389]  schedule_preempt_disabled+0xe/0x10
[ 5679.721390]  __mutex_lock.isra.0+0x183/0x4d0
[ 5679.721391]  ? dequeue_entity+0xdb/0x410
[ 5679.721393]  ? blk_mq_find_and_get_req+0x4f/0x90
[ 5679.721395]  __mutex_lock_slowpath+0x13/0x20
[ 5679.721395]  mutex_lock+0x32/0x40
[ 5679.721398]  device_reset+0x22/0x50 [usb_storage]
[ 5679.721401]  scsi_eh_ready_devs+0x57d/0xa50
[ 5679.721403]  ? __pm_runtime_resume+0x60/0x80
[ 5679.721406]  scsi_error_handler+0x446/0x520
[ 5679.721408]  ? scsi_eh_get_sense+0x230/0x230
[ 5679.721409]  kthread+0x128/0x150
[ 5679.721411]  ? set_kthread_struct+0x40/0x40
[ 5679.721412]  ret_from_fork+0x1f/0x30
[ 5679.721414]  </TASK>
[ 5679.721415] INFO: task usb-storage:9412 blocked for more than 241 seconds.
[ 5679.721416]       Tainted: P           O      5.13.0-30-generic #33~20.04.1-Ubuntu
[ 5679.721416] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 5679.721417] task:usb-storage     state:D stack:    0 pid: 9412 ppid:     2 flags:0x00004000
[ 5679.721418] Call Trace:
[ 5679.721418]  <TASK>
[ 5679.721419]  __schedule+0x2ee/0x900
[ 5679.721421]  ? usleep_range+0x90/0x90
[ 5679.721422]  schedule+0x4f/0xc0
[ 5679.721423]  schedule_timeout+0x202/0x290
[ 5679.721424]  ? xhci_urb_enqueue+0x1e6/0x530
[ 5679.721427]  ? usleep_range+0x90/0x90
[ 5679.721428]  __wait_for_common+0xba/0x160
[ 5679.721428]  wait_for_completion+0x24/0x30
[ 5679.721429]  usb_sg_wait+0xea/0x170
[ 5679.721431]  usb_stor_bulk_transfer_sglist+0x97/0xe0 [usb_storage]
[ 5679.721433]  usb_stor_bulk_srb+0x3d/0x70 [usb_storage]
[ 5679.721435]  usb_stor_Bulk_transport+0x177/0x410 [usb_storage]
[ 5679.721437]  ? schedule_timeout+0x202/0x290
[ 5679.721438]  usb_stor_invoke_transport+0x3e/0x520 [usb_storage]
[ 5679.721440]  ? usleep_range+0x90/0x90
[ 5679.721441]  ? __wait_for_common+0xfb/0x160
[ 5679.721442]  ? __raw_callee_save___native_queued_spin_unlock+0x15/0x23
[ 5679.721444]  usb_stor_transparent_scsi_command+0xe/0x10 [usb_storage]
[ 5679.721446]  usb_stor_control_thread+0x19b/0x2a0 [usb_storage]
[ 5679.721448]  ? storage_probe+0x2b0/0x2b0 [usb_storage]
[ 5679.721450]  kthread+0x128/0x150
[ 5679.721451]  ? set_kthread_struct+0x40/0x40
[ 5679.721452]  ret_from_fork+0x1f/0x30
[ 5679.721454]  </TASK>
[ 5762.810536] usb 2-2.2: USB disconnect, device number 6
[ 5762.810858] sr 2:0:0:0: Device offlined - not ready after error recovery
[ 5762.832826] blk_update_request: I/O error, dev sr0, sector 2048 op 0x0:(READ) flags 0x0 phys_seg 2 prio class 0
[ 5762.832840] Buffer I/O error on dev sr0, logical block 512, async page read
[ 5762.832846] Buffer I/O error on dev sr0, logical block 513, async page read

```

---

### Post by georgesgiralt on 2022-03-03
Hello Guys !
Let me answer my own question. 
I've done a lot of forensic analysis on this matter.
The BD writer is on an external enclosure fitted with an ASMT ASM105X chip. The reader is a BU-40N writer. 
I can't read a DVD from Paramount Pictures (Klondyke Annie with Mae West). I get the read errors above.
I tried to read it on the same computer using Windows 11 in the same reader on the same BD enclosure on the same USB port and it reads fine.
I tried to read it on another computer running Ubuntu 20.04.4 LTS but without the HWE kernel. No joy using the external BD writer. Same errors as above.
On this very same computer, using Windows 10, no problem. Ah ! Something to check here ! 
I swapped the BD writer into the external enclosure for a DVD writer .... The DVD reads fine under Windows but not under Ubuntu on either computer ! 
So I asked a friend for an external DVD writer (different enclosure and make, a Samsung external DVD writer). The DVD reads fine under Windows 10 & 11 but refuses to read under Ubuntu 20.04, be it kernel 5.4 or 5.13....
Then I tried to read another DVD (Greenland with Gerard Butler) and all reader can read it whatever operation system I use...Same with a BlueRay disc "Otages à Entebbe" with Daniel Brühl and Rosamund Pike. It reads fine in every case ! 
So IMHO, Paramount devised a new protection system ....  And this is not fun. 
Have a nice and bright day.

---

### Post by CharlesA on 2022-03-03
DVD uses DVDCSS for the copy protection, which is super old and has been cracked for many years now.

What application were you trying to use to play the DVD?

---

### Post by georgesgiralt on 2022-03-03
My problem arose BEFORE I tried to read the DVD. When you put a CD/DVD/BluRay on a reader, after some seconds, an icon show up to indicate the drive is ready. This icon never shows up. And if you use VLC to open the disc, nothing happens and vlc stalls. 
Once this has happened, you can do nothing with the drive. The only way to get it back is to unplug the USB cable.... Even restarting the computer takes ages (systemctl can't stop some processes )...
My explanation is that DVD use a filesystem to store the data (which is not true for pure audio CD) and this filesystem has been flawed in a way the kernel can't figure out.

---

### Post by CharlesA on 2022-03-03
> **georgesgiralt said:**
> My problem arose BEFORE I tried to read the DVD. When you put a CD/DVD/BluRay on a reader, after some seconds, an icon show up to indicate the drive is ready. This icon never shows up. And if you use VLC to open the disc, nothing happens and vlc stalls. 
Once this has happened, you can do nothing with the drive. The only way to get it back is to unplug the USB cable.... Even restarting the computer takes ages (systemctl can't stop some processes )...
My explanation is that DVD use a filesystem to store the data (which is not true for pure audio CD) and this filesystem has been flawed in a way the kernel can't figure out.

That's pretty weird. I've seen similar behavior with hot swapping hard drives when the system is under high load.

Did you get anything in dmesg when this stall occured?

---

### Post by georgesgiralt on 2022-03-04
You have the only messages above as an add-on on my first post. Nothing more. 
Have a nice and bright day.

---

