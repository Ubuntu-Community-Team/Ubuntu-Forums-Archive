---
title: "Xdiagnise made startup scripts show on screen, Xdiagnise gone, need to remove scripts"
date: 2019-06-04
forum: General Help
---

### Post by RogerDavis on 2019-06-04
Xdiagnise made startup scripts show on screen during boot.  Xdiagnose is now gone after I removed it for the upgrade to 18.04, but the scrolling commands are still there.  I need to remove scripts or whatever is causing this, so I don't get all the scrolling commands during start-up.

Where can I find info on this, or terminal commands to stop it, or ???

---

### Post by again? on 2019-06-04
Check /etc/default/grub has the line...
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

After editing, run...
```
sudo upate-grub
```

For reference you can view the default version of grub for your system...
```
cat /usr/share/grub/default/grub
```

---

### Post by RogerDavis on 2019-06-06
Is what I want to do - change the line 
GRUB_CMDLINE_LINUX_DEFAULT="plymouth:debug drm.debug=0xe plymouth:debug=1=1=1=1=1=1=1=1=1=1=1=1=1=1=1=1=1=1 plymouth:debug=1=1=1=1=1=1 plymouth:debug=1=1=1=1=1=1=1=1=1=1 " to make it GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
or should it be
GRUB_CMDLINE_LINUX_DEFAULT="plymouth:debug drm.debug=0xe nopat vesafb.invalid=1"
as it is in grub.bak.1 [read-only]    ???
================================================
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="plymouth:debug drm.debug=0xe plymouth:debug=1=1=1=1=1=1=1=1=1=1=1=1=1=1=1=1=1=1 plymouth:debug=1=1=1=1=1=1 plymouth:debug=1=1=1=1=1=1=1=1=1=1 plymouth:debug=1=1=1=1=1=1=1=1=1=1=1=1=1=1 plymouth:debug=1=1"
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

### Post by again? on 2019-06-06
Make a backup of /etc/default/grub first just in case.
Also take a look in /etc/default/ for existing backups labelled .bak that are auto made.
Drag and drop grub.bak files into gedit to view.
[ATTACH=CONFIG]283396[/ATTACH]

Testing here and this is what xdiagnose changes when all options are enabled. 
from...
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to...
```
GRUB_CMDLINE_LINUX_DEFAULT="nopat vesafb.invalid=1 drm.debug=0xe plymouth:debug"
```

After editing grub run... 
```
sudo update-grub
```

Another option would be to reinstall xdiagnose
and unmark all it's options and "Apply" then check grub.

[COLOR="#FF0000"]Edit:[/COLOR] I missed that you already found the .bak files due to you not using code tags.
Not sure how the baks work but you may have lost the original syntax after multiple backups being made.

---

### Post by RogerDavis on 2019-06-07
Something I forgot to mention, but may just be part of the same process - upon shutdown, there is also display of "checklist" kind of lines, very similar to those during startup.  Does this change anything?

FYI - Before Xdiagnose was removed, I did try unchecking all the boxes, but there was no difference in the lines.

Is there a place or file or log where these lines from start-up and shutdown are captured, or I can set to capture them, to absolutely identify them?

---

### Post by again? on 2019-06-08
System log files are in /var/log
You can view start up messages in terminal...
```
dmesg
sudo cat /var/log/boot.log

```
Note at the beginning dmesg shows grub command.
[ATTACH=CONFIG]283398[/ATTACH]

or use the space bar to scroll but loose colouring with
```
dmesg | less
```

systemd uses journalctl which enables you to select a previous boot.
Last boot...
```
journalctl -b
```

List boots and then choose boot to view...
```
journalctl --list-boots
journalctl -b 12
```

More info...
```
man journalctl
```

I use Xubuntu which doesn't use gdm3.

I installed Ubuntu 18.04 into a partition to test.
xdiagnose changes grub in these ways with the 6 selectable options.
[INDENT]1. drm.debug=0xe plymouth:debug
2. plymouth:debug
3. n/a
4. GRUB_GFXPAYLOAD_LINUX=text  **#adds a line**
5. vesafb.invalid=1
6. nopat[/INDENT]

When xdiagnose options are unticked it leaves these changed lines in grub.
```
GRUB_CMDLINE_LINUX_DEFAULT="plymouth:debug quiet splash"
GRUB_GFXPAYLOAD_LINUX=None
```

The simplest solution is to backup grub and replace with the system default.
```
sudo cp /etc/default/grub /etc/default/grub.my.bak
sudo cp /usr/share/grub/default/grub /etc/default/grub
sudo update-grub
```
Replacing grub, I don't see text at boot.

The plymouth splash has always been problematic and can also depend on the gfx drivers used.
eg when using nvidia drivers I will see some text.
The plymouth logo is supposed to cover the text and you should be able to toggle text/graphics with the escape key.

So from my tests xdiagnose doesn't cause the text to show if you revert grub.
As your install is an upgrade you may want to check some things.
Check gfx driver being used and display manager...
```
lspci -k | grep -A3 VGA
cat /etc/X11/default-display-manager
```

Might consider a fresh install of 18.04 as it's LTS and will also rule out possible upgrade conflicts.
```
glen@Bionic:~$ distro-info --all -rf --days=eol
-----------//snip//-------------------
Ubuntu 16.04 LTS "Xenial Xerus" 683
Ubuntu 16.10 "Yakkety Yak" -688
Ubuntu 17.04 "Zesty Zapus" -511
Ubuntu 17.10 "Artful Aardvark" -324
[COLOR="#FF0000"]Ubuntu 18.04 LTS "Bionic Beaver" 1418[/COLOR]
Ubuntu 18.10 "Cosmic Cuttlefish" 40
Ubuntu 19.04 "Disco Dingo" 224
Ubuntu 19.10 "Eoan Ermine" 405
```

---

