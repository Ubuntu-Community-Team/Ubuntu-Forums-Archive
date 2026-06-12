---
title: "failed to mount /home in ubuntu"
date: 2014-03-20
forum: General Help
---

### Post by Rgc183 on 2014-03-20
Hi,
    While booting up ubuntu, i am getting some error messages which shows that /home fails to mount. I am attaching the image. 
[ATTACH=CONFIG]251344[/ATTACH]


How can i solve this issue?

---

### Post by deadflowr on 2014-03-20
What's the output of
```
cat /etc/fstab
```
and do the UUID's match the ones for
```
sudo blkid
```

---

### Post by Rgc183 on 2014-03-20
> **deadflowr said:**
> What's the output of
```
cat /etc/fstab
```

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
UUID=3d868b8d-b5bb-4540-9d9b-a38aa8e1e876 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=50e45e89-03fd-49ce-bb3e-56be24fc6588 /home           ext3    defaults        0       2
# /usr/local was on /dev/sda5 during installation
UUID=0ba90b9c-7831-4bd5-8d6a-d8b3387c2b6c /usr/local      ext3    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=1ce96733-fecd-4515-98d1-821b47e4348c none            swap    sw              0       0
# /ub
UUID=7067e0e7-929c-43cd-ab9f-58afcafdfc21  /ub    ext4  defaults 0  2


```



and do the UUID's match the ones for
```
sudo blkid
```

```

/dev/sda1: UUID="3d868b8d-b5bb-4540-9d9b-a38aa8e1e876" TYPE="ext4" 
/dev/sda5: UUID="0ba90b9c-7831-4bd5-8d6a-d8b3387c2b6c" TYPE="ext3" 
/dev/sda6: UUID="1ce96733-fecd-4515-98d1-821b47e4348c" TYPE="swap" 
/dev/sda7: UUID="50e45e89-03fd-49ce-bb3e-56be24fc6588" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="7067e0e7-929c-43cd-ab9f-58afcafdfc21" TYPE="ext4" 


```


It looks like id matches. Is it hard disk issue? I mean it shows i/O error message

---

### Post by Bashing-om on 2014-03-20
Rgc183; Hi !

If it were me in this situation I would now - as the uuid's correlate -;
a) Run the SMART test available in the "disk utility";
b) Run a file system check repair from the liveDVD environment (can not run the test while the files are in use );
#From liveDVD so everything is unmounted,swap off if necessary, change example shown with partition sda7 as required;
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required;
```

sudo e2fsck -C0 -p -f -v /dev/sda7
#if errors: -y auto answers yes for fixes needing response see: -> man e2fsck
sudo e2fsck -f -y -v /dev/sda7

```

See then what results.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

