---
title: "Splash screen not showing during boot"
date: 2015-02-28
forum: General Help
---

### Post by Anuovis on 2015-02-28
This is not a huge issue but I would like to fix it.

I recently reinstalled my Xubuntu 14.04 and now the splash screen is not showing during the boot. It still shows up during the shutdown phase.
I tried pressing F6, F7... during the boot, and if I do that the splash screen comes up. But the screen stays black otherwise, until the login screen.

The system seems to be booting and working normally otherwise.
I didn't have this problem with the previous installation.

Tried searching for the solution but most of the cases seem to be related ot the prioprietary graphics drivers. I am not using those.

I also tried removing all the *$vt_handoff* in */boot/grub/grub.cfg* file.
It worked for a while but now those and the problem are back again.

I also tried this:
```

sudo dpkg-reconfigure plymouth
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u -k all

```
But it didn't work.

I don't really want to break my grub by trying other possible solutions so I though I would ask for any advice here.
I suspect the solution is really simple but I have no idea how to do it.

---

### Post by oldos2er on 2015-02-28
Please post the output of ```
cat /etc/default/grub
```

---

### Post by Anuovis on 2015-02-28
OK, here it is...

```
cat etc/default/grub
```

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
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

---

### Post by oldos2er on 2015-02-28
Well "splash" is there in the GRUB_CMDLINE_LINUX_DEFAULT line. I don't know enough about plymouth to advise any changes regarding it. I'm sure someone more knowledgeable than me will be along to help you.

Edit: Just for fun, run ```
sudo update-grub
``` to make sure everything's up to date, if you haven't already. Also it's not advised to directly edit /boot/grub/grub.cfg because /etc/default/grub and files in /etc/grub.d/ are used to configure it.

---

### Post by Anuovis on 2015-03-01
Thank you for your help.

When I ran sudo update-grub, I got this:

> Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.16.0-31-generic
Found initrd image: /boot/initrd.img-3.16.0-31-generic
Found linux image: /boot/vmlinuz-3.16.0-30-generic
Found initrd image: /boot/initrd.img-3.16.0-30-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done

So I tried setting the GRUB_TIMEOUT to 0 in the /etc/default/grub.
The warning message from above disappeared but the splash problem persisted.

I reverted it back to GRUB_TIMEOUT=10.

---

### Post by slickymaster on 2015-03-11
Have you, by any chance, have the 'None' option selected in Settings -> Session and Startup -> Splash

[IMG]http://i.imgur.com/yelfOD8.png[/IMG]

---

### Post by slickymaster on 2015-03-11
Never mind my previous post as the splash you're talking about has nothing to do with that.

---

