---
title: "fstab file"
date: 2016-11-25
forum: General Help
---

### Post by theb2b2 on 2016-11-25
Ok, I did something really boneheaded but it is done.:o

Blew away my fstab file, now I need to recreate it but not sure of the exact syntactic and structure. I Understand the general layout of the fstab but not sure how to get it back to a state I can reboot my server and get it come back up.

Below is the result of the df command;

```
Filesystem      1K-blocks       Used  Available Use% Mounted on
udev              1849176          8    1849168   1% /dev
tmpfs              378916        620     378296   1% /run
/dev/sdb1        23899004    2202144   20459820  10% /
none                    4          0          4   0% /sys/fs/cgroup
none                 5120          0       5120   0% /run/lock
none              1894560          0    1894560   0% /run/shm
none               102400          0     102400   0% /run/user
/dev/sdb6       144052920      60968  136651408   1% /home
/dev/sdb7       308496440     775516  292027100   1% /var


```

In general I get the /dev/sdb* and how to list them in fstab, but not specifically how. But what of the other items shown above, how to list them in fstab?
I also understand should use UUID instead of /dev/sdb*.
Of the balance is\are they normal or standard part of fstab?
BTW it is version 14.04

Thanks all in advance.

---

### Post by oldfred on 2016-11-25
Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

Typical fstab has comment line and the actual mount for all required partitions like /, /home & /var since you have those as separate partitions.
Need to know if ext4. The standard parameters should work but some others are often used.
To find UUIDs:
       sudo blkid -c /dev/null -o list 
    
Line 1391 is my fstab. But I do not have separate /home nor /var, but do have an ESP and data partitions that I mount.
[http://paste2.org/JCDWpOJM](http://paste2.org/JCDWpOJM)

Shows typical /home entry at end of copy process.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) 
    [URL="http://paste2.org/JCDWpOJM"]
[/URL]

---

### Post by Bashing-om on 2016-11-26
theb2b2; Hey !

My fstab file :
> 
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
UUID=136af805-5758-4880-acc4-0e1d35e2c266 /var            ext4    defaults     0        2
# swap was on /dev/sda5 during installation
UUID=192a4783-56fa-4fd0-a62f-c45a14c08482 none            swap    sw              0       0
#/moving /tmp to ram 27may13
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

sysop@1404mini:~$ sudo blkid
[sudo] password for sysop: 
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="ubie14.04std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdb2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
/dev/sdb3: LABEL="ubie1604" UUID="2ec4733f-db40-4db0-aef8-5c54e54085ab" TYPE="ext4" 
sysop@1404mini:~$


[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by theb2b2 on 2016-11-27
Sorry about the delay getting back, holiday\family commitments do come first.

Below is my "rebuilt fstab file, short of doing an actual reboot how can I tell or test it?
I have used command mount -fav and it returned this;

```
theb2b@srvlamp:~$ sudo mount -fav
mount: UUID=3d1ac338-dbbd-4654-9dcf-c88b165476d6 already mounted on /home
mount: UUID=10084b4c-8a6d-405d-b005-dbfd574788ff already mounted on /var
mount: UUID=4d31c4a5-42fc-4d47-b11e-ff47df5d4bd1 already mounted on /bareos
mount: tmpfs already mounted on /tmp


```

Should I be concerned the output of mount -fav doesn't show or list swap and root? 
He is the output from blkid;

```
/dev/sda3: UUID="4d31c4a5-42fc-4d47-b11e-ff47df5d4bd1" TYPE="ext4"
/dev/sdb1: LABEL="Root" UUID="102e3a36-a969-4e97-8856-b04a5d2e2ea5" TYPE="ext4"
/dev/sdb5: UUID="209827be-1a04-43fc-bb3f-3b58f9464d2c" TYPE="swap"
/dev/sdb6: LABEL="Home" UUID="3d1ac338-dbbd-4654-9dcf-c88b165476d6" TYPE="ext4"
/dev/sdb7: LABEL="Var" UUID="10084b4c-8a6d-405d-b005-dbfd574788ff" TYPE="ext4"


```

```
# swap was on /dev/sdb5 during installation
UUID=209827be-1a04-43fc-bb3f-3b58f9464d2c       none    swap    sw              0       0
# / was on /dev/sdb1 during installation
UUID=102e3a36-a969-4e97-8856-b04a5d2e2ea5       /       ext4    errors=remount-ro 0     1
# /home was on /dev/sdb6 during installation
UUID=3d1ac338-dbbd-4654-9dcf-c88b165476d6       /home   ext4    defaults        0       2
# /var was on /dev/sdb7 during installation
UUID=10084b4c-8a6d-405d-b005-dbfd574788ff       /var    ext4    defaults        0       2
# external drive added after installation - backup storage
UUID=4d31c4a5-42fc-4d47-b11e-ff47df5d4bd1       /bareos ext4    defaults        0       2
# move /tmp to ram
tmpfs /tmp tmpfs defaults,noatime,nosuid,nodev,mode=1777 0      0


```

---

### Post by Bashing-om on 2016-11-27
theb2b2; Hey ..

All looks good with a reservation about " # external drive added after installation " ; This external drive always connected when booting up 'buntu ?
I would suggest that this device " /bareos" mount point be changed to say '/mnt/bareos' . Where you have created that directory for the mount point . If this device is not always available at boot , then ya need to get creative with the fstab entry to so advise the system .

To test that the system accepts the fstab file run:
```

sudo mount -a

```
a return to prompt here is a good thing . Anything other than a simple return is UNgood .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by theb2b2 on 2016-11-27
All good! Sudo mount -a return to prompt, thanks for the help.

The external drive is always attached, ultimate irony I was working on getting the drive setup to be my backup repository when I wiped my fstab. Had I been successful .....

I will take your advice and look into looking at how to be creative with fstab entry.

---

### Post by Bashing-om on 2016-11-27
theb2b2; Outstanding ..

Glad to see that smile on your face .

There are GUI advantages to mounting the external drive in designated places ... might consider the outcome IF mounted in say ' /media/theb2b/<somename> ' ; you will see that the file manager picks it up ... as opposed to mounting somewhere on /mnt , for instance . Use case determines .

For my use-case my backup drives are just setting there - fat dumb and I hope happy -  all spun down. Activated as on-demand from the terminal or the desktop . Me, twice burned is 10 times shy .. anything happens on my backup drives I want to know about it prezactly when it happens ! Depending on what I am doing, I may even go so far as to have syslog tailing in another terminal output . I am paranoid and I have 3 backups ( thankfully I have never had to resort to the off-premise backup ) ! My take on data; one can never be careful enough - Murphy's law always applies.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]many paths to an end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

