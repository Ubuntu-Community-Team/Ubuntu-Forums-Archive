---
title: "System crashing while writing to external HDD"
date: 2013-10-27
forum: General Help
---

### Post by b1001421 on 2013-10-27
I have an issue while writing files to my external NTFS drive on Xubuntu through USB 2.0. I can tranfer so many files but it eventually locks up the entire system. It happened several times in a row. I am able to pull data off the drive without an issue. Before I didn't see anything in the log but I think I found something that is related. Can anyone help me with this? I am using Xubuntu 13.10 and I am trying to transfer about 50GB of data to the external drive. 


> Oct 27 16:59:38 Xubuntu kernel: [ 1440.744049] INFO: task pool:2158 blocked for more than 120 seconds.
Oct 27 16:59:38 Xubuntu kernel: [ 1440.744058] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.

Oct 27 16:59:38 Xubuntu kernel: [ 1440.744109] Call Trace:
Oct 27 16:59:38 Xubuntu kernel: [ 1440.744124]  [<c1079a8f>] ? __wake_up+0x3f/0x50
Oct 27 16:59:38 Xubuntu kernel: [ 1440.744134]  [<c123829d>] ? jbd2_journal_stop+0x25d/0x380
Oct 27 16:59:38 Xubuntu kernel: [ 1440.744141]  [<c10451d8>] ? default_spin_lock_flags+0x8/0x10
Oct 27 16:59:38 Xubuntu kernel: [ 1440.744149]  [<c1629ca3>] schedule+0x23/0x60
Oct 27 16:59:38 Xubuntu kernel: [ 1440.744156]  [<c1135ebd>] kmap_high+0xed/0x1f0
Oct 27 16:59:38 Xubuntu kernel: [ 1440.744163]  [<c107ed20>] ? wake_up_state+0x20/0x20
Oct 27 16:59:38 Xubuntu kernel: [ 1440.744171]  [<c104c08f>] kmap+0x5f/0x70
Oct 27 16:59:38 Xubuntu kernel: [ 1440.744178]  [<c1171603>] generic_pipe_buf_map+0x13/0x30
Oct 27 16:59:38 Xubuntu kernel: [ 1440.744186]  [<c11903fe>] write_pipe_buf+0x2e/0x70
Oct 27 16:59:38 Xubuntu kernel: [ 1440.744192]  [<c11f4731>] ? ext4_dirty_inode+0x51/0x60
Oct 27 16:59:38 Xubuntu kernel: [ 1440.744199]  [<c11903d0>] ? generic_file_splice_write+0x150/0x150
Oct 27 16:59:38 Xubuntu kernel: [ 1440.744206]  [<c118fdc0>] splice_from_pipe_feed+0x70/0x100
Oct 27 16:59:38 Xubuntu kernel: [ 1440.744212]  [<c11903d0>] ? generic_file_splice_write+0x150/0x150
Oct 27 16:59:38 Xubuntu kernel: [ 1440.744218]  [<c11903d0>] ? generic_file_splice_write+0x150/0x150
Oct 27 16:59:38 Xubuntu kernel: [ 1440.744224]  [<c11900d3>] __splice_from_pipe+0x53/0x80
Oct 27 16:59:38 Xubuntu kernel: [ 1440.744232]  [<c1628300>] ? mutex_lock+0x10/0x28
Oct 27 16:59:38 Xubuntu kernel: [ 1440.744238]  [<c1191acc>] splice_from_pipe+0x4c/0x60
Oct 27 16:59:38 Xubuntu kernel: [ 1440.744245]  [<c1191b3c>] default_file_splice_write+0x2c/0x50
Oct 27 16:59:38 Xubuntu kernel: [ 1440.744252]  [<c11903d0>] ? generic_file_splice_write+0x150/0x150
Oct 27 16:59:38 Xubuntu kernel: [ 1440.744258]  [<c1191b10>] ? generic_splice_sendpage+0x30/0x30
Oct 27 16:59:38 Xubuntu kernel: [ 1440.744265]  [<c1191f25>] SyS_splice+0x195/0x580
Oct 27 16:59:38 Xubuntu kernel: [ 1440.744272]  [<c1632ccd>] sysenter_do_call+0x12/0x28




It basically repeats this 4 times and then the log ends where I had to hold the power button on my computer to restart it.

---

### Post by b1001421 on 2013-10-29
Eh, I solved the problem by just formatting my external drive to EXT4. I copied the files over without a issue. I guess it is just a NTFS bug? I was able to reproduce it again with my USB flash drive formatted as NTFS.

---

