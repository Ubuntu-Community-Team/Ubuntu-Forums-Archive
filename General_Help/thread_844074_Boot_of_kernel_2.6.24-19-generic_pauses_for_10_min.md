---
title: "Boot of kernel 2.6.24-19-generic pauses for 10 minutes right after grub"
date: 2008-06-29
forum: General Help
---

### Post by boterbram on 2008-06-29
Hello

I already posted this, but this was some time ago and it had a crappy title
[http://ubuntuforums.org/showthread.php?t=796355](http://ubuntuforums.org/showthread.php?t=796355)

The problem is the following:
I upgraded to xubuntu 8.04 (tried both clean install as well as upgrade via 7.10). Xubuntu 8.04 uses kernel 2.6.24-19-generic. When I try to boot this kernel by selecting it in grub the boot stalls for 10 minutes after the screen says "Starting up...". The computer does not show any activity within those 10 minutes. It also is exactly 10 minutes (I timed it). After the pause it continues like normal.

Attached is the beginning of sys.log, starting at the first time it notices this day, ending somewhat later. The last entry in the syslog is 
```
Jun 29 09:29:44 bram-desktop anacron[5715]: Updated timestamp for job `cron.daily' to 2008-06-29
```

Showing the 10 minutes pause is not shown in the sys.log, because the processes in here only take 5 minutes, instead of 10

Does anybody have any idea what to do now, with or withour more info?

Regards, Bram

---

### Post by VMC on 2008-06-29
Type Alt+F2, then put this into the box "gksu gedit /boot/grub/menu.lst"
Then search for "title" of the first generic you boot. Go to the end of the line and remove the "quiet" from the line. Save and reboot.

That way you can view when it boots up where it stalls out. Also install "bootlog". That will give you a ghiphically view of your boot process.

---

### Post by boterbram on 2008-07-01
If I remember it correctly I already tried this with no usefull output because it didn't give me any info between starting up.. and  the lines loading kernel... (if i'm correct that that is the next line), but i will retry

---

### Post by boterbram on 2008-07-01
All right, maybe I didn't try this before. Anyway, removing quiet might have given some info, but I couldn't read it as it was going down my screen way to fast during boot. I did however pipe the dmesg command to a file, which I think might be helpfull. I'm not really sure about the output, but if the numbers in front represent the time from the beginning of the boot the pause is clearly recognizable.

Part of dmesg output:
```
...
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 902.095 MHz processor.
[  670.689426] Console: colour VGA+ 80x25
[  670.689440] console [tty0] enabled
[  670.692396] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[  670.693035] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[  670.723071] Memory: 247816k/262080k available (2177k kernel code, 13712k reserved, 1006k data, 368k init, 0k highmem)
[  670.723163] virtual kernel memory layout:
...
```

I couldn't find bootlog or anything like it in the repos..?

---

### Post by drs305 on 2008-07-01
If you install StartUp-Manager you can easily and safely edit your grub's menu.lst . I bring this up as your dmesg has a long delay and then cites video. I worked a problem with one reader who experienced long grub delays and she resolved it by changing the graphics settings in StartUp-Manager. If I recall, she changed the default 480x640 8-bit to 1280x1024 16-bit. You could experiement with different settings. It's probably a long shot but it's a simple procedure and is worth trying. Just having SUM is probably a good enough reason to try it ;-)

To install SUM:
```
sudo aptitude install startupmanager
```

To run:
System, Admininstration, StartUp-Manager
or:
gksudo startupmanager

To read about some of SUM's other features:
[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by boterbram on 2008-07-01
No luck, nothing changed

---

### Post by drs305 on 2008-07-01
Since you say it pauses exactly 10 minutes, have you looked at your cron jobs and anacrontab tasks:

```

crontab -l
sudo crontab -l
cat /etc/anacrontab
```

---

### Post by boterbram on 2008-07-01
No idea what these are, but no crontabs for my default user account as well as the root account. cat /etc/anacrontab output:

```
bram@bram-desktop:~$ cat /etc/anacrontab
# /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# These replace cron's entries
1	5	cron.daily	 nice run-parts --report /etc/cron.daily
7	10	cron.weekly	 nice run-parts --report /etc/cron.weekly
@monthly	15	cron.monthly nice run-parts --report /etc/cron.monthly

```

Any help?

---

### Post by drs305 on 2008-07-01
> **boterbram said:**
> 

Any help?

No, nothing that indicates any command invoked at boot is delaying things.

---

### Post by boterbram on 2008-07-01
Hmm ok too bad:(

---

### Post by adasiak on 2008-08-12
I've just discovered this problem myself, after re-instaling Kubuntu 8.04.

The initial kernel version was 2.6.24-16, but then I did the upgrades that installed 2.6.24-19, and now it hangs when booting.  I haven't let it sit for ten minutes, but it sounds like we have the same problem.

I googled ```
ubuntu kernel "2.6.24-19" (boot OR booting)
``` and found scads of cases like this.  Sounds like the 2.6.24-19 kernel is buggy and needs to be upgraded to 2.6.24-20.

Fortunately, I didn't remove the old 2.6.24-16 kernel from my [FONT="Courier New"]/boot/grub/menu.lst[/FONT], so it's just a matter of booting the old kernel and making sure this time I've got the new one.   (I hope so, that is.  The problem was there this morning, and I've only found this possible solution recently, away from my Linux box.)

Good luck to us all.

---

