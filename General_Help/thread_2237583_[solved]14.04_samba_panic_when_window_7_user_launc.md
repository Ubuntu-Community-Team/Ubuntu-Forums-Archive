---
title: "[solved]14.04 samba panic when window 7 user launches window explorer"
date: 2014-08-02
forum: General Help
---

### Post by zdude on 2014-08-02
My samba configuration file has not changed since 10.04 but after upgrading to 14.04, I started seeing these strange samba panics when someone using windows 7 and they launch the window explorer I see this in the log file.

-----
[2014/08/01 08:04:48.868528,  0] ../source3/lib/util.c:785(smb_panic_s3)
  PANIC (pid 19119): num_bytes too large: 4294966797
[2014/08/01 08:04:48.870951,  0] ../source3/lib/util.c:896(log_stack_trace)
  BACKTRACE: 23 stack frames:
   #0 /usr/lib/x86_64-linux-gnu/libsmbconf.so.0(log_stack_trace+0x1a) [0x7f11ae0e2f3a]
   #1 /usr/lib/x86_64-linux-gnu/libsmbconf.so.0(smb_panic_s3+0x20) [0x7f11ae0e3010]
   #2 /usr/lib/x86_64-linux-gnu/libsamba-util.so.0(smb_panic+0x2f) [0x7f11af60bc6f]
   #3 /usr/lib/x86_64-linux-gnu/samba/libsmbd_base.so.0(+0x1119a5) [0x7f11af1f79a5]
   #4 /usr/lib/x86_64-linux-gnu/samba/libsmbd_base.so.0(reply_outbuf+0x20) [0x7f11af1f8ac0]
   #5 /usr/lib/x86_64-linux-gnu/samba/libsmbd_base.so.0(send_trans_reply+0xee) [0x7f11af1940de]
   #6 /usr/lib/x86_64-linux-gnu/samba/libsmbd_base.so.0(api_reply+0x377) [0x7f11af1a2c07]
   #7 /usr/lib/x86_64-linux-gnu/samba/libsmbd_base.so.0(+0xaf013) [0x7f11af195013]
   #8 /usr/lib/x86_64-linux-gnu/samba/libsmbd_base.so.0(reply_trans+0x5b9) [0x7f11af1958a9]
   #9 /usr/lib/x86_64-linux-gnu/samba/libsmbd_base.so.0(+0x112de1) [0x7f11af1f8de1]
   #10 /usr/lib/x86_64-linux-gnu/samba/libsmbd_base.so.0(+0x113eaf) [0x7f11af1f9eaf]
   #11 /usr/lib/x86_64-linux-gnu/samba/libsmbd_base.so.0(+0x114480) [0x7f11af1fa480]
   #12 /usr/lib/x86_64-linux-gnu/libsmbconf.so.0(run_events_poll+0x16c) [0x7f11ae0f90ac]
   #13 /usr/lib/x86_64-linux-gnu/libsmbconf.so.0(+0x37300) [0x7f11ae0f9300]
   #14 /usr/lib/x86_64-linux-gnu/libtevent.so.0(_tevent_loop_once+0x8d) [0x7f11acad15ed]
   #15 /usr/lib/x86_64-linux-gnu/samba/libsmbd_base.so.0(smbd_process+0x9ca) [0x7f11af1fb59a]
   #16 smbd(+0x9fa4) [0x7f11afc6ffa4]
   #17 /usr/lib/x86_64-linux-gnu/libsmbconf.so.0(run_events_poll+0x16c) [0x7f11ae0f90ac]
   #18 /usr/lib/x86_64-linux-gnu/libsmbconf.so.0(+0x37300) [0x7f11ae0f9300]
   #19 /usr/lib/x86_64-linux-gnu/libtevent.so.0(_tevent_loop_once+0x8d) [0x7f11acad15ed]
   #20 smbd(main+0x13eb) [0x7f11afc6cb8b]
   #21 /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf5) [0x7f11ac729ec5]
   #22 smbd(+0x6f1d) [0x7f11afc6cf1d]
[2014/08/01 08:04:48.871952,  0] ../source3/lib/util.c:797(smb_panic_s3)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 19119]
[2014/08/01 08:04:49.010352,  0] ../source3/lib/util.c:805(smb_panic_s3)
  smb_panic(): action returned status 0
[2014/08/01 08:04:49.010685,  0] ../source3/lib/dumpcore.c:317(dump_core)
  dumping core in /var/log/samba/cores/smbd
-------
All shares from all devices work and this is the only error. Using wire shark it seems that when launching windows explorer it checks for various media players, and media PnP devices like mythtv,, etc. I believe that's causing the panic.  Does anyone have any ideas what might be causing this? The samba panic e-mails are driving me nuts (I know I can disable them)! Lastly is there a way to use an older samba version?

---

### Post by zdude on 2014-08-03
I fixed the problem by downloading, compiling and installing samba 4.11.1 and the problem is now fixed!

---

