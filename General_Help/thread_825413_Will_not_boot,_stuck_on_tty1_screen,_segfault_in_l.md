---
title: "Will not boot, stuck on tty1 screen, segfault in log"
date: 2008-06-11
forum: General Help
---

### Post by wwusnobrdr on 2008-06-11
I am an intermediate linux user and just experienced something beyond me.  I installed autoscan which is a .bin file.  This ran just fine and everything appeared to be okay.  I was just trying to copy the installation's bin/lib directories to my user bin/lib and when I typed the copy command the gdm seemed to reset and I had just my background with the spinny wheel.  I am not able to boot into any of my kernels and have not found much of note in the various log files except below.  I am able to get a root shell booting into recovery mode.  I have booted into a liveCD which is how I am posting.  I will continue to look through my log files and will provide any additional information needed.  Thanks.

> Jun 10 20:02:24 gondola kernel: [   74.456883] login[6175]: segfault at dc810091 eip dc810091 esp bffa0380 error 5
Jun 10 20:02:24 gondola init: tty1 main process (6175) killed by SEGV signal
Jun 10 20:02:24 gondola init: tty1 main process ended, respawning
Jun 10 20:02:28 gondola init: tty4 main process (4989) killed by TERM signal

EDIT:
While booting there are some failed processes all seem to be SAMBA related, winbind, and nmbd.  Here are some log snippets. The NMBD log is similar ending with a core dump
> WINBIND LOG
2008/06/10 21:08:31, 0] lib/fault.c:fault_report(42)
  INTERNAL ERROR: Signal 11 in pid 5771 (3.0.28a)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2008/06/10 21:08:31, 0] lib/util.c:smb_panic(1633)
  PANIC (pid 5771): internal error
[2008/06/10 21:08:31, 0] lib/util.c:log_stack_trace(1737)
  BACKTRACE: 17 stack frames:
   #0 /usr/sbin/winbindd(log_stack_trace+0x2d) [0x8122fbd]
   #1 /usr/sbin/winbindd(smb_panic+0x5d) [0x81230ed]  ETC............can put all 17 here
[2008/06/10 21:08:31, 0] lib/fault.c:dump_core(181)
  dumping core in /var/log/samba/cores/winbindd

EDIT2:
Upon further inspection it looks like copying the lib and bin folders from the installation overwrote some of my files I had in these directories, any way to recover?

---

