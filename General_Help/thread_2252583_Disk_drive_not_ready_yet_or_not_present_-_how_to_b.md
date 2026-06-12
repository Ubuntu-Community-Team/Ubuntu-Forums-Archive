---
title: "Disk drive not ready yet or not present - how to bypass?"
date: 2014-11-12
forum: General Help
---

### Post by Pete7874 on 2014-11-12
Hello,

Newbie here.   I am running Ubuntu 14.04 LTS on Intel NUC.  I frequently connect USB drives to the device, and wanted them mounted automatically during bootup so that all users could access them, so I edited Fstab as per the instructions given here:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

However, now if any one of these drives happens to not be connected at boot time, Ubuntu throws the following message and waits for input:

[IMG]http://i34.photobucket.com/albums/d102/escape2music/PC_stuff/DSC_6765_600.jpg[/IMG]

This is problematic as it prevents the system from rebooting.  I typically only have remote access to this device, so when I tell it to reboot, it gets stuck on this screen and won't boot to desktop until I connect a keyboard to it and press 'S'.  Is there any way to get around it so that it would just ignore these missing drives and continue booting?

Thanks!

---

### Post by Bucky Ball on 2014-11-13
Whatever you did in fstab, go in and delete the line as it is wrong. That's what that message is pretty much telling us.

You don't mention it, but I'm presuming you are using an NTFS partition on the USB. If this is the case, install ntfs-3g and ntfs-config from Software Centre.. You will then find 'NTFS configuration tool' in your apps menu. Run that with the USB plugged in. It will rewrite the fstab for you.

PS: You should ALWAYS make a back-up of important files prior to editing unless you have a good idea of what you're doing. 

```
sudo cp /etc/fstab /etc/fstab.backup
```

To replace if things go pear shaped:

```
sudo mv /etc/fstab.backup /etc/fstab
```

Having said all this, removable drives should automount when plugged in without diddling with fstab, anyhow. So that appears to be the problem. Once ntfs-3g is installed, try booting with the stick in and see if it is picked up without changing the fstab.

---

### Post by Impavidus on 2014-11-13
Usb drives should be mounted automatically when inserted, specifically at /media/username/driveID. Username is the user currently logged in to the GUI. So if this is a server where the only physical access is by plugging in usb drives, then this doesn't work.

If you want to use fstab to mount usb drives and allow all users to mount them, use fstab with the options **user** and **noauto**. **user** will allow any user to mount the partition, **noauto** will prevent the system from trying to mount the partition automatically at boot. Instead of **noauto** you can also use **nofail** (I think, not sure about this), which will try to mount the partition at boot, but will not cause an error when it's not present.

---

### Post by steeldriver on 2014-11-13
If nofail doesn't do the trick, you might want to try **nobootwait** instead

```

       The mountall(8) program that mounts filesystem during boot also recog&#8208;
       nises additional options that the ordinary  mount(8)  tool  does  not.
       These  are:  ``bootwait''  which  can be applied to remote filesystems
       mounted outside of /usr or /var, without which mountall(8)  would  not
       hold  up  the  boot  for these; [B]``nobootwait'' which can be applied to
       non-remote filesystems to explicitly instruct mountall(8) not to  hold
       up  the  boot  for  them[/B];  ``optional''  which  causes the entry to be
       ignored if the  filesystem  type  is  not  known  at  boot  time;  and
       ``showthrough''  which  permits  a mountpoint to be mounted before its
       parent mountpoint (this latter should be used  carefully,  as  it  can
       cause boot hangs).

```

(I have a feeling that nofail only suppresses the error message, it doesn't actually ignore the failure - but  I may be wrong about that)

---

### Post by Pete7874 on 2014-11-13
Thank you!  nobootwait did the trick.

---

