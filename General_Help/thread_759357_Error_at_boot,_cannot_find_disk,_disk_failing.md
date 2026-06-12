---
title: "Error at boot, cannot find disk, disk failing??"
date: 2008-04-19
forum: General Help
---

### Post by greatgoo on 2008-04-19
I have been running 7.10 on this box since it came out.  Lately the boot hangs.  Switching to the prompt I see the message ..

Loading Please wait ..

Then I see, some check requests for drivers etc.  Then I get an error ..

/dev/hda1/the uuid is displayed/ /ext3  does not exist

I assume this means the disk is failing or has lost some sectors.  Repeated resets will eventually load the OS and it runs well when it does load.  I'm thinking it is time for a new hard drive here.  Any other takes on this issue?

Think I will leave the box on for now.

David Davis
Toledo, OR 97391

---

### Post by pointone on 2008-04-19
Please post the *exact* error messages for our benefit. You'll likely be able to find it in /var/log/dmesg. Alternatively, you can use the Scroll Lock key during the boot process to pause and copy down the message verbatim.

---

### Post by greatgoo on 2008-04-20
Per a request, here is the error text as seen from the load screen .. (Alt F1)

Starting up ...
Loading Please wait ...

Check root = bootarg cat /proc/cmd line
or missing modules, devices :cat/proc/modules ls /dev


ALERT: /dev/disk/by-uuid (the disk uuid is listed I did not copy it)/does not exist
Dropping to shell

When I tried to use the recovery method it loads up to the disk and then fails.  I cannot tell if it is failing at the various mount points or if it is just a basic hard disk bad sector sort of thing.  But! it is not a total failure.  It will drop me to a busy box where I have some limited command line entry.

Two soft boots and I brought it up.  Could just be a mount point on the disk.

Where would I look for a log on the failed loads?

David Davis
Toledo, OR 97391

---

### Post by pointone on 2008-04-20
Sounds like somehow the UUID of your root partition has changed. This could be due to a kernel update or any major operations on the filesystem (resizing, reformatting, etc.). 

For a temporary fix, start your computer and wait for the GRUB menu to appear. If you are not dual booting, the menu may be hidden and require you to press "Esc" to access it.

Once in the menu, select the Ubuntu option, and press "e". This should open a new submenu. Select the line beginning with "kernel" and again press "e". A prompt should appear with several commands already entered into it.

Scroll back until you find the option:

```
root=UUID=########-####...
```

... change this to 

```
root=/dev/sd*#
```

... where "/dev/sd*#" is your root partition, (/dev/sda1, for example). If you are unsure what your root partition is in this format, please let me know.

After making the change, simply hit "Esc" to exit the prompt, and then press "b" to boot using your edited boot options.

If this solves the problem, you can make the change permanent by editing /boot/grub/menu.lst and changing the line:

```
kopt=root=UUID=########-####...
```

You can either correct the UUID, using "blkid" from the command line to retrieve a list of UUIDs for each of your partitions, or you can simply change it to "kopt=root=/dev/sd*#" format. UUIDs are more robust, apparently, but I generally use the "/dev/sd*#" notation.

After editing /boot/grub/menu.lst, run "update-grub".

Chances are your /etc/fstab file may be incorrect, as well. If this is the case, after performing the "temporary fix" described, your boot will still fail. In this case, you will be dropped to a BusyBox prompt, though, where you can correct /etc/fstab in the same way you would correct /boot/grub/menu.lst (i.e., either correct the UUIDs using blkid, or simply change to "/dev/sd*#" notation).

---

### Post by greatgoo on 2008-04-21
> **pointone said:**
> Sounds like somehow the UUID of your root partition has changed. This could be due to a kernel update or any major operations on the filesystem (resizing, reformatting, etc.). 

SNIP

Chances are your /etc/fstab file may be incorrect, as well. If this is the case, after performing the "temporary fix" described, your boot will still fail. In this case, you will be dropped to a BusyBox prompt, though, where you can correct /etc/fstab in the same way you would correct /boot/grub/menu.lst (i.e., either correct the UUIDs using blkid, or simply change to "/dev/sd*#" notation).

Hey! Thanks for the tips.  I will try them and report back.

I found another post earlier that spoke about the UUID and /etc/fstab.  I reviewed the configuration of the file to see if the UUID matched the one revealed with the blkid command.  It did.  However, there seemed to be a lot of space at the end of the line that held the UUID.  I don't know what affect that space may have on the kernal.  The posting I was reading talked about the structure of the line and although the UUID matched, not much else did.

David Davis
Toledo, OR 97391

---

### Post by greatgoo on 2008-04-26
I tried the edit at boot suggestion and it did not work,  8 resets to get the thing to come up today.  Here is the fstab ..

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=ac3c0119-1c53-4f1e-a6af-434ae584f3b8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=194c5d54-0ab6-4d87-9a95-555b3f0c4bb1 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


The uuid matches with the uuid from the blkid but I wonder about the structure of the file.  Are the various spaces significant?  For instance on the /dev/hda1 line, there are large gaps in the line, what effect do those have on the boot?

David Davis
Toledo, OR 97391

---

### Post by greatgoo on 2008-05-13
The system continued to worsen until it finally suffered a major error.  Once I got to the boot sequence the loader halted and entered a safe mode.  I was directed to run fsck with no options.  I did so and the utility found a number of errors.  I fixed them all.  Since then the system has booted first time every time.  I am not sure why the errors had not been caught by the forced check at 30 boots.

David Davis
Toledo, OR 97391

---

