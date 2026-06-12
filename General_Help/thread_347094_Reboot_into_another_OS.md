---
title: "Reboot into another OS?"
date: 2007-01-26
forum: General Help
---

### Post by Andy_D on 2007-01-26
Hi, 

I have searched these forums and 'googled' for the answer to this question but so far I have found no information.

I dual boot Ubuntu 6.10 and Windows XP home edition (I need WinXP for my tv tuner). I was wondering if it would be possible to reboot from Ubuntu and have Windows automatically booted? The reason for this is so that I can reboot from Ubuntu and not have to stick around to select Windows XP from the grub menu as my computer takes quite a while to reboot and it is easy to miss the grub menu if not concentrating! I saw recently that opensuse (10.2) has this feature available in its main menu, does anyone know if it would be possible to do this in Ubuntu?

Any ideas or pointers to other helpful threads would be appreciated.
Thanks for your time.

---

### Post by taurus on 2007-01-26
You can set your XP as default OS and after whatever seconds, it will boot XP automatically.  That way, you don't have to sit there and choose which OS to boot. But if you want to boot Ubuntu, then you need to use the arrow key to highlight Ubuntu within the giving amount of time and hit Return to boot Ubuntu.  

You can do that by editing /boot/grub/menu.lst and change the "default" from 0 to 3 if XP is the fourth entry in there.

```
gksudo gedit /boot/grub/menu.lst
```

p.s.  If not sure, post your /boot/grub/menu.lst here then.

---

### Post by Andy_D on 2007-01-26
Thanks for the quick reply, however that isn't quite what I was looking for. I use Ubuntu almost all the time and wish to keep it as my default OS in grub. I switch to Windows when I want to watch or record tv programmes, and for several reasons (mainly laziness!) I would like to temporarily have the default system set to windows. For example when I turn my computer on I want it to boot Ubuntu automatically but I would like some method (command, launcher etc.) that will allow me to reboot into windows from Ubuntu bypassing the grub menu. I previously dismissed this as not possible but recently whilst playing around with opensuse 10.2 I saw that it had this feature. On the suse menu in the tab with the shutdown and restart options there is an option that allows you to reboot the computer and load a different OS of your choice automatically. It is this functionality that I am interested in rather than permanently altering my menu.lst, however I was not sure whether this feature is specific to opensuse or whether it can be replicated in Ubuntu.

Thanks again.

---

### Post by vigleik on 2007-01-27
I haven't tried this (I don't have windowns) but I see no reason why the following shouldn't work, if you know some very basic shell scripting. Make two copies of menu.lst, say, menu.lst.default and menu.lst.windows, and make one script that runs on startup (search the forum for how to make a script run on startup, with root privileges) that copies menu.lst.default to menu.lst, and another script that you run when you want to shut down and boot into windows which replaces menu.lst with menu.lst.windows. Then you can make a button next to the usual shutoff button (or wherever) which executes the second script.

---

### Post by ~LoKe on 2007-01-27
Perhaps you could make your life all that much easier by just installing MythTV? ;)

---

### Post by Andy_D on 2007-01-27
Thanks vigleik, I hadn't thought of that. I'll give it a go as it sounds like a nice simple solution,

Also @ ~LoKe - I would love to be able to use my tv tuner in Ubuntu but even though I have been using Ubuntu for a while now I have absolutely no idea where to start with drivers and firmware etc.! I tried looking for advice on [www.linuxtv.org](www.linuxtv.org) and ivtvdriver.org but I ended up confused! If you can help me setup MythTV with my tuner (Hauppauge WinTV Nova-T-500) that would be great!

---

### Post by kwilliam on 2007-01-29
I saw your thread a few days ago and thought I'd try to solve it. My idea is to use shell scripts and batch files to edit menu.lst.  In my case, my first two grub entries are Ubuntu and Windows XP, so all the scripts need to do is change "default 0" to "default 1" and vice versa.  I got the batch file done tonight.  Maybe someone else will do the shell script for me/us?

This batch file requires that you have Ext2 IFS For Windows ([www.fs-driver.org](www.fs-driver.org)) installed. In this example, "U:" is the letter name of my Ubuntu partition.
[COLOR="Red"]WARNING!!!  This script changes your /boot/grub/menu.lst file, and could potentially lose your grub boot manager settings. It does make a backup file, but I make NO GUARANTEES about it's safety.[/COLOR] It works for me. (I've never written a batch file before, so forgive me if this is not the best way to implement the operation.)
```
:: Batch file to edit /boot/grub/menu.lst
:: Replaces "default 1" with "default 0"

@echo off

U:
CD\boot\grub\

:: Check if /boot/grub/menu.lst exists; if it doesn't, display a warning message and quit.
IF NOT EXIST .\menu.lst (ECHO GRUB menu.lst could not found.&ECHO Correct the problem and try again.&GOTO:EOF)

:: Create backup of menu.lst
copy menu.lst windows-reboot-backup-menu.lst

:: Create temporary output file.
if exist tempfile.txt del tempfile.txt

:: For each line in 
for /f "tokens=*" %%a in (menu.lst) do call :AddText "%%a
del menu.lst
rename tempfile.txt menu.lst
:: Reboot
shutdown -r -t 10
exit /b

:AddText %1
set Text=%~1%
if "%Text%"=="default		1" echo default		0 >> tempfile.txt
if not "%Text%"=="default		1" echo %Text% >> tempfile.txt
exit /b

:EOF

```

Save the file as "boot-linux.bat" and make a shortcut to it on your desktop.  It should change the default OS in GRUB to the first entry (Linux), then reboot.  (Obviously, to get any advantage out of this script, you want a timeout in GRUB to boot the default OS after a few seconds.)  The other half of the equation would be a shell script that changes the default OS to Windows, then reboots.

---

### Post by kwilliam on 2007-02-06
Here's the shell script for rebooting into Windows from Linux:
```
#!/bin/sh
# Function: Edit the GRUB menu file to make Windows the default OS.
cd /boot/grub; echo Editing GRUB...
cp menu.lst linux-reboot-backup-menu.lst
sed -i 's/^default\t\t0/default\t\t1/g' menu.lst; echo Rebooting...
reboot;
```

**[COLOR="Red"]Same disclaimer as the post above.[/COLOR]**

This assumes the line there are two tabs in between "default" and "0" and no spaces in front.  And again, if assumes that your second menu item is Windows, your first is Linux, and you are using a timeout.  Also, "cd /boot/grub" assumes that /boot/grub is where your menu.lst file is.

To use it, save it as "reboot-to-windows", make it executable, and run it as root.  (At least I *think* you have to be root to reboot.)  Also, I'm pretty sure that placing it in /usr/local/bin will make it available from the commandline.  E.g. reboot-to-windows instead of /path/to/wherever/reboot-to-windows.

Side notes:
For some reason, "cd" and "sed" wouldn't work without the semi-colons after them, but with the semi-colons after them, bash would complain that "command not found" for the blank space after the semi-colons.  (I'm still learning shell scripting, so if someone can explain this to me, please do.)

Also, I'm still not completely satisfied with the Batch File.  It does some weird things with whitespace; it removes blank lines and adds a single space to the end of every line.  So if someone is willing to write a better one, that would be great.

---

### Post by Andy_D on 2007-02-11
kwilliam:
Thanks a lot for taking the time to write the batch file and script to do this, I appreciate it. I tested them both out and the first time things worked perfectly. I rebooted from windows using the batch file and ubuntu was automatically booted, then I rebooted from ubuntu using the shell script and windows was automatically booted.

However when using the batch file once more from windows i found the computer rebooting back into windows. I looked at menu.lst and found two lines

default         0
default         4

(I changed the batch file and script and windows is my fourth menu entry) I'm guessing this means the batch file was unable to perform correctly the second time and simply added an extra 'default...' line. Do you think this could be due to formatting problems with menu.lst and/or some of those whitespace issues you had with the batch file? (I have no experience of writing batch files so I'm pretty much clueless!)

Thanks again for the time and effort.

---

### Post by dynamicdude on 2007-02-23
Good Evening Ubuntians, 
My problem no 1 is that I want to make Windows XP the default OS I don't know what to change. So I need the guidance of you expert


# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
default 4
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		1

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda7 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda7 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda7 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda7 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1






[COLOR="Red"][SIZE="5"]Problem Number 2[/SIZE][/COLOR] 

My Wireless connection is not working I guess my Acer laptop wireless card is not detecting i did installed ndiswrapper 1.37 but don't know how to edit and work out my wireless connection. i  m copying my ifconfig report with this post as well. any help is greatly appreciated....

dwijen@dwijen-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:3F:0A:E1:12
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1456 (1.4 KiB)  TX bytes:1456 (1.4 KiB)


eth0      Link encap:Ethernet  HWaddr 00:02:3F:0A:E1:12
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1656 (1.6 KiB)  TX bytes:1656 (1.6 KiB)

---

