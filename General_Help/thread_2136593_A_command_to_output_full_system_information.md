---
title: "A command to output full system information?"
date: 2013-04-18
forum: General Help
---

### Post by bigwax on 2013-04-18
[SIZE=2]I've used [COLOR=#0000ff][FONT=courier new]**sysinfo**[/FONT] [/COLOR]and [COLOR=#0000ff]**[FONT=courier new]gnome-system-monitor [/FONT]**[/COLOR]to view my system information, but I'm looking for a command that can output general system information to a text file rather than viewing it in a GUI.

I know it's a vague question but that's about as much info as I can provide considering it's for a school lab and all that was provided was:
[B]"The script will output full system information including the hostname."

[/B]Maybe he is looking for [FONT=courier new]**[COLOR=#0000ff]cat [/COLOR][COLOR=#0000ff]/proc/version[/COLOR]**[/FONT]?

[/SIZE][HR][/HR][SIZE=2]edit: I'm thinking it's most likely [COLOR=#0000ff][FONT=courier new]**sudo lshw **[/FONT][/COLOR][/SIZE]and [FONT=courier new][COLOR=#0000ff]**uname -n**[/COLOR][/FONT]

---

### Post by dargaud on 2013-04-18
lshw
    List hardware
lshal
    List Hardware Abstraction Layer devices (currently being phased out)
lspci
    List PCI cards
lsusb
    List USB devices
lsscsi
    List SCSI devices
systool
    Part of sysfsutils
hwinfo
    For instance use sudo hwinfo --framebuffer to get the vga codes of your video card to pass to the kernel as vga=xxx in /boot/grub/menu.lst
fdisk -l
    List hard drives
dmidecode
    Get info from bootloader
dmesg
    Boot messages, check this if you can't find a device that you expect
cat /proc/cpuinfo
    Processor information
cat /proc/meminfo
    Current memory status
lpstat
    Printer information

---

### Post by nerdtron on 2013-04-18
In Linux Mint I would just type ```
inxi -Fxz
```
and this will show up.
[http://trash80.org/trash80/inxi/pics/inxi_1.7_2.png](http://trash80.org/trash80/inxi/pics/inxi_1.7_2.png)

The command is actually a script pre-installed in Mint systems but you can also get the script and how to install it using this tutorial
[http://www.webupd8.org/2009/11/shell-system-information-tool-for-linux.html](http://www.webupd8.org/2009/11/shell-system-information-tool-for-linux.html)

So after running the installing inxi you can use the command
```
inxi -Fxz > ~/infofile.txt
```
to save the output to the infofile.txt in your home folder.

---

