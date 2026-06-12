---
title: "Kernel Parameters not taking effect when updating Grub"
date: 2014-05-19
forum: General Help
---

### Post by Gridwalker on 2014-05-19
Hi there,

I recently posted a thread in the hardware section to solve a problem with a SCSI RAID box that was running out of IOMMU space. We determined that adding the kernel parameter *iommu=allowdac,merge,memaper=3* was the correct fix, which I validated by editing boot options and adding the parameter through the Grub menu.

I am now trying to make the changes permanent, but I am not having much luck. I am starting by editing /etc/default/grub, then adding my parameter to the line GRUB_CMDLINE_LINUX_DEFAULT

I then save and run update-grub, which says that the new configuration has been generated successfully. When I reboot, the parameter hasn't taken effect and my IOMMU space is back to its default level.

I have also tried using grub customiser, making a few visual changes to the menu to more easily validate whether a new configuration is being used, but this hasn't been successful either.

Additionally, I am using a Nvidia graphics driver and have a broken Plymouth splash screen. I have been trying to fix that since I first installed 14.04 but none of the fixes have worked; I now suspect that has something to do with the same bug. I can live without splash screens, but I really want to get the RAID box working properly. Can anyone suggest a fix for this?

Here is my full /etc/default/grub file :
[INDENT]# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="5"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash iommu=allowdac,merge,memaper=3"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE="1024x768"
GRUB_GFXPAYLOAD_LINUX="1024x768-24"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

#GRUB_DISABLE_OS_PROBER="false"
[/INDENT]

---

### Post by matt_symes on 2014-05-19
Hi

I can help you with this but it will have to wait until wednesday as i`m currently on my phone and don`t have my laptop with me to check the exact syntax so hang tight until then - unless someone else answers.

Kind regards

---

### Post by Gridwalker on 2014-05-19
No need to worry, a friend has helped me find the issue. For some reason, my boot partition was listed in FSTAB and was mounting under its UUID. I have no idea how that happened, but it was obviously going to be messing up my grub updates. Now that has been fixed, everything is running smoothly. Thanks again for all of your help in the previous thread though :)

---

