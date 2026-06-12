---
title: "Plymouth resolution, GeForce 9600 GSO"
date: 2014-11-25
forum: General Help
---

### Post by coffeemugger651 on 2014-11-25
[SIZE=2]Hi,
So I have a common problem that should be easy to fix and isn't that big a deal anyway, but it's still driving me crazy.  Plymouth won't change the splash screen resolution no matter what I do.  [/SIZE]I would get counseling for my OCD, but that costs money.

Anyway, here are the specs that I'm sure you'll need, tell me if you need anything else:
Graphics: GeForce 9600 GSO
Resolution: 1440x900

[SIZE=2]I've already tried these methods of solving the problem, but none of them have worked.  Some of them have the same steps, but I did those anyway and undid redundancies in the files affected afterwards:

[/SIZE][HR][/HR][SIZE=2][COLOR=#333333][FONT=UbuntuRegular]#1:  [http://askubuntu.com/questions/412233/low-resolution-on-boot-not-login](http://askubuntu.com/questions/412233/low-resolution-on-boot-not-login)[/FONT][/COLOR][/SIZE]
[COLOR=#333333][FONT=UbuntuRegular][SIZE=2]1.sudo apt-get install v86d[/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][SIZE=2]2.gksu gedit /etc/default/grub[/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][SIZE=2]3.Replace Line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][SIZE=2]New Line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"[/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][SIZE=2]5.Replace Line:#GRUB_GFXMODE=640x480[/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][SIZE=2]New Line:#GRUB_GFXMODE=1280x1024 6.Save & Close[/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][SIZE=2]7.gksu gedit /etc/initramfs-tools/modules[/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][SIZE=2]8.Add Line: uvesafb mode_option=1280x1024-24 mtrr=3 scroll=ywrap Save & Close[/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][SIZE=2]9.sudo update-grub2[/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][SIZE=2]10.sudo update-initramfs -u
[/SIZE][/FONT][/COLOR]
[HR][/HR][SIZE=2]#2:  [http://askubuntu.com/questions/362722/how-to-fix-splash-screen-in-all-ubuntu-releases](http://askubuntu.com/questions/362722/how-to-fix-splash-screen-in-all-ubuntu-releases)

[/SIZE]
[SIZE=2]sudo apt-get install v86d
[/SIZE][COLOR=#333333][FONT=UbuntuRegular][SIZE=2]Then[/SIZE][/FONT][/COLOR]
[SIZE=2]sudo gedit /etc/default/grub
[/SIZE][COLOR=#333333][FONT=UbuntuRegular][SIZE=2]Find this line[/SIZE][/FONT][/COLOR]
[SIZE=2]#GRUB_GFXMODE=640x480
[/SIZE][COLOR=#333333][FONT=UbuntuRegular][SIZE=2]and chagne for this one (*of course choose your resolution)*[/SIZE][/FONT][/COLOR]
[SIZE=2][I]GRUB_GFXMODE=1440x900x24
GRUB_GFXPAYLOAD_LINUX=keep
[/I][/SIZE][COLOR=#333333][FONT=UbuntuRegular][SIZE=2]*Save file and type in terminal*[/SIZE][/FONT][/COLOR]
[SIZE=2][I]echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u
sudo update-grub2
[/I][/SIZE][COLOR=#333333][FONT=UbuntuRegular][SIZE=2][I]It's worked for me in all Ubuntu versions.
Give it a try :)[/I][/SIZE][/FONT][/COLOR]
[HR][/HR]#3: [http://www.youtube.com/watch?v=1jIegOR6A0M](http://www.youtube.com/watch?v=1jIegOR6A0M)


[HR][/HR]
If anyone could help me with this it would be great!  Thanks so much!

---

### Post by CantankRus on 2014-11-25
No problem here.
GeForce GTX 550 Ti
Default monitor resolution 1680x1050
Haven't installed v86d but did do the **FRAMEBUFFER=y** thingy.

I set both grub and plymouth to a lower resolution to increase the size.
_/etc/default/grub_
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="saved"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="5"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
[COLOR="#FF0000"]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/COLOR]
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
[B][COLOR="#FF0000"]GRUB_GFXMODE="1024x768"
GRUB_GFXPAYLOAD_LINUX=keep[/COLOR][/B]

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

At the grub screen press the "c" key and enter vbeinfo to make sure you are 
using a supported resolution.
May want to post your grub file just in case you have a slight error.

---

### Post by coffeemugger651 on 2014-11-25
Vbeinfo tells me that my current plymouth resolution is 1024x768x32.  It says that the preferred resolution is 1440x900, but it doesn't have 1440x900 or any other 16:10 resolution in the list.

Here's my /etc/default/grub file:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1440x900-24,mtrr=3,scroll=ywrap"
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
#GRUB_GFXMODE=1440x900
GRUB_GFXPAYLOAD_LINUX=keep


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by CantankRus on 2014-11-25
Try grub with values as in mine....
```
GRUB_CMDLINE_LINUX_DEFAULT="[COLOR="#FF0000"]quiet splash[/COLOR]"
GRUB_GFXMODE="[COLOR="#FF8C00"]1024x768[/COLOR]"
GRUB_GFXPAYLOAD_LINUX=keep
```
[COLOR="#FF8C00"]Use your preferred resolution[/COLOR]
....and remember to run **sudo update-grub**

---

### Post by oldfred on 2014-11-25
You should always test boot options by manually editing grub menu when booting. Then when you find what works, make those settings permanent in /etc/default/grub.

But I have a 9600GT and only had to use nomodeset once on grub menu when first booting after install. Then from System Settings install the nVidia driver and it just works.

But now you may have made changes to xorg, not sure if one got created or not?
 No xorg.conf in 14.04, but was in 12.04
If driver conflicts:
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

If you do not remove the # at beginning of line, then it is just a comment in /etc/default/grub.

      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

      
 NVIDIA is ceasing to support their older GeForce 8, 9, 200, and 300 series from their mainline driver but the NVIDIA 340.xx driver series will become a long-term legacy driver that they will commit to supporting until April of 2016. 
[http://nvidia.custhelp.com/app/answers/detail/a_id/3473](http://nvidia.custhelp.com/app/answers/detail/a_id/3473)
[http://nvidia.custhelp.com/app/answers/detail/a_id/3142/session/L2F2LzEvdGltZS8xNDAyMzMzMDI0L3NpZC9fVTZwRW9XbA%3D%3D](http://nvidia.custhelp.com/app/answers/detail/a_id/3142/session/L2F2LzEvdGltZS8xNDAyMzMzMDI0L3NpZC9fVTZwRW9XbA%3D%3D)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

---

