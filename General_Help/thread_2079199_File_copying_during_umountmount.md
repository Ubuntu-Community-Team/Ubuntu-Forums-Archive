---
title: "File copying during umount/mount"
date: 2012-11-01
forum: General Help
---

### Post by areyna3 on 2012-11-01
I am running Ubuntu 12.04 Sever (64-bit) and have opted to go with mhddfs to pool three drives (two 2TB and one 500GB) into one main share and another three identical drives (two 2TB and one 500GB) into a backup pool that nightly backs up everything from the main share pool onto the backup pool using rsync.

My main question is this: based on this user's experience in CentOS ([at the bottom of this page]("http://www.centos.org/modules/newbb/viewtopic.php?viewmode=thread&topic_id=31507&forum=38&post_id=171330")), using crontab I set my mhddfs pools to automatically umount and mount once a day at 5am so as to avoid "leaking free space counter of parent file system." Problem is that when doing a very large file copy (many files large and small totaling 2.5TB), and the pool automatically umounts and mounts in the middle of the transfer (and I'm asleep), what is happening to those files that are getting transferred at the time the umount and mount occur? I don't want to lose any files during a cp or rsync process because it missed a few during the minute while my pools are umounting and mounting themselves. Any way to tell whether or not I missed a file or two? Anyone else have experience with this issue?

As a side note, my drives are currently formatted as NTFS because I had tried Windows Home Server prior to installing Ubuntu and already suffered through excruciatingly long format times for each drive, so I kept NTFS so I didn't have to reformat to ext4. I have also read that mhddfs isn't the best in terms of file throughput, but it seems sufficient for my speed needs at this time. Any opinions on this set up are welcome!

---

### Post by papibe on 2012-11-01
Hi areyna3. Welcome to the forums ):P

In my experience you won't be able to unmount a partition when is being used (as in a rsync process running).

I would start by checking the logs in order to confirm if the unmounting is happening or not:
```
grep -i unmount /var/log/syslog
```
Let us know how it goes.
Regards.

---

### Post by areyna3 on 2012-11-01
Thanks for the quick response! That's good to hear that a umount command issued by crontab will not work if there is a process running on the partition (like cp or rsync) at the time. For a second, I thought I may have been losing files during the minute it took for the drive pool to unmount and then mount themselves again.

I ran the command you suggested, and there doesn't seem to be anything there. Could it be in another log? I searched for "unmount", "umount", and "mount" with no luck.

---

### Post by papibe on 2012-11-01
You can also look at daemon.log, and kernel.log

A proper mount command should be logged  as something like this:
```
Nov  1 14:17:03 server kernel: [682853.318793] EXT4-fs (sdb1): mounted filesystem with ordered data mode

```
Regards.

---

### Post by areyna3 on 2012-11-01
Thanks for that example. I was able to find a similar entry in kern.log.1 that read:

```
Oct 22 15:45:39 servername kernel: [    2.153368] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
Oct 22 15:45:39 servername kernel: [    9.556480] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
```

My system has been up since October 22, but what is weird is that I can't seem to find any logs that show that I have unmounted or mounted anything since then (which crontab is supposed to do at 5am every day). Maybe I am still not looking at the right logs or maybe my crontab is set up incorrectly? Here it is below:

```
00 05 * * * umount /mnt/virtual
01 05 * * * mhddfs /media/one,/media/two,/media/five /mnt/virtual -o allow_other
00 05 * * * umount /mnt/bak-virtual
01 05 * * * mhddfs /media/three,/media/four,/media/six /mnt/bak-virtual -o allow_other
02 05 * * * rsync -a --progress /mnt/virtual/ /mnt/bak-virtual
```

---

