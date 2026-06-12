---
title: "Failed to mount btrfs file system"
date: 2022-06-18
forum: General Help
---

### Post by David_Partridge on 2022-06-18
When I booted up my linux system after a power fail one of my logical drives (all 28TB of it):

```
Jun 18 15:40:27 charon kernel: BTRFS error (device sdb1): parent transid verify failed on 12554992156672 wanted 130582 found 127355
Jun 18 15:40:27 charon kernel: BTRFS error (device sdb1): parent transid verify failed on 12554992156672 wanted 130582 found 127355
Jun 18 15:40:27 charon kernel: BTRFS error (device sdb1): failed to read block groups: -5
Jun 18 15:40:27 charon mount[629]: mount: /shared: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or othe>
Jun 18 15:40:27 charon systemd[1]: shared.mount: Mount process exited, code=exited, status=32/n/a
Jun 18 15:40:27 charon systemd[1]: shared.mount: Failed with result 'exit-code'.
Jun 18 15:40:27 charon systemd[1]: Failed to mount /shared.
Jun 18 15:40:27 charon kernel: BTRFS error (device sdb1): open_ctree failed

```

How do I resolve this problem please - no I don't have a backup as I've nothing big enough to back it up onto (it's where i store my backups).

I'm not about to attempt anything without guidance here.
D.

---

### Post by #&amp;thj^% on 2022-06-18
Not sure I can help, but worth a shot, have you tried the option "compress=zstd:5" in /etc/fstab.
Documentation found here; [https://btrfs.readthedocs.io/en/latest/Compression.html](https://btrfs.readthedocs.io/en/latest/Compression.html)
But it also wouldn't hurt to show us this:
```
btrfs rescue super-recover -v
```
and
```
sudo btrfs check --repair /dev/sdb1
```

---

### Post by David_Partridge on 2022-06-18
I did a btrfs check and got:

```
root@charon:/home/amonra# btrfs check /dev/sdb1
Opening filesystem to check...
parent transid verify failed on 12554992156672 wanted 130582 found 127355
parent transid verify failed on 12554992156672 wanted 130582 found 127355
parent transid verify failed on 12554992156672 wanted 130582 found 127355
Ignoring transid failure
leaf parent key incorrect 12554992156672
ERROR: failed to read block groups: Operation not permitted
ERROR: cannot open file system
root@charon:/home/amonra# btrfs check -s 1 /dev/sdb1
using SB copy 1, bytenr 67108864
Opening filesystem to check...
parent transid verify failed on 12554992156672 wanted 130582 found 127355
parent transid verify failed on 12554992156672 wanted 130582 found 127355
parent transid verify failed on 12554992156672 wanted 130582 found 127355
Ignoring transid failure
leaf parent key incorrect 12554992156672
ERROR: failed to read block groups: Operation not permitted
ERROR: cannot open file system
root@charon:/home/amonra# btrfs check -s 2 /dev/sdb1
using SB copy 2, bytenr 274877906944
Opening filesystem to check...
parent transid verify failed on 12554992156672 wanted 130582 found 127355
parent transid verify failed on 12554992156672 wanted 130582 found 127355
parent transid verify failed on 12554992156672 wanted 130582 found 127355
Ignoring transid failure
leaf parent key incorrect 12554992156672
ERROR: failed to read block groups: Operation not permitted
ERROR: cannot open file system
root@charon:/home/amonra# 

```

So I don't think rescue super-recover will work.

I'm very wary of attempting check --repair based on things I have read.

Is a recover zero-log more likely to help (and is that safe)?

D.

---

### Post by #&amp;thj^% on 2022-06-18
> **David_Partridge said:**
> 
So I don't think rescue super-recover will work.

I'm very wary of attempting check --repair based on things I have read.

Is btrfs rescue super-recover a safe operation ?

Is a recover zero-log more likely to help (and is that safe)?

D.
Added pressure of not having a back-up in place is not a fun place for me to comment.
Try first booting to a older kernel to verify if all comes up good or the same.
Putting all your eggs in one basket is a risky hazard.

---

### Post by David_Partridge on 2022-06-18
btrfs rescue zero-log appeared to work, but attempt to mount afterwards:

```
Jun 18 18:58:38 charon kernel: BTRFS info (device sdb1): flagging fs with big metadata feature
Jun 18 18:58:38 charon kernel: BTRFS info (device sdb1): disk space caching is enabled
Jun 18 18:58:38 charon kernel: BTRFS info (device sdb1): has skinny extents
Jun 18 18:58:39 charon kernel: BTRFS error (device sdb1): parent transid verify failed on 12554992156672 wanted 130582 found 127355
Jun 18 18:58:39 charon kernel: BTRFS error (device sdb1): parent transid verify failed on 12554992156672 wanted 130582 found 127355
Jun 18 18:58:39 charon kernel: BTRFS error (device sdb1): failed to read block groups: -5
Jun 18 18:58:39 charon kernel: BTRFS error (device sdb1): open_ctree failed


```

btrfs check --repair gave me:

```
Opening filesystem to check...
parent transid verify failed on 12554992156672 wanted 130582 found 127355
parent transid verify failed on 12554992156672 wanted 130582 found 127355
parent transid verify failed on 12554992156672 wanted 130582 found 127355
Ignoring transid failure
leaf parent key incorrect 12554992156672
ERROR: failed to read block groups: Operation not permitted
ERROR: cannot open file system


```

---

### Post by #&amp;thj^% on 2022-06-18
Instead of me posting a wall of code, have a look here: [https://stackoverflow.com/questions/46472439/fix-btrfs-btrfs-parent-transid-verify-failed-on](https://stackoverflow.com/questions/46472439/fix-btrfs-btrfs-parent-transid-verify-failed-on)
Starting with,"Beware of btrfs-zero-log"
> btrfs-zero-log is not a general fix-everything tool, despite what many people believe and state around the internet. You generally don't need to use it.
Good Luck, and take your time with that information in the link.

---

### Post by David_Partridge on 2022-06-18
Sad to say that mount -t btrfs -o ro,usebackuproot /dev/sdb2 /mnt

Gave me this in the log:

```
Jun 18 20:36:01 charon kernel: BTRFS info (device sdb1): flagging fs with big metadata feature
Jun 18 20:36:01 charon kernel: BTRFS info (device sdb1): trying to use backup root at mount time
Jun 18 20:36:01 charon kernel: BTRFS info (device sdb1): disk space caching is enabled
Jun 18 20:36:01 charon kernel: BTRFS info (device sdb1): has skinny extents
Jun 18 20:36:01 charon kernel: BTRFS error (device sdb1): parent transid verify failed on 12554992156672 wanted 130582 found 127355
Jun 18 20:36:01 charon kernel: BTRFS error (device sdb1): parent transid verify failed on 12554992156672 wanted 130582 found 127355
Jun 18 20:36:01 charon kernel: BTRFS error (device sdb1): failed to read block groups: -5
Jun 18 20:36:01 charon kernel: BTRFS error (device sdb1): open_ctree failed

```

D.

---

### Post by #&amp;thj^% on 2022-06-18
That is very sad.
You never mentioned if you tried adding "**compress=zstd:5**" in /etc/fstab.

---

### Post by David_Partridge on 2022-06-18
I hadn't tried that - is there a particular reason you suggested it?

D.

---

### Post by David_Partridge on 2022-06-19
I booted a live ArchLinux distro (2022-06-01)  (**)  and issued: mount -t btrfs -o ro,rescue=all /dev/sdc1 /mnt
  
  And got this in the system log:
   
  Jun 19 13:04:32 archiso kernel: BTRFS info (device sdc1): flagging fs with big metadata feature
  Jun 19 13:04:32 archiso kernel: BTRFS info (device sdc1): enabling all of the rescue options
  Jun 19 13:04:32 archiso kernel: BTRFS info (device sdc1): ignoring data csums
  Jun 19 13:04:32 archiso kernel: BTRFS info (device sdc1): ignoring bad roots
  Jun 19 13:04:32 archiso kernel: BTRFS info (device sdc1): disabling log replay at mount time
  Jun 19 13:04:32 archiso kernel: BTRFS info (device sdc1): disk space caching is enabled
  Jun 19 13:04:32 archiso kernel: BTRFS info (device sdc1): has skinny extents
  Jun 19 13:04:32 archiso kernel: BTRFS error (device sdc1: state C): parent transid verify failed on 12554992156672 wanted 130582 found 127355
  Jun 19 13:04:32 archiso kernel: BTRFS error (device sdc1: state C): parent transid verify failed on 12554992156672 wanted 130582 found 127355
  Jun 19 13:05:12 archiso systemd[1]: dev-virtio\x2dports-org.qemu.guest_agent.0.device: Job dev-virtio\x2dports-org.qemu.guest_agent.0.device/start timed out.
  Jun 19 13:05:12 archiso systemd[1]: Timed out waiting for device /dev/virtio-ports/org.qemu.guest_agent.0.
  Jun 19 13:05:12 archiso systemd[1]: Dependency failed for QEMU Guest Agent.
  Jun 19 13:05:12 archiso systemd[1]: qemu-guest-agent.service: Job qemu-guest-agent.service/start failed with result 'dependency'.
  Jun 19 13:05:12 archiso systemd[1]: dev-virtio\x2dports-org.qemu.guest_agent.0.device: Job dev-virtio\x2dports-org.qemu.guest_agent.0.device/start failed with result 'timeout'.
  Jun 19 13:05:12 archiso systemd[1]: Reached target Multi-User System.
  Jun 19 13:05:12 archiso systemd[1]: Reached target Graphical Interface.
  Jun 19 13:05:12 archiso systemd[1]: Startup finished in 1min 4.847s (firmware) + 4.837s (loader) + 9.433s (kernel) + 1min 31.546s (userspace) = 2min 50.664s.
  Jun 19 13:05:38 archiso kernel: BTRFS info (device sda2): flagging fs with big metadata feature
  Jun 19 13:05:38 archiso kernel: BTRFS info (device sda2): disk space caching is enabled
  Jun 19 13:05:38 archiso kernel: BTRFS info (device sda2): has skinny extents
  Jun 19 13:05:38 archiso kernel: BTRFS info (device sda2): enabling ssd optimizations
   
  ll /mnt got me this:
   
  Jun 19 13:08:13 archiso kernel: verify_parent_transid: 4 callbacks suppressed
  Jun 19 13:08:13 archiso kernel: BTRFS error (device sdc1: state C): parent transid verify failed on 576192512 wanted 129948 found 122929
  Jun 19 13:08:13 archiso kernel: BTRFS error (device sdc1: state C): parent transid verify failed on 576192512 wanted 129948 found 122929
  Jun 19 13:08:13 archiso kernel: BTRFS error (device sdc1: state C): parent transid verify failed on 576192512 wanted 129948 found 122929
  Jun 19 13:08:13 archiso kernel: BTRFS error (device sdc1: state C): parent transid verify failed on 576192512 wanted 129948 found 122929
  Jun 19 13:08:13 archiso kernel: BTRFS error (device sdc1: state C): parent transid verify failed on 576192512 wanted 129948 found 122929
  Jun 19 13:08:13 archiso kernel: BTRFS error (device sdc1: state C): parent transid verify failed on 576192512 wanted 129948 found 122929
  Jun 19 13:08:13 archiso kernel: BTRFS error (device sdc1: state C): parent transid verify failed on 576192512 wanted 129948 found 122929
  Jun 19 13:08:13 archiso kernel: BTRFS error (device sdc1: state C): parent transid verify failed on 576192512 wanted 129948 found 122929
  Jun 19 13:08:13 archiso kernel: BTRFS error (device sdc1: state C): parent transid verify failed on 576192512 wanted 129948 found 122929
  Jun 19 13:08:13 archiso kernel: BTRFS error (device sdc1: state C): parent transid verify failed on 576192512 wanted 129948 found 122929
   
  ls: cannot access '/mnt/@': Input/output error
  ls: cannot access '/mnt/@_daily.20220525_00:11:01': Input/output error
  ls: cannot access '/mnt/@_daily.20220526_00:11:01': Input/output error
  ls: cannot access '/mnt/@_hourly.20220526_06:00:01': Input/output error
  ls: cannot access '/mnt/@_hourly.20220526_09:00:01': Input/output error
  ls: cannot access '/mnt/@_hourly.20220526_12:00:01': Input/output error
  total 0
  d????????? ? ?    ?      ?            ? @
  drwxrwxr-x 1 root 1000 204 May 15 16:27 @_daily.20220523_00:11:01
  drwxrwxr-x 1 root 1000 204 May 15 16:27 @_daily.20220524_00:11:01
  d????????? ? ?    ?      ?            ? @_daily.20220525_00:11:01
  d????????? ? ?    ?      ?            ? @_daily.20220526_00:11:01
  d????????? ? ?    ?      ?            ? @_hourly.20220526_06:00:01
  d????????? ? ?    ?      ?            ? @_hourly.20220526_09:00:01
  d????????? ? ?    ?      ?            ? @_hourly.20220526_12:00:01
  drwxrwxr-x 1 root 1000 184 Dec 16  2021 @_weekly.20220424_00:12:01
  drwxrwxr-x 1 root 1000 184 Dec 16  2021 @_weekly.20220508_00:12:01
  drwxrwxr-x 1 root 1000 184 Dec 16  2021 @_weekly.20220515_00:12:01
  drwxrwxr-x 1 root 1000 204 May 15 16:27 @_weekly.20220522_00:12:01
   
(**) I tried lubuntu 22.04 but even though it claimed kernel 5.15 it didn't like rescue=all mount option/

---

### Post by #&amp;thj^% on 2022-06-19
> **David_Partridge said:**
> 
(**) I tried lubuntu 22.04 but even though it claimed kernel 5.15 it didn't like rescue=all mount option/
Ok I now suggest to try "btrfsck --init-extent-tree".**_ If you don't have a backup you might be out of luck_**
Dang I wish you had a way to backup that huge drive first though. That's always going to be my Montra, so you'll have to forgive me for that instilled wisdom.
Fingers Crossed.....

---

