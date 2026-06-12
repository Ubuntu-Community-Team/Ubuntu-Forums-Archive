---
title: "Can't login from greeter screen"
date: 2013-01-26
forum: General Help
---

### Post by Leo Simon on 2013-01-26
Hi, I'm running 12.04.    Yesterday, my systems person was remotely logged in helping me solve a problem.    (He was trying to get the gnome-control-center to work successfully in fvwm.) Unfortunately I shut the system down without realizing he was still logged in as root.    I'm not sure whether this caused my problem, or whether it was some other modification he made, but since then, I've been unable to log in from the unity greeter screen.     My password is accepted, and then after a few moments the greeter screen reappears.    The same thing happens for all users and for all of the desktop managers I have installed (the usual plus fvwm).     We've checked and restored all the obvious things---like what system programs were modified that day, (mainly ones related to xsessions)---but the problem persists.     Here's a posting of what appears to be the relevant portion of syslog.

I can login ok if I disable the greeter and boot to a console, then everything works as it should, except for some reason certain font sizes have increased!!

Any advice would be very much appreciated

Except for the last two, none of the lines below appear in the syslog from the previous day, which logged my successful logins.

Jan 26 00:42:43 E6520 kernel: [  109.126112] init: tty6 main process ended, respawning
Jan 26 00:43:09 E6520 kernel: [  134.382345] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Jan 26 00:43:09 E6520 kernel: [  134.383177] SGI XFS Quota Management subsystem
Jan 26 00:43:09 E6520 kernel: [  134.402750] JFS: nTxBlock = 8192, nTxLock = 65536
Jan 26 00:43:09 E6520 kernel: [  134.432400] NTFS driver 2.1.30 [Flags: R/O MODULE].
Jan 26 00:43:09 E6520 kernel: [  134.505593] QNX4 filesystem 0.2.3 registered.
Jan 26 00:43:09 E6520 kernel: [  134.550542] Btrfs loaded
Jan 26 00:43:09 E6520 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
Jan 26 00:43:09 E6520 50mounted-tests: debug: mounted using GRUB fat filesystem driver
Jan 26 00:43:09 E6520 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Jan 26 00:43:09 E6520 10freedos: debug: /dev/sda1 is a FAT partition (mounted by GRUB)
Jan 26 00:43:09 E6520 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Jan 26 00:43:09 E6520 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Jan 26 00:43:09 E6520 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Jan 26 00:43:09 E6520 macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
Jan 26 00:43:09 E6520 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Jan 26 00:43:09 E6520 20microsoft: debug: /dev/sda1 is a FAT partition (mounted by GRUB)
Jan 26 00:43:09 E6520 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Jan 26 00:43:09 E6520 30utility: debug: /dev/sda1 is a FAT partition (mounted by GRUB)
Jan 26 00:43:09 E6520 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Jan 26 00:43:09 E6520 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Jan 26 00:43:09 E6520 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Jan 26 00:43:09 E6520 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
Jan 26 00:43:09 E6520 83haiku: debug: /dev/sda1 is not a BeFS partition: exiting
Jan 26 00:43:09 E6520 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90bsd-distro
Jan 26 00:43:10 E6520 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Jan 26 00:43:10 E6520 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Jan 26 00:43:10 E6520 os-prober: debug: /dev/sda2: is active swap
Jan 26 00:43:10 E6520 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda3
Jan 26 00:43:10 E6520 50mounted-tests: debug: /dev/sda3 type not recognised; skipping
Jan 26 00:43:10 E6520 os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Jan 26 00:43:10 E6520 os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda6
Jan 26 00:43:10 E6520 10freedos: debug: /dev/sda6 is not a FAT partition: exiting
Jan 26 00:43:10 E6520 os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda6
Jan 26 00:43:10 E6520 10qnx: debug: /dev/sda6 is not a QNX4 partition: exiting
Jan 26 00:43:10 E6520 os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda6
Jan 26 00:43:10 E6520 macosx-prober: debug: /dev/sda6 is not an HFS+ partition: exiting
Jan 26 00:43:10 E6520 os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda6
Jan 26 00:43:10 E6520 20microsoft: debug: /dev/sda6 is not a MS partition: exiting
Jan 26 00:43:10 E6520 os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda6
Jan 26 00:43:10 E6520 30utility: debug: /dev/sda6 is not a FAT partition: exiting
Jan 26 00:43:10 E6520 os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda6
Jan 26 00:43:10 E6520 os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda6
Jan 26 00:43:10 E6520 os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda6
Jan 26 00:43:10 E6520 os-prober: debug: running /usr/lib/os-probes/mounted/83haiku on mounted /dev/sda6
Jan 26 00:43:10 E6520 83haiku: debug: /dev/sda6 is not a BeFS partition: exiting
Jan 26 00:43:10 E6520 os-prober: debug: running /usr/lib/os-probes/mounted/90bsd-distro on mounted /dev/sda6
Jan 26 00:43:10 E6520 os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda6
Jan 26 00:43:10 E6520 os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda6
Jan 26 00:43:32 E6520 kernel: Kernel logging (proc) stopped.
Jan 26 00:43:32 E6520 rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="970" x-info="http://www.rsyslog.com"] exiting on signal 15.

---

