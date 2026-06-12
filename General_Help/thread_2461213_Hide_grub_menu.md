---
title: "Hide grub menu"
date: 2021-04-26
forum: General Help
---

### Post by tobipeter on 2021-04-26
Hey there,

I installed Ubuntu in EFI mode on 3 systems, on one of them, Grub is hidden by default and it's working as intended. 
On the other 2 on the other hand, grub is shown on every boot for 30secs, it doesn't matter which settings I choose in the edit file (I use Linux for about 5 years now, so I got a bit experience at least :P) 
I edited it on one system to match the settings on the other system where it works, but no changes. 
Yes, I did run update-grub. 
I also deactivated the OS prober without a change. 

The only difference between the systems is that on the not as intended working systems I have installed grub-btrfs to show my btrfs snapshots. 
Could this entry prevent the hiding of grub? 
Is there any way I can hide it anyway? 
Is there anything else I could try? 
Thanks in advance!

---

### Post by kneutron on 2021-04-26
Post contents of /etc/default/grub on the affected system

---

### Post by tobipeter on 2021-04-26
> **kneutron said:**
> Post contents of /etc/default/grub on the affected system

Here you go:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="drm_kms_helper.edid_firmware=edid/edid.bin"

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

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Lin>
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_ENABLE_CRYPTODISK=y
```

---

### Post by tobipeter on 2021-04-26
> **kneutron said:**
> Post contents of /etc/default/grub on the affected system

Is there anything wrong with my configuration?

---

### Post by grahammechanical on 2021-04-26
This is what the Grub 2 manual says

> &#8216;GRUB_TIMEOUT&#8217;
Boot the default entry this many seconds after the menu is displayed, unless a key is pressed. The default is &#8216;5&#8217;. Set to &#8216;0&#8217; to boot immediately without displaying the menu, or to &#8216;-1&#8217; to wait indefinitely.

And then there is this

> &#8216;GRUB_HIDDEN_TIMEOUT&#8217;
Wait this many seconds for a key to be pressed before displaying the menu. If no key is pressed during that time, display the menu for the number of seconds specified in GRUB TIMEOUT before booting the default entry. We expect that most people who use GRUB HIDDEN TIMEOUT will want to have GRUB TIMEOUT set to &#8216;0&#8217; so that the menu is not displayed at all unless a key is pressed. Unset by default.

You have 

> GRUB_TIMEOUT_STYLE=hidden

My copy of the Grub 2 manual is a few years old. It may be that there has been a change and there now is a GRUB_TIMEOUT_STYLE. Or, it may be not.

This is the link for Grub manual 2.4

[https://www.gnu.org/software/grub/manual/grub/html_node/Simple-configuration.html](https://www.gnu.org/software/grub/manual/grub/html_node/Simple-configuration.html)

Note this comment

> GRUB_HIDDEN_TIMEOUT_BUTTON&#8217;
Variant of &#8216;GRUB_HIDDEN_TIMEOUT&#8217;, used to support vendor-specific power buttons.  See [Vendor power-on keys]("https://www.gnu.org/software/grub/manual/grub/html_node/Vendor-power_002don-keys.html#Vendor-power_002don-keys"). 

 This option is unset by default, and is deprecated in favour of the less confusing &#8216;GRUB_TIMEOUT_STYLE=countdown&#8217; or &#8216;GRUB_TIMEOUT_STYLE=hidden&#8217;.


Here is the link to section 10. Using Grub with vendor power-on keys. Which you may have.

[https://www.gnu.org/software/grub/manual/grub/html_node/Vendor-power_002don-keys.html#Vendor-power_002don-keys](https://www.gnu.org/software/grub/manual/grub/html_node/Vendor-power_002don-keys.html#Vendor-power_002don-keys)

Regards





Regards

---

