---
title: "Mounting partitions with fstab"
date: 2016-02-22
forum: General Help
---

### Post by Macamba on 2016-02-22
I just installed Ubuntu 14.04 over 15.10. It works, but my /var and /home where not mounted. Now I'm working in fstab and want to ask you if I did okay.

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=60bd6b7c-555-001 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=ed8e6ed1-555-002 none            swap    sw              0       0

# Var	/dev/sdb7	forgotten during installation
UUID=6e3377c6-555-003	/var	ext4	auto	2

# Home	/dev/sdb5	forgotten during installation
UUID=12e4a613-555-004	/home/	ext4	nodev,nosuid,relatime	0	2
```

(I do not know if it is wise to post my UUIDs, so I masked them)

I am especially interested in the options, dump and pass

---

### Post by Macamba on 2016-02-22
Are these the directory listings I should expect? 
```
macamba@Hermod:~$ sudo mount -a
macamba@Hermod:~$ ls /home
lost+found  macamba
macamba@Hermod:~$ ls /var
backups  crash  local  log         mail     opt  spool
cache    lib    lock   lost+found  metrics  run  tmp
```

---

### Post by howefield on 2016-02-22
> **Macamba said:**
> Are these the directory listings I should expect? 
```
macamba@Hermod:~$ sudo mount -a
macamba@Hermod:~$ ls /home
lost+found  macamba
macamba@Hermod:~$ ls /var
backups  crash  local  log         mail     opt  spool
cache    lib    lock   lost+found  metrics  run  tmp
```

Looks fine, were you expecting a different result ?

Much as rtm is a horrible answer, a read of

```
man fstab
```

might help you out, it is a short man page and easily read/digested.

---

### Post by Macamba on 2016-02-22
Okay. Thanks.

---

### Post by oldfred on 2016-02-22
I am not an expert on mounting.
But it looks like you are missing a parameter on mount of /var. Should not a 0 be inserted for <dump>?

And most mounts of /home do not have /home/ or trailing /. Not sure what difference that makes.
I normally use just relatime to mount my data partitions. And after reading man mount I still not sure about nodev,nosuid?

example here is older as it still uses ext3 and defaults where ext4 & relatime are more common.
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Macamba on 2016-02-22
Thanks all for the feedback. I do have issues with my hardware. I aldeady re-installed twice. And this time I was able to assign the partitions during installation.

---

### Post by Bashing-om on 2016-02-22
Macamba; Hello;

My example of a working fstab file for separate partitions:
```

sysop@1404mini:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=3a47f1f1-ed1f-4134-b6aa-be101a7d97b4 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=29a6fc4f-ff12-4cac-8eb1-e98e50f1107f /home           ext4    defaults        0       2
# /var was on /dev/sda8 during installation
UUID=136af805-5758-4880-acc4-0e1d35e2c266 /var            ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=192a4783-56fa-4fd0-a62f-c45a14c08482 none            swap    sw              0       0
#/moving /tmp to ram 27may13
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

sysop@1404mini:~$

```
Note that these UUIDs are in accordance with the system identifiers as related by :
```

sudo blkid

```
mine:
```

sysop@1404mini:~$ sudo blkid
[sudo] password for sysop: 
The more you drive -- the dumber you get.
[sudo] password for sysop: 
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
/dev/sdc1: LABEL="ubie14.04std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdc2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
/dev/sdc3: LABEL="ubie15.10" UUID="2ec4733f-db40-4db0-aef8-5c54e54085ab" TYPE="ext4" 
sysop@1404mini:~$ 

```

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

