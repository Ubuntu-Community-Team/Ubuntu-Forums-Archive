---
title: "Can't change default boot in Ubuntu 14.04"
date: 2014-07-04
forum: General Help
---

### Post by JimLS on 2014-07-04
Installed Win7 and Ubuntu14.04 and can boot both(Win7 by manually selecting it during boot).  Want to make Win7 the default boot.  I have tried putting a number or the name in the /etc/default/grub file and have run update-grub each time.  It always defaults to the first entry which is Ubuntu.  I also tried adding:

GRUB_DISABLE_OS_PROBER=true
to the end of the file but then Win7 didn't show up on the boot menu at all.  I thought I might not be editing the actual file used for booting but since that caused the Win7 option to disappear it seems that is the proper file.

Here's my /etc/default/grub:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="Windows 7 (loader) on /dev/sda1"
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=15
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

Here is output of update-grub:
```

Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

```

---

### Post by grahammechanical on 2014-07-04
I have found that running update-grub is not enough to bring changes to the Grub menu. I always run two complimentary commands.

```
sudo update-grub
sudo grub-install /dev/sda
```

Of course, if we had a second hard disk (sdb) and Grub was installed on that hard disk we would change /dev/sda to /dev/sdb.

Regards.

---

### Post by ibjsb4 on 2014-07-04
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

[COLOR=#ff0000]GRUB_DEFAULT=0[/COLOR]
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
GRUB_CMDLINE_LINUX=""
```
Zero being the first entry in my boot menu.  So if your Windows install is the second entry you would change this to read ..
```
[COLOR=#ff0000]GRUB_DEFAULT=1[/COLOR]
```

---

### Post by yancek on 2014-07-04
To expand on the post above by ibjsb4, you did edit the correct file but you did it incorrectly as pointed out.  It is the GRUB_DEFAULT= line you need to edit and put a number there.  In this particular instance, Grub counts from zero so count the menuentries in the grub.cfg file to find the windows entry.

---

### Post by JimLS on 2014-07-04
I did try numbers there but started at 1 instead of zero.  Should have used 4 instead of 5 (which didn't exist so still booted the first entry).  It now works.

HOWEVER...  The use of a text name is allowed and avoids potential future additions to the list changing the default boot so I was attempting that.  Apparently I don't have the exact proper name or quotes or some such detail.  I just used the name as it appears on the screen during booting - same as displayed when running update-grub.  This comes from:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)


[LIST]
[*]**GRUB_DEFAULT="xxxx"** - An exact menu entry, including  the quotation symbols, may also be used. In this case, location in the  menu will not matter. Example: *GRUB_DEFAULT="Ubuntu, Linux 2.6.31-9-generic"*
[*]
[/LIST]
I guess I need to dig around in the files to find out if the name is different...Or just live with it and change it when needed.

---

### Post by JimLS on 2014-07-04
Figured it out...  See this page for where to find exact string needed:
[http://askubuntu.com/questions/52963/how-do-i-set-windows-to-boot-as-the-default-in-the-boot-loader](http://askubuntu.com/questions/52963/how-do-i-set-windows-to-boot-as-the-default-in-the-boot-loader)

Basically, if you enter this:

grep menuentry /boot/grub/grub.cfg

you will see the strings for all the boot options.  Use everthing between the quotes.

I ended up with:  
GRUB_DEFAULT="Windows 7 (loader) (on /dev/sda1)"

Thanks for giving me some ideas of things to try.

---

### Post by yancek on 2014-07-04
Glad you got what you wanted although it seems a lot simpler to type in a single number.

---

