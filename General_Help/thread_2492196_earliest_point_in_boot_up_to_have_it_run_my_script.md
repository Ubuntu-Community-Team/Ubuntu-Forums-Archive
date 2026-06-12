---
title: "earliest point in boot up to have it run my script"
date: 2023-11-02
forum: General Help
---

### Post by Skaperen on 2023-11-02
i'm looking for the earliest point to have the boot up sequence run a script i provide, in bash, owned by root.  i would like for this to be before any services are started.  before any file systems are mounted would be even better.  ideally this "point" exists in 22.04, 20.04, 18.04, and 16.04 but that's not essential (the more the better).  if this needs a binary instead of a script, i can do that.

---

### Post by ajgreeny on 2023-11-02
With so little information about the script and what it does, or what you want it to do, it is impossible to give you a definite answer.

Give us full details of what you're trying to do with this script and we may be able to give you an answer or even tell you of other ways to do it.

---

### Post by Yellow Pasque on 2023-11-02
You may want to search systemd's "local-fs-pre.target". That seems like what you're asking for.

---

### Post by MAFoElffen on 2023-11-02
Usually if I am trying to add something at boot, the first thing I look at is the timeline and dependencies:

RE: [https://www.freedesktop.org/software/systemd/man/latest/bootup.html](https://www.freedesktop.org/software/systemd/man/latest/bootup.html)
```

The following chart is a structural overview of these well-known units and their position in the boot-up logic. The arrows describe which units are pulled in and ordered before which other units. Units near the top are started before units nearer to the bottom of the chart.

                             cryptsetup-pre.target veritysetup-pre.target
                                                  |
(various low-level                                v
 API VFS mounts:             (various cryptsetup/veritysetup devices...)
 mqueue, configfs,                                |    |
 debugfs, ...)                                    v    |
 |                                  cryptsetup.target  |
 |  (various swap                                 |    |    remote-fs-pre.target
 |   devices...)                                  |    |     |        |
 |    |                                           |    |     |        v
 |    v                       local-fs-pre.target |    |     |  (network file systems)
 |  swap.target                       |           |    v     v                 |
 |    |                               v           |  remote-cryptsetup.target  |
 |    |  (various low-level  (various mounts and  |  remote-veritysetup.target |
 |    |   services: udevd,    fsck services...)   |             |              |
 |    |   tmpfiles, random            |           |             |    remote-fs.target
 |    |   seed, sysctl, ...)          v           |             |              |
 |    |      |                 local-fs.target    |             | _____________/
 |    |      |                        |           |             |/
 \____|______|_______________   ______|___________/             |
                             \ /                                |
                              v                                 |
                       sysinit.target                           |
                              |                                 |
       ______________________/|\_____________________           |
      /              |        |      |               \          |
      |              |        |      |               |          |
      v              v        |      v               |          |
 (various       (various      |  (various            |          |
  timers...)      paths...)   |   sockets...)        |          |
      |              |        |      |               |          |
      v              v        |      v               |          |
timers.target  paths.target   |  sockets.target      |          |
      |              |        |      |               v          |
      v              \_______ | _____/         rescue.service   |
                             \|/                     |          |
                              v                      v          |
                          basic.target         rescue.target    |
                              |                                 |
                      ________v____________________             |
                     /              |              \            |
                     |              |              |            |
                     v              v              v            |
                 display-    (various system   (various system  |
             manager.service     services        services)      |
                     |         required for        |            |
                     |        graphical UIs)       v            v
                     |              |            multi-user.target
emergency.service    |              |              |
        |            \_____________ | _____________/
        v                          \|/
emergency.target                    v
                              graphical.target


```
The earliest you can run a script for things, is after sysinit.target... Because the ExecStart+ directive can't really find a path to a script until that process is done. So something like this:
```

[Unit]
Description=Does something early on...
Before=basic.target
After=local-fs.target sysinit.target
DefaultDependencies=no

[Service]
Type=oneshot
ExecStart=/path/to/script

[Install]
WantedBy=basic.target

```

---

### Post by Skaperen on 2023-11-04
it will be testing some conditions the hardware randomly establishes at boot/reset time and if the conditions are not acceptable, it will do a reboot.  the objective is to reduce the time involved to reboot.  it rarely ever has more than two unacceptable conditions in a row so i am not concerned with counting the reboots and limiting this.  running before systemd starts would be nice.  running before any disk I/O happens would be nice.

long ago, i did this as init, before anything else in the system (back when i used Slackware).  now days, i have user admin autologin and its first .bashrc runs it.  if it was OK, then it would run the real init.  to run any earlier i'd have to put it in the bootloader (i did not use grub) or hack the BIOS (a friend of mine has done that).  now days if it has to reboot, it takes a couple extra minutes.  used to be it takes a couple extra seconds and that friend kept suggesting a BIOS hack.

---

### Post by MAFoElffen on 2023-11-04
In that case, and if you want to run it before the bootloader... Will what you want to check run from a UEFI shell script?

---

### Post by dragonfly41 on 2023-11-04
I use rEFInd as my boot manager. Although I do not run scripts at that point I vaguely remember that scripts can be run at that point. All I can suggest is exploring that possibility.  Here are some links. Search rEFInd.

Look in rEFInd.conf.

[https://gist.github.com/Darkhogg/82a651f40f835196df3b1bd1362f5b8c](https://gist.github.com/Darkhogg/82a651f40f835196df3b1bd1362f5b8c)

[https://wiki.archlinux.org/title/REFInd](https://wiki.archlinux.org/title/REFInd)

---

### Post by MAFoElffen on 2023-11-04
On an UEFI BIOS system, the presence of file 'startup.nsh' on a fat filesystem, is the same as is was for autoexec.bat on a DOS system... It looks for (by default) that file, and if present, executes it... It uses the same syntax as UEFI shell, where you can add if,then. else, and other decision tress, set ad clear variables, etc... But has some minor caveats that are specific to UEFI Shell.

---

### Post by Skaperen on 2023-11-14
> **MAFoElffen said:**
> In that case, and if you want to run it before the bootloader... Will what you want to check run from a UEFI shell script?

i have no idea because i don't know what a UEFI shell script is because i don't know anything technical about UEFI.  if it's not a Linux environment i don't know what i can do or how.  what i did long ago wedged onto bootloader I/O.  i forgot the bootloader's name but it was in assembly code (where my hack went into).  i don't think i have those files anymore.

it doesn't really have to run before anything in particular.  it's just "earlier is faster".  if someone did all this and showed me a boot up that did two reboots by chance, i'd likely have no idea where they put the test.  "in Bios" might well be faster than in **[FONT=courier new]/etc/rc.local [/FONT]**but would that much difference really matter?  2 minutes might matter but 5 seconds would not (it's just adding on to the time it takes to boot, again.  shutdown time needs to be figured in if the system is really up (disk space has been mounted beyond R/O)

---

### Post by Skaperen on 2023-11-15
the boot loader i was using back then was "SYSLINUX".  i am no longer using it.  i now use whatever Xubuntu installed which appears to be "grub2".

---

### Post by Skaperen on 2023-11-18
i was hoping for something simple, like a file path that it runs if it exists, is executable, and is owned by root.  or an alternate, a directory path and the files therein that meet the conditions,will be run in sorted order.  something like that.

---

### Post by MAFoElffen on 2023-11-18
If I want to run scripts an startup, I look at where in systemd I want to start it at (where some this are visible) and create a unit file to call it from, like in Post #4. It's not that complicated, and it just works. 

That way, I can see if the service had any errors, and in my script, I usually add a 'logger' call, so it adds an identifiable entry into the syslog to find out if it was called and ran. 

Simple and streamlined is a good thing.

---

