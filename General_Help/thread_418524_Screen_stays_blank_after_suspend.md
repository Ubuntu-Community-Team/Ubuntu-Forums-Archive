---
title: "Screen stays blank after suspend"
date: 2007-04-22
forum: General Help
---

### Post by cknoblock on 2007-04-22
Using feisty release, after I resume from a suspend the screen stays blank.  If I hit ctrl+alt+f1 there are some text messages:

scsi 0:0:0:0 rejecting I/O to dead device
and
metapage_write_end_io; I/O error

Not sure if those matter. If I hit alt+f7, the screen stays blank but the mouse pointer appears ??

I am running an IBM T40.

-ck

---

### Post by WilliamAnderson on 2007-04-23
Hi all,

I was having the same trouble. I have a Thinkpad R50p and am running feisty (beta 4-15 desktop cd fully upgraded ). Everything works great except this failure to resume from suspend (s3 to ram) and the loss of audio after resuming from hibernate (to disk).

My attempts to fix include:

1. adding the kernal boot parameter “acpi_sleep=s3_bios” (in /boot/grub/menu.lst)
2. uncommenting the “DOUBLE_CONSOLE_SWITCH=true” (in /etc/default/acpi-support)
3. uncommenting the “RESET_DRIVE=true” (in /etc/default/acpi-support)

I rebooted (shutdown and power cycle) before trying the suspend.

Number 2  switches to a terminal from X before suspending and is supposed to switch back after resuming. Mine fails to do this and sits with the hard drive activity led lit solid and displaying the I/O error when trying to access the root partition.

Numbers 1 and 3 made no difference.

...

I found the cause of this problem on the ThinkWiki web site. See [http://www.thinkwiki.org/wiki/Problems_with_ACPI_suspend-to-ram](http://www.thinkwiki.org/wiki/Problems_with_ACPI_suspend-to-ram) at the bottom in the section “SectorIdNotFound disk errors when laptop is resumed” and “Hidden Protected Area” link. When I disabled the HPA (or IBM Predesktop Area) in the BIOS, then rebooted, suspend to RAM now works. 

Now I need to decide if the ability to restore the factory installed Windows XP (useless) or access the IBM diagnostics (really nice) are more important then suspend to RAM.

Hope this helps,

William

---

