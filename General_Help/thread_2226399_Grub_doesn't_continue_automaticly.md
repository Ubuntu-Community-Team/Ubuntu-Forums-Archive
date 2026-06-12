---
title: "Grub doesn't continue automaticly"
date: 2014-05-27
forum: General Help
---

### Post by tovare13 on 2014-05-27
Hi:) 

I've got ubuntu 14.04 installed on a server, and usually it starts automaticly, but now it won't.
It just stands there in Grub and I have to physically press the enter button on a keyboard, so that it will continue.

I am pretty new at the whole linux thing, so i have no idea what kind of info you guys need, but here is the /etc/default/grub file

```

# If you change this file, run 'update-grub' afterwards to update# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash"
GRUB_CMDLINE_LINUX=""
GRUB_RECORDFAIL_TIMEOUT=0


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

---

### Post by philinux on 2014-05-27
Here's the top part of mine. Not sure how the recordfail bit got in yours but it's not in mine. 

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

---

### Post by tovare13 on 2014-05-27
I just tried that, and it's still the same problem :/

---

### Post by philinux on 2014-05-27
I assume you ran sudo update-grub

---

### Post by tovare13 on 2014-05-28
of course :)

---

### Post by nerdtron on 2014-05-28
Are you sure that it does GRUB does not automatically boot the system?
1. Poweroff the machine.
2. Remove keyboard and monitor.
3. After a few seconds, hit the power button.
4. Wait for it to boot.
5. Attach keyboard and monitor and see if it booted successfully.

Sometimes grub will stop the countdown for loading when you have keyboard connected of if you press during the last reboot process. It may seem a little flaky but in my experience that is what happens.

---

### Post by tovare13 on 2014-05-28
tried that, and i got no image on screen when i hooked it up again, but once i pressed enter it continued to boot into linux.

---

