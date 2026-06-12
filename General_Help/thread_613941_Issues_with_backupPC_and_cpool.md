---
title: "Issues with backupPC and cpool"
date: 2007-11-15
forum: General Help
---

### Post by shockwaver on 2007-11-15
Ok, I installed backupPC to backup my ubuntu 7.10 /home directory, as well as my wifes Windows PC. Using the CGI I changed the $TopDir to /media/backups/ instead of the /var/lib/backuppc. If I run a backup, it works however I get massive amounts of linking errors. Both of the -4 and the -3 variety. I believe I've narrowed it down to it's trying to hard link to /var/lib/backuppc/cpool but that is on a different volume, hence the failure. How do I get it to point to /media/backuppc/cpool? I tried copying /var/lib/backuppc/cpool to /media/backups, and putting a symlink in to /var/lib/backuppc:

```
root@ubuShock:/var/lib/backuppc# ls -ls
total 16
0 lrwxrwxrwx  1 root     root       21 2007-11-15 12:29 cpool -> /media/backups/cpool//
4 drwxr-x---  2 backuppc backuppc 4096 2007-11-15 06:38 log/
4 drwxr-x---  3 backuppc backuppc 4096 2007-11-10 17:46 pc/
4 drwxr-x--- 18 backuppc backuppc 4096 2007-11-10 18:00 pool/
4 drwxr-x---  2 backuppc backuppc 4096 2007-09-04 06:42 trash/
root@ubuShock:/var/lib/backuppc# cd /media/backups/cpool/

```
But, to no avail. Any help would be greatly appreciated.

Oh, my log files are filled with this:
```
root@ubuShock:/var/lib/backuppc/log# tail LOG
2007-11-15 12:33:34 BackupPC_link got error -4 when calling MakeFileLink(/media/backups//pc/ubushock/7/f%2fhome%2fchris%2f/fvmware/fWindows XP Professional/attrib, ec22f2b915822cdc61638733cf5e8619, 1)
2007-11-15 12:33:34 BackupPC_link got error -4 when calling MakeFileLink(/media/backups//pc/ubushock/7/f%2fhome%2fchris%2f/fwebip.out, 20254549cbce12747baa618ad83a7cd8, 1)
2007-11-15 12:33:34 BackupPC_link got error -4 when calling MakeFileLink(/media/backups//pc/ubushock/7/f%2fhome%2fchris%2f/attrib, c94d15bbe57365ea9954d101601393c5, 1)
2007-11-15 12:33:34 BackupPC_link got error -4 when calling MakeFileLink(/media/backups//pc/ubushock/7/attrib, 635c1d8e80ca624fd6ef3e6ce9db902f, 1)
```

***EDIT: Resolved. Ahem. At least I think it is. I linked /var/lib/backuppc/pool to /media/backups/pool and ran an incremental backup, with no massive e***rrors.

---

### Post by jonkjon1959 on 2008-01-27
I am about to do the same thing here but i do have a question about the pool data. Since you are  using a soft link to the pool directory which is still on the drive that is being backed up, i see how backuppc can access the pool data during the backup. But, what about during a restore if the original drive dies? Is the pool data only needed to do backups and not restores? 
BTW.....thanks for posting this. I have searched and searched for an answer to this but your post may have been, by far, the most useful.

---

