---
title: "What does &quot;EXT4-fs (sda2): mounted filesystem with ordered data mode.&quot; means?"
date: 2020-02-03
forum: General Help
---

### Post by pranav.bhattarai on 2020-02-03
What does this error message suppose to mean? If it is a problem, how can I solve this issue?

I use Ubuntu **19.10** with the** ZFS File System**.
```

 bond@007 ~ dmesg | grep error
[   28.547031] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: errors=remount-ro

```

*Let me know if you need some output.*

---

### Post by SeijiSensei on 2020-02-03
What is the entry for sda2 in /etc/fstab? I bet it includes "errors=remount-ro" in its specification like this:
```
UUID=f74a9941-0ebe-4a89-85b8-d91ac10a517b /               ext4    errors=remount-ro 0       1
```

My fstab uses UUIDs rather than /dev/sdX device names. That's pretty common on modern Ubuntu installations, but you may see /dev/sda2 instead.

If so, there's no error. Your grep just found the word in a valid dmesg entry.

---

### Post by pranav.bhattarai on 2020-02-04
```

 bond@007  ~  cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# /boot/efi was on /dev/sda1 during installation
UUID=43E7-B614  /boot/efi       vfat    umask=0077      0       1
UUID=6d988e71-7ff5-4aec-9b42-b98a767bf53b    /boot/grub    ext4    errors=remount-ro    01
UUID=198a8b95-c922-4bfc-aef0-6f5c4dd833d3    none    swap    discard    0    0

```

This is the complete output. What's wrong here?!

---

### Post by SeijiSensei on 2020-02-04
You don't have an entry for the root filesystem. Are you sure the second entry should be mounted at /boot/grub and not / itself?

Other than having a separate /boot and /home partitions, my fstab is pretty vanilla:

```

# / was on /dev/sda7 during installation
[color=blue]UUID=f74a9941-0ebe-4a89-85b8-d91ac10a517b /               ext4    errors=remount-ro 0       1[/color]
# /boot was on /dev/sda1 during installation
UUID=83c2a86a-938c-41ec-92e0-afb63a3de70e /boot           ext2    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=c6ffc626-fa92-4e62-9302-cc19e4e7af7f /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=f75ea6ad-431e-4c6d-81d9-44cc455de824 none            swap    sw              0       0

```

---

### Post by TheFu on 2020-02-04
The command you ran just found the "error" part of the mount option.  This isn't any issue. It is purely a configuration option. Nothing more.

---

### Post by pranav.bhattarai on 2020-02-05
The things is, form the last few days my Laptop (Dell Inspirion 5548) shutdown/startup weirdly. 
It works like this: Dell logo > Purple Screen > Dell logo > Purple Screen > actually start booting/shutdown.

So I started finding if there is some error.

---

### Post by pranav.bhattarai on 2020-02-05
I haven't modified anything. 
A few months ago, I took a 19.10 ubuntu image and installed it with the ZFS option purging dual boot option of Windows. Clean installed wiping everything. 
Things have changed a lot since then. 

More important thing is, what wrongs and how can I correct them if there is something wrong.

From last few days I am having some side effects (which I commented above). I want to solve that problem. And this might be a part of that problem.

"Are you sure the second entry should be mounted at /boot/grub and not / itself?"
This is not done by me. Ubuntu 19.10 **did not** gave any partition option to install **if** you choose **ZFS**.
 Do you want me to change them?

---

### Post by TheFu on 2020-02-05
To be clear.  The line you posted with 'error' in it is expected, correct, not a problem, the way it should be.
Further, it isn't using ZFS.  It clearly shows using EXT4, which is the default for Ubuntu and has been for about a decade.

Post #3 above, with the fstab, looks perfectly fine too.  If there is some issue, it likely isn't there.

Check all the log files for warnings and errors.
Check any storage using smartctl for problems.
If there are issues after those, create a fresh userid, login using that and see if the problems stop.  If they do, it is a configuration issue in the other userid's HOME.  If they continue, then it is a system problem or a misunderstanding about expected behavior.

---

