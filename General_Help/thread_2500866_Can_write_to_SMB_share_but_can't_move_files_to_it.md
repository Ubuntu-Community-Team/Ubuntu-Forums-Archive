---
title: "Can write to SMB share but can't move files to it"
date: 2024-09-14
forum: General Help
---

### Post by djeyewater on 2024-09-14
I have an SMB share setup in linux that I can write to, but cannot move files to from Windows. In Windows I can't move files to it from my Windows disk or from another share.
The share is an NTFS formatted partition.
For testing I am using files on a share of a ZFS formatted partition, and then trying to move them from there to the NTFS formatted share.
In MacOS, when using the shares via AFP I can move the files from the ZFS share to the NTFS share no problem. Additionally, after doing this I can then move them back and forth using Windows as well.
In MacOS, when using the shares via SMB I cannot move the files from the ZFS share to the NTFS share.
In a linux guest, when mounting the shares via SMB I can move the files from the ZFS share to the NTFS share no problem. Additionally, after doing this I can then move them back and forth using Windows as well.

fstab:
```
/dev/disk/by-label/v /mnt/v ntfs    auto,nofail,noatime,rw,windows_names,norecover,big_writes,streams_interface=windows,inherit,uid=share,gid=share   0   0
```
I have also tried with ,permissions,users but this made no difference.

smb.conf (just an excerpt but hopefully these are the relevant bits, the configuration for the ntfs share [v] is complete):
```
[global]
force user = share
force group = share
workgroup = WORKGROUP

[v]
    path=/mnt/v
    writable = yes
    create mask = 0775
    directory mask = 0775
```

Permissions on the test files in the ZFS share look like this (test-macos.zip is the file that was successfully moved on MacOS using AFP and test-linux-smb.zip is the file that was successfully moved on linux)
```
-rwxrwxrwx+  1 share share   23150939 Sep  6 07:51  test-macos.zip
-rwxrwxr-x+  1 share share   23150939 Sep  6 07:51  test.zip
-rwxrwxr-x+ 1 share share 23150939 Sep  6 07:51  test-linux-smb.zip
```

Permissions for the NTFS share where I am trying to move the files to: 
```
drwxrwxrwx 1 share share   8192 Sep 14 10:53  .
```

I'm very confused how I can move the files over SMB in Linux but not MacOS or Windows, and how after doing this I can then move the file in Windows despite the permissions between this and a file I can't move looking the same.

I'm guessing that there's either something in my fstab or smb configuration I need to change to get it working properly?

Thanks

---

### Post by TheFu on 2024-09-14
I have no idea, but SMB ignores local Linux permissions.  It runs as root and doesn't care at all about local permissions. Heck, you are even forcing a specific user to be used, always, so it matters even less.

There's no reason to use NTFS for any network shared storage from Linux.  Always prefer native Linux file systems when sharing from Linux regardless of the client.
Also, while CIFS can be used to share storage, I'd only use it for MS-Windows clients. For Unix-like OSes, use NFS, the native network storage protocol for Unix systems.  NFS isn't reverse engineered and isn't constantly being modified by a company who doesn't care about Linux support.  NFS has been "mature" since the mid-1990s, at least.  v4 of NFS has been available over 20 yrs.  Best of all, when NFS is setup between systems, it is server to server, not end-user to server, so native permissions work. No permissions overlay is used.

So, I threw out a bunch of ideas and suggestions.  I need to say, I don't have MacOS (not since around 2010) and I don't have any MS-Windows version 10 or 11 here, so these are not "I know this works" answers, just suggestions based on history.

BTW, the "+" at the end of the permissions (-rwxrwxr-x[COLOR="#FF0000"]+[/COLOR]) is there to tell you something about the permissions.  Basically, it says that ACLs are being used and you cannot trust the displayed permissions, since the ACLs overrule them. Use **getfacl** to see the true permissions.  It is very powerful and a huge pain when ACLs are used.  In 30 yrs as a Unix admin, I've needed to use ACLs less than 5 times, so they are really just a convenience for lazy people who don't/won't layout their directories in a way to avoid them.  OTOH, if the feature exists and it works, why not use it to make life easier?   Assuming it actually does make life easier.  I think that is debatable when it comes to ACLs.

---

### Post by djeyewater on 2024-09-14
Thanks, getfacl shows the same between a file I can't move:
```
# file: storage/share/tmp/move-test/test.zip
# owner: share
# group: share
user::rwx
user:share:rwx
group::rwx
group:share:rwx
mask::rwx
other::r-x
```

And one I can:
```
# file: storage/share/tmp/move-test/test-linux-smb.zip
# owner: share
# group: share
user::rwx
user:share:rwx
group::rwx
group:share:rwx
mask::rwx
other::r-x

```

NTFS is used for a couple of reasons:
[LIST=1]
[*]Disk and data was originally in a Windows machine
[*]AFAIK it is the most compatible journaled file system, so I can pop the disk in a MacOS, Windows, or Linux machine if needs be and have easy access.
[/LIST]
Probably I should change it to ext4 or zfs really, it's just a pain to do so.

---

