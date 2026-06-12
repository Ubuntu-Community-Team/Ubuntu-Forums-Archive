---
title: "kernel panic ubuntu won't boot"
date: 2014-03-17
forum: General Help
---

### Post by Pedroski55 on 2014-03-17
Hi, I run Ubuntu 12.04, all the latest updates. Lately I've been getting crashes when opening files. Nautilus crashes, the icons on my desktop disappear. From the log files, the nautilus crashes appear to be connected to 'segfault' whatever that is. Clicking on the home folder gets it going again. 
Now often I get a kind of kernel panic message on boot, and Ubuntu will not start, freezes at 22.something seconds into boot. 
I have run memtest all night, all tests passed, no errors.

I have kernel: Linux peterpu 3.5.0-47-generic #71~precise1-Ubuntu SMP Wed Feb 19 22:05:41 UTC 2014 i686 athlon i386 GNU/Linux

I've found that by booting from say kernel 3.5.0-39 The computer will start, albeit without a mouse. I can then ctrl alt f2, enter a virtual terminal, do a shutdown, and reboot the latest kernel. Just did that. This is somewhat frustrating.

Any tips on what is happening here?

I always wondered why Linux leaves so many kernel lying around. Maybe this is why!

I don't think Linux has time to log the mistake before it freezes, I've looked in /var/log/kernel.log and other logs. I can't see the message which I get before the screen freezes.

---

### Post by silex89 on 2014-03-17
Hi there.

Can you give us an insight to the specs of your machine? (CPU, RAM, Graphic card). Maybe it features a UEFI and you forgot to check settings there...

---

### Post by Pedroski55 on 2014-03-18
This is a Toshiba Satellite C600D with a Gallium 0.4 on AMD PALM graphics and AMD E350 CPUs. I recently reinstalled Ubuntu because nautilus kept crashing, but the problem persists. I have been using Ubuntu for a few years now, this problem is new. Some update was not too good. I just left home, closed down Ubuntu normally, came to the office, Ubuntu won't start. I keep Fedora 20 on another partition, that boots fine.

I did once have a problem with Fedora such that, every time I unplugged the internet cable the system froze. I never found out what caused that. Eventually it went away. Not all updates are good!

I found this in /var/log/syslog.1

Mar 15 09:19:31 peterpu kernel: [11000.559358] gnome-settings-[1812]: segfault at 85e637f ip 085e637f sp bf9d0964 error 15
Mar 15 09:19:36 peterpu gnome-session[1760]: WARNING: Application 'gnome-settings-daemon.desktop' killed by signal
Mar 15 10:17:01 peterpu CRON[4530]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 15 11:17:01 peterpu CRON[4592]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 15 12:17:01 peterpu CRON[4660]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

What's a segfault? Sounds bad!

and this again, might be the crashes nautilus has been having.

Mar 15 09:19:31 peterpu kernel: [11000.559358] gnome-settings-[1812]: segfault at 85e637f ip 085e637f sp bf9d0964 error 15
Mar 15 09:19:36 peterpu gnome-session[1760]: WARNING: Application 'gnome-settings-daemon.desktop' killed by signal

and

Mar 16 13:10:56 peterpu kernel: [  132.169438] show_signal_msg: 30 callbacks suppressed
Mar 16 13:10:56 peterpu kernel: [  132.169453] nautilus[1855]: segfault  at b747389b ip b6a04a44 sp bfa6ea9c error 7 in  libc-2.15.so[b68c5000+1a4000]

and this from kern.log.1

Mar 12 17:19:55 peterpu kernel: [  254.931957] indicator-print[1981]: segfault at 95b7080 ip 095b7080 sp bfe823c4 error 15
Mar 12 17:20:24 peterpu kernel: [  284.122013] nautilus[1829]: segfault  at 3924411c ip b6a09a0e sp bfd196ac error 4 in  libc-2.15.so[b68ca000+1a4000]

Can you make any sense of that??

---

