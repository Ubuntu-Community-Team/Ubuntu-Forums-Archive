---
title: "Making live distro: need help with linux boot process"
date: 2008-01-13
forum: General Help
---

### Post by rocketman768 on 2008-01-13
I am trying to make my own live distro on a USB thumbdrive.

Thumbdrive(fat16) /dev/sdb1 mounted on /mnt/usb

First, I made a directory and called debootstrap on it to make a minimal debian system in it. I chroot'd into it and used apt-get to install the kernel, modules, and initrd image. I then packaged it up into an ext2 filesystem on /mnt/usb/newroot.ext2.

Here's my problem: I want to load this filesystem into /dev/ram0 (I suppose while the initrd is loaded) so that the kernel mounts /dev/ram0 as root.

What I tried was to extract the default initrd.img that came with the kernel. I then modified the "init" script in the root directory of the uncompressed image to the following:

```

#!/bin/sh

echo "Loading, please wait..."

[ -d /dev ] || mkdir -m 0755 /dev
[ -d /root ] || mkdir --mode=0700 /root
[ -d /sys ] || mkdir /sys
[ -d /proc ] || mkdir /proc
[ -d /tmp ] || mkdir /tmp
mkdir -p /var/lock
mount -t sysfs none /sys -onodev,noexec,nosuid
mount -t proc none /proc -onodev,noexec,nosuid

# Note that this only becomes /dev on the real filesystem if udev's scripts
# are used; which they will be, but it's worth pointing out
mount -t tmpfs -o mode=0755 udev /dev
[ -e /dev/console ] || mknod /dev/console c 5 1
[ -e /dev/null ] || mknod /dev/null c 1 3
> /dev/.initramfs-tools
mkdir /dev/.initramfs

# Export the dpkg architecture
export DPKG_ARCH=
. /conf/arch.conf

# Export it for root hardcoding
export ROOT=

# Bring in the main config
. /conf/initramfs.conf
for i in conf/conf.d/*; do
	[ -f ${i} ] && . ${i}
done
. /scripts/functions

#=== I put this in ===
echo "0" > /proc/sys/kernel/printk

# Parse command line options
export break=
export init=/sbin/init
export quiet=n
export readonly=y
export rootmnt=/root
export debug=
export cryptopts=${CRYPTOPTS}
export panic

for x in $(cat /proc/cmdline); do
	case $x in
	init=*)
		init=${x#init=}
		;;
	root=*)
		ROOT=${x#root=}
		case $ROOT in
		LABEL=*)
			ROOT="/dev/disk/by-label/${ROOT#LABEL=}"
			;;
		UUID=*)
			ROOT="/dev/disk/by-uuid/${ROOT#UUID=}"
			;;
		/dev/nfs)
			BOOT=nfs
			;;
		esac
		;;
	rootflags=*)
		ROOTFLAGS="-o ${x#rootflags=}"
		;;
	rootfstype=*)
		ROOTFSTYPE="${x#rootfstype=}"
		;;
	rootdelay=*)
		ROOTDELAY="${x#rootdelay=}"
		;;
	loop=*)
		LOOP="${x#loop=}"
		;;
	loopflags=*)
		LOOPFLAGS="-o ${x#loopflags=}"
		;;
	loopfstype=*)
		LOOPFSTYPE="${x#loopfstype=}"
		;;
	cryptopts=*)
		cryptopts="${x#cryptopts=}"
		;;
	nfsroot=*)
		NFSROOT="${x#nfsroot=}"
		;;
	netboot=*)
		NETBOOT="${x#netboot=}"
		;;
	ip=*)
		IPOPTS="${x#ip=}"
		;;
	boot=*)
		BOOT=${x#boot=}
		;;
	resume=*)
		RESUME="${x#resume=}"
		;;
	noresume)
		NORESUME=y
		;;
	panic=*)
		panic="${x#panic=}"
		;;
	quiet)
		quiet=y
		;;
	ro)
		readonly=y
		;;
	rw)
		readonly=n
		;;
	debug)
		debug=y
		exec >/tmp/initramfs.debug 2>&1
		set -x
		;;
	debug=*)
		debug=y
		set -x
		;;
	break=*)
		break=${x#break=}
		;;
	break)
		break=premount
		;;
	esac
done

if [ -z "${NORESUME}" ]; then
	export resume=${RESUME}
fi

depmod -a
maybe_break top

# Don't do log messages here to avoid confusing usplash
run_scripts /scripts/init-top

maybe_break modules
log_begin_msg "Loading essential drivers..."
load_modules
log_end_msg

maybe_break premount
[ "$quiet" != "y" ] && log_begin_msg "Running /scripts/init-premount"
run_scripts /scripts/init-premount
[ "$quiet" != "y" ] && log_end_msg

#===BEGIN MYSTUFF===

insmod ext2 && echo "Ext2 loaded"
insmod vfat && echo "Vfat loaded"
mount /dev/sdb1 /mnt/tmp && echo "sdb1 mounted"
dd if=/mnt/tmp/newroot.ext2 of=/dev/ram0 && "FS copied to /dev/ram0"

#===END MYSTUFF===

maybe_break mount
log_begin_msg "Mounting root file system..."
. /scripts/${BOOT}
parse_numeric ${ROOT}
mountroot
log_end_msg

maybe_break bottom
[ "$quiet" != "y" ] && log_begin_msg "Running /scripts/init-bottom"
run_scripts /scripts/init-bottom
[ "$quiet" != "y" ] && log_end_msg

# Move virtual filesystems over to the real filesystem
mount -n -o move /sys ${rootmnt}/sys
mount -n -o move /proc ${rootmnt}/proc

while [ ! -x ${rootmnt}${init} ]; do
	panic "Target filesystem doesn't have ${init}"
done

# Confuses /etc/init.d/rc
if [ -n ${debug} ]; then
	unset debug
fi

# Chain to real filesystem
maybe_break init
exec run-init ${rootmnt} ${init} "$@" <${rootmnt}/dev/console >${rootmnt}/dev/console

```

...My changes are clearly marked with comments. Basically I mount /dev/sdb1 (which should be the thumbdrive) on /mnt/tmp (which exists in the initrd) and then use dd to copy /mnt/tmp/newroot.ext2 to /dev/ram0. By doing small tests on a working system, I know you can copy the ext2 filesystem to the ramdisk and mount it afterwards. I then packaged this back up with cpio and gzip.

I put syslinux on the thumdrive and boot up with this:

```
boot: vmlinuz initrd=initrd.gz ramdisk_size=1000000 root=/dev/ram0
```

And of course it fails. Something to the effect of a kernel panic, can't mount root fs, and that it tried the cramfs.

I think it's pretty much that I am not exactly sure what happens during bootup. I THINK that the initrd.gz gets decompressed, and then mounted to / and then executes /init. During the script, it should copy the newroot.ext2 to the ramdisk and later in the script should try to mount /dev/ram0 to / since I specify it at boot time.

Could someone help clarify what might be going wrong? Perhaps just a detailed explanation of the boot process? Maybe some tips to put in init? Also, don't reply saying to do it using some tool or something. I really want to figure out what is going on and how to do it myself. Thanks so much!

Here is a file list of the contents of init.img (decompressed)
```

./conf
./conf/conf.d
./conf/initramfs.conf
./conf/arch.conf
./conf/modules
./mnt
./mnt/tmp
./mnt/ramdisk
./bin
./bin/nfsmount
./bin/readlink
./bin/resume
./bin/minips
./bin/kinit
./bin/consolechars
./bin/chroot
./bin/sh
./bin/true
./bin/mknod
./bin/insmod
./bin/nuke
./bin/loadkeys
./bin/zcat
./bin/uname
./bin/sleep
./bin/false
./bin/ipconfig
./bin/halt
./bin/kill
./bin/cat
./bin/poweroff
./bin/reboot
./bin/kbd_mode
./bin/mkfifo
./bin/sh.shared
./bin/kinit.shared
./bin/mount
./bin/pivot_root
./bin/run-init
./bin/gunzip
./bin/ln
./bin/mkdir
./bin/cpio
./bin/umount
./bin/busybox
./bin/fstype
./bin/dd
./bin/gzip
./etc
./etc/udev
./etc/udev/udev.conf
./etc/udev/rules.d
./etc/udev/rules.d/80-programs.rules
./etc/udev/rules.d/00-init.rules
./etc/udev/rules.d/05-options.rules
./etc/udev/rules.d/20-names.rules
./etc/udev/rules.d/90-modprobe.rules
./etc/udev/rules.d/65-persistent-storage.rules
./etc/modprobe.d
./etc/modprobe.d/aliases
./etc/modprobe.d/blacklist-watchdog
./etc/modprobe.d/lrm-video.dpkg-new
./etc/modprobe.d/arch-aliases
./etc/modprobe.d/isapnp
./etc/modprobe.d/alsa-base
./etc/modprobe.d/options
./etc/modprobe.d/ipw3945.dpkg-new
./etc/modprobe.d/nvidia-kernel-nkc.dpkg-new
./etc/modprobe.d/blacklist-oss
./etc/modprobe.d/blacklist-modem
./etc/modprobe.d/arch
./etc/modprobe.d/arch/i386
./etc/modprobe.d/blacklist
./etc/modprobe.d/blacklist-framebuffer
./etc/console-setup
./etc/console-setup/Uni1-Fixed16.psf.gz
./etc/console-setup/boottime.kmap.gz
./etc/default
./etc/default/console-setup
./sbin
./sbin/rmmod
./sbin/udevd
./sbin/udevtrigger
./sbin/modprobe
./sbin/udevsettle
./sbin/depmod
./sbin/mke2fs
./sbin/pkill
./scripts
./scripts/local-top
./scripts/nfs-top
./scripts/nfs-top/udev
./scripts/local-bottom
./scripts/local
./scripts/functions
./scripts/local-premount
./scripts/local-premount/resume
./scripts/casper-premount
./scripts/init-bottom
./scripts/init-bottom/udev
./scripts/nfs-premount
./scripts/nfs
./scripts/nfs-bottom
./scripts/init-premount
./scripts/init-premount/udev
./scripts/init-premount/ps3
./scripts/init-top
./scripts/init-top/all_generic_ide
./scripts/init-top/framebuffer
./scripts/init-top/console_setup
./init
./modules
./var
./var/run
./lib
./lib/klibc-lASvnk07aNkfPyCauZ-jxAx49Jk.so
./lib/libcfont.so.0
./lib/ld-linux.so.2
./lib/udev
./lib/udev/path_id
./lib/udev/usb_device_name
./lib/udev/dvb_device_name
./lib/udev/vio_type
./lib/udev/watershed
./lib/udev/firmware_helper
./lib/udev/edd_id
./lib/udev/ide_media
./lib/udev/ata_id
./lib/udev/scsi_id
./lib/udev/vol_id
./lib/udev/pnp_modules
./lib/udev/usb_id
./lib/libctutils.so.0
./lib/libproc-3.2.7.so
./lib/libselinux.so.1
./lib/libsepol.so.1
./lib/libconsole.so.0
./lib/libdl.so.2
./lib/firmware
./lib/firmware/2.6.22-14-386
./lib/firmware/2.6.22-14-386/ql2100_fw.bin
./lib/firmware/2.6.22-14-386/ql2400_fw.bin
./lib/firmware/2.6.22-14-386/ql2200_fw.bin
./lib/firmware/2.6.22-14-386/aic94xx-seq.fw
./lib/firmware/2.6.22-14-386/ql2300_fw.bin
./lib/firmware/2.6.22-14-386/ql2322_fw.bin
./lib/libc.so.6
./lib/libvolume_id.so.0
./lib/modules
./lib/modules/2.6.22-14-386
./lib/modules/2.6.22-14-386/kernel
./lib/modules/2.6.22-14-386/kernel/security
./lib/modules/2.6.22-14-386/kernel/security/commoncap.ko
./lib/modules/2.6.22-14-386/kernel/security/capability.ko
./lib/modules/2.6.22-14-386/kernel/net
./lib/modules/2.6.22-14-386/kernel/net/sunrpc
./lib/modules/2.6.22-14-386/kernel/net/sunrpc/sunrpc.ko
./lib/modules/2.6.22-14-386/kernel/net/packet
./lib/modules/2.6.22-14-386/kernel/net/packet/af_packet.ko
./lib/modules/2.6.22-14-386/kernel/drivers
./lib/modules/2.6.22-14-386/kernel/drivers/cdrom
./lib/modules/2.6.22-14-386/kernel/drivers/cdrom/cdrom.ko
./lib/modules/2.6.22-14-386/kernel/drivers/acpi
./lib/modules/2.6.22-14-386/kernel/drivers/acpi/processor.ko
./lib/modules/2.6.22-14-386/kernel/drivers/acpi/fan.ko
./lib/modules/2.6.22-14-386/kernel/drivers/acpi/thermal.ko
./lib/modules/2.6.22-14-386/kernel/drivers/message
./lib/modules/2.6.22-14-386/kernel/drivers/message/fusion
./lib/modules/2.6.22-14-386/kernel/drivers/message/fusion/mptbase.ko
./lib/modules/2.6.22-14-386/kernel/drivers/message/fusion/mptfc.ko
./lib/modules/2.6.22-14-386/kernel/drivers/message/fusion/mptsas.ko
./lib/modules/2.6.22-14-386/kernel/drivers/message/fusion/mptscsih.ko
./lib/modules/2.6.22-14-386/kernel/drivers/message/fusion/mptspi.ko
./lib/modules/2.6.22-14-386/kernel/drivers/message/i2o
./lib/modules/2.6.22-14-386/kernel/drivers/message/i2o/i2o_block.ko
./lib/modules/2.6.22-14-386/kernel/drivers/message/i2o/i2o_core.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ieee1394
./lib/modules/2.6.22-14-386/kernel/drivers/ieee1394/ieee1394.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ieee1394/sbp2.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ieee1394/ohci1394.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/fd_mcs.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/NCR53C9x.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/aacraid
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/aacraid/aacraid.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/raid_class.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/gdth.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/eata.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/g_NCR5380_mmio.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/imm.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/53c700.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/ch.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/scsi_transport_fc.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/iscsi_tcp.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/initio.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/ips.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/lpfc
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/lpfc/lpfc.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/t128.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/mca_53c9x.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/ultrastor.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/qlogicfas408.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/megaraid
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/megaraid/megaraid_mm.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/megaraid/megaraid_sas.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/megaraid/megaraid_mbox.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/stex.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/dpt_i2o.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/u14-34f.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/pcmcia
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/pcmcia/qlogic_cs.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/pcmcia/fdomain_cs.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/pcmcia/nsp_cs.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/pcmcia/sym53c500_cs.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/pcmcia/aha152x_cs.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/sd_mod.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/ide-scsi.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/g_NCR5380.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/atp870u.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/wd7000.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/megaraid.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/scsi_tgt.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/pas16.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/st.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/in2000.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/sim710.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/scsi_wait_scan.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/aha152x.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/qla1280.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/seagate.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/ibmmca.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/nsp32.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/osst.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/NCR_D700.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/arcmsr
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/arcmsr/arcmsr.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/aha1740.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/sym53c8xx_2
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/sym53c8xx_2/sym53c8xx.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/aic7xxx
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/aic7xxx/aic79xx.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/aic7xxx/aic7xxx.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/libsrp.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/BusLogic.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/libsas
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/libsas/libsas.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/qla4xxx
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/qla4xxx/qla4xxx.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/scsi_debug.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/scsi_transport_iscsi.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/dc395x.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/qla2xxx
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/qla2xxx/qla2xxx.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/psi240i.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/sym53c416.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/dtc.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/NCR53c406a.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/scsi_mod.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/advansys.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/libiscsi.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/dmx3191d.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/sr_mod.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/aha1542.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/NCR_Q720_mod.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/scsi_transport_sas.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/qlogicfas.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/aic94xx
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/aic94xx/aic94xx.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/ipr.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/3w-xxxx.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/a100u2w.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/tmscsim.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/ppa.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/3w-9xxx.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/sg.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/scsi_transport_spi.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/hptiop.ko
./lib/modules/2.6.22-14-386/kernel/drivers/scsi/fdomain.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net
./lib/modules/2.6.22-14-386/kernel/drivers/net/b44.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/bnx2.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/r8169.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/sungem.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/tlan.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/8139too.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/natsemi.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/e1000
./lib/modules/2.6.22-14-386/kernel/drivers/net/e1000/e1000.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/qla3xxx.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/yellowfin.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/myri10ge
./lib/modules/2.6.22-14-386/kernel/drivers/net/myri10ge/myri10ge.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/3c59x.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/slhc.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/via-rhine.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/defxx.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/e100.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/8139cp.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/epic100.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/8390.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/s2io.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/sungem_phy.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/hp100.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/sis900.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/forcedeth.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/ns83820.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/sunhme.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/sundance.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/skge.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/eql.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/ne2k-pci.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/fealnx.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/netconsole.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/starfire.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/via-velocity.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/pcnet32.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/mii.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/dl2k.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/tg3.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/tulip
./lib/modules/2.6.22-14-386/kernel/drivers/net/tulip/de4x5.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/tulip/tulip.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/tulip/xircom_cb.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/tulip/de2104x.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/tulip/dmfe.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/tulip/xircom_tulip_cb.ko
./lib/modules/2.6.22-14-386/kernel/drivers/net/tulip/winbond-840.ko
./lib/modules/2.6.22-14-386/kernel/drivers/video
./lib/modules/2.6.22-14-386/kernel/drivers/video/vga16fb.ko
./lib/modules/2.6.22-14-386/kernel/drivers/video/vgastate.ko
./lib/modules/2.6.22-14-386/kernel/drivers/pcmcia
./lib/modules/2.6.22-14-386/kernel/drivers/pcmcia/pcmcia_core.ko
./lib/modules/2.6.22-14-386/kernel/drivers/pcmcia/pcmcia.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ide
./lib/modules/2.6.22-14-386/kernel/drivers/ide/pci
./lib/modules/2.6.22-14-386/kernel/drivers/ide/pci/opti621.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ide/pci/cmd64x.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ide/pci/cs5535.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ide/pci/delkin_cb.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ide/pci/sc1200.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ide/pci/hpt366.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ide/pci/pdc202xx_old.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ide/pci/ns87415.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ide/pci/cs5530.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ide/pci/aec62xx.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ide/pci/tc86c001.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ide/pci/trm290.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ide/pci/via82cxxx.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ide/pci/hpt34x.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ide/pci/atiixp.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ide/pci/amd74xx.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ide/pci/alim15x3.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ide/pci/cy82c693.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ide/ide-core.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ide/ide-generic.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ide/ide-cd.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ide/ide-tape.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ide/ide-floppy.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ide/ide-disk.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block
./lib/modules/2.6.22-14-386/kernel/drivers/block/cryptoloop.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/cpqarray.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/xd.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/floppy.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/DAC960.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/sx8.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/loop.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/cciss.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/umem.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/aoe
./lib/modules/2.6.22-14-386/kernel/drivers/block/aoe/aoe.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/pktcdvd.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/nbd.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/paride
./lib/modules/2.6.22-14-386/kernel/drivers/block/paride/pcd.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/paride/aten.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/paride/fit3.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/paride/friq.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/paride/on26.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/paride/fit2.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/paride/kbic.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/paride/epat.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/paride/bpck.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/paride/on20.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/paride/pg.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/paride/pf.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/paride/ktti.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/paride/pt.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/paride/bpck6.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/paride/epia.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/paride/dstr.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/paride/pd.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/paride/frpw.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/paride/comm.ko
./lib/modules/2.6.22-14-386/kernel/drivers/block/paride/paride.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata
./lib/modules/2.6.22-14-386/kernel/drivers/ata/sata_via.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/pata_sl82c105.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/sata_sis.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/pata_qdi.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/pata_triflex.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/sata_sil.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/pata_serverworks.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/sata_sil24.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/pata_pdc2027x.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/pata_cs5520.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/sata_promise.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/sata_qstor.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/sata_uli.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/sata_nv.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/sata_mv.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/sata_sx4.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/ata_piix.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/ahci.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/pata_jmicron.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/ata_generic.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/pata_marvell.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/sata_inic162x.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/sata_svw.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/pata_it8213.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/pata_sil680.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/pata_pcmcia.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/pata_mpiix.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/pata_oldpiix.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/sata_vsc.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/pata_netcell.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/pdc_adma.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/pata_sis.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/pata_efar.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/libata.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/pata_it821x.ko
./lib/modules/2.6.22-14-386/kernel/drivers/ata/pata_rz1000.ko
./lib/modules/2.6.22-14-386/kernel/drivers/usb
./lib/modules/2.6.22-14-386/kernel/drivers/usb/storage
./lib/modules/2.6.22-14-386/kernel/drivers/usb/storage/libusual.ko
./lib/modules/2.6.22-14-386/kernel/drivers/usb/storage/usb-storage.ko
./lib/modules/2.6.22-14-386/kernel/drivers/usb/core
./lib/modules/2.6.22-14-386/kernel/drivers/usb/core/usbcore.ko
./lib/modules/2.6.22-14-386/kernel/drivers/usb/host
./lib/modules/2.6.22-14-386/kernel/drivers/usb/host/ohci-hcd.ko
./lib/modules/2.6.22-14-386/kernel/drivers/usb/host/ehci-hcd.ko
./lib/modules/2.6.22-14-386/kernel/drivers/usb/host/uhci-hcd.ko
./lib/modules/2.6.22-14-386/kernel/drivers/parport
./lib/modules/2.6.22-14-386/kernel/drivers/parport/parport.ko
./lib/modules/2.6.22-14-386/kernel/drivers/hid
./lib/modules/2.6.22-14-386/kernel/drivers/hid/hid.ko
./lib/modules/2.6.22-14-386/kernel/drivers/hid/usbhid
./lib/modules/2.6.22-14-386/kernel/drivers/hid/usbhid/usbhid.ko
./lib/modules/2.6.22-14-386/kernel/lib
./lib/modules/2.6.22-14-386/kernel/lib/crc-ccitt.ko
./lib/modules/2.6.22-14-386/kernel/fs
./lib/modules/2.6.22-14-386/kernel/fs/lockd
./lib/modules/2.6.22-14-386/kernel/fs/lockd/lockd.ko
./lib/modules/2.6.22-14-386/kernel/fs/xfs
./lib/modules/2.6.22-14-386/kernel/fs/xfs/xfs.ko
./lib/modules/2.6.22-14-386/kernel/fs/isofs
./lib/modules/2.6.22-14-386/kernel/fs/isofs/isofs.ko
./lib/modules/2.6.22-14-386/kernel/fs/udf
./lib/modules/2.6.22-14-386/kernel/fs/udf/udf.ko
./lib/modules/2.6.22-14-386/kernel/fs/reiserfs
./lib/modules/2.6.22-14-386/kernel/fs/reiserfs/reiserfs.ko
./lib/modules/2.6.22-14-386/kernel/fs/jbd
./lib/modules/2.6.22-14-386/kernel/fs/jbd/jbd.ko
./lib/modules/2.6.22-14-386/kernel/fs/mbcache.ko
./lib/modules/2.6.22-14-386/kernel/fs/ext2
./lib/modules/2.6.22-14-386/kernel/fs/ext2/ext2.ko
./lib/modules/2.6.22-14-386/kernel/fs/nfs
./lib/modules/2.6.22-14-386/kernel/fs/nfs/nfs.ko
./lib/modules/2.6.22-14-386/kernel/fs/ext3
./lib/modules/2.6.22-14-386/kernel/fs/ext3/ext3.ko
./lib/modules/2.6.22-14-386/kernel/fs/jfs
./lib/modules/2.6.22-14-386/kernel/fs/jfs/jfs.ko

```

---

