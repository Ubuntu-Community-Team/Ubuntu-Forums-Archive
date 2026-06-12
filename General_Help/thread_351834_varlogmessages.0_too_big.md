---
title: "var/log/messages.0 too big"
date: 2007-02-02
forum: General Help
---

### Post by jmvidalvia on 2007-02-02
I run out of disk, so I checked it:
du -mc
I found /var/log/messages.0 , with over 100 MB.
I checked it and realize this secuence repeats every two seconds!

Jan 30 22:10:29 localhost kernel: [17187696.792000] [pg0+950535505/1069368320] firegl_irq_cleanup+0x121/0x1d0 [fglrx]
Jan 30 22:10:29 localhost kernel: [17187696.792000] [pg0+950532651/1069368320] firegl_takedown+0x89b/0xba0 [fglrx]
Jan 30 22:10:29 localhost kernel: [17187696.792000] [pg0+950528159/1069368320] firegl_release+0x12f/0x190 [fglrx]
Jan 30 22:10:29 localhost kernel: [17187696.792000] [__fput+119/352] __fput+0x77/0x160
Jan 30 22:10:29 localhost kernel: [17187696.792000] [filp_close+59/128] filp_close+0x3b/0x80
Jan 30 22:10:29 localhost kernel: [17187696.792000] [put_files_struct+114/192] put_files_struct+0x72/0xc0
Jan 30 22:10:29 localhost kernel: [17187696.792000] [do_exit+268/1008] do_exit+0x10c/0x3f0
Jan 30 22:10:29 localhost kernel: [17187696.792000] [do_group_exit+47/176] do_group_exit+0x2f/0xb0
Jan 30 22:10:29 localhost kernel: [17187696.792000] [get_signal_to_deliver+517/816] get_signal_to_deliver+0x205/0x330
Jan 30 22:10:29 localhost kernel: [17187696.792000] [do_signal+68/272] do_signal+0x44/0x110
Jan 30 22:10:29 localhost kernel: [17187696.792000] [del_timer+21/128] del_timer+0x15/0x80
Jan 30 22:10:29 localhost kernel: [17187696.792000] [del_timer+21/128] del_timer+0x15/0x80
Jan 30 22:10:29 localhost kernel: [17187696.792000] [schedule_timeout+73/176] schedule_timeout+0x49/0xb0
Jan 30 22:10:29 localhost kernel: [17187696.792000] [sys_nanosleep+274/384] sys_nanosleep+0x112/0x180
Jan 30 22:10:29 localhost kernel: [17187696.792000] [sys_sigreturn+162/192] sys_sigreturn+0xa2/0xc0
Jan 30 22:10:29 localhost kernel: [17187696.792000] [do_divide_error+0/160] do_divide_error+0x0/0xa0
Jan 30 22:10:29 localhost kernel: [17187696.792000] [do_notify_resume+39/64] do_notify_resume+0x27/0x40
Jan 30 22:10:29 localhost kernel: [17187696.792000] [work_notifysig+19/37] work_notifysig+0x13/0x25
Jan 30 22:10:29 localhost kernel: [17187696.792000] [schedule+1474/1680] schedule+0x5c2/0x690

Some questions:
¿is this normal to get messages so often(2 sec.)?
¿can I clean this file?
I run Kubuntu/Dapper

Thanks a lot!

jm

---

### Post by jasutton on 2007-02-02
Nothing relies on that file being there, so you're safe to delete it if you want.  However, that only solves the immediate problem (low disk space).  As for what is causing the problem, it looks like the logging level on something is set too high (ATI driver?).  I might check /etc/X11/xorg.conf to see if there are any logging parameters on the ATI driver portion of the file.

---

