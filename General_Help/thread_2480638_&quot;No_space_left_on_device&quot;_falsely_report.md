---
title: "&quot;No space left on device&quot; falsely reported by systemd. Inotify out of resources"
date: 2022-11-04
forum: General Help
---

### Post by John Nagle on 2022-11-04
Program (a Rust compile) aborted, and the terminal window closed. Checked syslog:

Errors in syslog:

Nov  4 11:35:50 Nagle-LTS systemd[2249]: app-gnome-synaptic-4759.scope: Failed to add control inotify watch descriptor for control group /user.slice/user-1000.slice/user@1000.service/app.slice/app-gnome-synaptic-4759.scope: No space left on device
Nov  4 11:35:50 Nagle-LTS systemd[2249]: app-gnome-synaptic-4759.scope: Failed to add memory inotify watch descriptor for control group /user.slice/user-1000.slice/user@1000.service/app.slice/app-gnome-synaptic-4759.scope: No space left on device
Nov  4 11:49:15 Nagle-LTS systemd[2249]: tracker-extract-3.service: Failed to add control inotify watch descriptor for control group /user.slice/user-1000.slice/user@1000.service/background.slice/tracker-extract-3.service: No space left on device


But no file system is out of space. Not even close. Checked inodes, too.

```
$ df
Filesystem                  1K-blocks      Used Available Use% Mounted on
tmpfs                          807844      3728    804116   1% /run
/dev/mapper/ubuntu--vg-root 952021260 747701544 155933056  83% /
tmpfs                         4039212         0   4039212   0% /dev/shm
tmpfs                            5120         4      5116   1% /run/lock
/dev/sda2                      481642    176833    279824  39% /boot
/dev/sda1                      523248      5364    517884   2% /boot/efi
tmpfs                          807840       156    807684   1% /run/user/1000


$ df -i
Filesystem                    Inodes   IUsed    IFree IUse% Mounted on
tmpfs                        1009803    1518  1008285    1% /run
/dev/mapper/ubuntu--vg-root 60465152 5725930 54739222   10% /
tmpfs                        1009803       1  1009802    1% /dev/shm
tmpfs                        1009803       5  1009798    1% /run/lock
/dev/sda2                     124928     317   124611    1% /boot
/dev/sda1                          0       0        0     - /boot/efi
tmpfs                         201960     185   201775    1% /run/user/1000

```

When I run "tail -f" on syslog, I get

```
tail: inotify resources exhausted
tail: inotify cannot be used, reverting to polling

```

This is new. This machine has been running Ubuntu for years, and has been on Ubuntu 22.04 LTS for months.

---

### Post by John Nagle on 2022-11-04
Still getting those messages after a reboot.

Checking obvious stuff: 

* Synaptic package manager says 0 packages broken.
* Other programs now running OK.

The errors above happened right after some snaps were remotely updated in background.

---

### Post by TheFu on 2022-11-04
I haven't a clue, but .... 
Have you checked pseudo-file systems for resources?
Do any processes have too many files open, running up against that limit?
What do all the log files show? Any errors or warnings in those?  It is often easiest to use journalctl to search logs based on a specific time of the error.  I'm not really a fan of systemd, but journalclt is amazing.

---

### Post by John Nagle on 2022-11-05
Found out what's happening. IDrive for Linux, the commercial backup software, is causing this.

More info. If inotify runs out of resources, it sets the error code ENOSPC. Ref: [https://man7.org/linux/man-pages/man2/inotify_add_watch.2.html](https://man7.org/linux/man-pages/man2/inotify_add_watch.2.html)
which says "**ENOSPC **The user limit on the total number of inotify watches was reached or the kernel failed to allocate a needed resource."
That error code is usually translated into "No space left on device". So this probably has nothing to do with file systems.

The failure of "tail" indicates that the system ran out of inotify watches.

Sysctl says:

    user.max_inotify_instances = 128
    user.max_inotify_watches = 65536

which is standard. So that's what we have available.

IDrive, the commercial backup program, is using all the inotify resources for what it calls "Continuous Data Protection"
 It's apparently trying to watch every file for changes, apparently, which is insane.

Here's some useful background from 11 years ago:

[https://unix.stackexchange.com/questions/15509/whos-consuming-my-inotify-resources](https://unix.stackexchange.com/questions/15509/whos-consuming-my-inotify-resources)

That suggests building and using a special tool, inotify-info, to read and sort inotify uses. That produces:

~/projects/inotify-info$ make
Using gold linker...
Building _release/inotify-info...
---- inotify-info.cpp ----
---- lfqueue/lfqueue.c ----
Linking _release/inotify-info...
john@Nagle-LTS:~/projects/inotify-info$ ls
images          inotify-info.h  LICENSE   README.md
inotify-info.cpp  lfqueue      Makefile  _release
john@Nagle-LTS:~/projects/inotify-info$ ls _release
inotify-info  inotify-info.d  inotify-info.dwo    inotify-info.o    lfqueue
john@Nagle-LTS:~/projects/inotify-info$ _release/inotify-info
------------------------------------------------------------------------------
INotify Limits:
  max_queued_events    16384
  max_user_instances   128
  max_user_watches     65536
------------------------------------------------------------------------------
     Pid  App                        Watches   Instances
     2518 perl                           64933   1
     2249 systemd                        121   5
     3604 xdg-desktop-portal-gnome        98   1
     3166 gsd-xsettings                   87   1
     3629 xdg-desktop-portal-gtk          86   1
...

So, process 2518 is causing the problem. What is it?

    ps -f --pid 2518
    UID          PID    PPID  C STIME TTY          TIME CMD
    john        2518       1  0 11:30 ?        00:00:10 IDrive:CDP-client

So, IDrive:CDP-client is using all the inotify resources. It's not even supposed to be running.
IDrive's status says it's not. I'll go beat on IDrive support.

---

### Post by TheFu on 2022-11-05
There are plenty of great backup tools for Linux. What's the point of a commercial tool?

1 specific tool that takes backups every hour, by default, is back-in-time.  It uses librsync and hardlinks, like many tools, so it has the file metadata issue that all of those tools have between the versions of backed up files.

To supercharge the backups, be certain that volume management is used with instantaneous snapshots. That means LVM+ext4 or ZFS or btrfs.

---

