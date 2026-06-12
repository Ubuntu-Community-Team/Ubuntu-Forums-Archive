---
title: "Timed out waiting for device dev-disk-by\x2duuid-8f8161e7\x2d54ae\x2d4525\x2da072\x2d"
date: 2024-11-01
forum: General Help
---

### Post by lmiksche on 2024-11-01
Hi Im getting this problem on my datastore (running cockpit) which is delaying boot for 90 seconds.
Checked the ussual - fstab and grub, and cant see anything that would indicate any problem there and all drives I need are mounted correctly.
I think it has somthing to do with me deleting and recreating array with different configuration, but I would think cockpit would take care of any problems. But I did at one time created btrfs raid 5 manually and deleted that in the cocpit, so thinking it may not have updated some config file. (not great in linux yet, so need a bit of help, thanks.)

Attaching a log, that can tell someone what is wrong as welll as lsblk and efibootmgr:

```

CODE_FILE src/core/job.c
CODE_FUNC job_emit_done_message
CODE_LINE 796
INVOCATION_ID JOB_ID 109
JOB_RESULT timeout
JOB_TYPE start
MESSAGE_ID be02cf6855d2428ba40df7e9d022f03d
PRIORITY 3
SYSLOG_FACILITY 3
SYSLOG_IDENTIFIER systemd
TID 1
UNIT dev-disk-by\x2duuid-8f8161e7\x2d54ae\x2d4525\x2da072\x2d207b4c21564d.device
_BOOT_ID d54e952fabbc4d258f203a801492fb46
_CAP_EFFECTIVE 1ffffffffff
_CMDLINE /sbin/init
_COMM systemd
_EXE /usr/lib/systemd/systemd
_GID 0
_HOSTNAME datastore
_MACHINE_ID 0d4ae5317c2a4c448f4623fcbe2daec4
_PID 1
_RUNTIME_SCOPE system
_SELINUX_CONTEXT unconfined
_SOURCE_REALTIME_TIMESTAMP 1730454687929476
_SYSTEMD_CGROUP /init.scope
_SYSTEMD_SLICE -.slice
_SYSTEMD_UNIT init.scope
_TRANSPORT journal
_UID 0
__CURSOR ;i=3a62c;b=d54e952fabbc4d258f203a801492fb46;m=5d8e0e2;t=625d6e0f960e7;x=dfdf44c26791d9b2
__MONOTONIC_TIMESTAMP 98099426
__REALTIME_TIMESTAMP 1730454687932647
__SEQNUM 239148
__SEQNUM_ID 0a5097fa456140ab9c67f717ce83d3e8

NAME                      FSTYPE            FSVER    LABEL           UUID                                   FSAVAIL FSUSE% MOUNTPOINTS
sda                                                                                                                        
&#9500;&#9472;sda1                    vfat              FAT32                    5E09-9F2D                                             
&#9500;&#9472;sda2                    ext4              1.0                      f7fcd2dc-b1e5-4ec6-af96-6e92f974cab9                  
&#9492;&#9472;sda3                    LVM2_member       LVM2 001                 cYRFBs-pSGM-xxCm-79F9-zgUM-jekB-oUfnkC                
  &#9492;&#9472;ubuntu--vg-ubuntu--lv ext4              1.0                      f10935df-a1c5-431e-a96d-da7bed713117      8.5G    35% /
sr0                                                                                                                        
nvme2n1                   linux_raid_member 1.2      datastore:raid0 9dfb779e-fc58-8444-6f4b-f607ba4aa089                  
&#9492;&#9472;md127                   ext4              1.0      DataStore       61b4480e-e35f-4e1e-bcba-bf1f19fda05d     41.1T    21% /mnt/DataStore
nvme3n1                   linux_raid_member 1.2      datastore:raid0 9dfb779e-fc58-8444-6f4b-f607ba4aa089                  
&#9492;&#9472;md127                   ext4              1.0      DataStore       61b4480e-e35f-4e1e-bcba-bf1f19fda05d     41.1T    21% /mnt/DataStore
nvme1n1                   linux_raid_member 1.2      datastore:raid0 9dfb779e-fc58-8444-6f4b-f607ba4aa089                  
&#9492;&#9472;md127                   ext4              1.0      DataStore       61b4480e-e35f-4e1e-bcba-bf1f19fda05d     41.1T    21% /mnt/DataStore
nvme0n1                   linux_raid_member 1.2      datastore:raid0 9dfb779e-fc58-8444-6f4b-f607ba4aa089                  
&#9492;&#9472;md127                   ext4              1.0      DataStore       61b4480e-e35f-4e1e-bcba-bf1f19fda05d     41.1T    21% /mnt/DataStore
root@datastore:/# efibootmgr
BootCurrent: 0004
Timeout: 3 seconds
BootOrder: 0004,0002,0000,0003
Boot0000* UiApp FvVol(7cb8bdc9-f8eb-4f34-aaea-3ee4af6516a1)/FvFile(462caa21-7614-4503-836e-8ab6f4662331)
Boot0002* UEFI QEMU QEMU HARDDISK       PciRoot(0x0)/Pci(0x1e,0x0)/Pci(0x4,0x0)/Pci(0x1,0x0)/SCSI(0,0){auto_created_boot_option}
Boot0003* EFI Internal Shell    FvVol(7cb8bdc9-f8eb-4f34-aaea-3ee4af6516a1)/FvFile(7c04a583-9e3e-4f1c-ad65-e05268d0b4d1)
Boot0004* Ubuntu        HD(1,GPT,3f319ca4-622a-485f-8995-bc75cc351979,0x800,0x219800)/File(\EFI\ubuntu\shimx64.efi)
```

---

### Post by yancek on 2024-11-01
The UUID show in your error message does not exist in your lsblk output so it is apparently incorrect.  Is sda2 a separate boot partition?  Did you compare that UUID to what you have in fstab and in the grub.cfg files on both the EFI partition and in /boot/grub?

---

### Post by lmiksche on 2024-11-01
> **yancek said:**
> The UUID show in your error message does not exist in your lsblk output so it is apparently incorrect.  Is sda2 a separate boot partition?  Did you compare that UUID to what you have in fstab and in the grub.cfg files on both the EFI partition and in /boot/grub?

The whole SDA is as created by unbuntu install.

This is GRUB
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

This is FSTAB
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/ubuntu-vg/ubuntu-lv during curtin installation
/dev/disk/by-id/dm-uuid-LVM-DVb6l6f6ndLsCNcLWO0cENIjNadr2h2bcR0PgyBAfccm2rmlgUGSaeH7mAS6gug9 / ext4 defaults,nofail,x-systemd.device-timeout=1ms 0 1
# /boot was on /dev/sda2 during curtin installation
/dev/disk/by-uuid/f7fcd2dc-b1e5-4ec6-af96-6e92f974cab9 /boot ext4 defaults,nofail,x-systemd.device-timeout=1ms 0 1
# /boot/efi was on /dev/sda1 during curtin installation
/dev/disk/by-uuid/5E09-9F2D /boot/efi vfat defaults,nofail,x-systemd.device-timeout=1ms 0 1


#Mount NVMe Stripe
UUID=61b4480e-e35f-4e1e-bcba-bf1f19fda05d /mnt/DataStore auto defaults,x-parent=9dfb779e:fc588444:6f4bf607:ba4aa089 nofail 0 0
#Mount partition on Backup server if available
192.168.0.221:/mnt/DataStore2 /mnt/pmx2 nfs nofail



So I dont see anything that could cause this. The call for the mount or service must be comming from somwhere else. I am even telling it to ignore mouting if not available and setting timeout to 1ms.

---

