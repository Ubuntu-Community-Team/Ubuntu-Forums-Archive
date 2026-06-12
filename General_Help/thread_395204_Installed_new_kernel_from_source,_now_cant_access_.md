---
title: "Installed new kernel from source, now cant access home directory"
date: 2007-03-27
forum: General Help
---

### Post by kdawg on 2007-03-27
OK heres the deal....

I am running dapper with kernel 2.6.15.28.  Everything works perfectly fine.

I decided to try and compile the newest kernel from source, 2.6.20.4 and had no problems compiling and creating debs to install the headers and image.

Here is what I did to compile it:

```
tar xjf linux-2.6.20.4.tar.bz2
ln -s linux-2.6.20.4 linux
cd /usr/src/linux
cp /boot/config-`uname -r` ./.config
make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
```

This worked without any problems.  I just took my old config from the current kernel and did not change anything, although some of the selections are deprecated in the new kernel.

Then I installed the debs and restarted......  heres the problem:

After booting it starts gdm and goes to the login screen, when choosing my name and typing the password it says:

```
Your home directory is listed as: '/home/kevin' but it does not appear to exist.
Do you want to log in with the / (root) directory as your home directory?
It is unlikley anything will work unless you use a failsafe session.

```

'No' takes you back to the login
'Yes' displays the following:

```
User's $HOME/.drmc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  Users $HOME directory must be owned by user and not writable by other users.
```

Then clicking 'OK' yields the following:

```
Your session lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some sort of installation problem or that you may be out of disk space.  Try logging in with one of the failsafe sessions to see if you can fix this problem.
```

and the details tab on the error box says this:

```
View Details: ~/.xsession-errors file

/etc/gdm/Presession/Default: Registering your session with wtmp and utmp
/etc/gdm/Presession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm:0.Xservers" -h "" -l ":0" "kevin"
/etc/gdm/Xsession: Beginning session setup:
trying to create local folder //.kde: permission denied
trying to create local folder //.kde: permission denied
trying to create local folder //.kde: permission denied
/usr/bin/startxfce4: Xserver already running on display :0
xlib: extension "GLX" missing on display ":0.0".
xlib: extension "GLX" missing on display ":0.0".
xlib: extension "GLX" missing on display ":0.0".
xlib: extension "GLX" missing on display ":0.0".
xlib: extension "GLX" missing on display ":0.0".
xlib: extension "GLX" missing on display ":0.0".
xlib: extension "GLX" missing on display ":0.0".
xlib: extension "GLX" missing on display ":0.0".
xlib: extension "GLX" missing on display ":0.0".
xlib: extension "GLX" missing on display ":0.0".
xlib: extension "GLX" missing on display ":0.0".
xlib: extension "GLX" missing on display ":0.0".
xlib: extension "GLX" missing on display ":0.0".
xlib: extension "GLX" missing on display ":0.0".
xfce4-session: Unable to access file /home/kevin/.ICEauthority: No such file or directory.

```

Most of the errors are because I had installed kde and xfce and then later uninstalled them, so thats not a big deal.

Then it takes you back to the login screen.  This is identical with any session, including all failsafe sessions.

I can only think that the problem is caused because my Home directory is on a seperate hard disk, hdb and there is some option in the kernel config that I have not selected and did not get carried over from the current .config file.

Any help is much apprecitated.

Also, this is not a permissions problem with the partition because if I start it in failsafe terminal, /dev/hdb does not exist anywhere in the tree, so it is not even recognizing the disk at boot time.  Reverting back to the old kernel 2.6.16 makes everything work great.

Sorry for the long post, please help!

PS all partitions are Ext3 if that makes a difference.

---

### Post by lloyd_b on 2007-03-27
Could you post a copy of "/etc/fstab" please?  What I'm looking for is whether the "/home" partition is defined by a UUID, or by a "/dev/hd.." definition.

The issue - IIRC, the newer kernels see SATA drives as "/dev/sd..", rather than "/dev/hd..".  This means that if you've got that filesystem reference with an explicit "/dev/hd..", the new kernel may not be able to find it (one of the reasons that the UUID method of identifying disks was implemented).

Lloyd B.

---

### Post by kdawg on 2007-03-27
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro,data=writeback 0       1
/dev/hdb1       /home           ext3    defaults,data=writeback        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

There ya go.

I dont have any sata drives, all pata.  I wonder if it is because ext3 support was compiled as a module??  Still new to the kernel compilation process though, so thats just a guess!

Thanks for the quick reply

---

### Post by lloyd_b on 2007-03-28
> **kdawg said:**
> ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro,data=writeback 0       1
/dev/hdb1       /home           ext3    defaults,data=writeback        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

There ya go.

I dont have any sata drives, all pata.  I wonder if it is because ext3 support was compiled as a module??  Still new to the kernel compilation process though, so thats just a guess!

Thanks for the quick reply

Don't be too quick to dismiss this possibility.  Here's a link you should read:
[Merging libata PATA support into the base kernel]("http://www.uwsg.iu.edu/hypermail/linux/kernel/0608.1/0806.html")

If I'm reading this correctly, PATA drives may also show up as /dev/sd.. entries, as of the 2.6.19 kernel.

Can you boot into recovery mode with the 2.6.20 kernel?  If so, try manually mounting the "/dev/sd.." entry that corresponds to your original "/dev/hd.." entry, and see what happens (the worst case - it tells you that "/dev/sd.." doesn't exist).

Lloyd B.

---

### Post by kdawg on 2007-03-28
Well tried to boot into recovery mode for the new kernel and it hangs and says waiting for root filesystem.  Waited about 20 mins and restarted, same thing happened.  I don't believe that it is an fschk and it seems to only happen every few boots when starting the kernel in normal user mode.  Very strange!

Thanks for the read links, I'll check them out and see what I can see, more help is welcome as well!

---

### Post by kdawg on 2007-03-28
Well now it doesn't boot to the login screen at all, it keeps saying waiting for root filesystem, and then after about 5 mins, it drops to a shell and says' /dev/hda1 cannot be found'

This is strange because when I first installed the kernel, it booted just fine to the login screen and after a few times now it doesnt at all.  The original kernel still works perfectly fine and recognizes and mounts all the partitions. 

 I read a little and saw a lot of other people with the same problems, most of it was due to sata vs pata issues like you said lloyb_b, so I'm not sure what to do to fix it.  I have 2 PATA drives, and no SATA at all, I looked through the kernel xconfig selections and nothing sticks out except for one selection under
Device Drivers>ATA/ATAPI support>Enhanced IDE>Include IDE/ATA-2 DISK Support that says to say yes if your root filesystem is on an ATA drive, which it is, and it is checked correctly.....

---

### Post by lloyd_b on 2007-03-28
When booted to the old kernel, try editing "/boot/grub/menu.lst", and modify the line for the new kernel (recovery mode) to use the "/dev/sd.." device, rather than the "/dev/hd.." device:
```
kernel          /boot/vmlinuz-2.6.20 **root=/dev/hda2** ro
```
to
```
kernel          /boot/vmlinuz-2.6.20 **root=/dev/sda2** ro
```
(Substituting the correct device for your system, of course).

Then try booting into recovery mode, and see if it works.

If that works, then you may wind up having to keep two different "fstab" files around ("fstab.new" and "fstab.old"), and then copy the appropriate one to "/etc/fstab" before rebooting to the other kernel.

I understand what the kernel developers are trying to accomplish (unifying IDE and SCSI devices into a single device scheme), but there *are* going to be issues as a result.

Lloyd B.

---

