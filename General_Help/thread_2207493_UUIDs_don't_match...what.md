---
title: "UUIDs don't match...what?"
date: 2014-02-23
forum: General Help
---

### Post by bc.haynes on 2014-02-23
It seems that the UUID in **blkid** does not match the one for **lsblk**. Why is that?
```
ben@MissionControl:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1   8:1    0 164.5G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part [COLOR="#000000"][/COLOR]
&#9500;&#9472;sda5   8:5    0   3.8G  0 part [SWAP]
&#9492;&#9472;sda6   8:6    0   150G  0 part 
sdb      8:16   1  29.9G  0 disk 
&#9492;&#9472;sdb1   8:17   1  29.9G  0 part /media/[COLOR="#FF0000"]4384cc38-484c-46b7-9b7d-212f211bba19[/COLOR]
sr0     11:0    1  1024M  0 rom  
ben@MissionControl:~$ blkid
/dev/sda1: UUID="10fd1489-5914-4f84-858f-049c21d25298" TYPE="ext4" 
/dev/sda5: UUID="55f4eb33-6e9b-4d49-9960-ea8ea177a1f5" TYPE="swap" 
/dev/sda6: UUID="2357c738-a474-4b9c-90f9-07ad38d63352" TYPE="ext4" 
/dev/sdb1: UUID="[COLOR="#FF0000"]fd7d28cb-7ae6-41f6-83bb-1479bf125d3b[/COLOR]" TYPE="ext4" 
ben@MissionControl:~$ 

```

---

### Post by coldcritter64 on 2014-02-23
> **bc.haynes said:**
> It seems that the UUID in **blkid** does not match the one for **lsblk**. Why is that?
```
ben@MissionControl:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE **MOUNTPOINT**
sda      8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1   8:1    0 164.5G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9500;&#9472;sda5   8:5    0   3.8G  0 part [SWAP]
&#9492;&#9472;sda6   8:6    0   150G  0 part 
sdb      8:16   1  29.9G  0 disk 
&#9492;&#9472;sdb1   8:17   1  29.9G  0 part **/media/[COLOR=#FF0000]4384cc38-484c-46b7-9b7d-212f211bba19[/COLOR]**
sr0     11:0    1  1024M  0 rom  
ben@MissionControl:~$ blkid
/dev/sda1: UUID="10fd1489-5914-4f84-858f-049c21d25298" TYPE="ext4" 
/dev/sda5: UUID="55f4eb33-6e9b-4d49-9960-ea8ea177a1f5" TYPE="swap" 
/dev/sda6: UUID="2357c738-a474-4b9c-90f9-07ad38d63352" TYPE="ext4" 
/dev/sdb1: UUID="[COLOR=#FF0000]fd7d28cb-7ae6-41f6-83bb-1479bf125d3b[/COLOR]" TYPE="ext4" 
ben@MissionControl:~$ 

```

The lsblk uuid is a mountpoint (not necessarily an actual uuid that is in use by the system), that is, the folder (mountpoint) is named after a devices uuid.

blkid checks for actual uuids on the devices.

Check /etc/fstab that the mounting of /dev/sdb1 and its details are correct in there. Post back /dev/sbb1's fstab entry here if you are unsure of the entry.

---

### Post by bc.haynes on 2014-02-23
I ran **sudo blkid** and it was changed.
```
ben@MissionControl:~$ sudo blkid /dev/sdb1
[sudo] password for ben: 
/dev/sdb1: UUID="4384cc38-484c-46b7-9b7d-212f211bba19" TYPE="ext4" 
```

---

### Post by coldcritter64 on 2014-02-23
Try issuing this command in the terminal for us please,

```
sudo blkid -c /dev/null
``` Using as sudo  and the "-c /dev/null" should give more accurate results as it tells it to read its cache from file /dev/null (no real file is here), this causes the command to poll the hardware rather than possibly giving you a cached result etc. 

Try this command and see if the result is the same for the first blkid command you used.

Edit: I misread your previous post, you've already noted this, I read your output as an fstab entry ... brainfreeze LOL

---

### Post by bc.haynes on 2014-02-23
I don't understand** fstab**.
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=10fd1489-5914-4f84-858f-049c21d25298 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=55f4eb33-6e9b-4d49-9960-ea8ea177a1f5 none            swap    sw              0       0

```
The code above^^ got the right UUID.

---

### Post by coldcritter64 on 2014-02-23
Ignore fstab now, you noted the cause was sudo. I'd suggest also using the cache switch to look at /dev/null to get actual hardware reads and not from cache.

edit : Going by the uuid as a mountpoint I now suspect it was mounted by mtab anyhow, so fstab is not necessary. Cheers.

---

### Post by bc.haynes on 2014-02-23
**+1** Thank you** coldcritter64** for the lookat & the info.

---

