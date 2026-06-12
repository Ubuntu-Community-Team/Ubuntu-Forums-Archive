---
title: "Unexpected error message from crontab execution of executable script"
date: 2021-03-08
forum: General Help
---

### Post by Old Jimma on 2021-03-08
Hi Community:

I have a laptop and want to back up my home directory weekly.

I have a **3Tb external mechanical HD** that I put in a HD encllosure that is connected to my laptop via a SATA 3 USB port.

I used the "Disks" app to mount the 3 TB HD to mount it on system start up.

The mount point is:** /mnt/sdb1** and the drive is identified as **/dev/sdb1**

At 1am every Monday crontab is instructed to execute an executable script  that starts with the code:
> 

testfile="/mnt/sdb1"
if [ -e "$testfile" ]
then
  echo "drive is mounted."

  # code to do the back up goes here

else
	echo "No sdb1 mounted"
	date

fi



Output from crontab's execution of this script is directed to a file... that gives the error code



> /bin/sh: 1: /home/mynames/path/backup_sdb1.sh: Permission denied

this seems to indicate that there is something about the mount point or the name of the mount point that is wrong.

Could you suggest what I might do to correct this?

THanks,
Old Jimma

---

### Post by Old Jimma on 2021-03-08
/etc/fstab looks like this:

> /dev/sdb1 /mnt/sdb1 auto nosuid,nodev,nofail,x-gvfs-name=WD%203TB,x-gvfs-icon=WD%203TB,x-gvfs-symbolic-icon=WD%203TB 0 0

---

### Post by Bashing-om on 2021-03-08
Old Jimma - Hello

> 
Permission denied

Begs the question from where ?
what shows - with sdb1 mounted -
```

ls -al /mnt/
ls -al /mnt/sdb1

```

and who owns the file ?
```

ls -al /home/mynames/path/backup_sdb1.sh

```

All instances with the same ownership ?

[INDENT]If "you" do not own it
[INDENT][INDENT]you do not access
[/INDENT][/INDENT][/INDENT]

---

### Post by Old Jimma on 2021-03-08
Thank you for your reply, Bashin-om:

Looks like "mynames" owns everything here is the output:

> 
mynames$ [COLOR="#FF0000"]**ls -al /mnt/**[/COLOR]
total 16
drwxr-xr-x  4 root         root         4096 Mar  4 08:15 .
drwxr-xr-x 21 root         root         4096 Mar  1 06:03 ..
drwxrwxrwx  3 mynames mynames 4096 Mar  8 00:23 sda1
drwxrwxrwx  6 mynames mynames 4096 Mar  8 16:57 sdb1


mynames$ [COLOR="#FF0000"]**ls -al /mnt/sdb1**[/COLOR]
total 24
drwxrwxrwx  6 mynames mynames 4096 Mar  8 16:57 .
drwxr-xr-x  4 root         root         4096 Mar  4 08:15 ..
drwxrwxrwx 22 mynames mynames 4096 Feb 28 06:43 mynames-21-03-04
drwxrwxrwx 22 mynames mynames 4096 Feb 28 06:43 mynames-21-03-08
drwxrwxrwx 49 mynames mynames 4096 Nov 21 06:54 mynames-20-11-22
drwxrwxrwx 24 mynames mynames 4096 Jan 29 07:28 mynames-21-02-01
mynames$ ls -al /home/mynames/path/backup_sdb1.sh
ls: cannot access '/home/mynames/path/backup_sdb1.sh': No such file or directory


mynames$ [COLOR="#FF0000"]**ls -al /home/mynames/path/backup_sdb1.sh**[/COLOR]
-rw-rw-r-- 1 mynames mynames 486 Mar  8 18:47 /home/mynames/Documents/path/backup_sdb1.sh
mynames$ 





Bashin-on: I wondered about 3 things:

1. crontab runs like a background sudo job, right? Is there something missign that sudo needs that I'm not providing.

2. Note that the mount point is [COLOR="#FF0000"]/mnt/sdb1[/COLOR] and the Disks app has the "identify as" being [COLOR="#FF0000"]/dev/sdb1[/COLOR]. Does this difference matter?

3. ftab looks like this

> /dev/sdb1 /mnt/sdb1 auto nosuid,nodev,nofail,x-gvfs-name=WD%203TB,x-gvfs-icon=WD%203TB,x-gvfs-symbolic-icon=WD%203TB 0 0


Does this look ok?

Thanks,
Old Jimma

---

### Post by Old Jimma on 2021-03-08
Bashing-on:

I just noticed that backup_sdb1.sh does not have executable priveleges.

When I changed that to allow it to be executable, it worked.

THanks.

Old

---

### Post by Bashing-om on 2021-03-08
Old Jimma

Yay !

You done good work.

[INDENT]had to be a reason
[/INDENT]

---

### Post by Old Jimma on 2021-03-09
I used to know how to program with unix commands 35 years ago. With a linux comuter, it'd be nice to dust off my old skills. THere are alot of things that can be done under the hood to make everything work better exactly the way I'd like!

Old Jimma from the Old Country

---

