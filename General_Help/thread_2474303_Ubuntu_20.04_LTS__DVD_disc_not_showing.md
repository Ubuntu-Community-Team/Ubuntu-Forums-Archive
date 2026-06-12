---
title: "Ubuntu 20.04 LTS : DVD disc not showing"
date: 2022-04-26
forum: General Help
---

### Post by georgesgiralt on 2022-04-26
Hello Guys,
The laptop is a Lenovo 15G2 ITL. The drive is a BluRay external HL-DT-ST BD-RE BU40N connected through an ASMT ASM105 device.
I connect the external drive, insert a DVD disc in it. Wait for some time and the DVD icon does not show on the "favorite" bar. 
I do not see it in files either and can't open it in VLC. 
This is not hardware related because if I reboot into Windows 11, the DVD, once inserted, directly plays in VLC. 
I have the same behavior on my wife's little Asus E203M Notebook running also Ubuntu 20.04 LTS. 
here is the dmesg output relevant to this issue : 
```

[ 3226.583711] usb 2-1: new SuperSpeed USB device number 2 using xhci_hcd
[ 3226.604912] usb 2-1: New USB device found, idVendor=174c, idProduct=55aa, bcdDevice= 1.00
[ 3226.604922] usb 2-1: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[ 3226.604925] usb 2-1: Product: ASM105X
[ 3226.604927] usb 2-1: Manufacturer: ASMT
[ 3226.604929] usb 2-1: SerialNumber: 2020082000000047
[ 3226.642136] usb-storage 2-1:1.0: USB Mass Storage device detected
[ 3226.642264] usb-storage 2-1:1.0: Quirks match for vid 174c pid 55aa: 400000
[ 3226.642303] scsi host1: usb-storage 2-1:1.0
[ 3226.642405] usbcore: registered new interface driver usb-storage
[ 3226.644443] usbcore: registered new interface driver uas
[ 3228.037466] scsi 1:0:0:0: CD-ROM            HL-DT-ST BD-RE BU40N      A100 PQ: 0 ANSI: 0
[ 3228.267942] sr 1:0:0:0: Power-on or device reset occurred
[ 3228.498160] sr 1:0:0:0: [sr0] scsi3-mmc drive: 0x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[ 3228.498164] cdrom: Uniform CD-ROM driver Revision: 3.20
[ 3228.635553] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 3228.635651] sr 1:0:0:0: Attached scsi generic sg1 type 5
[ 3229.000665] pktcdvd: pktcdvd0: writer mapped to sr0
[ 3278.243846] usb 2-1: reset SuperSpeed USB device number 2 using xhci_hcd
[ 3278.264800] sr 1:0:0:0: [sr0] tag#0 FAILED Result: hostbyte=DID_TIME_OUT driverbyte=DRIVER_OK cmd_age=31s
[ 3278.264810] sr 1:0:0:0: [sr0] tag#0 CDB: Read(10) 28 00 00 00 02 00 00 00 02 00
[ 3278.264812] blk_update_request: I/O error, dev sr0, sector 2048 op 0x0:(READ) flags 0x80700 phys_seg 1 prio class 0
[ 3308.963912] usb 2-1: reset SuperSpeed USB device number 2 using xhci_hcd
[ 3505.432279] INFO: task scsi_eh_1:12238 blocked for more than 120 seconds.
[ 3505.432292]       Tainted: P           O      5.13.0-40-generic #45~20.04.1-Ubuntu
[ 3505.432295] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 3505.432297] task:scsi_eh_1       state:D stack:    0 pid:12238 ppid:     2 flags:0x00004000
[ 3505.432305] Call Trace:
[ 3505.432308]  <TASK>
[ 3505.432312]  __schedule+0x2ee/0x900
[ 3505.432321]  schedule+0x4f/0xc0
[ 3505.432324]  schedule_preempt_disabled+0xe/0x10
[ 3505.432328]  __mutex_lock.isra.0+0x183/0x4d0
[ 3505.432332]  ? dequeue_entity+0xdb/0x410
[ 3505.432339]  ? blk_mq_find_and_get_req+0x4f/0x90
[ 3505.432345]  __mutex_lock_slowpath+0x13/0x20
[ 3505.432348]  mutex_lock+0x32/0x40
[ 3505.432354]  device_reset+0x22/0x50 [usb_storage]
[ 3505.432362]  scsi_eh_ready_devs+0x57d/0xa50
[ 3505.432370]  ? __pm_runtime_resume+0x60/0x80
[ 3505.432374]  scsi_error_handler+0x446/0x520
[ 3505.432380]  ? scsi_eh_get_sense+0x230/0x230
[ 3505.432385]  kthread+0x128/0x150
[ 3505.432389]  ? set_kthread_struct+0x40/0x40
[ 3505.432393]  ret_from_fork+0x1f/0x30
[ 3505.432400]  </TASK>
[ 3505.432403] INFO: task usb-storage:12240 blocked for more than 120 seconds.
[ 3505.432407]       Tainted: P           O      5.13.0-40-generic #45~20.04.1-Ubuntu
[ 3505.432410] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 3505.432411] task:usb-storage     state:D stack:    0 pid:12240 ppid:     2 flags:0x00004000
[ 3505.432416] Call Trace:
[ 3505.432417]  <TASK>
[ 3505.432419]  __schedule+0x2ee/0x900
[ 3505.432423]  ? usleep_range_state+0x90/0x90
[ 3505.432427]  schedule+0x4f/0xc0
[ 3505.432430]  schedule_timeout+0x202/0x290
[ 3505.432434]  ? xhci_urb_enqueue+0x1e6/0x530
[ 3505.432441]  ? usleep_range_state+0x90/0x90
[ 3505.432445]  __wait_for_common+0xba/0x160
[ 3505.432450]  wait_for_completion+0x24/0x30
[ 3505.432453]  usb_sg_wait+0xea/0x170
[ 3505.432459]  usb_stor_bulk_transfer_sglist+0x97/0xe0 [usb_storage]
[ 3505.432467]  usb_stor_bulk_srb+0x3d/0x70 [usb_storage]
[ 3505.432473]  usb_stor_Bulk_transport+0x177/0x410 [usb_storage]
[ 3505.432480]  ? schedule_timeout+0x202/0x290
[ 3505.432484]  usb_stor_invoke_transport+0x3e/0x520 [usb_storage]
[ 3505.432491]  ? usleep_range_state+0x90/0x90
[ 3505.432495]  ? __wait_for_common+0xfb/0x160
[ 3505.432498]  ? __raw_callee_save___native_queued_spin_unlock+0x15/0x23
[ 3505.432505]  usb_stor_transparent_scsi_command+0xe/0x10 [usb_storage]
[ 3505.432511]  usb_stor_control_thread+0x19b/0x2a0 [usb_storage]
[ 3505.432518]  ? storage_probe+0x2b0/0x2b0 [usb_storage]
[ 3505.432525]  kthread+0x128/0x150
[ 3505.432528]  ? set_kthread_struct+0x40/0x40
[ 3505.432532]  ret_from_fork+0x1f/0x30
[ 3505.432538]  </TASK>

```
My machine runs 
```

Linux hostname 5.13.0-40-generic #45~20.04.1-Ubuntu SMP Mon Apr 4 09:38:31 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

```
The netbook runs an older kernel version. Mine has the HWE kernel because of it's new hardware (the laptop is less than a year old and the Lenovo support repo installs the HWE). But as the notebook has the same behavior, I guess the kernel version is not that important. 
I've tried to insert a CD (audio) in the drive to check if the laser diode was faulty and it works flawlessly.
So I wonder what is wrong here and how could I fix it ? 
Many thanks in advance for your help. 
Have a nice day !

---

### Post by Holger_Gehrke on 2022-04-26
Is that a commercial video DVD ? Those are partially encrypted using the Content Scrambling System (CSS, not to be confused with Cascading Style Sheets, the formatting language for web pages and quite a lot of similar content). That encryption is not really meant as copy protection, it's mainly aimed at manufacturers of DVD-Players who need to pay for a license from the DVD consortium to get a key so their players will work. Obviously this means that open source applications can't get an official key since openly available source code makes it difficult to keep the key secret and hidden ... 

CSS has been broken almost before the first DVD's where available but the code to do this is of rather questionable legality depending on the copyright laws in your country. In some places the source code is seen as protected free speech but the binary and it's use is ... problematic. That's why that package is not installed by default and makes you jump through a few hoops to actually run it. It will actually download the source code and compile it for you.

To install the code you need to install the package libdvd-pkg ('sudo apt install libdvd-pkg' in a terminal).

Holger

---

### Post by georgesgiralt on 2022-04-26
Thank you Holger for this. I already have the libdvdcss library installed. I've version 1.4.2 (per libdvd-pkg) and I tried to replace it with 1.4.3 from Videolan GitHub to no avail. 
And yes, it is a movie DVD.

---

