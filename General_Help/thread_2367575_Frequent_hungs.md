---
title: "Frequent hungs"
date: 2017-08-01
forum: General Help
---

### Post by xrkr on 2017-08-01
Hi All,

I am seeing frequent hungs of my server. Below are the messages/calltrace before the hung. Can anybody let me know how to solve this issue. Additionally i lowered [COLOR=#111111][FONT=monospace]dirty_ratio and [/FONT][/COLOR][COLOR=#111111][FONT=monospace]dirty_background_ratio to 10 and 5. But still the load is getting high and subsquently going to hung.[/FONT][/COLOR][COLOR=#111111][FONT=monospace]
[/FONT][/COLOR]
```
INFO: task xfsaild/sdz:3177 blocked for more than 120 seconds.      Not tainted 3.19.0-25-generic #26~14.04.1-Ubuntu
"echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
xfsaild/sdz     D ffff88201ff43d28     0  3177      2 0x00000000
 ffff88201ff43d28 ffff882035c8bae0 0000000000013e80 ffff88201ff43fd8
 0000000000013e80 ffff8820393d2740 ffff882035c8bae0 ffff882035edd000
 ffff882035edd128 ffff882035c8bae0 0000000000000000 ffff882035edd000
Call Trace:
 [<ffffffff817b22e9>] schedule+0x29/0x70
 [<ffffffffc080ca31>] _xfs_log_force+0x171/0x270 [xfs]
 [<ffffffff810a0a70>] ? wake_up_state+0x20/0x20
 [<ffffffff810da970>] ? internal_add_timer+0x80/0x80
 [<ffffffffc080cb5a>] xfs_log_force+0x2a/0x90 [xfs]
 [<ffffffffc08172d0>] ? xfs_trans_ail_cursor_first+0x90/0x90 [xfs]
 [<ffffffffc0817410>] xfsaild+0x140/0x5a0 [xfs]
 [<ffffffffc08172d0>] ? xfs_trans_ail_cursor_first+0x90/0x90 [xfs]
 [<ffffffff81093802>] kthread+0xd2/0xf0
 [<ffffffff81093730>] ? kthread_create_on_node+0x1c0/0x1c0
 [<ffffffff817b65d8>] ret_from_fork+0x58/0x90
 [<ffffffff81093730>] ? kthread_create_on_node+0x1c0/0x1c0
INFO: task xfsaild/sdu:3212 blocked for more than 120 seconds.
      Not tainted 3.19.0-25-generic #26~14.04.1-Ubuntu
"echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
xfsaild/sdu     D ffff8820354ffd28     0  3212      2 0x00000000
 ffff8820354ffd28 ffff88102aa06bf0 0000000000013e80 ffff8820354fffd8
 0000000000013e80 ffff8820393d5850 ffff88102aa06bf0 0000000000000286
 ffff882035447928 ffff88102aa06bf0 0000000000000000 ffff882035447800
Call Trace:
 [<ffffffff817b22e9>] schedule+0x29/0x70
 [<ffffffffc080ca31>] _xfs_log_force+0x171/0x270 [xfs]
 [<ffffffff810a0a70>] ? wake_up_state+0x20/0x20
 [<ffffffff810da970>] ? internal_add_timer+0x80/0x80
 [<ffffffffc080cb5a>] xfs_log_force+0x2a/0x90 [xfs]
 [<ffffffffc08172d0>] ? xfs_trans_ail_cursor_first+0x90/0x90 [xfs]
 [<ffffffffc0817410>] xfsaild+0x140/0x5a0 [xfs]
 [<ffffffffc08172d0>] ? xfs_trans_ail_cursor_first+0x90/0x90 [xfs]
 [<ffffffff81093802>] kthread+0xd2/0xf0
 [<ffffffff81093730>] ? kthread_create_on_node+0x1c0/0x1c0
 [<ffffffff817b65d8>] ret_from_fork+0x58/0x90
 [<ffffffff81093730>] ? kthread_create_on_node+0x1c0/0x1c0
INFO: task app: port blocked for more than 120 seconds.
      Not tainted 3.19.0-25-generic #26~14.04.1-Ubuntu
"echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
app D ffff88100f2afe28     0  port      1 0x00000000
 ffff88100f2afe28 ffff88103917c4b0 0000000000013e80 ffff88100f2affd8
 0000000000013e80 ffffffff81c1d4e0 ffff88103917c4b0 ffffea0027e8df80
 00000051001d65a0 ffff882035edd128 ffff88100f2afef4 ffff882028aea118
Call Trace:
 [<ffffffff817b22e9>] schedule+0x29/0x70
 [<ffffffffc080cd73>] _xfs_log_force_lsn+0x163/0x2d0 [xfs]
 [<ffffffff810a0a70>] ? wake_up_state+0x20/0x20
 [<ffffffffc07f0360>] xfs_file_fsync+0x190/0x200 [xfs]
 [<ffffffff8121c791>] do_fsync+0x51/0x80
 [<ffffffff8121ca20>] SyS_fsync+0x10/0x20
 [<ffffffff817b668d>] system_call_fastpath+0x16/0x1b
```

---

### Post by BenginM on 2017-08-01
So *xfs* seems to use a lot of CPU and it hangs and crashes ..!

check the CPU usage ratio ..

what did you expects from lowering those dirty_ ratios ..!

What are the machine's specs ..

is the BIOS up-to-date .. 

$ inxi -M

you may want to preform a MemTest ..

---

### Post by xrkr on 2017-08-02
> **BenginM said:**
> So *xfs* seems to use a lot of CPU and it hangs and crashes ..!

check the CPU usage ratio ..

what did you expects from lowering those dirty_ ratios ..!

What are the machine's specs ..

is the BIOS up-to-date .. 

$ inxi -M

you may want to preform a MemTest ..

CPU usage is absolutely fine. The only thing i could see in the sar outputs is high load before the hung. Are there any bugs with the kernel?

[TABLE="width: 300"]
[TR]
  [TD="class: xl63, width: 300"]Intel(R)  Xeon(R) CPU E5-2620 v3 @ 2.40GHz 
* 2
[TABLE="width: 151"]
[TR]
  [TD="class: xl65, width: 151"]Ubuntu  14.04.3 LTS x64 ; 3.19.0-25-generic

[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

---

### Post by BenginM on 2017-08-02
I don't know , you may want to test with a newer kernel base 4.* .

test the latest upstream kernel available following [https://wiki.ubuntu.com/KernelMainlineBuilds](https://wiki.ubuntu.com/KernelMainlineBuilds) ? It will allow additional upstream developers to examine the issue. Please do not test the kernel in the daily folder, but the one all the way at the bottom. [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) 

consider reporting a bug against 3.19.0-25-generic

in terminal run :
ubuntu-bug linux
with the title xfs hags with high load 
 and then , run 

apport-collect -p linux <replace-with-bug-number>


## Helpful Bug Reporting Links:
[https://help.ubuntu.com/community/ReportingBugs#A3._Make_sure_the_bug_hasn.27t_already_been_reported](https://help.ubuntu.com/community/ReportingBugs#A3._Make_sure_the_bug_hasn.27t_already_been_reported)
[https://help.ubuntu.com/community/ReportingBugs#Adding_Apport_Debug_Information_to_an_Existing_Launchpad_Bug](https://help.ubuntu.com/community/ReportingBugs#Adding_Apport_Debug_Information_to_an_Existing_Launchpad_Bug)
[https://help.ubuntu.com/community/ReportingBugs#Adding_Additional_Attachments_to_an_Existing_Launchpad_Bug](https://help.ubuntu.com/community/ReportingBugs#Adding_Additional_Attachments_to_an_Existing_Launchpad_Bug)
please read the official Ubuntu documentation:
Ubuntu Bug Control and Ubuntu Bug Squad: [https://wiki.ubuntu.com/Bugs/BestPractices#X.2BAC8-Reporting.Focus_on_One_Issue](https://wiki.ubuntu.com/Bugs/BestPractices#X.2BAC8-Reporting.Focus_on_One_Issue)
Ubuntu Kernel Team: [https://wiki.ubuntu.com/KernelTeam/KernelTeamBugPolicies#Filing_Kernel_Bug_reports](https://wiki.ubuntu.com/KernelTeam/KernelTeamBugPolicies#Filing_Kernel_Bug_reports)
Ubuntu Community: [https://help.ubuntu.com/community/ReportingBugs#Bug_reporting_etiquette](https://help.ubuntu.com/community/ReportingBugs#Bug_reporting_etiquette)

---

