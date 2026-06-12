---
title: "OneDrive cifs mount fails after upgrading to 24.04.1 LTS"
date: 2024-11-06
forum: General Help
---

### Post by dawg6 on 2024-11-06
Edit: this only fails on a Windows OneDrive folder. I am able to mount a folder that is outside of the OneDrive diirectory tree.

[SOLVED] Edit 2: I solved this by switching to rclone ([https://rclone.org/onedrive/](https://rclone.org/onedrive/)).

I've seen several posts about this happening to others, but none of the solutions are working for me.


Trying to mount a windows 11 shared folder on Ubuntu 24.04.1 VM running in Hyper-V on the same host. This was working fine on 22.04 and stopped working right after I upgraded to 24.04 (using do-release-upgrade).

My mount command is:

```

sudo mount -t cifs //ip-address/shared /mnt/shared -o username=email,password=password

```

The shared folder is accessible from another windows host, but none of my 24.04 linux hosts can mount it. 

I created a fresh 22.04.5 VM from .iso and using the same exact mount command, I can mount the folder.

I also created a fresh 24.04.1 VM from .iso and it is unable to mount the shared folder.

The error in response to the mount command is:

```
mount error(95): Operation not supported
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs) and kernel log messages (dmesg)

```


The error I get in dmesg is:


```
CIFS: VFS: parse_reparse_point: unhandled reparse tag: 0x9000601a
CIFS: VFS: cifs_read_super: get root inode failed


```

I've made sure all my packages are up to date. The cifs-utils package is installed.


I've tried adding ",vers=1.0" (and 2.0 and 3.0) to the mount command.


I ran nmap to find out what smb versions are supported by the windows server and tried those versions as well:


```
Host script results:
| smb-protocols:
|   dialects:
|     NT LM 0.12 (SMBv1) [dangerous, but default]
|     2:0:2
|     2:1:0
|     3:0:0
|     3:0:2
|_    3:1:1

```

I've tried adding the below lines to /etc/samba/smb.conf (as was suggested in one of the posts I came across):


```
server min protocol = NT1
client min protocol = NT1

```

Anything else I should try?

---

