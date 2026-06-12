---
title: "smb issues after upgrading to 22.04"
date: 2022-05-11
forum: General Help
---

### Post by archiel on 2022-05-11
I am relatively new to ubuntu and have just upgraded a windows Hyper-V VM from 21:10 to 22.04.   Since the upgrade the VM crashes whenever there are large file transfers from the VM to any PCs on the LAN.  
The PCs are a mixture of Windows 11 and Windows 10, all 64 bit and all fully patched.  The files are being transferred from a shared folder on the VM and the crashes occur whether using drag and drop from file manager or automated ( via Jackett with Radarr or Sonarr).

The issue does not occur with small or single transfers, but when a larger block of files is being copied (typically 5 GB+).  Prior to the upgrade from 21.10 there was no problem.

The apport.log shows
```
ERROR: apport (pid 6800) Wed May 11 13:53:54 2022: called for pid 6703, signal 6, core limit 18446744073709551615, dump mode 1ERROR: apport (pid 6800) Wed May 11 13:53:54 2022: ignoring implausibly big core limit, treating as unlimited
ERROR: apport (pid 6800) Wed May 11 13:53:54 2022: executable: /usr/sbin/smbd (command line "/usr/sbin/smbd --foreground --no-process-group")
ERROR: apport (pid 6800) Wed May 11 13:53:54 2022: is_closing_session(): no DBUS_SESSION_BUS_ADDRESS in environment
ERROR: apport (pid 6800) Wed May 11 13:54:01 2022: wrote report /var/crash/_usr_sbin_smbd.0.crash
ERROR: apport (pid 6800) Wed May 11 13:54:01 2022: writing core dump to core._usr_sbin_smbd.0.1b378373-8eb2-4f51-af51-95fe9edccbaf.6703.7542682 (limit: -1)
ERROR: apport (pid 6800) Wed May 11 13:54:01 2022: writing core dump core._usr_sbin_smbd.0.1b378373-8eb2-4f51-af51-95fe9edccbaf.6703.7542682 of size 37265408
```


I have attached _usr_sbin_smbd.0.crash and apport.log (as input.zip).   Can anyone suggest where the error is / how I can fix this.

---

### Post by TheFu on 2022-05-11
I don't know, but vaguely recall that the 22.04 release notes have some important things about new samba versions changing some defaults.  Would that be worth reading?

---

### Post by archiel on 2022-05-12
Looked at the release notes, including the specific notes for smbd, but nothing that seemed obvious to me there.  

The vm has crashed a couple more times today, bringing tracker-miner-fs into the picture, but both smbd and tracker-miner-fs are latest versions

```
ERROR: apport (pid 8394) Thu May 12 07:52:52 2022: called for pid 8387, signal 6, core limit 18446744073709551615, dump mode 1ERROR: apport (pid 8394) Thu May 12 07:52:52 2022: ignoring implausibly big core limit, treating as unlimited
ERROR: apport (pid 8394) Thu May 12 07:52:52 2022: executable: /usr/sbin/smbd (command line "/usr/sbin/smbd --foreground --no-process-group")
ERROR: apport (pid 8394) Thu May 12 07:52:52 2022: is_closing_session(): no DBUS_SESSION_BUS_ADDRESS in environment
ERROR: apport (pid 8394) Thu May 12 07:52:53 2022: writing core dump to core._usr_sbin_smbd.0.180a3b97-9b7e-466c-be47-d6cf53665ba7.8387.4903572 (limit: -1)
ERROR: apport (pid 8394) Thu May 12 07:52:53 2022: this executable already crashed 2 times, ignoring
ERROR: apport (pid 8906) Thu May 12 09:06:02 2022: called for pid 3085, signal 11, core limit 0, dump mode 1
ERROR: apport (pid 8906) Thu May 12 09:06:02 2022: executable: /usr/libexec/tracker-miner-fs-3 (command line "/usr/libexec/tracker-miner-fs-3")
ERROR: apport (pid 8906) Thu May 12 09:06:02 2022: debug: session gdbus call: (true,)


ERROR: apport (pid 8906) Thu May 12 09:06:02 2022: this executable already crashed 2 times, ignoring
ERROR: apport (pid 11973) Thu May 12 13:32:39 2022: called for pid 8913, signal 11, core limit 0, dump mode 1
ERROR: apport (pid 11973) Thu May 12 13:32:39 2022: executable: /usr/libexec/tracker-miner-fs-3 (command line "/usr/libexec/tracker-miner-fs-3")
ERROR: apport (pid 11973) Thu May 12 13:32:40 2022: debug: session gdbus call: (true,)


ERROR: apport (pid 11973) Thu May 12 13:32:40 2022: this executable already crashed 2 times, ignoring

```

---

### Post by TheFu on 2022-05-12
I really don't know much about hyper-v or 22.04 or samba, so I'll just ask questions which may lead you to a solution in your effort to get the answers.
Does the version of hyper-v support 22.04, specifically?
When you say "VM has crashed", what, exactly, does that mean?  Samba stopped working?  Unresponsive GUI?  No ping allowed?
Which type of network is hyper-v providing to this VM?  bridge, NAT, host-only?

I don't know what tracker-miner-fs or pirctue or smdb are. You think they are causing the issues?

Since you have a core dump, have you attempted to get a full stack trace from that information?

---

### Post by #&amp;thj^% on 2022-05-12
> **archiel said:**
>  and and tracker-miner-fs 

FWIW: It is in fact a process of tracker, GNOME's file indexer. It is used to index the names and contents of your files in order to easily search and access them in Nautilus or Filemanager

---

### Post by archiel on 2022-05-13
'pirctue or smdb' are picture and smbd (aka my fat fingered typing)

In regard to the other points raised, the VMs are simply run as hosted desktop machines on the same LAN as the physical devices  (DNS and DHCP is handled by the router).  While Microsoft have not yet explicitly added 22.04 to its Ubuntu VM (they only include LTS and only add them slowly) I have previously upgraded 20.04 > 20.10 > 21.04 > 21.10 without the current issues arising.

The process leading to the issues is the same, jackett will locate and download lists of potential torrents.   If the VM (or its host) is already under high load, for instance transferring a large file or files from the VM to another device then (It looks to me that) when tracker is called to index the results it will fail.  Depending on the load, this can just result in tracker failing (an transmission being shut down) or the VM rebooting.  The most recent events have just involved tracker / transmission rather than a full reboot.

Looking at apport.log and syslog when the tracker failure occurs
```
ERROR: apport (pid 5050) Fri May 13 03:02:25 2022: called for pid 790, signal 11, core limit 0, dump mode 1ERROR: apport (pid 5050) Fri May 13 03:02:25 2022: executable: /usr/libexec/tracker-miner-fs-3 (command line "/usr/libexec/tracker-miner-fs-3")
ERROR: apport (pid 5050) Fri May 13 03:02:26 2022: debug: session gdbus call: (true,)


ERROR: apport (pid 5050) Fri May 13 03:02:35 2022: wrote report /var/crash/_usr_libexec_tracker-miner-fs-3.1000.crash
ERROR: apport (pid 8199) Fri May 13 08:54:03 2022: called for pid 5076, signal 11, core limit 0, dump mode 1
ERROR: apport (pid 8199) Fri May 13 08:54:03 2022: executable: /usr/libexec/tracker-miner-fs-3 (command line "/usr/libexec/tracker-miner-fs-3")
ERROR: apport (pid 8199) Fri May 13 08:54:04 2022: debug: session gdbus call: (true,)


ERROR: apport (pid 8199) Fri May 13 08:54:04 2022: this executable already crashed 2 times, ignoring
```
SYSLOG (first incident)
```
May 13 03:02:24 pere-ubu kernel: [40619.264692] tracker-miner-f[790]: segfault at 28 ip 00007fdca5e1c5b3 sp 00007ffc0a009a10 error 4 in libtracker-miner-3.0.so[7fdca5e0d000+1c000]May 13 03:02:24 pere-ubu kernel: [40619.264703] Code: 48 01 fd 85 f6 0f 84 3c 01 00 00 48 8d 7d 38 e8 93 35 ff ff 48 8b 7d 30 e8 6a 35 ff ff 48 8b 45 78 8b 35 94 ba 01 00 4c 89 e7 <8b> 50 28 44 8b 48 20 44 8b 40 1c 52 8b 50 24 52 48 8b 08 31 d2 31
May 13 03:02:26 pere-ubu systemd[1]: Starting Process error reports when automatic reporting is enabled...
May 13 03:02:26 pere-ubu systemd[1]: Started crash report submission.
May 13 03:02:26 pere-ubu whoopsie-upload-all[5057]: INFO:root:Collecting info for /var/crash/_usr_libexec_tracker-miner-fs-3.1000.crash...
May 13 03:02:27 pere-ubu systemd[1]: whoopsie.service: Deactivated successfully.
May 13 03:02:27 pere-ubu whoopsie[5058]: [03:02:27] Using lock path: /var/lock/whoopsie/lock
May 13 03:02:35 pere-ubu systemd[731]: tracker-miner-fs-3.service: Main process exited, code=dumped, status=11/SEGV
May 13 03:02:36 pere-ubu systemd[731]: tracker-miner-fs-3.service: Failed with result 'core-dump'.
May 13 03:02:36 pere-ubu systemd[731]: tracker-miner-fs-3.service: Consumed 2.099s CPU time.
May 13 03:02:36 pere-ubu systemd[1]: Started crash report submission.
May 13 03:02:36 pere-ubu whoopsie[5075]: [03:02:35] Using lock path: /var/lock/whoopsie/lock
May 13 03:02:36 pere-ubu systemd[731]: tracker-miner-fs-3.service: Scheduled restart job, restart counter is at 1.
May 13 03:02:36 pere-ubu systemd[731]: Stopped Tracker file system data miner.
May 13 03:02:36 pere-ubu systemd[731]: tracker-miner-fs-3.service: Consumed 2.099s CPU time.
May 13 03:02:36 pere-ubu systemd[731]: Starting Tracker file system data miner...
May 13 03:02:37 pere-ubu systemd[1]: whoopsie.service: Deactivated successfully.
May 13 03:02:43 pere-ubu systemd[731]: Started Tracker file system data miner.
May 13 03:03:04 pere-ubu dbus-daemon[766]: [session uid=1000 pid=766] Activating via systemd: service name='org.freedesktop.Tracker3.Miner.Extract' unit='tracker-extract-3.service' requested by ':1.122' (uid=1000 pid=5076 comm="/usr/libexec/tracker-miner-fs-3 " label="unconfined")
May 13 03:03:04 pere-ubu systemd[731]: Starting Tracker metadata extractor...
May 13 03:03:08 pere-ubu dbus-daemon[766]: [session uid=1000 pid=766] Successfully activated service 'org.freedesktop.Tracker3.Miner.Extract'
May 13 03:03:08 pere-ubu systemd[731]: Started Tracker metadata extractor.
May 13 03:03:16 pere-ubu whoopsie-upload-all[5057]: INFO:root:Marking /var/crash/_usr_libexec_tracker-miner-fs-3.1000.crash for whoopsie upload
May 13 03:03:16 pere-ubu whoopsie-upload-all[5057]: INFO:root:/var/crash/_usr_sbin_smbd.0.crash already marked for upload, skipping
May 13 03:03:16 pere-ubu whoopsie-upload-all[5057]: INFO:root:Waiting for whoopsie to upload reports (timeout: 20 s)
May 13 03:03:16 pere-ubu whoopsie-upload-all[5057]: INFO:root:  missing (remaining: 20 s): /var/crash/_usr_libexec_tracker-miner-fs-3.1000.uploaded
May 13 03:03:16 pere-ubu systemd[1]: Started crash report submission.
May 13 03:03:16 pere-ubu whoopsie[5560]: [03:03:16] Using lock path: /var/lock/whoopsie/lock
May 13 03:03:17 pere-ubu whoopsie[5560]: [03:03:16] Parsing /var/crash/_usr_libexec_tracker-miner-fs-3.1000.crash.
May 13 03:03:17 pere-ubu whoopsie[5560]: [03:03:16] Unable to parse report (/var/crash/_usr_libexec_tracker-miner-fs-3.1000.crash): Report key must not be a duplicate.
May 13 03:03:17 pere-ubu systemd[1]: whoopsie.service: Deactivated successfully.
May 13 03:03:26 pere-ubu whoopsie-upload-all[5057]: INFO:root:All reports uploaded successfully
May 13 03:03:26 pere-ubu systemd[1]: apport-autoreport.service: Deactivated successfully.
May 13 03:03:26 pere-ubu systemd[1]: Finished Process error reports when automatic reporting is enabled.
May 13 03:03:26 pere-ubu systemd[1]: apport-autoreport.service: Consumed 1.571s CPU time.
```
SYSLOG (2nd incident)
```
May 13 08:54:00 pere-ubu kernel: [61714.126442] Code: 48 01 fd 85 f6 0f 84 3c 01 00 00 48 8d 7d 38 e8 93 35 ff ff 48 8b 7d 30 e8 6a 35 ff ff 48 8b 45 78 8b 35 94 ba 01 00 4c 89 e7 <8b> 50 28 44 8b 48 20 44 8b 40 1c 52 8b 50 24 52 48 8b 08 31 d2 31May 13 08:54:04 pere-ubu systemd[731]: tracker-miner-fs-3.service: Main process exited, code=dumped, status=11/SEGV
May 13 08:54:04 pere-ubu systemd[731]: tracker-miner-fs-3.service: Failed with result 'core-dump'.
May 13 08:54:04 pere-ubu systemd[731]: tracker-miner-fs-3.service: Consumed 4.989s CPU time.
May 13 08:54:04 pere-ubu systemd[731]: tracker-miner-fs-3.service: Scheduled restart job, restart counter is at 2.
May 13 08:54:04 pere-ubu systemd[731]: Stopped Tracker file system data miner.
May 13 08:54:04 pere-ubu systemd[731]: tracker-miner-fs-3.service: Consumed 4.989s CPU time.
May 13 08:54:04 pere-ubu systemd[731]: Starting Tracker file system data miner...
May 13 08:54:09 pere-ubu systemd[731]: Started Tracker file system data miner.
May 13 08:54:26 pere-ubu dbus-daemon[766]: [session uid=1000 pid=766] Activating via systemd: service name='org.freedesktop.Tracker3.Miner.Extract' unit='tracker-extract-3.service' requested by ':1.166' (uid=1000 pid=8207 comm="/usr/libexec/tracker-miner-fs-3 " label="unconfined")
May 13 08:54:26 pere-ubu systemd[731]: Starting Tracker metadata extractor...
May 13 08:54:27 pere-ubu dbus-daemon[766]: [session uid=1000 pid=766] Successfully activated service 'org.freedesktop.Tracker3.Miner.Extract'
May 13 08:54:27 pere-ubu systemd[731]: Started Tracker metadata extractor.
May 13 08:59:01 pere-ubu tracker-miner-f[8207]: g_file_equal: assertion 'G_IS_FILE (file1)' failed
May 13 08:59:01 pere-ubu tracker-miner-f[8207]: g_file_has_prefix: assertion 'G_IS_FILE (file)' failed
May 13 08:59:01 pere-ubu tracker-miner-f[8207]: g_file_equal: assertion 'G_IS_FILE (file1)' failed
May 13 08:59:01 pere-ubu tracker-miner-f[8207]: g_file_has_prefix: assertion 'G_IS_FILE (file)' failed
May 13 09:01:22 pere-ubu NetworkManager[449]: <info>  [1652428882.5572] manager: NetworkManager state is now CONNECTED_SITE
May 13 09:01:22 pere-ubu systemd[1]: Starting Network Manager Script Dispatcher Service...
May 13 09:01:22 pere-ubu dbus-daemon[448]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.12' (uid=0 pid=449 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
May 13 09:01:22 pere-ubu systemd[1]: Started Network Manager Script Dispatcher Service.
May 13 09:01:22 pere-ubu dbus-daemon[448]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 13 09:01:22 pere-ubu NetworkManager[449]: <info>  [1652428882.8414] manager: NetworkManager state is now CONNECTED_GLOBAL
```

What I cannot see is why transmission is shutdown and why it is not restarted - the standard transmission log just runs from after the restart, is there a way retain the log during the incidents and also see why no re-start is triggered?

In respect of a full stack trace, I have never done this, don't know where to start or how I would interpret the results.

---

### Post by TheFu on 2022-05-13
In the past, some programs, usually system programs run at nominal priority (0) like the MTA and cron automatically stop running when system load (as shown in xload) is over 90%. This is to prevent crashes. In the past, this was much more common.  These days, I haven't seen that very often, since we always have a spare core or run more batch tasks at lower priority.  It must be 20 yrs since I last saw cron or postfix refuse to run due to system load.

Could that be happening?

The system should never crash.  It is possible to set a debug GNOME environment variable which will spew all sorts of information. That  might be helpful with tracker-miner-fs. Try putting a **nice** in the "Exec = nice /path/to/tracker-miner-fs" command in the systemd unit file. Can't hurt.  That would be where to add any environment variables to a specific service too.

Is your  VM NIC using virtio or something else?  virtio is meant for VM use.

>  In respect of a full stack trace, I have never done this, don't know where to start or how I would interpret the results. 
Google for the command, then it is 15 seconds to see where a program crashed - that's what the stack trace says and extremely helpful for when you let the Gnome project know where the bug is happening. It shows every function that was called on the way to the program failing. Usually, it is less than 20 lines.

There are many things different in your setup. Stuff I just don't use, so I doubt I can help.

---

### Post by archiel on 2022-05-13
[COLOR=#000000]I have noted below how I ran the back trace and the output.[/COLOR]

[COLOR=#000000]Can you advise if it ran correctly and also how I interpret the result or where I should send it.

```
[/COLOR]archiel@pere-ubu:~$ sudo apport-unpack /var/crash/_usr_sbin_smbd.0.crash /home/archiel/test1archiel@pere-ubu:~$ cd test1
archiel@pere-ubu:~/test1$ gdb `cat ExecutablePath` CoreDump
GNU gdb (Ubuntu 12.0.90-0ubuntu1) 12.0.90
Copyright (C) 2022 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Type "show copying" and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<https://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
    <http://www.gnu.org/software/gdb/documentation/>.


For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from /usr/sbin/smbd...
(No debugging symbols found in /usr/sbin/smbd)


warning: Can't open file /var/cache/samba/printing/EPSON_WF_2830_Series.tdb during file-backed mapping note processing


warning: Can't open file /run/samba/smbXsrv_open_global.tdb during file-backed mapping note processing


warning: Can't open file /run/samba/names.tdb during file-backed mapping note processing


warning: Can't open file /run/samba/smbXsrv_session_global.tdb during file-backed mapping note processing


warning: Can't open file /run/samba/smbXsrv_client_global.tdb during file-backed mapping note processing


warning: Can't open file /var/lib/samba/private/passdb.tdb during file-backed mapping note processing


warning: Can't open file /var/lib/samba/account_policy.tdb during file-backed mapping note processing


warning: Can't open file /run/samba/smbXsrv_tcon_global.tdb during file-backed mapping note processing


warning: Can't open file /var/lib/samba/group_mapping.tdb during file-backed mapping note processing


warning: Can't open file /var/lib/samba/share_info.tdb during file-backed mapping note processing


warning: Can't open file /var/lib/samba/private/secrets.tdb during file-backed mapping note processing


warning: Can't open file /run/samba/smbXsrv_version_global.tdb during file-backed mapping note processing
[New LWP 2222]
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
Core was generated by `/usr/sbin/smbd --foreground --no-process-group'.
Program terminated with signal SIGABRT, Aborted.
#0  __pthread_kill_implementation (no_tid=0, signo=6, threadid=140299692374592) at ./nptl/pthread_kill.c:44
44	./nptl/pthread_kill.c: No such file or directory.
(gdb) bt
#0  __pthread_kill_implementation (no_tid=0, signo=6, threadid=140299692374592) at ./nptl/pthread_kill.c:44
#1  __pthread_kill_internal (signo=6, threadid=140299692374592) at ./nptl/pthread_kill.c:78
#2  __GI___pthread_kill (threadid=140299692374592, signo=signo@entry=6) at ./nptl/pthread_kill.c:89
#3  0x00007f9a156b0476 in __GI_raise (sig=sig@entry=6) at ../sysdeps/posix/raise.c:26
#4  0x00007f9a156967f3 in __GI_abort () at ./stdlib/abort.c:79
#5  0x00007f9a15ab0344 in dump_core () from /lib/x86_64-linux-gnu/libsmbconf.so.0
#6  0x00007f9a15aa6a15 in smb_panic_s3 () from /lib/x86_64-linux-gnu/libsmbconf.so.0
#7  0x00007f9a15fb150e in smb_panic () from /lib/x86_64-linux-gnu/libsamba-util.so.0
#8  0x00007f9a15fb1595 in ?? () from /lib/x86_64-linux-gnu/libsamba-util.so.0
#9  <signal handler called>
#10 __strlen_avx2 () at ../sysdeps/x86_64/multiarch/strlen-avx2.S:74
#11 0x00007f9a15a8be31 in volume_label () from /lib/x86_64-linux-gnu/libsmbconf.so.0
#12 0x00007f9a15dc3aa3 in smbd_do_qfsinfo () from /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0
#13 0x00007f9a15e26675 in smbd_smb2_request_process_getinfo () from /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0
#14 0x00007f9a15e0f519 in smbd_smb2_request_dispatch () from /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0
#15 0x00007f9a15e108c7 in ?? () from /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0
#16 0x00007f9a1589d745 in tevent_common_invoke_fd_handler () from /lib/x86_64-linux-gnu/libtevent.so.0
#17 0x00007f9a158a3def in ?? () from /lib/x86_64-linux-gnu/libtevent.so.0
#18 0x00007f9a158a1f3b in ?? () from /lib/x86_64-linux-gnu/libtevent.so.0
#19 0x00007f9a1589cb58 in _tevent_loop_once () from /lib/x86_64-linux-gnu/libtevent.so.0
#20 0x00007f9a1589ce3b in tevent_common_loop_wait () from /lib/x86_64-linux-gnu/libtevent.so.0
#21 0x00007f9a158a1ecb in ?? () from /lib/x86_64-linux-gnu/libtevent.so.0
#22 0x00007f9a15dfa188 in smbd_process () from /usr/lib/x86_64-linux-gnu/samba/libsmbd-base.so.0
#23 0x00005634a90f93cd in ?? ()
#24 0x00007f9a1589d745 in tevent_common_invoke_fd_handler () from /lib/x86_64-linux-gnu/libtevent.so.0
#25 0x00007f9a158a3def in ?? () from /lib/x86_64-linux-gnu/libtevent.so.0
#26 0x00007f9a158a1f3b in ?? () from /lib/x86_64-linux-gnu/libtevent.so.0
#27 0x00007f9a1589cb58 in _tevent_loop_once () from /lib/x86_64-linux-gnu/libtevent.so.0
#28 0x00007f9a1589ce3b in tevent_common_loop_wait () from /lib/x86_64-linux-gnu/libtevent.so.0
#29 0x00007f9a158a1ecb in ?? () from /lib/x86_64-linux-gnu/libtevent.so.0
#30 0x00005634a90f5f82 in main ()
(gdb) 
[COLOR=#000000]
```[/COLOR]

---

### Post by TheFu on 2022-05-13
That looks like a stack trace to me.  Seems the volume label has a problem based on these:
```
#10 __strlen_avx2 () at ../sysdeps/x86_64/multiarch/strlen-avx2.S:74
#11 0x00007f9a15a8be31 in volume_label () from /lib/x86_64-linux-gnu/libsmbconf.so.0
```

I don't know if you ran the command correctly or not, but I doubt you'd get the correct stack trace for smbd if it wasn't close enough or correct.

Check your label and the name for the mount location.

Also, why is tracker-miner-fs even looking at CIFS storage?  I'd stop that.

---

### Post by archiel on 2022-05-14
In order to remove CIFS / tracker from the situation, I have created a new shared folder for the torrent downloads and excluded this from tracker-miner-fs (using dconf editor).  I then removed the network shares from Documents and Downloads 

In respect of the stack trace I tried looking at lines 10 and 11
```
(gdb) f 11#11 0x00007f9a15a8be31 in volume_label () from /lib/x86_64-linux-gnu/libsmbconf.so.0
(gdb) list
39	in ./nptl/pthread_kill.c
(gdb) f 10
#10 __strlen_avx2 () at ../sysdeps/x86_64/multiarch/strlen-avx2.S:74
74	../sysdeps/x86_64/multiarch/strlen-avx2.S: No such file or directory.
(gdb) list
69	in ../sysdeps/x86_64/multiarch/strlen-avx2.S
```

but I do not know how to interpret this  or move it forward - how do I find the expected path to the non-extant location

In regard to '[COLOR=#000000]Check your label and the name for the mount location.'  I ran blkid
```
[/COLOR]/dev/sr0: BLOCK_SIZE="2048" UUID="2019-09-03-06-21-27-00" LABEL="GParted-live" TYPE="iso9660" PTUUID="2cdaaa37" PTTYPE="dos"/dev/sda2: UUID="31e27cc8-7ede-457f-9041-e7377dcfd852" TYPE="swap" PARTUUID="961a167e-2f48-4d14-ba5c-facbd0984c3f"
/dev/sda15: LABEL_FATBOOT="UEFI" LABEL="UEFI" UUID="D7FD-9D85" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="79d2d254-6b8f-4034-b3b9-6bd0207ec689"

/dev/sda1: LABEL="desktop-rootfs" UUID="55829715-0091-4b86-b060-1cb88f342faf" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="43e99d31-1277-402c-a13b-6cc8fb93169b"[COLOR=#000000]
```
but do not know how to use this in the context of the stack trace error[/COLOR]

---

### Post by TheFu on 2022-05-14
The LABEL could be the name of the CIFS mount?
BTW, network mounts are best never placed under any user's HOME.  Mount them elsewhere.  I use /d or /data or /misc to avoid conflicts that arise with other, commonly used, locations.  Never under /home/ anywhere.

Avoiding issues BEFORE they can happen is being a good admin.

---

### Post by archiel on 2022-05-14
I have moved the share away from /home but would like to understand why this can be an issue as I am much more used to windows systems where the location of shares is not, AFAIK, an issue. 

Hopefully this has resolved the issue, will see next time I run a large file download / transfer.

---

### Post by TheFu on 2022-05-14
> **archiel said:**
> I have moved the share away from /home but would like to understand why this can be an issue as I am much more used to windows systems where the location of shares is not, AFAIK, an issue. 

Hopefully this has resolved the issue, will see next time I run a large file download / transfer.

The location of a shared drive isn't the issue. It is the location of the mount that matters - and that it isn't a native Linux file system, so things like owner, group, permissions, ACLs and xattrs aren't part of the samba controls.  Samba does file locking different from native Linux and NFS (the native Unix network file system).  There have been issues with CIFS mounts when placed under HOME directories even when the mount wasn't active.  

**_Avoiding issues is part of being a good admin._** Sometimes there isn't any better answer.

The best practice is to mount remote storage outside /home/ and then setup symlinks or a cdpath or an alias to make accessing that other location easier.

When you backup your HOME directory, do you really want to backup the CIFS files?  Backups should be made on the system where the physical storage is connected.

One more tip.  Always, always, add an extra, empty line, to the end of any text config file.  Some parsers see EOL and EOF different, so the last line will be ignored.  In theory, it shouldn't matter, but when 100,000+ people are coding across different projects, you never know what you'll get.  Perhaps their compiler implementation treats EOF as EOL too, but on our platform, that isn't the situation.  We never know.  Get burned by this one time, 20+ yrs ago, and you'll always add an extra line to the bottom of every file, just to avoid the issue.

---

