---
title: "Drive Permissions problems"
date: 2008-06-16
forum: General Help
---

### Post by JoeDuncan on 2008-06-16
Here's my problem:

I have a dual-boot laptop running Kubuntu 8.04, with a shared FAT32 partition that I use to share data between Windows and Linux. I also have an external USB hard-drive that I use for backups, shared files between computers (home desktop, work desktop).

I am trying to check-out data from a subversion server to a directory on the FAT32 partition, using an SSH key residing on the USB hard-drive.

This gives me two problems.

Number one, when I try to use the SSH key it says:

```

Permissions 0755 for '<yourkey>' are too open.
It is recommended that your private key files are NOT accessible by others.
This private key will be ignored.

```

I can fix this, by manually using "chmod" every time the drive is mounted, but I would rather automatically set the drive permissions when the drive is hotplugged, but I don't know how this system works in Ubuntu. There's no entries for the drive in /etc/fstab. When I plug in the drive, a a dialog box pops up and I select "Open in a window". The drive gets mounted in /media/disk. So how do I make sure it gets mounted with 700 permissions only for the current user?

My second problem is that when I try to check out files to the FAT32 partition I get this:

```

Execute: Checkout
Error: Error while performing action: Can't check path '<checkoutpath>': Permission denied

```

This is the fstab entry for the drive:

```

UUID=XXXX-XXXX       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       0

```

The directory is owned by root.plugdev, and I can read and write to it normally. Now, I can use uid=XXXX to set the ownership of the drive to my user, but I would rather have the drive ownership automatically set to whatever user logs in, but I am unsure how to accomplish this either.

If anyone knows how to fix these problems, please let me know.

Thanks!

---

### Post by diaa on 2008-06-26
> **JoeDuncan said:**
> 
 ```

 Execute: Checkout
 Error: Error while performing action: Can't check path '<checkoutpath>': Permission denied
 
```This is the fstab entry for the drive:
 
 ```

 UUID=XXXX-XXXX       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       0
 
```The directory is owned by root.plugdev, and I can read and write to it normally. Now, I can use uid=XXXX to set the ownership of the drive to my user, but I would rather have the drive ownership automatically set to whatever user logs in, but I am unsure how to accomplish this either.
 
 If anyone knows how to fix these problems, please let me know.
 
 Thanks!
 
 I had the same problem, but with NTFS, I get the message
 ```

 svn: Can't set permissions on 'directory_name/.svn/entries.2.tmp': Operation not permitted
 
``` actually I thought it was a bug in subversion but only now I realized it's the permissions problem, since I don't own the file, I can't change its permissions and that's the problem with svn, when I used uid=1000 in fstab it worked properly.
 so I have two solution for this problem:

[LIST=1]
[*]Use the *user* option for this partition in fstab, so it can be mounted by any user and tell KDE to mount it automatically as a user on startup
For the reference, note that this solution doesn't work with NTFS because of the way NTFS-3g works, or in other words it works but it's cumbersome and unsecure, see [http://ntfs-3g.org/support.html#useroption](http://ntfs-3g.org/support.html#useroption)
[*]use sudo when doing svn co, this is a workaround but it works flawlessly, svn is smart enough to set proper permissions on the file so it doesn't need anything special(I thought you'll have to chmod the files after the svn co so you can read/write them)
[/LIST]

---

