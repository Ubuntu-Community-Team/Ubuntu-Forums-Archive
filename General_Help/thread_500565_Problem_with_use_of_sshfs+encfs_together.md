---
title: "Problem with use of sshfs+encfs together"
date: 2007-07-14
forum: General Help
---

### Post by dpchemist on 2007-07-14
Hello all,

I have a problem with sshfs+encfs "collaboration". I have a remote host accessible via ssh. I have a test folder on that remote host:

```
ls -lh /storage

drwxrwxrwx   3 remoteuser remoteuser 4.0K 2007-04-23 00:13 test
```

I also have two folder on the local host:

```
ls -lh /media

drwxr-xr-x  1 localuser  localuser     4.0K 2007-07-12 02:06 sshremote
drwxrwx---  1 localuser  localuser     4.0K 2007-04-23 00:13 encfs

```

Than I mount test folder on the remote host to local sshremote folder using sshfs

```
sshfs remoteuser@remotehost:/storage/ /media/sshremote/
```

and then mount encrypted test folder to local encfs folder

```
encfs /media/sshremote/test/ /media/encfs/
```

After that I have

```
drwxrwxrwx  1 localuser  localuser     4.0K 2007-04-23 00:13 sshremote
drwxrwxrwx  2 localuser  localuser     4.0K 2006-10-04 08:14 encfs

```

The problem is that when I try to copy files to encfs folder I get error:

```
cp -v Computers/out.eps /media/encfs/
`Computers/out.eps' -> `/media/encfs/out.eps'
cp: cannot create regular file `/media/encfs/out.eps': Invalid argument

```

I cannot copy or create any file in the "decrypted" encfs directory (which is where encrypted folder mounted). However, I can create a directory there without any problem.

Another thing is that if I mount encrypted folder on the remote host using encfs and then use sshfs to copy files to that "decrypted" directory everything goes well. However, I am not only one user on the remote host.  So I would like to not have "decrypted" files available there. Besides, the weirdness of the situation is just annoying - I should work right, after all!

Both remote and local filesystems are ext3. Local host runs Feisty while remote one runs Dapper.

Any help will be greatly appreciated.

---

### Post by keithweddell on 2007-07-14
I think this is a user/permissions problem.  Try creating a file /etc/fuse.conf which contrains just "user_allow_other" (without " obviously).  Then when you try again, use additional options to sshfs "-0 uid=xxx,gid=xxx".  I know I got this working and I think this is what I needed.


Keith

---

### Post by dpchemist on 2007-07-14
> **keithweddell said:**
> I think this is a user/permissions problem.  Try creating a file /etc/fuse.conf which contains just "user_allow_other" (without " obviously).  Then when you try again, use additional options to sshfs "-0 uid=xxx,gid=xxx".  I know I got this working and I think this is what I needed.

Keith

Thanks for answer. Unfortunately it did not help. As you recommended I made /etc.fuse.conf file with user_allow_other in it and used sshfs -o uid=1000,gid=1000 but I am still getting "Invalid argument" error when I try to copy files there. (with cp Computers/out.eps /media/encfs/)

When I run encfs with -d (debug fuse option) and tried to copy file I got following:
```
unique: 23, opcode: READDIR (28), nodeid: 1, insize: 64
   unique: 23, error: 0 (Success), outsize: 120
unique: 24, opcode: READDIR (28), nodeid: 1, insize: 64
   unique: 24, error: 0 (Success), outsize: 16
unique: 25, opcode: RELEASEDIR (29), nodeid: 1, insize: 64
   unique: 25, error: 0 (Success), outsize: 16
unique: 26, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 26, error: 0 (Success), outsize: 112
unique: 27, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 27, error: 0 (Success), outsize: 112
unique: 28, opcode: OPENDIR (27), nodeid: 1, insize: 48
   unique: 28, error: 0 (Success), outsize: 32
unique: 29, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 29, error: 0 (Success), outsize: 112
unique: 30, opcode: READDIR (28), nodeid: 1, insize: 64
   unique: 30, error: 0 (Success), outsize: 120
unique: 31, opcode: READDIR (28), nodeid: 1, insize: 64
   unique: 31, error: 0 (Success), outsize: 16
unique: 32, opcode: RELEASEDIR (29), nodeid: 1, insize: 64
   unique: 32, error: 0 (Success), outsize: 16
unique: 33, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 33, error: 0 (Success), outsize: 112
[B]unique: 34, opcode: LOOKUP (1), nodeid: 1, insize: 48
LOOKUP /out.eps
   unique: 34, error: -2 (No such file or directory), outsize: 16[/B]
[B]unique: 35, opcode: LOOKUP (1), nodeid: 1, insize: 48
LOOKUP /out.eps
   unique: 35, error: -2 (No such file or directory), outsize: 16[/B]
[B]unique: 36, opcode: CREATE (35), nodeid: 1, insize: 56
   unique: 36, error: -38 (Function not implemented), outsize: 16[/B]
[B]unique: 37, opcode: MKNOD (8), nodeid: 1, insize: 56
MKNOD /out.eps
   unique: 37, error: -22 (Invalid argument), outsize: 16[/B]
unique: 38, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 38, error: 0 (Success), outsize: 112
[B]unique: 39, opcode: LOOKUP (1), nodeid: 1, insize: 48
LOOKUP /out.eps
   unique: 39, error: -2 (No such file or directory), outsize: 16[/B]
[B]unique: 40, opcode: LOOKUP (1), nodeid: 1, insize: 48
LOOKUP /out.eps
   unique: 40, error: -2 (No such file or directory), outsize: 16
unique: 41, opcode: MKNOD (8), nodeid: 1, insize: 56
MKNOD /out.eps
   unique: 41, error: -22 (Invalid argument), outsize: 16[/B]


```

Does anybody know what it means? :confused:

---

### Post by keithweddell on 2007-07-15
I don't know what the debug info means but here are a couple of things to try:

1.  I think you have to be owner of the mount points.  Try mounting to directories within your home directory.  Works for me following your commands.

2.  Have a look at the --public option in the encfs man page. Some of this may apply to your situation.

For the record, I had this working in a script as follows (can't remember why I needed to be root but probably irrelevant here):
```

sshfs user@host:backup /data/backup/remote -C -o uid=$UID,gid=$(id -g)
encfs /data/backup/remote /data/backup/local --extpass=/data/backup/passfile -- -o allow_root
tar czpf /data/backup/local/backup.tgz --exclude-from=/data/backup/exclude.txt --files-from=/data/backup/include.txt

```


Keith

---

### Post by dpchemist on 2007-07-15
Keith, thank you for help. However, it did not work neither. At the same time I found that this behavior is a bug in the Feisty version of encfs. There is already a thread with its discussion:
[http://ubuntuforums.org/showthread.php?t=453110](http://ubuntuforums.org/showthread.php?t=453110)

So, the suggested solution was to compile the latest version of encfs (1.3.2) from the source. I am going to try this.

D.

---

### Post by dpchemist on 2007-07-15
I was not that brave to compile encfs from the source and I just installed debian package (1.3.2-1) instead. And now everything works well. So, apparently, the problem was in not-up-to-date encfs package in Feisty.

---

