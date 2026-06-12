---
title: "Cpu fan speed constantly on max"
date: 2013-01-22
forum: General Help
---

### Post by stefankorun on 2013-01-22
Hello guys. I am trying to set up some starter server just to see how things are going. I have installed xampp(lampp) on my machine running fresh Lubuntu (latest), but my fan is constantly running at full speed. 

Here is the system report from HardInfo: [http://dl.dropbox.com/u/13758661/hardinfo_report.html](http://dl.dropbox.com/u/13758661/hardinfo_report.html). 
My motherboard is Matsonic MS9107C+, and my graphic card is pretty old too - GeForce2 MX200 having 32mb RAM

I have tried to install lm-sensors using this guide (and many more that I found): [http://ubuntuforums.org/showthread.php?t=2780&highlight=fan+running+max+speed](http://ubuntuforums.org/showthread.php?t=2780&highlight=fan+running+max+speed)
and the only thing I get is 
```

stefan@ubuntu-SERVERK:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +32.0°C  (crit = +70.0°C)

```Also I tried to edit /boot/grub/grub.cfg and experimented with some parameters
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
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force"
#GRUB_CMDLINE_LINUX_DEFAULT="acpi_enforce_resources=lax"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtainsGRUB_CMDLINE_LINUX="acpi_enforce_resources=lax"
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

```If I should post additional info please let me know.
Thanks.

---

### Post by tgalati4 on 2013-01-22
Usually, the fan speed is controlled in BIOS.  Did you check all of the settings in BIOS?  Sometimes there are options for setting fan speeds and thermal limits.  See if you can flash a newer BIOS on your machine.

Have you tried thinkfan and fancontrol?

---

### Post by stefankorun on 2013-01-22
> **tgalati4 said:**
> Usually, the fan speed is controlled in BIOS.  Did you check all of the settings in BIOS?  Sometimes there are options for setting fan speeds and thermal limits.  See if you can flash a newer BIOS on your machine.

Have you tried thinkfan and fancontrol?

Thanks for the reply, I checked everywhere in BIOS and there is only stats about the rpm of the fan (>4000 rpm) but I will double check. Also because of the age of the motherboard it was hard to find a reliable source for bios download as I don't want to screw the motherboard.
It is the first time I hear about those programs I will check them out now and see what happens/

---

