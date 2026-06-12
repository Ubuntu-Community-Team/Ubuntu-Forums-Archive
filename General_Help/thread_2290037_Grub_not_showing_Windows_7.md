---
title: "Grub not showing Windows 7"
date: 2015-08-08
forum: General Help
---

### Post by dustysvs on 2015-08-08
Hey there, my Windows 7 is not showing in the Grub menu

Ubuntu 14.04 LTS
> [SIZE=3][B]
[http://paste.ubuntu.com/12034270/](http://paste.ubuntu.com/12034270/)[/B][/SIZE]

> [SIZE=3] **/boot/grub/grub.cfg**[/SIZE]
if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
  menuentry_id_option=""
export menuentry_id_option
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-06d8041d-ba94-4496-9c9d-279c6d7fd4ce' {
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-06d8041d-ba94-4496-9c9d-279c6d7fd4ce' {
    menuentry 'Ubuntu, with Linux 3.16.0-45-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-45-generic-advanced-06d8041d-ba94-4496-9c9d-279c6d7fd4ce' {
    menuentry 'Ubuntu, with Linux 3.16.0-45-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-45-generic-recovery-06d8041d-ba94-4496-9c9d-279c6d7fd4ce' {
    menuentry 'Ubuntu, with Linux 3.16.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-30-generic-advanced-06d8041d-ba94-4496-9c9d-279c6d7fd4ce' {
    menuentry 'Ubuntu, with Linux 3.16.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-30-generic-recovery-06d8041d-ba94-4496-9c9d-279c6d7fd4ce' {
    menuentry 'Ubuntu, with Linux 3.13.0-61-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-61-generic-advanced-06d8041d-ba94-4496-9c9d-279c6d7fd4ce' {
    menuentry 'Ubuntu, with Linux 3.13.0-61-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-61-generic-recovery-06d8041d-ba94-4496-9c9d-279c6d7fd4ce' {
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {


> [SIZE=3]**update-grub**[/SIZE]
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-45-generic
Found initrd image: /boot/initrd.img-3.16.0-45-generic
Found linux image: /boot/vmlinuz-3.16.0-30-generic
Found initrd image: /boot/initrd.img-3.16.0-30-generic
Found linux image: /boot/vmlinuz-3.13.0-61-generic
Found initrd image: /boot/initrd.img-3.13.0-61-generic
Adding boot menu entry for EFI firmware configuration
done


> [SIZE=3]**cat /etc/default/grub**[/SIZE]
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
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
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



> [SIZE=3]**fdisk -l**[/SIZE]

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcf894941

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  2111074303  1055536128    7  HPFS/NTFS/exFAT
/dev/sda2      2111074304  2920507896   404716796+  83  Linux
/dev/sda3   *  2920507897  2926367271     2929687+   b  W95 FAT32
/dev/sda4      2926367272  2930272064     1952396+  83  Linux



Thanks.

---

### Post by oldfred on 2015-08-09
Your Windows is installed in BIOS boot mode on MBR(msdos) partitioned drive.
Windows only boots in BIOS mode from MBR.
Windows only boots in UEFI from gpt.
UEFI & BIOS are not compatible and once you start booting in one mode cannot change to other mode, or from grub menu you can only boot installs in same boot mode.

You booted Boot-Repair in UEFI mode. Best to only boot in BIOS mode since install is BIOS.
It does look like originally you installed Ubuntu in UEFI mode as you have a comment out entry in fstab for mounting /efi/boot. And Boot-Repair recognized install should be BIOS/MBR so reinstalled the BIOS boot version of grub to MBR, not the UEFI boot to ESP- efi partition.

I would move boot flag back to Windows NTFS partition. With BIOS/MBR boot flag must be on Windows partition for Windows boot loader to boot Windows, for Windows repair or installers to work on NTFS partition.
Grub does not use boot flag with BIOS/MBR and will keep booting Windows whether it has boot flag or not.
In UEFI boot flag must be on efi partition and no other, but normally drive is partitioned as gpt not MBR.

Since grub reinstalled in BIOS mode, run this:
sudo update-grub

Grub really only boots working Windows, so if not found Windows may be hibernated or needs chkdsk. You can only fix those issues from Windows and need to use Windows repairCD or flash drive. You may be able to install a Windows boot loader with Boot-Repair or Windows repair disk to directly boot Windows & make repairs(boot flag must be on NTFS partition first). Then restore grub to MBR to dual boot.

---

