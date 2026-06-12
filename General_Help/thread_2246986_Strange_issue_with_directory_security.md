---
title: "Strange issue with directory security"
date: 2014-10-04
forum: General Help
---

### Post by carlo-1973 on 2014-10-04
Hey everyone, I could really use your help here.

Never had this happen before so not sure what is going on.

Issue with directory security settings.

I have 4 hard drives on this system.
/dev/sda - OS and Swap
/dev/sdb - TV Series downloads
/dev/sdc - Temp holding space and misc stuff
/dev/sdd - Movie downloads.

They are all partitioned with ext4 filesystem.

FSTAB is as follows:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=4ba5da4e-30a6-410f-8954-aa8765ef355a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=43bf3819-bfce-48ce-ab46-88ad0a2975d0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=7748f2f3-53f6-4405-9b21-380ffd1e7045       /mnt/Series     ext4    defaults        0       0
UUID=102bcb65-aeab-41d8-9cab-e92a1eb6c252       /mnt/temp       ext4    defaults        0       0
UUID=5830645f-b31d-433d-8fce-64ce8534ba7f       /mnt/Movies     ext4    defaults        0       0

```

I have a group called deluge, where the following users are members myuser,root,deluge,debian-deluge
i have set folder rights as follows:

chown -R root:deluge Series
I then chmod the folder: chmod 775 Series

I am able to access the directory, however I can't seem to make any additional directories.

The only thing that seemed to work was setting chown myuser:deluge  (as in the example for directory Movies)

ls -la
```
drwxrwsr-x  4 myuser deluge 4096 Oct  4 17:23 Movies
drwxrwxr-x 20 root     deluge 4096 Sep 28 05:35 Series
drwxrwxr-x  7 root     deluge 4096 Oct  4 01:36 temp

```

I originally wanted only those with access to SUDO to be able to delete files but this was counter productive as I need the system user "deluge" to be able to create folders and delete files as needed.

I really do not want to have to do chmod 777 on everything as this is highly insecure.

If I remember correctly, the way I have it set with chown root:deluge should make it so that the owner of the folder is root, but anyone in the deluge groop can access the folder to the extent of the rights for that group. chmod 775 should give root, and the group full access, but give read only access to "Other" users. 

Where did I mess up?

---

### Post by JKyleOKC on 2014-10-04
> **carlo-1973 said:**
> I originally wanted only those with access to SUDO to be able to delete files but this was counter productive as **I need the system user "deluge" to be able to create folders and delete files** as needed.I can't really help much with the specific question, but I **can** help with this part of your requirements. You can provide limited SUDO capability to all members of the "deluge" group so that they can create folders and delete files, and even let them do so without needing to enter any password. Full details are in the manual page for "sudo" that you can find via "man sudo."

This ability to provide limited admin capability via group membership is one of the more powerful things in the *nix three-level permissions design, and isn't nearly as widely known as it should be.

---

### Post by carlo-1973 on 2014-10-05
Okay this can be marked as closed, because the issue has literally resolved itself.

Went out to see a movie with my wife (Hector and the persuit for happiness - a fairly decent feel good movie btw), went to dinner, came home, logged in, and for shoots and giggles tried to make a subdirectory within the Series parent directory. Bam, works, with my regular account (myuser) and not sudo.
Checked ls -la and everything was root:deluge with permissions set to 775.

Not 100% sure but seemed like there was a weird delay between assigning the permissions and when they took effect. As I was still logged into the system through an SSH shell, I know a reboot did not take place. 

Very bizzare but glad its working now.

Reset the folder Movies to owner/group root:deluge, and reset the folder permissions to 775, rebooted the system, logged in with my local account without root, and everything is working fine again.

There was one thing I did do before I left - and that was to remove root from the deluge group, but not sure if that alone would have made the difference here, but I did test it before leaving and it wasn't working at that point either.

Note to others if they have weird permission issues that don't seem to be sticking - give your system a reboot and see if the settings take.

---

### Post by claracc on 2014-10-05
So, as the problem has been fixed, please, mark the thread as solved with thread tools menu in the right upper part of the webpage.

Thanks.

---

