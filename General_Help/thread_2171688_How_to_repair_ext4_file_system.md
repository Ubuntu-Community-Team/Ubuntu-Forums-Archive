---
title: "How to repair ext4 file system?"
date: 2013-09-01
forum: General Help
---

### Post by peter1897 on 2013-09-01
I used a program that had to fix partition table errors but it actually messed up and deleted some of the partitions and i had to use partition recovery software to recover the partitions but some partition were recovered with errors. I fixed ntfs partitions using chkdsk /f command, but I have two ext4 partitions, one with Ubuntu installed and on Linux Swap, which i don't know how to fix.

[ATTACH=CONFIG]245887[/ATTACH]


What command or what program can i use to fix them?

---

### Post by TheFu on 2013-09-01
Linux swap doesnt' need fixing. It doesn't hold anything when the system isn't running or in standby. If the swap is complaining - and I've never seen that in 20+ yrs - delete the partition, then add it back using **gparted** or **parted**. fdisk may or may not be safe, best to avoid it.

For ext-whatever, use **fsck**.  If the problem file system is /, then you'll want to force the fsck at the next reboot (sudo touch /forcefsck) ... or do it from a liveCD or live-Flash boot instead.

Other options for fsck can be learned in the man page - **man fsck**.

---

### Post by deadflowr on 2013-09-01
Linux swap has it's own file type (linux-swap) which differs from ext4 or other file types.

Running fsck should help fix the ext4 problems.

Also, what partition fixer program did you run?

It might help us to understand where the problem originated from.

---

### Post by SeijiSensei on 2013-09-01
Actually swap isn't a filesystem, it's just a binary blob.  The standard way to create swap is to use

```
dd if=/dev/zero of=/path/to/swap
```

which just fills the file or partition with zeroes.  Swap doesn't have any of the standard features of a POSIX file system like ext4 with directories, permissions, dates, etc.

However there is a partition type called "Linux swap" (type 82) which is created during the disk partitioning.

---

### Post by peter1897 on 2013-09-02
I recreated the linux swap partition with GParted but for Ubuntu partition what exactly command to use? If i use **sudo fsck dev/sda6** nothing happens.

I used Partition Wizard to recover the deleted partition. They were not actually deleted but partition table was corrupted.

---

### Post by TheFu on 2013-09-02
You cannot run fsck on a mounted partition. #2 explains how to do it for the root partition (/).
Or just boot from a liveCD and run it against the ext4 partitions on the HDD.

BTW, ```

sudo fsck dev/sda6
```
is wrong.
```
sudo fsck /dev/sda6
```
is probably what you wanted.  Computers only do what we tell them to do.
Also, I don't know of sda6 is the correct partition. Didn't look back through this thread.

---

### Post by peter1897 on 2013-09-02
I didn't run the command on mounted partition, i run it from Ubuntu live cd and it didn't work. Than i run the same command **sudo fsck /dev/sda6** from Parted Magic terminal and it worked, fixed the errors. I don't know why it didn't work form Ubuntu live cd.

---

### Post by TheFu on 2013-09-02
> **peter1897 said:**
> I didn't run the command on mounted partition, i run it from Ubuntu live cd and it didn't work. Than i run the same command **sudo fsck /dev/sda6** from Parted Magic terminal and it worked, fixed the errors. I don't know why it didn't work form Ubuntu live cd.

Happy it is fixed now.  Was there a "command not found" error?
From the liveCD, perhaps the PATH wasn't set to include the fsck program? When that happens, just point to the full path of the program /sbin/fsck.  /sbin is usually not included in the PATH for most users. That directory contains system admin programs, not programs for average users.

---

### Post by peter1897 on 2013-09-02
There was not "command not found" error but if i tried to close the terminal it showed message that there are still operations running even so the terminal window didn't show any activity.

---

### Post by TheFu on 2013-09-02
If you append the '&' character in any command, it goes to the background.  
If you press <cnt>-z, that will stop a job.
If you spawn a GUI program from the terminal, the same things apply.

The command not found was probably why the liveCD didn't work - wrong path. A different - save-your-butt distro probably adds /sbin/ to the PATH, since we don't use those distros unless we need the admin tools.

These are all guesses ... when you learn more about Linux and the shell, you'll understand better. Plus, I could be wrong. ;)

---

