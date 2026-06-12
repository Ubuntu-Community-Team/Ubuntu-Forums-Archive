---
title: "umount Confussion"
date: 2021-11-27
forum: General Help
---

### Post by Quarkrad on 2021-11-27
I have a 20.04 mate system where with **dad ALL=(ALL) NOPASSWD: /usr/bin/mount, /usr/bin/umount** in /etc/sudoers.d/config I can successfully unmount a partition/device with the command **sudo /usr/bin/umount /media/dad/backup**.    On a different 20.04 system everything is set up the same, apart from the username, I consistently get:

```
sudo /usr/bin/umount /media/username/backup
sudo: /usr/bin/umount: command not found
```

But if I type: sudo /bin/umount /media/username/back it works OK.  Problem is when  change the sudoers.d/config file everything gets messed/doesn't work.  Should the mount/umount executable be in /usr/bin/?

---

### Post by Quarkrad on 2021-11-27
Same if I type sudo /usr/bin/mount      I get sudo: /usr/bin/mount: command not found

---

### Post by Quarkrad on 2021-11-27
Hmm on my system there is a mount and umount file in /usr/bin/  which makes sense.  On this new system (upgraded from 18.04 to 20.04 today) these two files are not in /usr/bin - they are in /bin/  again this makes sense in terms of what is happening.  Should they be in /usr/bin/ and how do I move them?

---

### Post by Quarkrad on 2021-11-27
Made soft links of the files between /bin/ and /usr/bin/  - appears to work.  Is this OK?

---

### Post by SeijiSensei on 2021-11-27
Usually mount/umount are found in /bin since they are both used while the machine is still running in single-user mode.  Traditionally the /usr file system was only mounted after the machine went multi-user so many standard utilities needed to be available to the root user in /bin. I don't know whether that's still the case in modern implementations.

On my 21.04 machine the file /bin/umount and /usr/bin/umount are hard linked to the same inode.
```

$ ls -i /bin/umount /usr/bin/umount
264732 /bin/umount  264732 /usr/bin/umount

```
where 264732 is the number of the inode where the data are stored.  In this case the entries are identical.

So  if you want to replicate the configuration of a stock Ubuntu machine, then you should probably use a hard link instead. In practice I doubt using symlinks matters an iota. [https://www.redhat.com/sysadmin/linking-linux-explained](https://www.redhat.com/sysadmin/linking-linux-explained) is pretty good.

---

### Post by Impavidus on 2021-11-28
/usr is traditionally allowed to be on a separate partition. To mount that partition, you need the mount command, which is unavailable if it's on the still unmounted /usr partition. Therefore, mount was put in /bin, not /usr/bin. Nowadays, I think starting from Ubuntu 21.04, /bin is normally a symlink to /usr/bin (and similar for /sbin and /lib*), so it's all conveniently in one directory (I'm not sure what's so inconvenient about the old way), but this no longer allows a separate /usr partition (nobody used those anymore). It's triggered by the usrmerge package, so you can prevent this merge by preventing installation of the usrmerge package. There's no automatic undo; removing usrmerge doesn't cleanly undo the merge.

---

### Post by ActionParsnip on 2021-11-28
If you run:
```

which mount
which umount

```
You will see where the files are. I suspect that you guessed the location and weren't accurate

---

### Post by TheFu on 2021-11-28
Always make a script. You can make it a toggle.

```
MOUNT="$(which mount || echo '/usr/bin/mount')"
```
That way, if the PATH isn't reasonable, we get the specific location.  Wouldn't hurt to test that $MOUNT exists and try a different location or error out too.

Do the same for umount.

Of course, you could just setup **autofs** and this stuff is solved already.

---

### Post by SeijiSensei on 2021-11-29
> **Impavidus said:**
> /Nowadays, I think starting from Ubuntu 21.04, /bin is normally a symlink to /usr/bin (and similar for /sbin and /lib*), so it's all conveniently in one directory (I'm not sure what's so inconvenient about the old way), but this no longer allows a separate /usr partition (nobody used those anymore).
Actually, as I said, on my 21.04 machine the entries in /bin and /usr/bin are both hard links, not symbolic links.

---

