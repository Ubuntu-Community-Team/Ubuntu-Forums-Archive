---
title: "Not able to import &quot;Online&quot; ZFS pool in 22.04 after kernel panic and hard shutdown"
date: 2022-07-25
forum: General Help
---

### Post by frdrk on 2022-07-25
Upgraded from 21.10 Impish to 22.04 Jammy without problem. This is an old ZFS pool that's been online for years and been through multiple upgrades.
Started a scrub in Jammy, after a while the system freezes with kernel panic, so I had to do a hard shutdown. After this, the pool is gone. 

Obviously the pool hasn't been, properly, exported, but I can still see it with **zpool import** and it seems healthy, all disks ONLINE, there's no SMART errors etc... but the pool cannot be imported, even though the output claims so:

```
root@voidlnx ~> zpool list
no pools available

root@voidlnx ~> zpool import
   pool: tank
     id: 5973150268162290010
  state: ONLINE
 action: The pool can be imported using its name or numeric identifier.
 config:

        tank        ONLINE
          raidz1-0  ONLINE
            sdb     ONLINE
            sdc     ONLINE
            sdd     ONLINE

root@voidlnx ~> zpool import tank
cannot import 'tank': no such pool or dataset
        Destroy and re-create the pool from
        a backup source.
root@voidlnx ~>
```

Manually specifying the devices with -d, or forcing the import with -f, doesn't help.

Is there anything to do here to get the pool back?

Box is an old GIGABYTE GA-D525TUD with the D525 Atom CPU, 4G RAM, the raidz comprises 3x 3TB WDC WD30EFRX-68E

---

### Post by #&amp;thj^% on 2022-07-25
What happens if you use:
```
zpool import -d /dev/disk/by-id tank
```
As root
I see what you have posted, but also include this please:
```
systemctl status zfs.target
```
 That's what handles pool import/export on boot/shutdown.

---

### Post by frdrk on 2022-07-25
> **1fallen said:**
> What happens if you use:
```
zpool import -d /dev/disk/by-id tank
```
As root

Same
```

root@voidlnx ~> zpool import -d /dev/disk/by-id/ tank
cannot import 'tank': no such pool or dataset                                                    
        Destroy and re-create the pool from                                                      
        a backup source.

```



> **1fallen said:**
> 
I see what you have posted, but also include this please:
```
systemctl status zfs.target
```
 That's what handles pool import/export on boot/shutdown.

```

root@voidlnx ~> systemctl status zfs.target
&#9679; zfs.target - ZFS startup target
     Loaded: loaded (/lib/systemd/system/zfs.target; enabled; vendor preset: enabled)
     Active: active since Mon 2022-07-25 10:32:16 CEST; 12h ago


Jul 25 10:32:16 voidlnx systemd[1]: Reached target ZFS startup target.
root@voidlnx ~> 

```



I did however manage to force import with readonly, **zpool import -f -o readonly=on tank**, so now I can at least read from the pool.. which kind of acknowledge at least that the pool still exists.

---

### Post by #&amp;thj^% on 2022-07-26
If you run the command "**sudo zfs get all**" it should list all the properties of you current zfs pools and file systems. One of those properties, if correctly set, should be mountpoint=.

Zfs will mount the pool automatically, unless you are using legacy mounts, mountpoint tells zfs where the pool should be mounted in your system by default. If not set you can do so with

```
sudo zfs set mountpoint=/foo_mount data

```
That will make zfs mount your data pool into a designated foo_mount point of your choice.

After that is done and since root owns the mount point you can change the owner of the mount with

```
sudo chown -R user:user /foo_mount
```

That will make the user user and the group user own the mount point and everything inside it, adjust the command to assign correct user:group privileges to the mount point.

NOTE:I have to add, there is another property for datasets "**canmount**" which can either be "on | off | noauto off and noauto prevent auto-mounting" as well for individual datasets. For more info use man zfs.
You have my interest Peaked here..

---

### Post by frdrk on 2022-07-27
> **1fallen said:**
> If you run the command "**sudo zfs get all**" it should list all the properties of you current zfs pools and file systems. One of those properties, if correctly set, should be mountpoint=.

Zfs will mount the pool automatically, unless you are using legacy mounts, mountpoint tells zfs where the pool should be mounted in your system by default. If not set you can do so with

```
sudo zfs set mountpoint=/foo_mount data

```
That will make zfs mount your data pool into a designated foo_mount point of your choice.

After that is done and since root owns the mount point you can change the owner of the mount with

```
sudo chown -R user:user /foo_mount
```

That will make the user user and the group user own the mount point and everything inside it, adjust the command to assign correct user:group privileges to the mount point.

NOTE:I have to add, there is another property for datasets "**canmount**" which can either be "on | off | noauto off and noauto prevent auto-mounting" as well for individual datasets. For more info use man zfs.
You have my interest Peaked here..

These are both correctly set
```

fl@voidlnx ~> zfs get all tank | egrep "mountpoint|canmount"
tank  mountpoint            /tank                  default
tank  canmount              on                     default
fl@voidlnx ~> 

```

Might just give in and backup the essentials, destroy and recreate the pool to get this going again.

---

