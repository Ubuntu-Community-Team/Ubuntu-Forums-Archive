---
title: "iSCSI Issue - Ubuntu Server 16.04.1 - iscsi_targets problem?"
date: 2018-02-26
forum: General Help
---

### Post by Andrew_Murdoch on 2018-02-26
Hey Guys

I'm running into a strange issue on Ubuntu Server 16.04.1 regarding iSCSI Targets.  I have ZFS (ZFS On Linux) installed mapped to dataset /tank/iscsi Inside of it I have a some ZFS volumes ex:

/tank/iscsi/a
/tank/iscsi/b
/tank/iscsi/c

etc....

I can see those volumes under /dev/zvol/tank/iscsi/a b c

When I boot a computer on my network, iPXE attempts to allocate an iSCSI target, this works 98% of the time, but randomly fails, the following is a sample of my output:

[FONT=arial]Feb 26 15:35:33 nextjen kernel: (13548.293697) iscsi_trgt: iscsi_volume_del(319) 348b87 0[/FONT]
[FONT=arial]Feb 26 15:35:33 nextjen kernel: (13548.439285) iscsi_trgt: iscsi_volume_del(319) 348b87 0[/FONT]
[FONT=arial]Feb 26 15:35:38 nextjen kernel: (13552.768854)  zd64: p1 p2[/FONT]
[FONT=arial]Feb 26 15:35:41 nextjen kernel: (13556.087650) iscsi_trgt: blockio_open_path(161) Can't open device /dev/zvol/tank/iscsi/a, error -2[/FONT]
[FONT=arial]Feb 26 15:35:41 nextjen kernel: (13556.089547) iscsi_trgt: blockio_attach(288) Error attaching Lun 0 to Target iqn.2017.foo:a [/FONT]
[FONT=arial]Feb 26 15:35:41 nextjen kernel: (13556.210798) iscsi_trgt: iscsi_volume_del(319) 348b87 0[/FONT]
[FONT=arial]Feb 26 15:35:43 nextjen kernel: (13558.323362) iscsi_trgt: blockio_open_path(161) Can't open device /dev/zvol/tank/iscsi/a, error -2[/FONT]
[FONT=arial]Feb 26 15:35:43 nextjen kernel: (13558.325422) iscsi_trgt: blockio_attach(288) Error attaching Lun 0 to Target iqn.2017.foo:a[/FONT]
[FONT=arial]Feb 26 15:35:57 nextjen kernel: (13571.728464) iscsi_trgt: scsi_cmnd_start(977) 18ae0002 0[/FONT]
[FONT=arial]Feb 26 15:35:57 nextjen kernel: (13571.730680) iscsi_trgt: cmnd_skip_pdu(471) 18ae0002 1c 0 0[/FONT]
[FONT=arial]Feb 26 15:36:07 nextjen kernel: (13582.416629) iscsi_trgt: iscsi_volume_del(319) 348b8a 0[/FONT]
[FONT=arial]Feb 26 15:36:08 nextjen kernel: (13582.836647) iscsi_trgt: iscsi_volume_del(319) 348b8a 0[/FONT]
[FONT=arial]Feb 26 15:36:12 nextjen kernel: (13586.738001)  zd48: p1 p2[/FONT]
[FONT=arial]Feb 26 15:36:15 nextjen kernel: (13590.204722) iscsi_trgt: blockio_open_path(161) Can't open device /dev/zvol/tank/iscsi/b, error -2[/FONT]
[FONT=arial]Feb 26 15:36:15 nextjen kernel: (13590.207729) iscsi_trgt: blockio_attach(288) Error attaching Lun 0 to Target iqn.2017.foo:b [/FONT]
[FONT=arial]Feb 26 15:36:15 nextjen kernel: (13590.309884) iscsi_trgt: iscsi_volume_del(319) 348b8a 0[/FONT]
[FONT=arial]Feb 26 15:36:17 nextjen kernel: (13592.479314) iscsi_trgt: blockio_open_path(161) Can't open device /dev/zvol/tank/iscsi/b, error -2[/FONT]
[FONT=arial]Feb 26 15:36:17 nextjen kernel: (13592.482783) iscsi_trgt: blockio_attach(288) Error attaching Lun 0 to Target iqn.2017.foo:b[/FONT]
[FONT=arial]Feb 26 15:36:48 nextjen kernel: (13623.048541) iscsi_trgt: scsi_cmnd_start(977) 18ae0002 0[/FONT]
[FONT=arial]Feb 26 15:36:48 nextjen kernel: (13623.052083) iscsi_trgt: cmnd_skip_pdu(471) 18ae0002 1c 0 0[/FONT]
[FONT=arial]Feb 26 15:36:48 nextjen kernel: (13623.132714) iscsi_trgt: scsi_cmnd_start(977) 18ae000c 0[/FONT]
[FONT=arial]Feb 26 15:36:48 nextjen kernel: (13623.137331) iscsi_trgt: cmnd_skip_pdu(471) 18ae000c 1c 0 0[/FONT]
[FONT=arial]Feb 26 15:37:08 nextjen kernel: (13643.499023) iscsi_trgt: iscsi_volume_del(319) 348b87 0[/FONT]
[FONT=arial]Feb 26 15:37:08 nextjen kernel: (13643.591240) iscsi_trgt: iscsi_volume_del(319) 348b87 0[/FONT]
[FONT=arial]Feb 26 15:37:09 nextjen kernel: (13643.887082)  zd64: p1 p2[/FONT]
[FONT=arial]Feb 26 15:37:41 nextjen kernel: (13676.384024) NOP-In ping timed out - closing sid:cid 8482732798050368:0[/FONT]
[FONT=arial]Feb 26 15:37:43 nextjen kernel: (13678.008182) iscsi_trgt: iscsi_volume_del(319) 348b8a 0

Has anyone ran into something similar?  I've seen forum posts where people have changed from iscsi_targets over to lio and it's seem to solve the issue, but is there a better solution?  I was thinking of looking at the kernel and seeing if I can change the configuration options, but I'm not sure.  

Thanks
Docmur[/FONT]

---

### Post by antamnoivongtinh on 2018-02-27
I've got this issue in the past and was able to resolve it with a clean closing of the iscsi cache connection.  Do not close the target, just the cache connection. If I remember correctly it is an option in lvm.conf as well as an additional code to sense the disconnect of the machine a, b, c.  Working 100% now.

---

