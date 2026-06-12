---
title: "ubuntu 12.04 btrfs issues after installing latest updates"
date: 2013-07-03
forum: General Help
---

### Post by egandt on 2013-07-03
I just installed the latest updates for ubuntu 12.0.4.  After the updates were installed I rebooted (new kernel), now I'm in a pickle.  The system boots up fine, but access to by BTRFS, is well m=basically useless.  I tried booting back to the previous kernel, same issue, then I tried a mainline kernel, again same issue.  Now this is on a RAID6 array and the array is stable (optimal).  Now everything I have an issue it could be any app using the array, but the call trace is always the same (well very similar):

Jul  3 18:37:45 fileserver kernel: [  360.262668] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jul  3 18:37:45 fileserver kernel: [  360.262670] sabnzbdplus     D 0000000000000002     0  5737      1 0x00000004
Jul  3 18:37:45 fileserver kernel: [  360.262672]  ffff8801e2b0fa98 0000000000000002 ffff8801e2b0fa74 ffff8801e57126f8
Jul  3 18:37:45 fileserver kernel: [  360.262674]  ffff8801e2b0ffd8 ffff8801e2b0ffd8 ffff8801e2b0ffd8 00000000000144c0
Jul  3 18:37:45 fileserver kernel: [  360.262676]  ffff880213c6ddc0 ffff8801f185ddc0 ffff8801e2b0fa98 ffff88021f314d80
Jul  3 18:37:45 fileserver kernel: [  360.262676] Call Trace:
Jul  3 18:37:45 fileserver kernel: [  360.262678]  [<ffffffff811386e0>] ? __lock_page+0x70/0x70
Jul  3 18:37:45 fileserver kernel: [  360.262681]  [<ffffffff8170d999>] schedule+0x29/0x70
Jul  3 18:37:45 fileserver kernel: [  360.262684]  [<ffffffff8170da6f>] io_schedule+0x8f/0xd0
Jul  3 18:37:45 fileserver kernel: [  360.262686]  [<ffffffff811386ee>] sleep_on_page+0xe/0x20
Jul  3 18:37:45 fileserver kernel: [  360.262689]  [<ffffffff8170b88a>] __wait_on_bit_lock+0x5a/0xc0
Jul  3 18:37:45 fileserver kernel: [  360.262690]  [<ffffffff811386d7>] __lock_page+0x67/0x70
Jul  3 18:37:45 fileserver kernel: [  360.262693]  [<ffffffff81080e70>] ? autoremove_wake_function+0x40/0x40
Jul  3 18:37:45 fileserver kernel: [  360.262695]  [<ffffffff81139447>] find_lock_page+0x67/0x80
Jul  3 18:37:45 fileserver kernel: [  360.262697]  [<ffffffff81139a1f>] find_or_create_page+0x3f/0xb0
Jul  3 18:37:45 fileserver kernel: [  360.262699]  [<ffffffff8170e93e>] ? _raw_spin_lock+0xe/0x20
Jul  3 18:37:45 fileserver kernel: [  360.262714]  [<ffffffffa00d7049>] prepare_pages.isra.19+0x199/0x370 [btrfs]
Jul  3 18:37:45 fileserver kernel: [  360.262717]  [<ffffffff811abe54>] ? link_path_walk+0x74/0x860
Jul  3 18:37:45 fileserver kernel: [  360.262732]  [<ffffffffa00d7ddd>] __btrfs_buffered_write+0x17d/0x330 [btrfs]
Jul  3 18:37:45 fileserver kernel: [  360.262735]  [<ffffffff810609f6>] ? current_fs_time+0x16/0x60
Jul  3 18:37:45 fileserver kernel: [  360.262749]  [<ffffffffa00d818d>] **btrfs_file_aio_write+0x1fd/0x340 [btrfs]**
Jul  3 18:37:45 fileserver kernel: [  360.262752]  [<ffffffff8119f52a>] do_sync_write+0x7a/0xb0
Jul  3 18:37:45 fileserver kernel: [  360.262754]  [<ffffffff811a02ee>] vfs_write+0xce/0x1e0
Jul  3 18:37:45 fileserver kernel: [  360.262757]  [<ffffffff811a07d2>] SyS_write+0x52/0xa0
Jul  3 18:37:45 fileserver kernel: [  360.262759]  [<ffffffff81717def>] tracesys+0xe1/0xe6

This time the cause was sabnzbdplus, but it could be smbd, mysql or anything else accessing this drive.  Since I've had this setup for months and months (well over a year) without any issues, I assume it is related to the update, but I'm unsure what was installed to back it out.  So 2 questions:

Anyone encounter such an issue, with the latest updates as I'm not looking forward to working out how to backup 13GB, and fix this?
Second any suggestion how to figure out what the last set of updates installed were?


Thanks,
ERIC

---

