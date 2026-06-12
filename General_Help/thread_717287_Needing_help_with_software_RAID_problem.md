---
title: "Needing help with software RAID problem"
date: 2008-03-06
forum: General Help
---

### Post by m.musashi on 2008-03-06
I need help solving a software RAID issue. I will try and explain. When I installed 7.10 (cleanly) I did so with the alternate CD and set up 2 identical drives to be a RAID 1 array. However, for whatever reason the first drive was not being mirrored. The second drive remained nearly empty. After a bit of research and outside help I managed to get the second drive to mirror and all seemed well. When I rebooted the computer, however, it failed to boot. It did load the kernel and began the boot sequence. In verbose mode I could see that the RAID drives were being stopped. Once they were stopped it would no longer boot. The computer hung for several minutes and then dumped into a busybox shell. Some of the errors refer to attempts to mount /root/dev, /root/sys, /root/proc and then "target filesystem doesn't have /sbin/init" before dumping to busybox and an (initramfs) prompt. I don't why it's stopping the drives but that is probably the cause of the problem.

I have a theory as to how I created the problem but it's only a guess. While trying to get the second drive to mirror, I ran the mdadm --add command like this.

```
sudo mdadm --add /dev/md1 /dev/sdb1
```

My system has two partitions (well 3 counting swap). md0 is where /home is mounted and md1 is /. These correspond to sda1 and sda2. These should mirror on sdb1 and sdb2. The above command was a mistake in that md1 (aka sda2) was mirrored to sdb1 - the wrong size partition (/ was being mirrored to where I wanted /home). I made a guess that I could undo this and fix it by using

```
sudo mdadm -- remove /dev/md1 /dev/sdb1
```

That seemed to work so I then did it the correct way. Output as follows. Notice the last line where it reports that mdadm: RE-ADDED /dev/sdb2

```
[~] sudo mdadm --add /dev/md0 /dev/sdb1
mdadm: added /dev/sdb1
[~] sudo mdadm --add /dev/md1 /dev/sdb2
mdadm: re-added /dev/sdb2
```

I suspect that the --remove option did more than I thought and I did not do enough to fix it. Like I said. This is just a guess.

I then proceeded to get the devices mirroring with

```
sudo mdadm /dev/md0 -G -n 2
sudo mdadm /dev/md1 -G -n 2
```

That resulted in mdstat output like this

```
md0 : active raid1 sdb1[2] sda1[0]
      291017344 blocks [2/1] [U_]
      [>....................] recovery = 0.2% (618560/291017344) finish=70.4min speed=68728K/sec
```

which I assumed meant everything was working fine. The process completed on both drive and when I rebooted it failed as described above.

I have another drive installed with Ubuntu so I am able to boot that install. I can mount the RAID drives and was able to see the status with /proc/mdstat. Here is the output.

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sda2[0] sdb2[1]
      19534976 blocks [2/2] [UU]

md0 : active raid1 sda1[0] sdb1[1]
      291017344 blocks [2/2] [UU]
```

The data is intact. It just won't boot. Sorry for the long explanation but I wanted to be clear. I hope someone knows how to fix this. I'd like to be able to use my RAID setup without have to reinstall all over again. Next time I'm going hardware RAID.

---

### Post by m.musashi on 2008-03-08
Okay, maybe that too complex a question. Let me ask this - is there a way to have the RAID drives somehow "rebuild" without destryoing the data that would also reset everything to a normal state? Basically, I'd like to reset it back to some default setting that will boot. I don't know why the RAID devices are being stopped during boot but I'm hoping there is a command that will reset everything.

Any ideas?

---

### Post by alexandreracine on 2008-03-10
Mabe with the mdadm --scan option? You'll have to check it out, I just remember seeing this.

---

