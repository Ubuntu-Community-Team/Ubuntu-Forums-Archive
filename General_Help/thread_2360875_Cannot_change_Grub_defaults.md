---
title: "Cannot change Grub defaults"
date: 2017-05-09
forum: General Help
---

### Post by Paddy Landau on 2017-05-09
I cannot change the Grub defaults. The computer had Ubuntu, and I couldn't change the defaults. I have completely reinstalled, this time with Lubuntu, and still the Grub defaults won't change.

Specifically, Grub always selects Windows by default and ignores the timeout.

**More information**


[LIST]
[*]Dual-boot Windows 10 with Lubuntu 16.04 64-bit (was Ubuntu 16.04 64-bit)
[*]System has UEFI (and therefore an EFI partition)
[/LIST]

**What I've tried**


[LIST]
[*]Using Grub Customizer
[*]Manually changing [FONT=lucida console]/etc/default/grub[/FONT] and running [FONT=lucida console]sudo update-grub[/FONT]
[*]Manually running [FONT=lucida console]grub-install[/FONT], [FONT=lucida console]grub-mkconfig[/FONT] and [FONT=lucida console]update-initramfs[/FONT]. Unfortunately, these have made it worse: Grub now complains, "error: file /EFI/ubuntu/grubenv does not found", but starts up anyway.
[/LIST]

The current contents of [FONT=lucida console]/etc/default/grub[/FONT] are shown below.

Maybe the best thing to do would be to reinstall Grub from scratch, but I don't know how to do that.

If you can please help me to figure out this conundrum, I would be most appreciative!

```
# If you change this file, run 'update-grub' afterwards to update# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT="saved"
GRUB_SAVEDEFAULT="true"
##GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="false"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
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
#GRUB_GFXMODE="640x480"


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by oldfred on 2017-05-09
Typically not a grub issue, but an UEFI issue.

What brand/model system?

Many brands violate UEFI standard that says NOT to use description as part of UEFI boot.
And only valid description is "Windows Boot Manager". 
But many work arounds depending on configuration.

And Windows updates will reset Windows to first in boot order with just about all systems, just as a grub update/reinstall will update to have Ubuntu first (if system works with Ubuntu).

The easiest way to reinstall grub from scratch is to use Boot-Repair and its advanced options to totally uninstall/reinstall grub. That will also reset all changes to original defaults.

Grub-Customizer makes it easy to make minor changes, but adds its own versions of grub scripts that may cause issues. 
 Customizer has backups of original files
[http://ubuntuforums.org/showthread.php?t=2279347&page=3](http://ubuntuforums.org/showthread.php?t=2279347&page=3) 

      
 May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Paddy Landau on 2017-05-09
Thank you for your reply, oldfred.

> **oldfred said:**
> What brand/model system?
It's an old one, an Asus X501U.

> **oldfred said:**
> … use Boot-Repair and its advanced options to totally uninstall/reinstall grub.
I installed Boot Repair (from the PPA), and it complained that I had to disable secure boot.
So, I instead booted from a Live CD, installed Boot Repair, and ran it from there.
After a lot of processing, it complained about some unspecific error — but, it worked!

> **oldfred said:**
> Many brands violate UEFI…
Bearing that in mind, I'll leave well enough alone. I'll just live with having to choose Ubuntu each time I boot.

Thank you for your help! I'll consider this closed, as it is clearly not a good idea to try to "fix" it further than Boot Repair already did.

---

