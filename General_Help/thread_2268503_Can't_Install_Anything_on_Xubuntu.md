---
title: "Can't Install Anything on Xubuntu"
date: 2015-03-09
forum: General Help
---

### Post by krampalli-kr on 2015-03-09
Recently, whenever I went to the terminal on Xubuntu 14.04 and tried to install something, it would give me rapid errors flying on the screen, saying "No space left on device", when I have 44 GB left on my partition for home. Do I need to expand my partition? Thanks in Advance! Here's the error message:
```
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/virtio_scsi.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/virtio_scsi.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/ppa.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/ppa.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/bfa/bfa.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/bfa/bfa.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/firmware/cbfw-3.2.1.1.bin’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/firmware/cbfw-3.2.1.1.bin’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/osst.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/osst.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/libsrp.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/libsrp.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/pcmcia/fdomain_cs.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/pcmcia/fdomain_cs.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/pcmcia/sym53c500_cs.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/pcmcia/sym53c500_cs.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/pcmcia/aha152x_cs.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/pcmcia/aha152x_cs.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/qlogicfas408.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/qlogicfas408.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/pcmcia/qlogic_cs.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/pcmcia/qlogic_cs.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/mpt3sas/mpt3sas.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/mpt3sas/mpt3sas.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/osd/libosd.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/osd/libosd.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/osd/osd.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/osd/osd.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/aic94xx/aic94xx.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/aic94xx/aic94xx.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/imm.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/imm.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/qla1280.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/qla1280.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/firmware/3.13.0-46-generic/qlogic/12160.bin’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/firmware/3.13.0-46-generic/qlogic/12160.bin’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/firmware/3.13.0-46-generic/qlogic/1280.bin’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/firmware/3.13.0-46-generic/qlogic/1280.bin’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/firmware/3.13.0-46-generic/qlogic/1040.bin’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/firmware/3.13.0-46-generic/qlogic/1040.bin’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/vmw_pvscsi.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/vmw_pvscsi.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/mvumi.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/mvumi.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/fcoe/fcoe.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/scsi/fcoe/fcoe.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/message/fusion/mptbase.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/message/fusion/mptbase.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/message/fusion/mptscsih.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/message/fusion/mptscsih.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/message/fusion/mptfc.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/message/fusion/mptfc.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/message/fusion/mptsas.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/message/fusion/mptsas.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/message/fusion/mptspi.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/message/fusion/mptspi.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/null_blk.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/null_blk.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/cryptoloop.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/cryptoloop.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/pktcdvd.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/pktcdvd.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/net/ceph/libceph.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/net/ceph/libceph.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/rbd.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/rbd.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/paride.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/paride.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/ktti.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/ktti.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/pd.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/pd.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/on20.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/on20.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/epat.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/epat.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/aten.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/aten.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/friq.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/friq.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/dstr.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/dstr.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/bpck.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/bpck.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/comm.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/comm.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/fit3.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/fit3.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/pg.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/pg.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/pt.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/pt.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/fit2.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/fit2.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/pf.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/pf.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/pcd.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/pcd.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/epia.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/epia.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/on26.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/on26.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/kbic.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/kbic.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/frpw.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/paride/frpw.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/skd.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/skd.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/nvme.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/nvme.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/xen-blkback/xen-blkback.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/xen-blkback/xen-blkback.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/nbd.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/nbd.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/osdblk.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/osdblk.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/rsxx/rsxx.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/rsxx/rsxx.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/umem.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/umem.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/mtip32xx/mtip32xx.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/mtip32xx/mtip32xx.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/floppy.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/floppy.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/aoe/aoe.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/aoe/aoe.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/DAC960.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/DAC960.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/lib/lru_cache.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/lib/lru_cache.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/drbd/drbd.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/drbd/drbd.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/sx8.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/sx8.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/cciss.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/block/cciss.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_via.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_via.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_nv.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_nv.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/libahci.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/libahci.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/acard-ahci.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/acard-ahci.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_platform.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_platform.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_pcmcia.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_pcmcia.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_sil680.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_sil680.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_piccolo.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_piccolo.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_marvell.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_marvell.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_netcell.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_netcell.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_sl82c105.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_sl82c105.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_svw.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_svw.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_sis.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_sis.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_rcar.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_rcar.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_hpt37x.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_hpt37x.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_it821x.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_it821x.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_ninja32.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_ninja32.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_via.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_via.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_ns87415.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_ns87415.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_ns87410.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_ns87410.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_amd.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_amd.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_sc1200.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_sc1200.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_opti.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_opti.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_hpt3x3.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_hpt3x3.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_cs5520.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_cs5520.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_rz1000.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_rz1000.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_oldpiix.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_oldpiix.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_vsc.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_vsc.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_sil24.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_sil24.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_sx4.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_sx4.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pdc_adma.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pdc_adma.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_radisys.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_radisys.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_cypress.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_cypress.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_mpiix.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_mpiix.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_artop.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_artop.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_jmicron.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_jmicron.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_sch.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_sch.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_serverworks.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_serverworks.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_pdc2027x.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_pdc2027x.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_cs5536.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_cs5536.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_pdc202xx_old.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_pdc202xx_old.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/phy/phy-core.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/phy/phy-core.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/ahci_platform.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/ahci_platform.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_promise.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_promise.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_acpi.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_acpi.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_uli.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_uli.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_it8213.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_it8213.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_hpt366.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_hpt366.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_qstor.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_qstor.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_hpt3x2n.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_hpt3x2n.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_inic162x.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_inic162x.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_atiixp.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_atiixp.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_rdc.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_rdc.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_legacy.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_legacy.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_cmd640.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_cmd640.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_atp867x.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_atp867x.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_arasan_cf.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_arasan_cf.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_efar.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_efar.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_cs5530.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_cs5530.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/ahci.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/ahci.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_cmd64x.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_cmd64x.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_triflex.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_triflex.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_mv.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_mv.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_optidma.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_optidma.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_ali.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/pata_ali.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_sil.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/ata/sata_sil.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/message/i2o/i2o_core.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/message/i2o/i2o_core.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/message/i2o/i2o_block.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/message/i2o/i2o_block.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/firewire/firewire-core.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/firewire/firewire-core.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/firewire/firewire-ohci.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/firewire/firewire-ohci.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/firewire/firewire-sbp2.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/firewire/firewire-sbp2.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/misc/tifm_core.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/misc/tifm_core.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/tifm_sd.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/tifm_sd.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/vub300.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/vub300.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/via-sdmmc.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/via-sdmmc.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mfd/rtsx_pci.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mfd/rtsx_pci.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/rtsx_pci_sdmmc.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/rtsx_pci_sdmmc.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/sdhci.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/sdhci.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/sdhci-pltfm.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/sdhci-pltfm.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/sdhci-pxav3.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/sdhci-pxav3.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/wbsd.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/wbsd.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/lib/crc7.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/lib/crc7.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/mmc_spi.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/mmc_spi.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/sdhci-pxav2.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/sdhci-pxav2.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/ushc.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/ushc.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/misc/cb710/cb710.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/misc/cb710/cb710.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/cb710-mmc.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/cb710-mmc.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/sdhci-pci.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/sdhci-pci.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/sdhci-acpi.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/sdhci-acpi.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/sdricoh_cs.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/host/sdricoh_cs.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/card/mmc_block.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/card/mmc_block.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/card/sdio_uart.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/mmc/card/sdio_uart.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/usb-storage.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/usb-storage.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-sddr09.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-sddr09.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-sddr55.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-sddr55.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-cypress.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-cypress.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-eneub6250.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-eneub6250.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/firmware/ene-ub6250/ms_rdwr.bin’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/firmware/ene-ub6250/ms_rdwr.bin’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/firmware/ene-ub6250/msp_rdwr.bin’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/firmware/ene-ub6250/msp_rdwr.bin’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/firmware/ene-ub6250/ms_init.bin’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/firmware/ene-ub6250/ms_init.bin’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/firmware/ene-ub6250/sd_rdwr.bin’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/firmware/ene-ub6250/sd_rdwr.bin’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/firmware/ene-ub6250/sd_init2.bin’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/firmware/ene-ub6250/sd_init2.bin’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/firmware/ene-ub6250/sd_init1.bin’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/firmware/ene-ub6250/sd_init1.bin’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-karma.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-karma.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-isd200.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-isd200.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-usbat.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-usbat.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-realtek.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-realtek.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-jumpshot.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-jumpshot.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-freecom.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-freecom.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-datafab.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-datafab.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-onetouch.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-onetouch.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-alauda.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/usb/storage/ums-alauda.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/hv/hv_utils.ko’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/modules/3.13.0-46-generic/kernel/drivers/hv/hv_utils.ko’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/init’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/init’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/scripts/./init-top/blacklist’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/scripts/./init-top/blacklist’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/scripts/./init-top/udev’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/scripts/./init-top/udev’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/scripts/./init-top/all_generic_ide’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/scripts/./init-top/all_generic_ide’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/scripts/./nfs’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/scripts/./nfs’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/scripts/./panic/console_setup’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/scripts/./panic/console_setup’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/scripts/./panic/keymap’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/scripts/./panic/keymap’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/scripts/./local’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/scripts/./local’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/scripts/./init-bottom/udev’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/scripts/./init-bottom/udev’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/scripts/./local-bottom/ntfs_3g’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/scripts/./local-bottom/ntfs_3g’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/scripts/./functions’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/scripts/./functions’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/scripts/./local-premount/fixrtc’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/scripts/./local-premount/fixrtc’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/scripts/./local-premount/resume’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/scripts/./local-premount/resume’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/scripts/./local-premount/ntfs_3g’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/scripts/./local-premount/ntfs_3g’: No space left on device
sh: echo: I/O error
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/conf/initramfs.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/conf/initramfs.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//conf/conf.d/resume’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//conf/conf.d/resume’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//sbin/wait-for-root’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//sbin/wait-for-root’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/x86_64-linux-gnu/libudev.so.1’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/x86_64-linux-gnu/libudev.so.1’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/x86_64-linux-gnu/libc.so.6’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/x86_64-linux-gnu/libc.so.6’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/x86_64-linux-gnu/libcgmanager.so.0’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/x86_64-linux-gnu/libcgmanager.so.0’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/x86_64-linux-gnu/libnih.so.1’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/x86_64-linux-gnu/libnih.so.1’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/x86_64-linux-gnu/libnih-dbus.so.1’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/x86_64-linux-gnu/libnih-dbus.so.1’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/x86_64-linux-gnu/libdbus-1.so.3’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/x86_64-linux-gnu/libdbus-1.so.3’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/x86_64-linux-gnu/librt.so.1’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/x86_64-linux-gnu/librt.so.1’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib64/ld-linux-x86-64.so.2’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib64/ld-linux-x86-64.so.2’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/x86_64-linux-gnu/libpthread.so.0’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/x86_64-linux-gnu/libpthread.so.0’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//sbin/modprobe’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//sbin/modprobe’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//sbin/rmmod’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//sbin/rmmod’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/alsa-base.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/alsa-base.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/blacklist-ath_pci.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/blacklist-ath_pci.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/blacklist-bcm43.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/blacklist-bcm43.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/blacklist-firewire.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/blacklist-firewire.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/blacklist-framebuffer.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/blacklist-framebuffer.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/blacklist-modem.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/blacklist-modem.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/blacklist-rare-network.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/blacklist-rare-network.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/blacklist-watchdog.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/blacklist-watchdog.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/blacklist.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/blacklist.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/dkms.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/dkms.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/fbdev-blacklist.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/fbdev-blacklist.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/iwlwifi.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/iwlwifi.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/mlx4.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/mlx4.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/vmware-fuse.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/vmware-fuse.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/vmwgfx-fbdev.conf’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng/etc/modprobe.d/vmwgfx-fbdev.conf’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//sbin/blkid’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//sbin/blkid’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/x86_64-linux-gnu/libblkid.so.1’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/x86_64-linux-gnu/libblkid.so.1’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//lib/x86_64-linux-gnu/libuuid.so.1’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//lib/x86_64-linux-gnu/libuuid.so.1’: No space left on device
cp: error writing ‘/tmp/mkinitramfs_9G3Sng//bin/date’: No space left on device
cp: failed to extend ‘/tmp/mkinitramfs_9G3Sng//bin/date’: No space left on device
E: /usr/share/initramfs-tools/hooks/fixrtc failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.13.0-46-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.13.0-46-generic.postinst line 1025.
dpkg: error processing package linux-image-3.13.0-46-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-46-generic:
 linux-image-extra-3.13.0-46-generic depends on linux-image-3.13.0-46-generic; however:
  Package linux-image-3.13.0-46-generic is not configured yet.


dpkg: error processing package linux-image-extra-3.13.0-46-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
No apport report written because the error message indicates its a followup error from a previous failure.
                           linux-image-generic depends on linux-image-3.13.0-46-generic; however:
  Package linux-image-3.13.0-46-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.13.0-46-generic; however:
  Package linux-image-extra-3.13.0-46-generic is not configured yet.


dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.46.53); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic-lts-quantal:
 linux-generic-lts-quantal depends on linux-generic; however:
  Package linux-generic is not configured yet.


dpkg: error processing package linux-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-signed-image-3.13.0-46-generic:
 linux-signed-image-3.13.0-46-generic depends on linux-image-3.13.0-46-generic (= 3.13.0-46.76); however:
  Package linux-image-3.13.0-46-generic is not configured yet.
 linux-signed-image-3.13.0-46-generic depends on linux-image-extra-3.13.0-46-generic (= 3.13.0-46.76); however:
  Package linux-image-extra-3.13.0-46-generic is not configured yet.


dpkg: error processing package linux-signed-image-3.13.0-46-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-signed-image-generic:
 linux-signed-image-generic depends on linux-signed-image-3.13.0-46-generic; however:
  Package linux-signed-image-3.13.0-46-generic is not configured yet.


dpkg: error processing package linux-signed-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-generic:
 linux-signed-generic depends on linux-signed-image-generic (= 3.13.0.46.53); however:
No apport report written because MaxReports is reached already
                                                                Package linux-signed-image-generic is not configured yet.


dpkg: error processing package linux-signed-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up gdebi-core (0.9.5.3ubuntu2) ...
Setting up gdebi (0.9.5.3ubuntu2) ...
Errors were encountered while processing:
 linux-image-3.13.0-46-generic
 linux-image-extra-3.13.0-46-generic
 linux-image-generic
 linux-generic
 linux-generic-lts-quantal
 linux-signed-image-3.13.0-46-generic
 linux-signed-image-generic
 linux-signed-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

[COLOR=#000000]I was just using sudo apt-get install package when this happend.


[/COLOR]

---

### Post by v3.xx on 2015-03-09
Is your boot full?
```
df -h
```

---

### Post by The Cog on 2015-03-09
I suspect it's the main / partition that is full because that's normally where you find /tmp. Still, **df -h** should confirm.

---

### Post by slickymaster on 2015-03-09
> **v3.xx said:**
> Is your boot full?
```
df -h
```
Besides that ^^^, can you also provide the output of```
dpkg -l 'linux-image*'
```

---

