---
title: "ecryptfs doubling disk usage causing low disk space errors"
date: 2016-04-15
forum: General Help
---

### Post by DanglingPointer on 2016-04-15
I'm needing assistance on how to solve a bizarre disk usage problem.
I have an encrypted home folder and when I go into it, it shows my home folder name (decrypted files) and the ecryptfs folder which I assume is the real location of all my encrypted files.
thus...
[LIST=1]
[*]/home/danglingpointer/ 
[*]/home/.encryptfs/ 
[/LIST]

With the assumption that 1 is virtual and 2 the real files.
The problem is Ubuntu 14.04.4 is adding both and popping up a warning of low disk space!  System Monitor window shows the file system as full same as "df -h" and "ncdu /home".  
baobab the disk usage analyser application reports the size correctly, but that's it!  I can't for example copy a 13GB file from another mounted partition to my home because it says there is no disk space!
I'm hoping others have come across this issue and can resolve it because I would hate having to reinstall!

output of ncdu:
```
--- /home ----------------------------------------------------------------------
. 105.8GiB [##########] /.ecryptfs                                              
. 105.8GiB [######### ] /danglingpointer

```

If you add both sizes above, it equals the size of sde2 and .Private underneath.

output of df -h
```
$ df -h
Filesystem                                                                                Size  Used Avail Use% Mounted on
udev                                                                                      7.9G  4.0K  7.9G   1% /dev
tmpfs                                                                                     1.6G  1.3M  1.6G   1% /run
/dev/sde2                                                                                 222G  209G  1.5G 100% /
/home/danglingpointer/.Private                                                            222G  209G  1.5G 100% /home/danglingpointer
```

Does anyone have any idea how to fix this.  I should have half the space free or close to it!

---

### Post by DanglingPointer on 2016-04-15
12hr bump

---

### Post by DanglingPointer on 2016-04-17
So I'm guessing no one here has sorted this in the past?

From my perspective I think the only way I can bake my cake and eat it as well would be to re-install ubuntu on a fully encrypted partition instead of just encrypting /home.

All I can say is what a bloody hassle! I reckon this should be flagged as a design bug! Why provide the option to encrypt your home directory if it will take twice the amount of space (it appears as twice to system monitor, nautilus, and nemo. And copying errors out if they reckon there isn't enough space!).

I would really appreciate if anyone has insight into this which could fix the reported space without having to re-install to a fully encrypted partition.

---

### Post by DanglingPointer on 2016-04-23
Ok all fixed now.

For those with a similar problem this is how I fixed it...

1) Backup your entire home and preserve permissions.  Make sure to copy links as links and not their targets.  Easiest way to do this is to download Grsync and rsync your home to a path outside your home.
2) Create a new Administrator Temp account from System Settings>>User Accounts.
3) Logout of your account and login to the new Admin Temp account.
4) Delete the old account from System Settings>>User Accounts.  Ensure to delete all file as well.  Leave nothing behind!
5) Go to the backup location and delete the folders .ecryptfs and .Private.
6) Create a new Admin account with the exact same name as the old one.
7) Encrypt the Home of that account. Using eccryptfs-migrate-home command.
```
sudo ecryptfs-migrate-home -u user
```
8) Once done with the migration, logout of the Admin Temp account and login to the newly created (and encrypted) account .
9) Use Grsync to rsync the backup you did at point 1 to the home directory.
10) For stability's sake restart the desktop.
11) Once you're satisfied the space has been recovered and everything is stable, you can clean up the backup and delete the Admin Temp account.

That's pretty much how I fixed it without having to go through a costly reinstall!

I hope that helps others who may have encountered the same problem.

---

