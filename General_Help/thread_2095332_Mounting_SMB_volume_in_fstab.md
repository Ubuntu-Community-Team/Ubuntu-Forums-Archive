---
title: "Mounting SMB volume in fstab"
date: 2012-12-16
forum: General Help
---

### Post by TMSpack on 2012-12-16
I am trying to mount a WD MyBook World drive on my Ubuntu 12.04 machine.  I want it mounted permanently, so I put the following line in my fstab file.

[I]192.168.1.2:/Public /mnt/Public smbfs guest,username=admin,password=admin 
[/I]
That works, but the drive mounts as read only.  I also tried

*192.168.1.2:/Public /mnt/Public smbfs rw,username=admin,password=admin* 

with the same result.

Okay - So I'm still a newb, but what am I missing?

Thanks for the help!

---

### Post by Cheesemill on 2012-12-16
What are the permissions on the mount point?
```
ls -l /mnt/Public
```

---

### Post by TMSpack on 2012-12-16
Thanks, Cheese!
Here is the output:

[I]tom@Red:/mnt$ ls -l /mnt/Public
total 47632
-rw-rw-r--  1   99  99       14 Oct 27 22:54 end
drwxrwxr-x  4   99  99        0 Aug 23  2009 Eric
drwxrwxr-x 15   99  99        0 Apr  2  2012 FinancialRecords
drwxrwxr-x 10   99  99        0 Nov 12  2011 Home Movies
-rw-rw-r--  1   99  99   620974 May 29  2009 IMG00084-20090522-1604.jpg
drwxrwxr-x  2   99  99        0 May 29  2011 Julie
drwxrwxr-x  2   99  99        0 Aug 19  2011 Laurie
-rw-rw-r--  1   98 tom  4417624 Oct 27 22:51 Mt_More_1x01.part2.rar_downloader.exe
-rw-rw-r--  1   99  99  7449995 Apr 26  2009 MyBookWorldManual.pdf
drwxrwxr-x  3   99  99        0 Aug 25  2009 My WD_Backup
drwxrwxr-x  3  501 tom        0 Feb 26  2010 Network Trash Folder
drwxrwxr-x  9   99  99        0 Feb 28  2012 Old Stuff
-rw-rw-r--  1   98 tom     6144 May 28  2011 photothumb.db
drwxrwxr-x  2   98 tom        0 Jan 25  2012 public
-rw-rw-r--  1   99  99      299 Apr 30  2012 Recovery (D) - Shortcut.lnk
drwxrwxr-x  2   98 tom        0 Oct  7 22:47 Shared Documents
drwxrwxr-x  6 root tom        0 May  5  2012 Shared Music
drwxrwxr-x 27 root tom        0 Nov 13 11:29 Shared Pictures
drwxrwxr-x  5 root tom        0 Oct 27 23:29 Shared Videos
drwxrwxr-x  3  501 tom        0 Feb 26  2012 Temporary Items
drwxrwxr-x  3   99  99        0 Oct 22 20:51 TiVo Recordings
drwxrwxr-x  6   99  99        0 Oct 29 22:00 Tom
drwxrwxr-x  5   99  99        0 Aug 14  2010 TomLauriePC
drwxrwxr-x  2   98 tom        0 Feb  3  2012 video
drwxrwxr-x  2   99  99        0 Jul 22  2011 Virus Removal Tool
-rw-rw-r--  1   99  99 36207128 Apr 10  2011 WG111v3_v2.0.0_Setup.exe
[/I]

---

### Post by TMSpack on 2012-12-18
Okay - So I can see that I don't have write permissions in the above listing.  I could probably change that, but I don't want to change it every time I mount the drive.  When I connect to this drive using windows machines, I have no permissions issues.  Any thoughts?

---

### Post by TMSpack on 2012-12-18
I found a workaround!

I noticed that most files and directories, if not owned by me (tom), were owned by 99.  The group is also 99.  Not sure why - Must be a Western Digital thing.  Anyway, I didn't have a GID 99, so I created a group for shareusers, gave it GID 99.  I added myself to the group, and now I have write access.

Thanks for your help, and I hope this helps somebody else!

---

### Post by JKyleOKC on 2012-12-18
In your fstab entry, you told the system to mount the drive with username "admin" and, as it happens, *buntu already has a system group named "admin" and it's apparently interpreted as UID=99 on your system (on mine, the UID is 118). In all versions of *buntu, UIDs below 1000 are "system users" and normally have greatly restricted capabilities.

You could change that username in /etc/fstab to be your own user name, if you are the only one needing access. Lots of other options exist, also, if you need more general access to the drive...

EDIT: The permissions are set up by the fstab entry, not on the drive itself. And normally, the "ls" comment will translate the UID and GID numeric values that actually identify ownership into User and Group names for display. The fact that it failed to translate "99" indicates that no such user or group existed; perhaps your fstab option isn't doing what you intend.

---

