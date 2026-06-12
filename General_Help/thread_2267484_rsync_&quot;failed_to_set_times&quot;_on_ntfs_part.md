---
title: "rsync &quot;failed to set times&quot; on ntfs partition"
date: 2015-03-01
forum: General Help
---

### Post by mme oscar on 2015-03-01
Hi everyone,

I'm updating the backup script I've been using for a while in 12.04 for Ubuntu 14.04 (I've been living dangerously in the past few months ;) ). I ran into an error when using rsync with an NTFS partition as destination folder. In order to simplify things I'll explain the problem with only one file and the minimal options to rsync, as this is enough to reproduce the error:

```
rsync -v -t  myfile  /mnt/shared/
```

gives

```
myfile
rsync: failed to set times on "/mnt/shared/.myfile.2kIJ7B": Operation not permitted (1)

sent 90 bytes  received 127 bytes  434.00 bytes/sec
total size is 6  speedup is 0.03
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1183) [sender=3.1.0]


```


[LIST]
[*]The file is actually copied (which means that the write permissions are ok, I guess), but if I run the command again with the file unchanged it is copied again (its time is updated). 
[*]The same command without -t gives no error (but of course I need -t) 
[/LIST]

The partition /mnt/shared, which is NTFS, is mounted automatically. It was also configured automatically by Ubuntu during the first install in /etc/fstab:

```

UUID=7D9A7E49385BFDF9 /mnt/shared     ntfs    defaults,umask=007,gid=46 0       0
```

I didn't modify it and would prefer not to, if possible... but I suspect that there is something wrong with the fact that the mounted filesystem doesn't belong to my user, as ls -l shows:

```

-rwxrwx--- 1 root plugdev 6 Mar  2 01:36 /mnt/shared/myfile
```

Any advice please?

---

### Post by mme oscar on 2015-03-02
Hi everyone,

I did some more testing and found out that this is definitely a problem due to the permissions. 

I tried to change the content of my /etc/fstab for this partition; first I tried only changing the umask to 0000 (all permissions), but it didn't solve anything. Then I removed "umask=007,gid=46", so that the line is now:

```
UUID=7D9A7E49385BFDF9 /mnt/shared     ntfs    defaults 0       0
```

As a consequence the filesystem is still owned by root (same as before) but with group root as well, which is different from before (it was "plugdev", group id 46). *ls -l /mnt/shared/myfile* now gives:

```

-rwxrwxrwx 1 root root 4 Mar  3 00:28 /mnt/shared/myfile

```


More importantly, this way there is no error anymore (and delta sync also works properly). But I'm not entirely satisfied because I don't really understand why it works this way... and it's usually not a good thing to modify some general settings without understanding why ;). So I'm still confused about these two points:

 
[LIST]
[*]first, it seems that there is some kind of special permission which is not read/write/execute but "set the modification time of a file": I would like to know how this works w.r.t standard permissions? Why is there an issue even when all possible standard permissions are set? 
[*]I checked that my user id belongs to the group plugdev, so as far as I understand the original configuration should work: gid was set to 46 which is plugdev, and umask was set to 007 which gives all permissions to all members of this group. What is wrong? And what makes it work when the files are owned by user *and group* root? 
[/LIST]

If anybody has some ideas or pointers about these questions, that would be very helpful!

---

### Post by papibe on 2015-03-02
Hi mme oscar.

NTFS does not support permissions, so it's all a matter of using the proper mount options.

You need to know your uid, and gid. They are usually 1000 both, but it is better to double check by using this command:
```
id
```
Then use those values to set this entry on your fstab:
```
UUID="7D9A7E49385BFDF9"   /mnt/shared     ntfs    uid=1000,gid=1000,umask=077    0       0
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by mme oscar on 2015-03-03
Thank you for your answer, but if possible I would prefer a more generic solution: if the partition is mounted with a specific user id, it means that another user would not be able to use it, right? 

Additionally it is not clear to me why the uid needs to be changed: with proper permissions (I tried with umask=0000) any user is able to read and write anything to the partition, so why is there a problem with setting the modification time of a file?

---

