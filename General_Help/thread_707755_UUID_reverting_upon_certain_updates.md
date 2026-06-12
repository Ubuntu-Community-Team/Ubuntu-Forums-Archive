---
title: "UUID reverting upon certain updates"
date: 2008-02-25
forum: General Help
---

### Post by Audiosears on 2008-02-25
In the past few months, I replaced the HD's in our Gutsy server, meaning there were new partitions and therefore new UUID's to define them.  The changeover was a little rocky, but I more or less cloned the data from the original main boot partition to the new drive and it has been working fine with the new UUID.

However, the problem I now seem to be running into is every so often during update processes (usually the ones requiring a reboot).  The UUID for the boot partition seems to be reverting to the original UUID in Fstab from time to time, so upon the next reboot the server will hang, looking for a partition that is no longer available.

Once I figured out what the problem was, I booted to the CD and replaced Fstab with an older file containing the correct UUID's.  However, I would like to avoid having to do this every time going forward with future updates...

I imagine the UUID data for the server must be in some text file somewhere that the system is using to overwrite Fstab that didn't get changed when I installed the new HD.  Anyone have a cluse where that file / setting might be?

Thanks in advance!

---

### Post by pointone on 2008-02-25
I hop around from distro to distro quite often and my UUIDs would change any time I formatted a partition. Rather than specifcy partitions in fstab by UUID, I switched to the /dev/sda* notation to get around this problem and haven't had a problem. Since my partitioning layout isn't going to change as often as I will be formatting, this works out better for me.

---

### Post by Audiosears on 2008-02-26
I had thought about that, but I want to make sure that any changes I make, including moving to /sda aren't overwritten again by wherever the base configuration data is.

Any idea which config file or text could be the key?

---

### Post by Audiosears on 2008-03-24
I may have found the answer to this - There was an entry in menu.lst that I ignored beccause it was commented out, but upon looking again had the old UUID number.  I changed it and have not yet had the problem recur (though it could certainly be the case that it simply hasn't been overwritten again).

This example has the correct UUID after I reverted it.

***********************
(menu.lst headers)
.
.
.

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
# kopt=root=UUID=**3e6db4cc-a653-404e-b400-cb52247ad5cf **ro quiet splash

.
.
.
**********************************

---

