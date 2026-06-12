---
title: "Ubuntu 15.04 won't shut down"
date: 2015-08-18
forum: General Help
---

### Post by al.adab on 2015-08-18
I never had this issue with Ubuntu 14.04.02 running on a Asus UX301. 

it first happened after upgrading to 14.04.03. After tampering with */etc/default/grub/* (and adding *acpi=force* among other lines I tried out) eventually I was no longer able to log in, let alone access Unity. 

A fresh install (15.04) and the problem hasn't gone away: I click on *shut down*, the Ubuntu shut-down screen doesn't disappear (it looks like it's stuck), and the pc remains powered-on. No Ctrl + Alt + F1 (or other tricks) work, except for holding the power bottom (which is hardly a trick or solution). 

here's what my */etc/default/grub/* looks like 

[I]# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi= "
GRUB_CMDLINE_LINUX="noprompt persistent"

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
[/I]

please notice that the *acpi_osi= "* line was added to enable *Fn + F5/F6* (screen brightness control) on the Asus. Before the previous version of Ubuntu crashed any line (see above) I added to *GRUB_CMDLINE_LINUX_DEFAULT* disabled the *Fn + F5/F6* function. 

can anyone please advise? thanks.

---

### Post by al.adab on 2015-08-18
forgotten to add that *sudo shutdown now* works most of the time (not always, maybe 8 out of 10) and *shut down* from taskbar works (say) 2 times out of 10.

---

### Post by al.adab on 2015-08-22
er....bump? :)

---

### Post by matt_symes on 2015-08-22
Hi

If you remove the acpi_osi= parameter from the grub command line and update grub, does it shutdown then ? 

Just wondering if that is interfering after the kernel upgrade from 14.2, through 14.3 to 15.4.

Kind regards

---

### Post by al.adab on 2015-08-26
Thanx matt_symes for the suggestion. 
I tried and tried again, and it doesn't seem to make any difference...
Now "downgrading" to 14.04.03 again. Will report on any development shortly.
Thanks again!

---

### Post by al.adab on 2015-08-27
so here's a quick update: 

i'm now back to 14.04.03 and have tested it last night and today. 

half of the time it doesn't shut down and i have to resort to force-shut (power-button). 

i tried with and without the acpi_osi= parameter: it makes no difference. Matter of fact, on 14.04.02 I had that very parameter from the very beginning and it never caused troubles. 

can someone please help - this is getting really frustrating...thank you

---

### Post by al.adab on 2015-08-28
a wild-card scenario: while shutting down, ubuntu disconnect active wifi connections...

could the reason for the hang-up be that ubuntu can't disconnect? that it sends a signal like "disconnect now!" and there's no reply? 

what would be the best way to test this hypothesis?

---

### Post by al.adab on 2015-09-03
bump? has anyone come across this problem?

---

### Post by george126 on 2015-09-10
im running 15.04, hasnt shut down since first installed a week ago, havn`t messed with system files yet, just tried that sudo shutdown, same thing. im new with ubuntu, shure apreciate tips

---

