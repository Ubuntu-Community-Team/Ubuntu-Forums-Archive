---
title: "Zero disk space on Root with space there!"
date: 2017-09-18
forum: General Help
---

### Post by rwlloyd69 on 2017-09-18
Hello!

I got a message that my root filesystem was low on space, so I moved some stuff off to another drive and rebooted.  Now the Unity Toolbar and top bar does not come up, only my Desktop Icons and my VM manager window. Also, 'df' shows that I have 217GB on that partition, 213GB used, and 0 free.

I've booted on a live USB and ran fsck & e2fsck on the partition.

---

### Post by ian-weisser on 2017-09-18
What is filling all that space? There are [several easy ways]("https://superuser.com/questions/529797/how-to-find-out-the-top-space-consuming-directories-or-files") to find out.

---

### Post by Bashing-om on 2017-09-18
rwlloyd69; Hello, Welcome to the forum .

/boot partition with old kernels ?
what results:
```

sudo apt autoremove

```
that not only removes orphaned files but also old kernels ( if the system has the operating head room ) .

. Now if you desire that the system take case of these little details, well it can of you enable it in "unattended-upgrades". However, that is the subject of another thread .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by rwlloyd69 on 2017-09-18
There is 4GB+ available on  the drive already, but I still get the no space errors.  No matter how much stuff I move, it says there's no space - but df says I have 213GB of 217GB free.

> **Bashing-om said:**
> 

```

sudo apt autoremove

```


Nothing done, nothing to do. All upgraded, all purged.

Thanks for the welcome, folks... sorry if I seem a bit "focused" at the moment... this is my primary PC that's down, and it is quite frustrating, to say the least!

---

### Post by Bashing-om on 2017-09-18
rwlloyd69; Well !

Then do as Ian advises ^^ .
Our telepathy powers are weak, and we can not see your terminal . You must provide - between code tags - what you see in your terminal.
With out seeing those errors and warning - in context - we do not have the information to work to a solution.

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]'buntu
[INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by rwlloyd69 on 2017-09-18
Hello all!

I have made space on the device, that isn't the issue:

```

robert@rwlquad:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  9.9M  1.6G   1% /run
/dev/sda3       217G  213G     0 100% /
tmpfs           7.8G  252K  7.8G   1% /dev/shm
tmpfs           5.0M  8.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/sdb1       466G  433G   34G  93% /media/Projects
/dev/sdc1       1.9T  1.6T  283G  85% /media/MediaShare
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           1.6G   36K  1.6G   1% /run/user/1000

```

As you can see, this shows around 4GB free on root, but 0 available.  I deleted / moved stuff to make that 4GB, but the "Avail" remains at 0.  I can't even copy a 20-byte text file onto this device.

I really appreciate the help, folks... this is a bit of a priority for me.

-Robert

---

### Post by rwlloyd69 on 2017-09-18
Hello all!

For more info, I was able to create a 0-byte file, but not add a byte to it:

```

robert@rwlquad:~$ touch test.txt
robert@rwlquad:~$ ls test.txt
test.txt
robert@rwlquad:~$ ls -l test.txt
-rw-rw-r-- 1 robert robert 0 Sep 18 11:24 test.txt
robert@rwlquad:~$ echo "X">test.txt
-bash: echo: write error: No space left on device

```

If I move or delete more info from this drive, I will still get the same error.

---

### Post by rwlloyd69 on 2017-09-18
Hello All!

Okay, guys, you were right and I was wrong.  (bows head in shame)  I cleared off what I thought was plenty of space, but once Ubuntu hits the wall, it needs to see more than 5% free - so when I moved a VM disk file off, it worked great.  Thanks for all your help, folks!

-Robert

---

### Post by Bashing-om on 2017-09-18
rwlloyd69; Great !

Glad you got your head wrapped around it .
(operating head room )

If this matter is now concluded:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

