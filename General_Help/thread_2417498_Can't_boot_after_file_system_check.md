---
title: "Can't boot after file system check"
date: 2019-04-23
forum: General Help
---

### Post by tritures on 2019-04-23
I set my pc on sleep, after some time I tried to turn it back but monitor was black. After few unsuccessful attempts I rebooted it. File system checking was started on booting but I cancelled it with Ctrl + C and everything was normal. After doing same thing again (setting to sleep and then trying to unsuccessful turn it on) I did same thing, reboot. But, this time, it I let it to check file system and it ended up in emergency mode at the end of this process. While using PC after that first reboot, I was just browsing. 

Here are some red lines from journalistctl which I have found:
```

[COLOR=#b22222]fsck failed with exit status 4.[/COLOR]
[COLOR=#b22222]Failed to start File system Check on /dev/disk/by-uuid/7361d313-2b81-481b-87b2-0728f759d8b8[/COLOR]

```

I think that this might be useful too: Dependency failed for /home

It says that I should do fsck manually but it's root partition and it's mounted. Attempt to umount root (/dev/sda6/) gives me messages that it's busy.
I'm not sure what to do, I was searching for solution but I couldn't fine anything that works this problem.

---

### Post by TheFu on 2019-04-23
Boot from any Ubuntu installation media like a CD or flash drive, then run the fsck on that partition.  This skill will work for many boot issues on any Linux distro. Use rescue mode, at a terminal you'll be root, run fsck -y /dev/sd..... on the partition.  Definitely run it on all the partitions with linux file systems, if you can.

There is a way to tell systemd to fsck / on the next boot, but I've never gotten that to work.

Before systemd, we'd just run **sudo touch /forcefsck** and at the next boot, it would run fsck on the / partition.  That was too easy for systemd to keep, I suppose.

[B]
Next time the OS asks to run fsck, let it!!![/B]

---

### Post by tritures on 2019-04-24
I executed similar commands before, but it didn't work. This time, I did it for home partition and then command sudo touch /forcefsck. I guess that command was a key point for this problem.
Thanks for replying! :)

---

