---
title: "GRUB2 dropdown to CLI for &quot;Check Rootdelay&quot;"
date: 2013-05-25
forum: General Help
---

### Post by Arny006 on 2013-05-25
Hello Mates,

thanks your support and suggestions was I finally able to install Kubuntu 12.10 on an Intel-BIOS-RAID 0+1.

Naturally made also modifications of /etc/fstab & /etc/default/grub to force GRUB2 load BIOS-RAID-drivers as follow:
/etc/fstab= convert UUIDs in /dev/mapper/.... & comment UUIDs
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# ext4 was on /dev/mapper/isw_bejjdcfdi_Arny006p3 equal  UUID=8076ced3-3f20-4785-9e97-6d42008477af during installation
/dev/mapper/isw_bejjdcfdi_Arny006p3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/mapper/isw_bejjdcfdi_Arny006p2 equal UUID=9400cb40-d206-4d3a-b5ac-0f936d3c3c02 during installation
/dev/mapper/isw_bejjdcfdi_Arny006p2 none            swap    sw              0       0
# Am Ende der fstab muss immer noch eine Leerzeile kommen, sonst erhält man die Fehlermeldung: no final newline at the end of /etc/fstab


```
/etc/default/grub= add rootdelay, disable UUID
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="rootdelay=90 quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
GRUB_INIT_TUNE="480 440 1"


```

**The problem** now, is the randomly dropdown to CLI cause of "Check Rootdelay" even if GRUB2 (when start) use much less time (5-10 seconds ca.)
I try also setting different "rootdelay" times 30-60-90-120-130 and finally remain by 90 because the "rootdelay" is not the only parameter granting the start.

**Observations:**
1) When the start don't succeed I cannot hear the four disks in RAID 0+1 working. I don't know for what Grub is waiting there. One is sure, don't load drivers.
2) When the start fails I restart with "Cntrl+Alt+Del" go in Grub with "E", go to the rootdelay-line (still 90 sec.) than press "F10", the start succeed in few seconds.
3) A "cold start" succeed almost every-time (if the PC is shutdown), by a "restart" hang almost everytime and dropdown to CLI/error.
4) To increase the chances to start successfully, I'm forced to make an additional "update-grub" by kernel-update and shutdown the PC instead of restart.

**How to force GRUB2 to look everytimes to RAID-drivers?**

Thanks in advance for your reply.

---

### Post by Arny006 on 2013-06-21
also a modification of /usr/share/initramfs-tools/scripts/local-top/dmraid with
> 
if devices=$(dmraid -r -c); then
    sleep 10
    dmraid -ay
fi
 don't give the expected results.

Any idea?

---

