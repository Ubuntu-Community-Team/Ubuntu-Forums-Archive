---
title: "Ubuntu 15.10 - FSCK is never done :-("
date: 2015-12-29
forum: General Help
---

### Post by Franz_Schindler on 2015-12-29
Hello,

i've already tried to force the fsck using
```

sudo touch /forcefsck

```

and on login the system shows:
[FONT=Menlo]*** /dev/sda1 will be checked for errors at next reboot ***[/FONT]

But unfortunately  it never checks the FS :-(

Any ideas why?

```

[FONT=Menlo]adminuser@fortuna:~$ mount | grep ext[/FONT]
[FONT=Menlo]/dev/sda1 on / type [COLOR=#c33720]**ext**[/COLOR]4 (rw,relatime,errors=remount-ro,data=ordered)[/FONT]

```

---

### Post by matt_symes on 2015-12-29
Hi

> **Franz_Schindler said:**
> Hello,

i've already tried to force the fsck using
```

sudo touch /forcefsck

```

and on login the system shows:
[FONT=Menlo]*** /dev/sda1 will be checked for errors at next reboot ***[/FONT]

But unfortunately  it never checks the FS :-(

Any ideas why?

```

[FONT=Menlo]adminuser@fortuna:~$ mount | grep ext[/FONT]
[FONT=Menlo]/dev/sda1 on / type [COLOR=#c33720]**ext**[/COLOR]4 (rw,relatime,errors=remount-ro,data=ordered)[/FONT]

```

Why do you think it's not running fsck ?

Kind regards

---

### Post by Franz_Schindler on 2015-12-30
I think first of all because the Message
> 
[COLOR=#000000][FONT=Menlo]*** /dev/sda1 will be checked for errors at next reboot ***[/FONT][/COLOR]

is still there.

and 2nd
> 
[FONT=Menlo]adminuser@fortuna:~$ dmesg | grep fsck[/FONT]
[FONT=Menlo][    8.671055] systemd[1]: Listening on [COLOR=#c33720]**fsck**[/COLOR] to [COLOR=#c33720]**fsck**[/COLOR]d communication Socket.[/FONT]
[FONT=Menlo][    9.814452] EXT4-fs (sda1): warning: checktime reached, running e2[COLOR=#c33720]**fsck**[/COLOR] is recommended[/FONT]


and 3rd
> 
[FONT=Menlo]adminuser@fortuna:/var/log/fsck$ cat *[/FONT]
[FONT=Menlo](Nothing has been logged yet.)[/FONT]
[FONT=Menlo](Nothing has been logged yet.)[/FONT]


---

### Post by coldraven on 2015-12-30
I'm running 15.10 64 bit.
I have done ```
sudo touch /forcefsck
```
and will post back after a reboot.

Edit: I just re-booted and it does not seem to be working for me too. I did not see the message below.

> [COLOR=#000000][FONT=Menlo]*** /dev/sda1 will be checked for errors at next reboot ***[/FONT][/COLOR]

```
coldraven@happy:/var/log/fsck$ cat *
(Nothing has been logged yet.)
(Nothing has been logged yet.)

```

```
coldraven@happy:~$ dmesg | grep fsck
[    6.523551] systemd[1]: Listening on fsck to fsckd communication Socket.

```

---

### Post by Dennis N on 2015-12-30
(Another) Way to verify or check last time fsck ran:

Last Check:

```
[dmn@Zotac ~]$ sudo dumpe2fs -h /dev/sda4 | grep -i "last"
[sudo] password for dmn: 
dumpe2fs 1.42.13 (17-May-2015)
Last mounted on:          /
Last mount time:          Wed Dec 30 05:50:49 2015
Last write time:          Wed Dec 30 05:50:49 2015
[COLOR="#FF0000"]Last checked:             Fri Dec  4 13:31:02 2015[/COLOR]
```

Adjust command to your filesystem.

---

### Post by coldraven on 2015-12-30
My result, I would imagine that I had rebooted 30 times since Oct 26. I wonder where the boot counter is stored.

```
dumpe2fs 1.42.12 (29-Aug-2014)
Last mounted on:          /
Last mount time:          Wed Dec 30 13:02:44 2015
Last write time:          Wed Dec 30 13:02:38 2015
Last checked:             Mon Oct 26 11:00:07 2015


```

This seems to show that it's overdue

```
sudo dumpe2fs -h /dev/sda1 | grep -i 'mount count'
dumpe2fs 1.42.12 (29-Aug-2014)
Mount count:              36
Maximum mount count:      -1


```

Is Max mount count = -1 a valid value?

---

### Post by Dennis N on 2015-12-30
From what I have read, journaled file systems like ext4 are not normally checked unless a possible problem is flagged. **Maximum mount count = -1** means no regular checking is done based on number of mounts, and is the default setting now. Used to be set to 30 or so, but that was before journaling.

In my case, Dec 4 is when this system was installed.

---

### Post by coldraven on 2015-12-30
> **Dennis N said:**
> From what I have read, journaled file systems like ext4 are not normally checked unless a possible problem is flagged. **Maximum mount count = -1** means no regular checking is done based on number of mounts, and is the default setting now. Used to be set to 30 or so, but that was before journaling.

In my case, Dec 4 is when this system was installed.

That would explain why my previous install of 14.04 was doing file system checks, the drive was failing. Oct 26 was when I replaced the drive and installed 15.10

---

### Post by Franz_Schindler on 2015-12-30
Yes, what i've did was that i've set back the file check option to 30 days or 60 mount's. (for security reasons)
But nevertheless the system will not do an fsck

---

### Post by matt_symes on 2015-12-30
Hi

> **Franz_Schindler said:**
> I think first of all because the Message

> *** /dev/sda1 will be checked for errors at next reboot ***

is still there.

That's not telling it it has not run, only that it will run it on next boot.

Does the file /forcefsck still exist in the root partition ? 

If so then it'll re-run fsck until it's removed. I know it used to delete it but i have noticed that it doesn't anymore and hasn't for a while now, even though fsck still runs.

> and 2nd

[QUOTE]adminuser@fortuna:~$ dmesg | grep fsck
[ 8.671055] systemd[1]: Listening on fsck to fsckd communication Socket.
[ 9.814452] EXT4-fs (sda1): warning: checktime reached, running e2fsck is recommended
[/QUOTE]

This is interesting. 

I know that fsck has run on this 16.04 installation (i've seen it run), but i'll reboot forcing an fsck and see what i get. 

> and 3rd

[QUOTE]adminuser@fortuna:/var/log/fsck$ cat *
(Nothing has been logged yet.)
(Nothing has been logged yet.)
[/QUOTE]

These logs have always been empty on my systems, on systemd and upstart init systems, even though i know that fsck has run.

Is there anything in the systemd journal ?

i don't think journald forwards to the fsck log and that log was always empty on my 12.04 and 14.04 installations. It may be that you have to enable a fsck logging flag to log to that file. I've never needed to find out.
 
Kind regards

---

### Post by matt_symes on 2015-12-30
Hi

I just forced an fsck and it did run. I received a notification on the console when booting up but it looks like nothing was logged.

The 'last check' information below most definitely incorrect. There's no two ways about this. My filing system was fixed using the journal in the last 10 reboots after it hung while suspending. I saw fsck fixing it while booting.

```

matthew-xu-16-04:/home/matthew % sudo dumpe2fs -h /dev/sda1 | grep -i "last"
dumpe2fs 1.42.13 (17-May-2015)
Last mounted on:          /
Last mount time:          Wed Dec 30 17:06:34 2015
Last write time:          Wed Dec 30 17:06:29 2015
Last checked:             Mon Nov 30 22:02:36 2015
matthew-xu-16-04:/home/matthew % 
```

```
matthew-xu-16-04:/home/matthew % last -n10 reboot
reboot   system boot  4.4.0-040400rc7- Wed Dec 30 17:06   still running
reboot   system boot  4.4.0-040400rc7- Wed Dec 30 17:00 - 17:05  (00:05)
reboot   system boot  4.4.0-040400rc7- Tue Dec 29 19:20 - 17:00  (21:39)
reboot   system boot  4.4.0-040400rc7- Tue Dec 29 03:11 - 17:00 (1+13:48)
reboot   system boot  4.3.0-2-generic  Tue Dec 29 02:58 - 17:00 (1+14:01)
reboot   system boot  4.3.0-2-generic  Mon Dec 28 19:54 - 02:58  (07:03)
reboot   system boot  4.3.0-2-generic  Mon Dec 28 00:37 - 02:58 (1+02:21)
reboot   system boot  4.3.0-2-generic  Sat Dec 26 03:05 - 02:58 (2+23:53)
reboot   system boot  4.3.0-2-generic  Wed Dec 23 16:11 - 02:58 (5+10:47)
reboot   system boot  4.3.0-2-generic  Tue Dec 22 12:37 - 16:10 (1+03:33)

wtmp begins Thu Dec  3 23:58:52 2015
matthew-xu-16-04:/home/matthew % 
```

Interestingly, it did delete the forcefsck file on this 16.04 installation so that looks to be working again.

@OP. What release of Ubuntu are you using ? 15.10 ? Things may be different in this dev release so it would be better to try to replicate your findings on your version.

I'll take a look and see if i can figure what's going on with fsck's logging as well.

Kind regards

---

### Post by matt_symes on 2015-12-30
Hi

As for not logging to the checkfs and checkroot log files....

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/513644](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/513644)

It hasn't from Karmic (9.10) to Vivid (15.04) and, i expect, Wily. It's not logging in 16.04 dev. 

It's been marked as a 'won't fix', 'wish list' item since Karmic.

It may log else where.

Kind regards

---

### Post by Dennis N on 2015-12-30
Interesting discussion.

To test a different method, I forced a check on mine by changing the maximum mount count to 12, one less than the current mount count (which was 13). Rebooted, checked, and it was recorded (below) that a check was done.

```
dmn@Sydney:~$ sudo dumpe2fs -h /dev/sdb6 | grep -i "last"
[sudo] password for dmn: 
dumpe2fs 1.42.12 (29-Aug-2014)
Last mounted on:          /
Last mount time:          Wed Dec 30 10:55:54 2015
Last write time:          Wed Dec 30 10:55:45 2015
Last checked:             Wed Dec 30 10:55:45 2015

```
As you indicate, nothing in this particular log file, however:
```
dmn@Sydney:/var/log/fsck$ cat checkfs
(Nothing has been logged yet.)

```
Mount count was also reset to 1, as it should be:
```
dmn@Sydney:~$ sudo dumpe2fs -h /dev/sdb6 | grep -i "mount count"
dumpe2fs 1.42.12 (29-Aug-2014)
Mount count:              1
Maximum mount count:      12
```

This system: 15.04.

---

### Post by matt_symes on 2015-12-30
Hi

> **Dennis N said:**
> Interesting discussion.

To test a different method, I forced a check on mine by changing the maximum mount count to 12, one less than the current mount count (which was 13). Rebooted, checked, and it was recorded (below) that a check was done.

```
dmn@Sydney:~$ sudo dumpe2fs -h /dev/sdb6 | grep -i "last"
[sudo] password for dmn: 
dumpe2fs 1.42.12 (29-Aug-2014)
Last mounted on:          /
Last mount time:          Wed Dec 30 10:55:54 2015
Last write time:          Wed Dec 30 10:55:45 2015
Last checked:             Wed Dec 30 10:55:45 2015

```
As you indicate, nothing in this particular log file, however:
```
dmn@Sydney:/var/log/fsck$ cat checkfs
(Nothing has been logged yet.)

```
Mount count was also reset to 1, as it should be:
```
dmn@Sydney:~$ sudo dumpe2fs -h /dev/sdb6 | grep -i "mount count"
dumpe2fs 1.42.12 (29-Aug-2014)
Mount count:              1
Maximum mount count:      12
```

This system: 15.04.

Good sleuthing !

So it looks like it'll only reset the 'last checked' value when it runs a scheduled check then and not when forcing an fsck manually.

@Dennis N

Are you using upstart or systemd as the init system in 15.04 ? (I can never remember these things).

```
/etc/init/mountall.conf
``` 

is where the magic happens in upstart, and it uses the mountall daemon. 

Kind regards

---

### Post by Dennis N on 2015-12-30
> Are you using upstart or systemd as the init system in 15.04 ?

systemd on 15.04:

```
dmn@Sydney:~$ sudo stat /proc/1/exe
[sudo] password for dmn: 
  File: ‘/proc/1/exe’ -> ‘/lib/systemd/systemd’

```

---

### Post by matt_symes on 2015-12-30
Hi

@Dennis N.

From 

```
man systemd-fsck  | less +/"^KERNEL"
```

```

KERNEL COMMAND LINE
       systemd-fsck understands **one kernel** command line parameter:

       fsck.mode=
           One of "auto", "force", "skip". Controls the mode of operation. The default is "auto", and ensures that file
           system checks are done when the file system checker deems them necessary.  "force" unconditionally results in
           full file system checks.  "skip" skips any file system checks.

       fsck.repair=
           One of "preen", "yes", "no". Controls the mode of operation. The default is " preen", and will automatically
           repair problems that can be safely fixed.  "yes " will answer yes to all questions by fsck and "no" will answer
           no to all questions.

```

The above looks like two kernel command line parameters to me but what do i know :)

Anyway, maybe editing the kernel command line from the grub menu, after pressing the 'e' key is the *systemd specific* way of forcing a fsck instead of creating the file /forcefsck.

```
fsck.mode=force
```

That may make sense if the file system has been remounted read-only after an error of some kind.

It may also update the filing systems 'last check' value correctly.

I would also need to look at the service files to see what they are doing.

I can't currently verify this as i can't reboot at the moment.

**EDIT:**

And to answer my own question...

> @OP. What release of Ubuntu are you using ? 15.10 

...read the thread title Matthew ! :D

Kind regards

---

