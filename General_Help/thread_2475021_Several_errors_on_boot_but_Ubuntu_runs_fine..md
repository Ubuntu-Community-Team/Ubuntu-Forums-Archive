---
title: "Several errors on boot but Ubuntu runs fine."
date: 2022-05-14
forum: General Help
---

### Post by beastfromair on 2022-05-14
I am running solely Ubuntu 22.04 LTS on an Asus Zenbook 14. Upon launch, I am greeted by the following error messages:

* x86/cpu: SGX disabled by BIOS.
* ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220) X74
* nvme nvme0: failed to set APST feature (2)
* Bluetooth: hci0: sending frame failed (-19)
* GLib-GObject: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
* Unsupported conditions are present
* Sink echoCancel_sink does not exist.
* GLib-GIO-CRITICAL: g_bus_get_sync: assertion 'error == NULL || *error == NULL' failed
* Failed to start Service for snap application snapd-desktop-integration.snapd-desktop-integration.
* gkr-pam: unable to locate daemon control file
* Failed to start Application launched by gnome-session-binary.
* GLib-GObject: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
* GLib-CRITICAL: g_hash_table_foreach_remove_or_steal: assertion 'version == hash_table->version' failed

Could somebody help me determine if are safe to ignore? If not, how can I fix this? The BIOS menu doesn't seem to have an option to enable SGX

---

### Post by exploder on 2022-05-15
I get some of those on boot too. I can't ever read it all though, the system boots too fast. Have seen this in the past also. These messages are generally harmless and can be ignored. There is a way of editing a system file that will stop these from displaying but I have not found the instructions again yet... 

A couple years ago I bought a new laptop, it got a slew of these messages but ran perfectly fine. I found instructions that stopped them from displaying. It also stopped Plymouth from displaying but new systems boot so fast that I really did not care about that, just wanted the errors gone. 

If I find the solution again, I would be happy to share it with you. If your system is running fine, just ignore the errors for the time being.

---

### Post by exploder on 2022-05-15
Just tried this and all the messages are now gone except for one line that tells me the volume is clesn.

[https://ubuntu-mate.community/t/how-to-suppress-kernel-boot-error-messages/10617/6](https://ubuntu-mate.community/t/how-to-suppress-kernel-boot-error-messages/10617/6)

You have to run sudo update-grub after you edit the file.

---

### Post by grahammechanical on 2022-05-15
> The BIOS menu doesn't seem to have an option to enable SGX

Where are you looking? I am new to having an UEFI motherboard. So, I am still learning this kind of setup utility. On my system I went to Advanced>Advanced Chipset Control>Software Guard Extensions (SGX). On my system SGX is enabled but then I did buy from a supplier that sold laptops with Ubuntu pre-installed.

As regards the messages that Linux produces during boot, I find that Ubuntu has a very good error detection system. After the desktop loads I sometimes get a "some thiing went wrong" dialog with an option to examine the details and/or send a report to the developers. I am not curious about Linux messages and if the system is working fine I even ignore the Ubuntu "Some thing went wrong" messages if what wrong wrong did not seem too serious.

Regards

---

### Post by exploder on 2022-05-15
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet loglevel=0 splash"
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

Line 10 is what I edited. GRUB_CMDLINE_LINUX_DEFAULT="quiet loglevel=0 splash", then ran sudo update-grub.

---

### Post by tea for one on 2022-05-15
> **beastfromair said:**
> x86/cpu: SGX disabled by BIOS.
Could somebody help me determine if are safe to ignore? If not, how can I fix this? The BIOS menu doesn't seem to have an option to enable SGX

Software Guard Extensions - a set of security-related instruction codes that are built into some Intel central processing units.

I have the option to enable and disable this in my UEFI settings.
It has been disabled for more than 3 years without presenting any problem.
I always ignore it.

Enterprise/business users may find it beneficial.

---

