---
title: "Why do I have an /etc/default/grub.ucf-dist file?"
date: 2015-05-22
forum: General Help
---

### Post by CantankRus on 2015-05-22
Using Ubuntu 14.04 and I have simple script that uses grub-reboot (set the default boot entry for GRUB, for the next boot only) to reboot me into my Windows install.
```
#!/bin/bash

## grub-reboot sets the default boot entry for GRUB, for the next boot only
## To enable grub-reboot to be edited by any user run
## sudo chmod +s /usr/bin/grub-editenv

## To find the grub menu entry you want run
## grep menuentry /boot/grub/grub.cfg | grep "^menuentry" | sed -e 's/.*Memory test.*//g' -e "s/menuentry '//g" -e 's/ --class.*//g' -e "s/'//g" -e '/^$/d'

# This will grab a windows grub menu item
grubentry=$(grep menuentry /boot/grub/grub.cfg | grep "^menuentry" | sed -e 's/.*Memory test.*//g' -e "s/menuentry '//g" -e 's/ --class.*//g' -e "s/'//g" -e '/^$/d' | grep -i windows)

grub-reboot "$grubentry"  # preface with gksudo if you didn't run the chmod command  
gnome-session-quit --reboot
```

Recently the script stopped working after updates to grub-common grub2-common grub-pc-bin grub-pc
Poking around I noticed I have an **/etc/default/grub.ucf-dist** file which I have never seen before.
The file just looks like a default grub file...
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
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
```

Why do I have this file and is boot using this instead of **/etc/default/grub**?

---

### Post by efflandt on 2015-05-22
Booting does not use /etc/default/grub, running **sudo update-grub** (by you or system updates) uses that file to generate /boot/grub/grub.cfg which is used during boot.

I have never used grub-reboot, so not familiar with syntax for selecting a specific menu item for that or as a default. I simply used the following in /etc/default/grub to default to whatever grub successfully booted last:```
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
```That way in the rare case that I boot Win7 and it needs to reboot for updates it will reboot itself. However, in rare cases some Windows updates do not work unless they boot from a regular DOS/Win mbr, for example one that I had trouble with is KB3033929 that needs a regular DOS/Win (or syslinux) mbr to succeed (besides Win7 Service Pack 1 long ago).

---

### Post by CantankRus on 2015-05-22
Hi efflandt,
Been doing some reading.
> GRUB_DEFAULT='Example GNU/Linux distribution'
If you set this to &#8216;saved&#8217;, then the default menu entry will be that saved by &#8216;GRUB_SAVEDEFAULT&#8217;, grub-set-default, or **grub-reboot**.

The default is &#8216;0&#8217;.

&#8216;GRUB_SAVEDEFAULT&#8217;
If this option is set to &#8216;true&#8217;, then, when an entry is selected, save it as a new default entry for use by future runs of GRUB. 
This is only useful if &#8216;GRUB_DEFAULT=saved&#8217;; it is a separate option because &#8216;GRUB_DEFAULT=saved&#8217; is useful without this option, 
in conjunction with grub-set-default or grub-reboot. Unset by default.

I found an installed package "ucf"...
> Debian policy mandates that user changes to configuration files must be
preserved during package upgrades. The easy way to achieve this behavior
is to make the configuration file a 'conffile', in which case dpkg
handles the file specially during upgrades, prompting the user as
needed.
so I gather this new /etc/default/grub.ucf-dist file was created during a grub upgrade.
This file has...
```
GRUB_DEFAULT=0
```

while my /etc/default/grub file had been edited by me to...
```
GRUB_DEFAULT=saved
```

[S]Strange thing is, I renamed /etc/default/grub.ucf-dist to /etc/default/grub.ucf-dist.bak
and I am now using the **GRUB_DEFAULT=saved** from my /etc/default/grub file 
without even running sudo update-grub[/S] 

It appears the grub upgrade reset permissions on **/usr/bin/grub-editenv** which I had changed
so any user could run grub-reboot.
I am still using /etc/default/grub

Long story short ....still don't know the purpose of the **/etc/default/grub.ucf-dist** file
but my issue is fixed and the script is working again.
grub-reboot allows me to go make a coffee while computer boots into Windows ;)

---

