---
title: "Is possible an delay when mounting discs in OS startup ?"
date: 2022-07-25
forum: General Help
---

### Post by aug7744 on 2022-07-25
Hello.
Thanks for read my topic.
Disc is partitioned
1 \boot
2 \root
3 \home
4 \opt
All partitions are in fstab.

The problem is ramdonly when computer power on and in OS boot starting the partition 4 \opt not is mounted thus need to restart the computer to another try to mount.
The disc not has any problems being HDD SATA 2.
Possibly when try mount \opt are being started services not having enough time to mount.

Have any configuration to set an delay to mount between partitions listed in fstab ?

Thanks.

---

### Post by TheFu on 2022-07-26
'\' isn't a valid character for directory separation for mounts in **any** Unix.  Could that be the problem?

Rather than describing the issue without some facts, please post the contents of the /etc/fstab file.  Most of those mounts should be using UUIDs, not device names, since device names aren't guaranteed NOT to change from boot to boot.

In addition to the file, the output from 
```
lsblk -e 7 -o name,size,type,fstype,mountpoint,uuid
```
would be helpful once you get it booted with all the mounted storage where you like.

There are many other possible issues, which those 2 items will clarify, so I won't make any other guesses before seeing both.

Also, use forum 'code-tags' when posting. I did that for the lsblk command above, so you can see what it should look like.  This keeps the columns in the correct location. Without code tags, it is just too hard to read the output and mistakes are extremely likely.

---

### Post by ActionParsnip on 2022-07-26
You could always add
```

mount /opt

```
in /etc/rc.local (above the "exit 0" line) as a work around

---

### Post by MAFoElffen on 2022-07-27
> **ActionParsnip said:**
> You could always add
```

mount /opt

```
in /etc/rc.local (above the "exit 0" line) as a work around

If you do it this way, Linux Users report a delay in the boot, unless...
```

mount /dev/sda4 /opt &

```
Or put it in a script in a loop waiting, on success to exit the loop... and call the script the same way, as a background process.

In /etc/rc.local
```

/usr/sbin/WaitForMount &

```
Pointing to a Script similar to this:
```

#!/bin/bash
# MAFoElffen, <mafoeffen@ubuntu.com>, 2022.07.27
#
# WaitForMount: 
#    Script runs in loop to MAX = number of TRIES 
#    or until mount is successful

Function WaitForMount() {
    Mount_Status=1
    Counter=0

    # Wait until next loop
    Seconds=0.5

    # Stop trying N times
    Tries=10

    until [ $Counter -eq "$Tries" ] 
    do
        let Counter=Counter+1
    
        mount /dev/sda4 /opt
        Mount_Status=$?
      
        if [ $Mount_Status -eq 0 ]
        then
            Counter=$Tries
        else
            sleep $Seconds
        fi
    done
}

WaitForMount
exit $Mount_Status

```
Just an idea... You use similar scripts like this to wait for network connectivity (different conditions), before mounting network shares from /etc/rc.local

---

### Post by aug7744 on 2022-07-27
@TheFu

Hello. All right with you ?

" '\' isn't a valid character for directory separation for mounts in **any** Unix. Could that be the problem?"
I only sad typed "\" for reference. Not exactly the correct /opt :)

```
NAME                   SIZE             TYPE  FSTYPE MOUNTPOINT UUID
sda                       931,5G disk                   
&#9500;&#9472;sda1                  8M part                   
&#9500;&#9472;sda2                600M part ext2   /boot      67aa475d-75ae-4aa7-a745-6a4756da7a54
&#9500;&#9472;sda3                 12G part btrfs             64aa465d-74ae-4aa6-a765-6a4557da7a54
&#9474; &#9492;&#9472;rc-wb_sda3    12G dm   btrfs  /          64aa465d-74ae-4aa6-a765-6a4557da7a54
&#9500;&#9472;sda4                  1G part btrfs             a1254aa7-a6d6-45a7-74d5-a447fdaae7d6
&#9474; &#9492;&#9472;rc-wb_sda4     1G dm   btrfs  /home      a1254aa7-a6d6-45a7-74d5-a447fdaae7d6
&#9492;&#9472;sda5                  21G part btrfs             6757ad45-74e6-4645-a7ed-746d4de4567a
  &#9492;&#9472;rc-wb_sda5     21G dm   btrfs  /opt       6757ad45-74e6-4645-a7ed-746d4de4567a

rc-wb means an dm-writecache using Rapiddisk cache in OS boot startup.

```
@MAFoElffen
Thanks for your reply.
I will try.

---

### Post by TheFu on 2022-07-28
a) please use code tags. Too hard to read as posted.  Columns matter.

b) btrfs lies and it has very different behavior from other file systems.  I've never used btrfs, so I cannot help. Sorry.  I do know that to get the "truth", we have to use btrfs tools, since only those will actually know what is going on.

---

