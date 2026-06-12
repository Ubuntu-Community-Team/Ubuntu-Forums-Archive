---
title: "Help needed for a SCSI error thread hang (SATA drives, HGST HDD and Sandisk SSD)"
date: 2017-03-10
forum: General Help
---

### Post by viswesh2 on 2017-03-10
Hi,

I am reaching out regarding a SCSI error handler issue, which we see
in our lab systems.

Environment: Ubuntu 4.4.0-31-generic

Issue: Write IOs are getting stuck in our system randomly. All drives
seen with the issue are all SATA drives.
Root cause: SCSI error handler is not woken up (or) it is up, but not
able to flush commands and hence the IOs get stuck. (as the requests
are not flushed out and host is not restarted)

We have 6 instances seen till now.

This is what we see.
1) As part of testing our drives, we start lot of read/writes, along
with some user space utilities running to check the drive health.
1) In our recent testing, we see lot of commands going through the
"abort scheduled" path. And we see that in between, for one of the
commands, the error handler is not woken up, and majority of
processes, which were writing, gets stalled.
2) We are still trying to figure out what is causing this much number
of abort? Is it usual? Are there some other debugs, which I could
enable to get more information? We know these are user space commands
which are being aborted, but not sure which exact command it is for
now.
3) I see the "abort scheduled" messages in almost all drives in all
systems, hence i dont believe it is a drive issue.
4) I checked the host_failed and host_busy variables, both are set to
1 in system 1. 2nd one is still alive, havent taken a crash dump yet.
5) All drives seen with the issue are SATA drives.
6) I have attached udevadm info of a drive which failed in system 2.

Thanks in advance,
Viswesh


Logs
-------
System 1

[371546.605736] sd 9:0:0:0: scsi_block_when_processing_errors: rtn: 1
[371546.606727] sd 9:0:0:0: scsi_block_when_processing_errors: rtn: 1
[371546.607721] sd 9:0:0:0: scsi_block_when_processing_errors: rtn: 1
[371546.618113] sd 9:0:0:0: [sg19] tag#20 abort scheduled
[371546.624039] sd 9:0:0:0: [sg19] tag#20 aborting command
[371546.624045] sd 9:0:0:0: [sg19] tag#20 cmd abort failed
[371546.624051] scsi host9: Waking error handler thread
[371546.624060] scsi host9: scsi_eh_9: waking up 0/1/1
[371546.624081] sd 9:0:0:0: [sg19] tag#20 scsi_eh_9: flush finish cmd
[371546.624095] scsi host9: waking up host to restart
[371546.624098] scsi host9: scsi_eh_9: sleeping


[371546.635314] sd 8:0:0:0: [sg17] tag#13 abort scheduled
[371546.640031] sd 8:0:0:0: [sg17] tag#13 aborting command
[371546.640037] sd 8:0:0:0: [sg17] tag#13 cmd abort failed
[371546.640043] scsi host8: Waking error handler thread
[371546.640078] scsi host8: scsi_eh_8: waking up 0/1/1
[371546.640098] sd 8:0:0:0: [sg17] tag#13 scsi_eh_8: flush finish cmd
[371546.640113] scsi host8: waking up host to restart
[371546.640117] scsi host8: scsi_eh_8: sleeping

[371546.657269] sd 6:0:0:0: [sg12] tag#1 abort scheduled
[371546.664034] sd 6:0:0:0: [sg12] tag#1 aborting command
[371546.664040] sd 6:0:0:0: [sg12] tag#1 cmd abort failed

Here we can see that, error handler is not woken up.  And the entire
IO subsystem goes for a toss.

[371777.594510] INFO: task md2_raid1:508 blocked for more than 120 seconds.
[371777.594571]      Not tainted 4.4.0-31-generic #50~14.04.1-Ubuntu
[371777.594613] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs"
disables this message.
[371777.594665] md2_raid1      D ffff883fed2afc78    0  508      2 0x00000000
[371777.594673]  ffff883fed2afc78 ffff881fef0e8000 ffff883fed21c4c0
ffff883fed2b0000
[371777.594678]  ffff883ff236e298 ffff883ff236e000 ffff883ff236e018
ffff883ff236e018

By enabling more scsi logs(in a different system), including LL, we
get some more info ( I have enabled the full scsi levels for all
categories and it is still running)


System 2

[405197.171574] sd 5:0:0:0: [sg3] sg_write: count=88
[405197.171577] sd 5:0:0:0: scsi_block_when_processing_errors: rtn: 1
[405197.171581] sd 5:0:0:0: [sg3] sg_common_write:  scsi
opcode=0x85, cmd_size=16
[405197.171583] sd 5:0:0:0: [sg3] sg_start_req: dxfer_len=512
[405197.171605] sd 5:0:0:0: [sg3] sg_link_reserve: size=512
[405197.171623] sd 5:0:0:0: [sg3] sg_poll: res=0x104
[405197.172648] sd 5:0:0:0: [sg3] sg_cmd_done: pack_id=0, res=0x0
[405197.172701] sd 5:0:0:0: [sg3] sg_poll: res=0x145
[405197.172710] sd 5:0:0:0: [sg3] sg_read: count=88
[405197.172716] sd 5:0:0:0: [sg3] sg_finish_rem_req: res_used=1
[405197.172721] sd 5:0:0:0: [sg3] sg_unlink_reserve: req->k_use_sg=1
[405197.172756] sd 5:0:0:0: [sg3] sg_write: count=88
[405197.172760] sd 5:0:0:0: scsi_block_when_processing_errors: rtn: 1
[405197.172764] sd 5:0:0:0: [sg3] sg_common_write:  scsi
opcode=0x85, cmd_size=16
[405197.172767] sd 5:0:0:0: [sg3] sg_start_req: dxfer_len=512
[405197.172774] sd 5:0:0:0: [sg3] sg_link_reserve: size=512
[405197.172793] sd 5:0:0:0: [sg3] sg_poll: res=0x104
[405197.173806] sd 5:0:0:0: [sg3] sg_cmd_done: pack_id=0, res=0x0
[405197.173829] sd 5:0:0:0: [sg3] sg_poll: res=0x145
[405197.173836] sd 5:0:0:0: [sg3] sg_read: count=88
[405197.173839] sd 5:0:0:0: [sg3] sg_finish_rem_req: res_used=1
[405197.173843] sd 5:0:0:0: [sg3] sg_unlink_reserve: req->k_use_sg=1
[405197.173893] sd 5:0:0:0: [sg3] sg_write: count=88
[405197.173896] sd 5:0:0:0: scsi_block_when_processing_errors: rtn: 1
[405197.173900] sd 5:0:0:0: [sg3] sg_common_write:  scsi
opcode=0x85, cmd_size=16
[405197.173903] sd 5:0:0:0: [sg3] sg_start_req: dxfer_len=0
[405197.173921] sd 5:0:0:0: [sg3] sg_poll: res=0x104

[405197.174082] sd 5:0:0:0: [sg3] tag#5 abort scheduled
[405197.179372] sd 5:0:0:0: [sg3] tag#5 aborting command
[405197.179378] sd 5:0:0:0: [sg3] tag#5 cmd abort failed

[405257.225584] sd 5:0:0:0: [sg3] sg_poll: res=0x104
[405257.225599] sd 5:0:0:0: [sg3] sg_release
[405257.225617] sd 5:0:0:0: [sg3] sg_open: flags=0x8002

Error handler thread is not waken up here (or) i dont see flush
command trace (even if it is already woken up)

[405349.082863] INFO: task md2_raid1:484 blocked for more than 120 seconds
[405349.082922]      Not tainted 4.4.0-31-generic #50~14.04.1-Ubuntu
[405349.082964] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs"
disables this message.
[405349.083016] md2_raid1      D ffff881feca2bc78    0  484      2 0x00000000

[**["udevadm_sdd_130.2" (application/octet-stream)]**]("http://marc.info/?l=linux-scsi&m=148884815231422&q=p3")


Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1f.2/ata6/host5/target5:0:0/5:0:0:0/b \
lock/sdd':  KERNEL=="sdd"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{ro}=="0"
    ATTR{size}=="1953525168"
    ATTR{stat}=="  594416       53  5146632  2403584  1841671  1150754 30806441 \
15645364        6 74491712 311854740"  ATTR{range}=="16"
    ATTR{discard_alignment}=="0"
    ATTR{events}==""
    ATTR{ext_range}=="256"
    ATTR{events_poll_msecs}=="-1"
    ATTR{alignment_offset}=="0"
    ATTR{inflight}=="       0        6"
    ATTR{removable}=="0"
    ATTR{capability}=="50"
    ATTR{events_async}==""

  looking at parent device \
'/devices/pci0000:00/0000:00:1f.2/ata6/host5/target5:0:0/5:0:0:0':  \
KERNELS=="5:0:0:0"  SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{rev}=="A3U0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="6"
    ATTRS{model}=="HGST HTE721010A9"
    ATTRS{state}=="running"
    ATTRS{unload_heads}=="0"
    ATTRS{queue_type}=="none"
    ATTRS{iodone_cnt}=="0x3c27d2"
    ATTRS{iorequest_cnt}=="0x3e4c09"
    ATTRS{queue_ramp_up_period}=="120000"
    ATTRS{device_busy}=="1"
    ATTRS{evt_capacity_change_reported}=="0"
    ATTRS{timeout}=="30"
    ATTRS{evt_media_change}=="0"
    ATTRS{ioerr_cnt}=="0x14b9"
    ATTRS{queue_depth}=="31"
    ATTRS{vendor}=="ATA     "
    ATTRS{evt_soft_threshold_reached}=="0"
    ATTRS{device_blocked}=="1"
    ATTRS{evt_mode_parameter_change_reported}=="0"
    ATTRS{evt_lun_change_reported}=="0"
    ATTRS{evt_inquiry_change_reported}=="0"
    ATTRS{dh_state}=="detached"
    ATTRS{iocounterbits}=="32"
    ATTRS{inquiry}==""
    ATTRS{vpd_pg80}==""
    ATTRS{vpd_pg83}==""
    ATTRS{eh_timeout}=="10"

  looking at parent device '/devices/pci0000:00/0000:00:1f.2/ata6/host5/target5:0:0':
    KERNELS=="target5:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1f.2/ata6/host5':
    KERNELS=="host5"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1f.2/ata6':
    KERNELS=="ata6"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1f.2':
    KERNELS=="0000:00:1f.2"
    SUBSYSTEMS=="pci"
    DRIVERS=="ahci"
    ATTRS{irq}=="43"
    ATTRS{subsystem_vendor}=="0x152d"
    ATTRS{broken_parity_status}=="0"
    ATTRS{class}=="0x010601"
    ATTRS{index}=="1"
    ATTRS{label}=="Intel(R) C610 series/X99 chipset SATA Controller"
    ATTRS{driver_override}=="(null)"
    ATTRS{consistent_dma_mask_bits}=="64"
    ATTRS{dma_mask_bits}=="64"
    ATTRS{local_cpus}=="00,3ff003ff"
    ATTRS{device}=="0x8d02"
    ATTRS{enable}=="1"
    ATTRS{msi_bus}=="1"
    ATTRS{local_cpulist}=="0-9,20-29"
    ATTRS{vendor}=="0x8086"
    ATTRS{subsystem_device}=="0x89d5"
    ATTRS{numa_node}=="0"
    ATTRS{d3cold_allowed}=="1"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

---

### Post by kingneutron on 2017-03-15
--One suggestion: Try upgrading the kernel to the latest available - for Ubuntu 14.04, I see that the latest as of this writing for your kernel series is 4.4.0-67-generic. Also make sure all installed software is up to date as much as possible with ' apt-get upgrade ' and see if that helps. Post back with results.

---

### Post by kingneutron on 2017-03-15
--Another thought: could be a cabling or power issue, is your lab using quality SATAIII cabling and UPS (uninterruptible power)?

--And finally (although this is a long shot) what I/O scheduler are you using ?

$ cat /sys/block/sda/queue/scheduler
noop deadline [cfq]

---

