---
title: "[SOLVED] Big Problems with /boot"
date: 2008-01-02
forum: General Help
---

### Post by austinderrick2 on 2008-01-02
Ok, so I used a gparted live CD to resize my partition that holds my Ubuntu dist.

The gparted "finished with errors"... Now I have no /boot folder. 

After several searches, I have managed to get grub reinstalled, however, I am missing all of the files outside of the /grub folder. **I believe they have something to do with the kernal, memtest, ect...** (Examples include, but are not limited to: memtest86+.bin, vmlinux-debug-2.6.22-14-generic, vmlinux-2.6.22-14-generic)

I tryed coping these files from a similar Ubuntu machine at the office, but that didn't work...

I'm about to pull out my hair lol... Any suggestions besides a big reformat?

---

### Post by ~LoKe on 2008-01-02
In a terminal....
```
sudo dpkg-reconfigure linux-image-generic
```
See if that helps?

---

### Post by austinderrick2 on 2008-01-02
Will I be able to do that from the LiveCD kernal... Cause I can't load the ubuntu drive (Kinda hard without boot files lol)

---

### Post by ~LoKe on 2008-01-02
> **austinderrick2 said:**
> Will I be able to do that from the LiveCD kernal... Cause I can't load the ubuntu drive (Kinda hard without boot files lol)

You should be able to, but it'll be more difficult.  Boot up the LiveCD, then..
```
sudo mkdir /media/gutsy
sudo mount /dev/**** /media/gutsy
```
Replace /dev/**** with the name of the partition with your linux install on.

Then...
```
sudo chroot /media/gutsy su
```

Then you can follow the steps I mentioned.

---

### Post by austinderrick2 on 2008-01-02
```

ubuntu@ubuntu:~$ sudo chroot /media/disk su
chroot: cannot run command `su': Permission denied
ubuntu@ubuntu:~$ sudo chroot /media/disk
chroot: cannot run command `/bin/bash': Permission denied

```

---

### Post by austinderrick2 on 2008-01-02
```

ubuntu@ubuntu:/media/disk$ chmod 0777 '/media/disk/bin/bash' 
chmod: cannot access `/media/disk/bin/bash': Input/output error

```

---

### Post by ~LoKe on 2008-01-02
What's the output of:
```
cat /etc/fstab
```
There might be a line in there blocking your access.

---

### Post by austinderrick2 on 2008-01-02
```

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

```

---

### Post by austinderrick2 on 2008-01-03
For the information of others: I was using the 32bit CD with a 64bit OS installed on the hard drive.

That is what caused the above issue chrooting.

---

### Post by ~LoKe on 2008-01-03
> **austinderrick2 said:**
> For the information of others: I was using the 32bit CD with a 64bit OS installed on the hard drive.

That is what caused the above issue chrooting.

Sorry I just got back to you.  Looks like you needed some help.  So, have you tried using a 64bit CD?  If so, did it work?

---

### Post by austinderrick2 on 2008-01-03
After switching to a 64bit CD:

```

ubuntu@ubuntu:~$ sudo chroot /media/disk su
root@ubuntu:/# sudo dpkg-reconfigure linux-image-generic
sh: cannot create /dev/null: Permission denied
sh: cannot create /dev/null: Permission denied

```

---

### Post by ~LoKe on 2008-01-03
> **austinderrick2 said:**
> After switching to a 64bit CD:

```

ubuntu@ubuntu:~$ sudo chroot /media/disk su
root@ubuntu:/# sudo dpkg-reconfigure linux-image-generic
sh: cannot create /dev/null: Permission denied
sh: cannot create /dev/null: Permission denied

```

Try just...
```
dpkg-reconfigure linux-image-generic
```

---

### Post by austinderrick2 on 2008-01-03
Also, if this helps...
```

root@ubuntu:/# sudo apt-get install linux-headers-2.6.22-14-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-headers-2.6.22-14-generic
1 upgraded, 0 newly installed, 0 to remove and 63 not upgraded.
Need to get 594kB of archives.
After unpacking 4096B of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  linux-headers-2.6.22-14-generic
Install these packages without verification [y/N]? y
Get:1 http://security.ubuntu.com gutsy-security/main linux-headers-2.6.22-14-generic 2.6.22-14.47 [594kB]
Fetched 594kB in 2s (212kB/s)                           
sh: cannot create /dev/null: Permission denied
sh: cannot create /dev/null: Permission denied
dpkg-preconfigure: unable to re-open stdin: 
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 92009 files and directories currently installed.)
Preparing to replace linux-headers-2.6.22-14-generic 2.6.22-14.46 (using .../linux-headers-2.6.22-14-generic_2.6.22-14.47_amd64.deb) ...
Unpacking replacement linux-headers-2.6.22-14-generic ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up linux-headers-2.6.22-14-generic (2.6.22-14.47) ...

```

[b]

Can not write log, openpty() failed (/dev/pts not mounted?)
[/b]

I've seen other people mounting stuff other than the main drive, folders inside the main drive... Do I need to do this?

---

### Post by austinderrick2 on 2008-01-03
```

root@ubuntu:/# dpkg-reconfigure linux-image-generic
sh: cannot create /dev/null: Permission denied
sh: cannot create /dev/null: Permission denied

```

---

### Post by ~LoKe on 2008-01-03
Type "exit" into the terminal to leave chroot, and if it's showing ubuntu@ubuntu then type this:
```
sudo mount --bind /dev /media/disk/dev
```
Then try to chroot.

---

### Post by austinderrick2 on 2008-01-03
OK, that got me through that part.

```

sudo mount --bind /dev /media/disk/dev

dpkg-reconfigure linux-image-generic


```

Works, but let me reboot and see if it gets me into ubuntu now...

---

### Post by ~LoKe on 2008-01-03
> **austinderrick2 said:**
> OK, that got me through that part.

```

sudo mount --bind /dev /media/disk/dev

dpkg-reconfigure linux-image-generic


```

Works, but let me reboot and see if it gets me into ubuntu now...

*crosses fingers*

---

### Post by austinderrick2 on 2008-01-03
Ok, now it gets stuck at

```

BEGIN: Waiting on root file system

```

I suspect this might be a configuration problem with my Grub (Also missing when I had the issues with gparted... But I've already reinstalled it.)

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=f5bb4608-eaca-41dc-ba11-c6a2774a1dc4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f5bb4608-eaca-41dc-ba11-c6a2774a1dc4 ro nosplash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f5bb4608-eaca-41dc-ba11-c6a2774a1dc4 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00026b35

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        9526    76517563+  83  Linux
/dev/sda3            9527        9729     1630597+   5  Extended
/dev/sda5            9527        9729     1630566   82  Linux swap / Solaris

```

```

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,1)

```

---

### Post by ~LoKe on 2008-01-03
Mm...perhaps changing this:
> root=UUID=f5bb4608-eaca-41dc-ba11-c6a2774a1dc4
To this:
> root=/dev/sda2

---

### Post by ~LoKe on 2008-01-03
On another forum, this was mentioned as a possible solution:
> sudo mkinitramfs -o /boot/initrd.img-2.6.22-14-generic 2.6.22-14-generic
sudo update-grub
sudo aptitude reinstall linux-restricted-modules-2.6.22-14-generic

---

### Post by austinderrick2 on 2008-01-03
Dies at:

```

[44.036555] sd 0:0:0:0 Attached Scsi Generic sg0 type 0
[44.036555] sd 0:0:0:1 Attached Scsi Generic sg0 type 5
[44.044555] sda2 sda3 <sda5>
[44.060869] sd 0:0:0:0 [sda] Attached SCSI disk



Check root = boot arg
cat /proc/cmdline or missing modules ls /dev Alert! /dev/disk/by-uuid/f5bb4608-eaca... does not exist. Dropping to a shell!


```

---

### Post by ~LoKe on 2008-01-03
Try...
```
ls -l /dev/disk/by-uuid
```
It should output something similar to this...
> total 0
lrwxrwxrwx 1 root root 10 2008-01-01 18:58 4dca6b1c-ba68-40c5-b055-47b28349d3fa -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-01-01 18:58 776eb45a-ef14-493a-8852-68444d1a10ef -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-01-01 18:58 79b94531-e9c2-423f-b10e-19d1f6eab496 -> ../../sda2

Use the UUID you get for /dev/sda2 in your menu.lst.  It should look similar to this:
> kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=79b94531-e9c2-423f-b10e-19d1f6eab496 ro nosplash

---

### Post by austinderrick2 on 2008-01-03
> 
Mm...perhaps changing this:
Quote:
root=UUID=f5bb4608-eaca-41dc-ba11-c6a2774a1dc4
To this:
Quote:
root=/dev/sda2



This after updating grub worked. I now am getting to the login screen.

When I login, I get this error:

```

User's $Home/.dmrc file is being ignored. This prevents the default session and language from being saved. Files should be owned by the user and have 644 permissions. User's $Home/ directory must be owned by the user and not writable by others.
[/quote]

After clicking OK I get

[code]
Your session only lasted less than 10 seconds... blah... blah...

```


and then I go back to the login screen.



Trying some chmoding...I'll be back in a few, any ideas?

---

### Post by ~LoKe on 2008-01-03
```
sudo chmod 644 $HOME/.dmrc
```
Should be as simple as that.

---

### Post by austinderrick2 on 2008-01-03
Ok, I chmod'ed my home direcorty to 644 with

```

sudo chmod 0644 -r /home/zug

```

This fixed the first error ^^... 

Now gnome still crashes though, I **can** get into failsafe terminal, however (Not failsafe gnome though)...

The error that pops up says something like:
```

Your session lasted only less than 10 seconds... (blah..blah)

```

Error Log: (~/.xsession-errors)
```


(process:6478): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:6482): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Warning: Only changing the first 7 of 10 buttons.
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  116 (X_SetPointerMapping)
  Value in failed request:  0x4
  Serial number of failed request:  9
  Current serial number in output stream:  9
.: 2: Can't open /etc/X11/imwheel/startup.conf


```


I tryed making a new user, but this didnt work either... did the same thing actually.

New xsession-errors log:

```


(process:6017): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:6021): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Warning: Only changing the first 7 of 10 buttons.
.: 2: Can't open /etc/X11/imwheel/startup.conf

```

---

### Post by austinderrick2 on 2008-01-03
```

sudo apt-get install imwheel

```

Got the new username to work, however, I have no network connctivity... (the DHCP settings Must have been screwed up somehow)

Also, the old username doesn't work. It has the same error,except instead of the imwheel it says "Can not create /.gnome2"

---

### Post by austinderrick2 on 2008-01-03
Ok, the issue with logging with was a permissions issue with the user's home directory... Still no networking, but that should be easy to reconfigure.


Thanks!!!

---

### Post by ~LoKe on 2008-01-03
Can't believe you recovered from that.  Haha. ;)

---

### Post by austinderrick2 on 2008-01-04
Yah, that was pretty crazy stuff... Amazing what linux can do though... :)

I just wish I knew what caused gparted to mess up like that, so I don't break anything next time lol...

---

