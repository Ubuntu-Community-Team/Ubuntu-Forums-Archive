---
title: "Errors in boot up"
date: 2015-02-09
forum: General Help
---

### Post by nogi on 2015-02-09
Hi, I am running ubuntu server (latest version) and am seeing this error on start-up. Note that my CIF shares work but I am not sure where these are coming from?

```
[   14.191189] piix4_smbus 0000:00:01.3: SMBus Host Controller at 0xb100, revision 0
[   14.193670] parport_pc 00:04: reported by Plug and Play ACPI
[   14.855440] CIFS VFS: Error connecting to socket. Aborting operation.
[   14.901241] CIFS VFS: Error connecting to socket. Aborting operation.
[   14.934723] CIFS VFS: cifs_mount failed w/return code = -101
[   14.948284] CIFS VFS: cifs_mount failed w/return code = -101
[   15.015278] CIFS VFS: Error connecting to socket. Aborting operation.
[   15.105155] CIFS VFS: Error connecting to socket. Aborting operation.
[   15.150277] CIFS VFS: cifs_mount failed w/return code = -101

```

CIF shares work fine but I do also get this now:

```
[COLOR=#000000][FONT=consolas][  812.465179] CIFS VFS: No writable handles for inode[/FONT][/COLOR]

```
I am also seeing a service related error but not sure where to look to resolve?

```
[   61.269196] systemd-logind[2010]: Failed to start unit user@1000.service: Unknown unit: user@1000.service
[   61.269430] systemd-logind[2010]: Failed to start user service: Unknown unit: user@1000.service

```

---

### Post by sandyd on 2015-02-09
> **nogi said:**
> Hi, I am running ubuntu server (latest version) and am seeing this error on start-up. Note that my CIF shares work but I am not sure where these are coming from?

```
[   14.191189] piix4_smbus 0000:00:01.3: SMBus Host Controller at 0xb100, revision 0
[   14.193670] parport_pc 00:04: reported by Plug and Play ACPI
[   14.855440] CIFS VFS: Error connecting to socket. Aborting operation.
[   14.901241] CIFS VFS: Error connecting to socket. Aborting operation.
[   14.934723] CIFS VFS: cifs_mount failed w/return code = -101
[   14.948284] CIFS VFS: cifs_mount failed w/return code = -101
[   15.015278] CIFS VFS: Error connecting to socket. Aborting operation.
[   15.105155] CIFS VFS: Error connecting to socket. Aborting operation.
[   15.150277] CIFS VFS: cifs_mount failed w/return code = -101

```

CIF shares work fine but I do also get this now:

```
[COLOR=#000000][FONT=consolas][  812.465179] CIFS VFS: No writable handles for inode[/FONT][/COLOR]

```
I am also seeing a service related error but not sure where to look to resolve?

```
[   61.269196] systemd-logind[2010]: Failed to start unit user@1000.service: Unknown unit: user@1000.service
[   61.269430] systemd-logind[2010]: Failed to start user service: Unknown unit: user@1000.service

```
```
cifs_mount failed w/return code = -101
``` is normal - sometimes the system cannot immediately contact the CIFS server due to networking not being up yet. Can also be caused by the DNS server not being contactable yet if you use a hostname-based mount in fstab
```
[   61.269196] systemd-logind[2010]: Failed to start unit user@1000.service: Unknown unit: user@1000.service
[   61.269430] systemd-logind[2010]: Failed to start user service: Unknown unit: user@1000.service

```
[https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1359439](https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1359439)

---

### Post by nogi on 2015-02-09
Aaah cool so nothing to worry about then.

What about the inode error?

---

### Post by ajgreeny on 2015-02-10
What, if anything, does **df --inodes** tell you?

I ask as a user who has never used a server, and it doesn't seem that you are running out of inodes, but I just wonder if it will give you any clues.

---

### Post by nogi on 2015-02-10
```
$ df --inodes
Filesystem                      Inodes  IUsed   IFree IUse% Mounted on
/dev/vda1                      6488064 126103 6361961    2% /
none                            320697      4  320693    1% /sys/fs/cgroup
udev                            317903    414  317489    1% /dev
tmpfs                           320697    390  320307    1% /run
none                            320697      3  320694    1% /run/lock
none                            320697      2  320695    1% /run/shm
none                            320697      2  320695    1% /run/user
```

---

### Post by ajgreeny on 2015-02-11
OK, no problem there with inodes usage.  I didn't think it would get us far but it was worth trying.

---

