---
title: "reading jpg files on ntfs drive"
date: 2016-10-06
forum: General Help
---

### Post by Nailhac on 2016-10-06
I have numerous jpg files on win 10 system. I can access the folders through ububtu 16.04 but the jpg files are greyed out in **[B]shotwell image viewe**r[/B] and cannot view them. Is this normal or am I missing something? Comments would be appreciated.:(

---

### Post by colmax on 2016-10-06
Hi Nailhac
Can you boot into win10 then Reboot into ubuntu
Sometimes that makes the ntfs volumes more manageable
Otherwise it could be a win10 permission issue
You could try (in win10) copying your jpegs into a shared folder
Cheers

---

### Post by SeijiSensei on 2016-10-06
Is this on a drive connected to the machine, or are you accessing the files over the network?

If the latter, then you don't have the proper permissions in Windows.  Make sure you've set up the share to have public access.

If the drive is connected directly, it's also a permissions problem, but one you can fix by mounting the device in [/etc/fstab]("https://help.ubuntu.com/community/Fstab") with proper rights.  I access my NTFS partition by mounting it like this:
```
UUID=7BD7EBD65436CD44   /windows    ntfs    defaults,umask=007,gid=46    0    0
```
The UUID is unique to the partition.  Run the command "sudo blkid" in a terminal to get a list of the UUIDs for the devices on your system.

The group with ID 46 is called "plugdev".  You should have been added to this group at installation.  You can check this by running the command "id" in a terminal which will list all your group memberships by both name and numeric ID.

---

