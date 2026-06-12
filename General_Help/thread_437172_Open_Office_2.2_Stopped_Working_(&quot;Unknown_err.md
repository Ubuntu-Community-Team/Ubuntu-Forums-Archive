---
title: "Open Office 2.2 Stopped Working? (&quot;Unknown error forking main binary...&quot;)"
date: 2007-05-08
forum: General Help
---

### Post by khughitt on 2007-05-08
Heya,

I Just went to use open office calc, and for some reason, it would not open. The splash screen appeared, and then when the progress bar reached about 70%, it just dissapeared. I check oowrite and it was the same deal. So i tried running oocalc in the terminal to see if it gave me any informative output. There was a long list of similar output ending in:

```

.
.
.
b7b25000-b7b26000 rwxp b7b25000 00:00 0 
b7b26000-b7c3a000 r-xp 00000000 08:16 507129     /usr/lib/openoffice/program/libsvl680li.so
b7c3a000-b7c40000 rwxp 00114000 08:16 507129     /usr/lib/openoffice/program/libsvl680li.so
b7c40000-b7c41000 rwxp b7c40000 00:00 0 
b7c41000-b7faf000 r-xp 00000000 08:16 507141     /usr/lib/openoffice/program/libvcl680li.so
b7faf000-b7fc3000 rwxp 0036e000 08:16 507141     /usr/lib/openoffice/program/libvcl680li.so
b7fc3000-b7fc6000 rwxp b7fc3000 00:00 0 
b7fc6000-b7fdf000 r-xp 00000000 08:16 392923     /lib/ld-2.5.so
b7fdf000-b7fe1000 rwxp 00019000 08:16 392923     /lib/ld-2.5.so
bfd1a000-bfd5e000 rwxp bfd1a000 00:00 0          [stack]
bfd5e000-bfd60000 rw-p bfd5e000 00:00 0 
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]

** (process:10335): WARNING **: Unknown error forking main binary / abnormal early exit ...
home~$ 

```

I Tried re-booting but no luck. I haven't reported a bug yet because of time, and i thought i would see if anyone had any ideas what is happening first. I may also just end up removing and reinstalling office, but i'm not so sure that that would help.

Any suggestions would be greatly appreciated :)
Thanks

---

### Post by dcstar on 2007-05-09
> **pwnedd said:**
> Heya,

I Just went to use open office calc, and for some reason, it would not open. The splash screen appeared, and then when the progress bar reached about 70%, it just dissapeared. I check oowrite and it was the same deal. So i tried running oocalc in the terminal to see if it gave me any informative output. There was a long list of similar output ending in:
..........
Any suggestions would be greatly appreciated :)
Thanks

By any chance did you do some printer configuration/changes since the last time it worked?

---

### Post by Hagar Delest on 2007-05-09
Have you tried to install from the official RPMs (not the distro ones) ? There are several threads about that here.

---

### Post by khughitt on 2007-05-09
> By any chance did you do some printer configuration/changes since the last time it worked?

I don't think so, but its possible. I have printed recently.

> Have you tried to install from the official RPMs (not the distro ones) ?
Nope. Just using the version installed with 7.04 upgrade.

---

### Post by khughitt on 2007-05-11
Okay, i'm not exactly sure what the problem was, but i was able to get things working again by uninstalling & reinstalling openoffice.org. Now i just need to re-install the spell check so that firefox won't underline every word i type in red :P

---

### Post by LinuxVox on 2007-05-11
I had the same problem, also just added just added an HP printer. Used Synaptic to reinstall OpenOffice & everything working fine now!

Vox

---

### Post by Whaaa? on 2007-05-12
. . . and then what?

I still get the  'WARNING **: Unknown error forking main binary' in a terminal window.  Thanks for hinting the oocalc command to open the spreadsheet -
I've found Systems\Administration\Synaptic Package Manager and tried reinstalling as well as uninstall\reinstall of Editors\OpenOffice to no avail.

I removed anything that looked associated with HP print driver.

Running Ubuntu v6.1. with latest updates, + nVidia drivers and nothing else on the system.

---

### Post by Hagar Delest on 2007-05-14
You could also see here : [Unknown error forking main binary / abnormal early exit ...]("http://www.oooforum.org/forum/viewtopic.phtml?t=57039")

---

### Post by carloslosgrande on 2007-05-16
I've got this problem also. The only change I made was to install an extra language thru language support. I have had this problem before and the only solution then was to reinstall.
I've removed the extra language support (chinese) no change, I've removed any new font files (MS) no change, I've removed and reinstalled open office (all of it) no change. I followed that link but the error I get is a little different. When I run > strace -f oowriter I get errors referring to SIGABRT and SIGCHILD (x2).
The last file tried is /usr/lib/openoffice/program/libvcl680li.so or ....libutl680li.so or ....libucpfile.. or ....libsvt680li.so etc etc. Each time I run strace the file will be different. 
b7a31000-b7a56000 rw-p 003e1000 08:01 12501240   /usr/lib/openoffice/program/libsvt680li.so
b7a56000-b7a58000 rw-p b7a56000 00:00 0 
b7a58000-b7b6c000 r-xp 00000000 08:01 12501239   /usr/lib/ope) = 467
[pid  5899] <... nanosleep resumed> NULL) = 0
[pid  5899] write(5, "8\2\4\0\2\0\200\3\4\0\0\0\323\323\323\0C\0\5\0\1\0\200"..., 72) = 72
[pid  5899] ioctl(5, FIONREAD, [0])     = 0
[pid  5899] poll([{fd=4, events=POLLIN|POLLPRI}], 1, 0) = 0
[pid  5899] nanosleep({0, 20000000},  <unfinished ...>
[pid  5916] close(32)                   = 0
[pid  5916] rt_sigprocmask(SIG_UNBLOCK, [ABRT], NULL, 8) = 0
[pid  5916] tgkill(5916, 5916, SIGABRT) = 0
[pid  5916] --- SIGABRT (Aborted) @ 0 (0) ---
[pid  5916] exit_group(78)              = ?
Process 5901 resumed
Process 5916 detached
[pid  5917] <... futex resumed> )       = -1 EINTR (Interrupted system call)
Process 5917 detached
[pid  5918] <... accept resumed> 0, NULL) = ? ERESTARTSYS (To be restarted)
Process 5918 detached
Process 5916 detached
[pid  5901] <... wait4 resumed> [{WIFEXITED(s) && WEXITSTATUS(s) == 78}], 0, NULL) = 5916
[pid  5901] --- SIGCHLD (Child exited) @ 0 (0) ---
[pid  5901] exit_group(0)               = ?
Process 5901 detached
[pid  5899] <... nanosleep resumed> NULL) = 0
[pid  5899] write(5, "8\2\4\0\2\0\200\3\4\0\0\0\323\323\323\0C\0\5\0\1\0\200"..., 72) = 72
[pid  5899] ioctl(5, FIONREAD, [0])     = 0
[pid  5899] poll([{fd=4, events=POLLIN|POLLPRI, revents=POLLHUP}], 1, 0) = 1
[pid  5899] poll([{fd=4, events=POLLIN|POLLPRI, revents=POLLHUP}], 1, 0) = 1
[pid  5899] getpid()                    = 5899
[pid  5899] open("/usr/lib/charset.alias", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
[pid  5899] open("/usr/lib/gconv/gconv-modules.cache", O_RDONLY) = 6
[pid  5899] fstat64(6, {st_mode=S_IFREG|0644, st_size=25460, ...}) = 0
[pid  5899] mmap2(NULL, 25460, PROT_READ, MAP_SHARED, 6, 0) = 0xb7f43000
[pid  5899] close(6)                    = 0
[pid  5899] write(2, "\n** (process:5899): WARNING **: "..., 92
** (process:5899): WARNING **: Unknown error forking main binary / abnormal early exit ...
) = 92
[pid  5899] close(4)                    = 0
[pid  5899] write(5, "<\2\2\0\0\0\200\3+\0\1\0", 12) = 12
[pid  5899] read(5, 0xbfe8e500, 32)     = -1 EAGAIN (Resource temporarily unavailable)
[pid  5899] poll([{fd=5, events=POLLIN, revents=POLLIN}], 1, -1) = 1
[pid  5899] read(5, "\1\2j\1\0\0\0\0 \0@\3\0\0\0\0008\241s\10\230Z\264\277\250"..., 32) = 32
[pid  5899] shutdown(5, 2 /* send and receive */) = 0
[pid  5899] close(5)                    = 0
[pid  5899] munmap(0xb7c08000, 380928)  = 0
[pid  5899] exit_group(0)               = ?
Process 5898 resumed
Process 5899 detached
<... wait4 resumed> [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 5899
--- SIGCHLD (Child exited) @ 0 (0) ---
read(10, "", 8192)                      = 0
exit_group(0)                           = ?
Process 5898 detached
ozymandias@ramses:~$ 

What the heck?:confused:
All comments/advice appreciated 'coz this is weird
ps where you see the smiley face it where '8' and ')' are together - not done by me

---

### Post by aldeby on 2007-05-28
If you installed SCIM imput for non latin languages this fix done the job for me: 
> [http://ubuntuforums.org/showpost.php?p=2568329](http://ubuntuforums.org/showpost.php?p=2568329)
Hope it helps. It has been a very annoying bug.

---

### Post by carloslosgrande on 2007-05-28
Thanks Aldeby, I've since reinstalled the system and also reinstalled Chinese, no trouble so far. I'll keep that link in case of future difficulties.
Much appreciated

---

