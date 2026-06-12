---
title: "Console messages &amp; crashes from syslogd,kernel -- what to do?"
date: 2006-11-24
forum: General Help
---

### Post by jdpipe on 2006-11-24
Hi all

Recently I've upgraded from Dapper to Edgy. I'm getting some kernel messages from time to time (perhaps twice a day). Often those messages appear then 10 seconds or so later, the system hangs.

On this occasion the system didn't hang so I've got a copy of the messages. Can anyone tell me (a) whether these messages indicate the source of the problem and indeed whether these might be the same problems that usually cause my machine to hang, and (b) what can I do about them, or where should I  report the bug?

This is Ubuntu 6.10 on a P4 running off a USB hard drive with an SIS video card and 512 MB RAM.

Cheers
JP

--------8<------
Message from syslogd@roadwork at Sat Nov 25 12:59:07 2006 ...
roadwork kernel: [17180107.220000] Oops: 0000 [#1]

Message from syslogd@roadwork at Sat Nov 25 12:59:07 2006 ...
roadwork kernel: [17180107.220000] CPU:    0

Message from syslogd@roadwork at Sat Nov 25 12:59:07 2006 ...
roadwork kernel: [17180107.220000] EIP is at pipe_poll+0x34/0xa0

Message from syslogd@roadwork at Sat Nov 25 12:59:07 2006 ...
roadwork kernel: [17180107.220000] eax: b7793444   ebx: 00000000   ecx: 00000001   edx: 00000000

Message from syslogd@roadwork at Sat Nov 25 12:59:07 2006 ...
roadwork kernel: [17180107.220000] esi: d4762d40   edi: 23232323   ebp: d5329eac   esp: d5329c18

Message from syslogd@roadwork at Sat Nov 25 12:59:07 2006 ...
roadwork kernel: [17180107.220000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@roadwork at Sat Nov 25 12:59:07 2006 ...
roadwork kernel: [17180107.220000] Process gnome-settings- (pid: 4614, threadinfo=d5328000 task=d943da90)

Message from syslogd@roadwork at Sat Nov 25 12:59:07 2006 ...
roadwork kernel: [17180107.220000] Stack: 00000020 d4762d40 00000002 c016a6f5 d5329c54 d5329fac 081b3698 081b36e0 

Message from syslogd@roadwork at Sat Nov 25 12:59:07 2006 ...
roadwork kernel: [17180107.220000]        d5329e94 d5329e94 00000009 00000000 00000001 00000009 d5329e94 c016b3c0 

Message from syslogd@roadwork at Sat Nov 25 12:59:07 2006 ...
roadwork kernel: [17180107.220000]        00000000 00000000 00000009 d475e6c0 00000000 d943da90 c0115da0 d829cc00 

Message from syslogd@roadwork at Sat Nov 25 12:59:07 2006 ...
roadwork kernel: [17180107.220000] Call Trace:

Message from syslogd@roadwork at Sat Nov 25 12:59:07 2006 ...
roadwork kernel: [17180107.220000]  <c016a6f5> do_sys_poll+0x205/0x400  <c016b3c0> __pollwait+0x0/0xf0

Message from syslogd@roadwork at Sat Nov 25 12:59:07 2006 ...
roadwork kernel: [17180107.220000]  <c0115da0> default_wake_function+0x0/0x10  <c0115da0> default_wake_function+0x0/0x10

Message from syslogd@roadwork at Sat Nov 25 12:59:07 2006 ...
roadwork last message repeated 3 times

Message from syslogd@roadwork at Sat Nov 25 12:59:07 2006 ...
roadwork kernel: [17180107.220000]  <c0115da0> default_wake_function+0x0/0x10  <c0115429> __wake_up_common+0x39/0x60

Message from syslogd@roadwork at Sat Nov 25 12:59:07 2006 ...
roadwork kernel: [17180107.220000]  <c02bdb1b> unix_write_space+0x5b/0x60  <c025bd78> sock_wfree+0x38/0x40

Message from syslogd@roadwork at Sat Nov 25 12:59:07 2006 ...
roadwork kernel: [17180107.220000]  <c025d928> __kfree_skb+0x48/0x110  <c02bc3c2> unix_stream_recvmsg+0x222/0x4e0

Message from syslogd@roadwork at Sat Nov 25 12:59:07 2006 ...
roadwork kernel: [17180107.220000]  <c025723a> do_sock_read+0xca/0xe0  <c0257a80> sock_aio_read+0x80/0x90

Message from syslogd@roadwork at Sat Nov 25 12:59:07 2006 ...
roadwork kernel: [17180107.220000]  <c01581e4> do_sync_read+0xc4/0x100  <c012a640> autoremove_wake_function+0x0/0x50

Message from syslogd@roadwork at Sat Nov 25 12:59:07 2006 ...
roadwork kernel: [17180107.220000]  <c02bb2a9> unix_ioctl+0x89/0xc0  <c0257ba5> sock_ioctl+0x115/0x220

Message from syslogd@roadwork at Sat Nov 25 12:59:07 2006 ...
roadwork kernel: [17180107.220000]  <c0257a90> sock_ioctl+0x0/0x220  <c0169bef> do_ioctl+0x1f/0x70

Message from syslogd@roadwork at Sat Nov 25 12:59:07 2006 ...
roadwork kernel: [17180107.220000]  <c016a92d> sys_poll+0x3d/0x50  <c0102dbb> sysenter_past_esp+0x54/0x79

Message from syslogd@roadwork at Sat Nov 25 12:59:07 2006 ...
roadwork kernel: [17180107.220000] Code: d3 89 74 24 04 89 c6 89 7c 24 08 8b 40 08 8b 40 08 8b b8 f4 00 00 00 74 0c 85 ff 74 08 89 d1 89 f0 89 fa ff 13 0f b7 4e 1c 31 d2 <8b> 5f 08 f6 c1 01 74 17 8b 87 5c 01 00 00 31 d2 85 db 0f 9e c2 

Message from syslogd@roadwork at Sat Nov 25 12:59:07 2006 ...
roadwork kernel: [17180107.220000] EIP: [pipe_poll+52/160] pipe_poll+0x34/0xa0 SS:ESP 0068:d5329c18

---

### Post by deepwave on 2006-11-24
Not sure... I think that gnome-settings is tripping itself up.  Most of messages deal with sockets and such.

You can see if this is kernel related by running dmesg.
Another place to look is /var/log/messages

---

### Post by jdpipe on 2007-01-02
This problem seems to have gone away. As I recall there was a GTK+ update from Ubuntu, so this may have fixed the problem if it was as deepwave suggested.

Another user wrote to me asking about this -- maybe it was related.
[http://lkml.org/lkml/2006/12/20/127](http://lkml.org/lkml/2006/12/20/127)

Cheers
JP

---

