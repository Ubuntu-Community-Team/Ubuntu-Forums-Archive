---
title: "All files are executables in NTFS file system"
date: 2013-09-07
forum: General Help
---

### Post by elang on 2013-09-07
I use an Ubuntu 12.04 32b installation.
Most of my data is on an NTFS partition, and it is auto-mounted at startup.

For the longest time, I was not able to execute any linux executables (even gcc compiled programs) on that disk. But, after getting to know that it had something to do with permissions at loading time, I did some googling and changed my fstab entry for that drive to
```

/dev/sda4                                  /media/sda4           ntfs  nls=iso8859-1,users,umask=000,user,uid=1000,gid=1000,dmask=0000,exec     0  0

```
Now I am able to run executables from the NTFS partition, but _**NOW EVERY FILE IS TREATED AS EXECUTABLE**_. 
This is a huge inconvenience, as everytime I open a file, I get a "do you want to display/execute" or similar messages.

My Dropbox folder is on that partition, and for other reasons, I'd like to operate (read code/develop) mainly out of it
Is there a way to run/execute from NTFS and not face the problem of all files being treated as executable?

---

### Post by TheFu on 2013-09-07
Data can be placed on NTFS drives, but building and running programs off NTFS can be a huge security risk.  Developing Linux software without using linux file systems is a losing effort.  File permissions are core to the security of all UNIX systems. 

I'd resize the partitions, make room for a Linux partition and use that if you must use the external drive.  You can also create a tiny script to migrate the files between the disks or partitions and fix the permissions to whatever you like going either way.

BTW, you probably want that last option in the fstab to be a 2, not a 0. [**update**] for portable devices - this is bad advice. My apologies.

I'd be interested if anyone else has a viable option. I've only been a cross-platform developer since 1993.  Of course, I don't point-n-click much while developing either. Learned the old-school way to develop.

---

### Post by elang on 2013-09-08
Yes, there is some security risk involved in developing off NTFS.

But given that people (like me) also use windows, it would be a much less cumbersome task to copy the files onto NTFS at various stages, especially when you code in mutiple languages, and have your work segregated into multiple folders. Is there no workaround?

Also, what does the changing the last entry do?

---

### Post by TheFu on 2013-09-08
> **elang said:**
> Yes, there is some security risk involved in developing off NTFS.

But given that people (like me) also use windows, it would be a much less cumbersome task to copy the files onto NTFS at various stages, especially when you code in mutiple languages, and have your work segregated into multiple folders. Is there no workaround?

Also, what does the changing the last entry do?

There are lots of workarounds ... just that NTFS makes this harder. Why not make it an EXT4 partition, then mount that under Windows? That is a workaround (I've never used it). [http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows](http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows) .

When I was developing cross-platform C/C++ (mixed with other languages like gmake, bison, flex, perl, sql, bash, installshield, IDL, etc... ), all the code was stored on UNIX systems, shared between then using NFS mounts and shared to Windows using samba. Best possible compromise, IMHO.  If you aren't dual booting, this is an option.

Version control was always 1 system, but we migrated from RCS to Visual SourceSafe to StarTeam during that period.  These days, I use **git** regardless of platform. It is a nice bridge between the different platforms.  The entire git repo for all of Linux is not so large, so I cannot imagine that your project(s) would be that large either.

If you cannot use version control in a cross-platform way - and I would really stress that as a mandatory requirement - then just use **rsync** before and after your development cycles. Work on the file system for the OS. I wouldn't fight it.  Seems like a 32G USB3 flash drive ($15) could be partitioned and formatted with both an NTFS and an EXT4 partition. That solves the portability issue, assuming that really is the issue.

Anyway, if you shared which languages and the hardware configs involved, we might be able to help with more tools. One size doesn't fit all and there must be complexities that we don't understand.

```
man fstab
``` will explain better than I can.

---

### Post by grahammechanical on 2013-09-08
> Fsck order is to tell fsck what order to check the file systems, if set to "0" file system is ignored. 

Often a source of confusion, there are only 3 options : 


[LIST]
[*]0 == do not check. 
[*]1 == check this partition first. 
[*]2 == check this partition(s) next 
[/LIST]
In  practice, use "1" for your root partition, / and 2 for the rest. All  partitions marked with a "2" are checked in sequence and you do not need  to specify an order. 

Use "0" to disable checking the file system at boot or for network shares.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Regards.

---

### Post by CatKiller on 2013-09-08
The problem is that NTFS can't handle UNIX permissions, so you can't set executable per-file. As you've found, you have to set it at mount time, and the permissions you set apply to all files. AFAIK there's no way round this if you want to use NTFS; all files are executable or none are.

The dialogue box is a different matter. That's provided by Nautilus and you can tell it to always execute (or never execute) if you wish. I can't remember exactly how at the moment, but it's probably a Nautilus preference or a dconf/gconf key.

---

### Post by TheFu on 2013-09-08
The only workaround that I know is to have another program spawn files that are not executable with permission flags.

For example, running any shell script that is NOT marked as executable is possible by starting "sh" or "bash" and passing in the script.

**$ sh /mnt/ntfs-stuff/some-script**

Don't know if this can work for compiled programs.  I think the first line with the #!/bin/path-to-interpreter  is needed.

Nautilus is just 1 of the file managers. There are others with different options. pcmanfm will let us control program launchers by extension ... if you like. Yuck.  That just "feels" wrong.  Extensions mean nothing to Linux, though some programs can use them, it is purely a program-by-program decision.

---

