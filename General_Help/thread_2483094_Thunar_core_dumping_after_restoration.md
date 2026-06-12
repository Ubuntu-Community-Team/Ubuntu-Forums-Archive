---
title: "Thunar core dumping after restoration"
date: 2023-01-20
forum: General Help
---

### Post by BarnOwl on 2023-01-20
This is on Xubuntu 20.04.  I was trying to migrate to a different OS and I did back things up first. The migration didn't go well and I used my backup to go back.  I did have to do a boot rescue to get things to boot but, for the most part things are okay except for Thunar.  As my user it gets a segmentation fault and core dumps.  As root it seems to work fine.  I tried deleting the Thunar config files I was able to find in my home directory.  It didn't make any difference.  I'm no expert at this but. here's what I was able to get from coredumpctl.

```
           PID: 5367 (thunar)
           UID: 1000 (*********)
           GID: 1000 (*********)
        Signal: 11 (SEGV)
     Timestamp: Fri 2023-01-20 08:12:41 EST (3min 10s ago)
  Command Line: thunar
    Executable: /usr/bin/thunar
 Control Group: /user.slice/user-1000.slice/session-c1.scope
          Unit: session-c1.scope
         Slice: user-1000.slice
       Session: c1
     Owner UID: 1000 (*********)
       Boot ID: 7d7ea2d253a046b8bd273e34c10a4d81
    Machine ID: c0bbe755574b40bcb17c236931780821
      Hostname: zeppo
       Storage: /var/lib/systemd/coredump/core.thunar.1000.7d7ea2d253a046b8bd273e34c10a4d81.5367.1674220361000000000000.lz4
       Message: Process 5367 (thunar) of user 1000 dumped core.
                
                Stack trace of thread 5367:
                #0  0x00007fba34429623 g_slice_alloc (libglib-2.0.so.0 + 0x70623)
                #1  0x00007fba34429aae g_slice_alloc0 (libglib-2.0.so.0 + 0x70aae)
                #2  0x00007fba34956535 gdk_event_new (libgdk-3.so.0 + 0x3d535)
                #3  0x00007fba349892a0 n/a (libgdk-3.so.0 + 0x702a0)
                #4  0x00007fba349510e4 gdk_display_get_event (libgdk-3.so.0 + 0x380e4)
                #5  0x00007fba349890e6 n/a (libgdk-3.so.0 + 0x700e6)
                #6  0x00007fba3440b17d g_main_context_dispatch (libglib-2.0.so.0 + 0x5217d)
                #7  0x00007fba3440b400 n/a (libglib-2.0.so.0 + 0x52400)
                #8  0x00007fba3440b4a3 g_main_context_iteration (libglib-2.0.so.0 + 0x524a3)
                #9  0x00007fba34624fe5 g_application_run (libgio-2.0.so.0 + 0xe2fe5)
                #10 0x000056202a095471 n/a (thunar + 0x2d471)
                #11 0x00007fba341e9083 __libc_start_main (libc.so.6 + 0x24083)
                #12 0x000056202a0955ae n/a (thunar + 0x2d5ae)
                
                Stack trace of thread 5368:
                #0  0x00007fba342d799f __GI___poll (libc.so.6 + 0x11299f)
                #1  0x00007fba3440b36e n/a (libglib-2.0.so.0 + 0x5236e)
                #2  0x00007fba3440b4a3 g_main_context_iteration (libglib-2.0.so.0 + 0x524a3)
                #3  0x00007fba3440b4f1 n/a (libglib-2.0.so.0 + 0x524f1)
                #4  0x00007fba34434ad1 n/a (libglib-2.0.so.0 + 0x7bad1)
                #5  0x00007fba34055609 start_thread (libpthread.so.0 + 0x8609)
                #6  0x00007fba342e4133 __clone (libc.so.6 + 0x11f133)
                
                Stack trace of thread 5370:
                #0  0x0000           PID: 5367 (thunar)
           UID: 1000 (*********)
           GID: 1000 (*********)
        Signal: 11 (SEGV)
     Timestamp: Fri 2023-01-20 08:12:41 EST (3min 10s ago)
  Command Line: thunar
    Executable: /usr/bin/thunar
 Control Group: /user.slice/user-1000.slice/session-c1.scope
          Unit: session-c1.scope
         Slice: user-1000.slice
       Session: c1
     Owner UID: 1000 (*********)
       Boot ID: 7d7ea2d253a046b8bd273e34c10a4d81
    Machine ID: c0bbe755574b40bcb17c236931780821
      Hostname: zeppo
       Storage: /var/lib/systemd/coredump/core.thunar.1000.7d7ea2d253a046b8bd273e34c10a4d81.5367.1674220361000000000000.lz4
       Message: Process 5367 (thunar) of user 1000 dumped core.
                
                Stack trace of thread 5367:
                #0  0x00007fba34429623 g_slice_alloc (libglib-2.0.so.0 + 0x70623)
                #1  0x00007fba34429aae g_slice_alloc0 (libglib-2.0.so.0 + 0x70aae)
                #2  0x00007fba34956535 gdk_event_new (libgdk-3.so.0 + 0x3d535)
                #3  0x00007fba349892a0 n/a (libgdk-3.so.0 + 0x702a0)
                #4  0x00007fba349510e4 gdk_display_get_event (libgdk-3.so.0 + 0x380e4)
                #5  0x00007fba349890e6 n/a (libgdk-3.so.0 + 0x700e6)
                #6  0x00007fba3440b17d g_main_context_dispatch (libglib-2.0.so.0 + 0x5217d)
                #7  0x00007fba3440b400 n/a (libglib-2.0.so.0 + 0x52400)
                #8  0x00007fba3440b4a3 g_main_context_iteration (libglib-2.0.so.0 + 0x524a3)
                #9  0x00007fba34624fe5 g_application_run (libgio-2.0.so.0 + 0xe2fe5)
                #10 0x000056202a095471 n/a (thunar + 0x2d471)
                #11 0x00007fba341e9083 __libc_start_main (libc.so.6 + 0x24083)
                #12 0x000056202a0955ae n/a (thunar + 0x2d5ae)
                
                Stack trace of thread 5368:
                #0  0x00007fba342d799f __GI___poll (libc.so.6 + 0x11299f)
                #1  0x00007fba3440b36e n/a (libglib-2.0.so.0 + 0x5236e)
                #2  0x00007fba3440b4a3 g_main_context_iteration (libglib-2.0.so.0 + 0x524a3)
                #3  0x00007fba3440b4f1 n/a (libglib-2.0.so.0 + 0x524f1)
                #4  0x00007fba34434ad1 n/a (libglib-2.0.so.0 + 0x7bad1)
                #5  0x00007fba34055609 start_thread (libpthread.so.0 + 0x8609)
                #6  0x00007fba342e4133 __clone (libc.so.6 + 0x11f133)
                
                Stack trace of thread 5370:
                #0  0x00007fba342dd73d syscall (libc.so.6 + 0x11873d)
                #1  0x00007fba34458746 g_cond_wait_until (libglib-2.0.so.0 + 0x9f746)
                #2  0x00007fba343db581 n/a (libglib-2.0.so.0 + 0x22581)
                #3  0x00007fba344354ca n/a (libglib-2.0.so.0 + 0x7c4ca)
                #4  0x00007fba34434ad1 n/a (libglib-2.0.so.0 + 0x7bad1)
                #5  0x00007fba34055609 start_thread (libpthread.so.0 + 0x8609)
                #6  0x00007fba342e4133 __clone (libc.so.6 + 0x11f133)
                
                Stack trace of thread 5369:
                #0  0x00007fba342d799f __GI___poll (libc.so.6 + 0x11299f)
                #1  0x00007fba3440b36e n/a (libglib-2.0.so.0 + 0x5236e)
                #2  0x00007fba3440b6f3 g_main_loop_run (libglib-2.0.so.0 + 0x526f3)
                #3  0x00007fba34660f8a n/a (libgio-2.0.so.0 + 0x11ef8a)
                #4  0x00007fba34434ad1 n/a (libglib-2.0.so.0 + 0x7bad1)
                #5  0x00007fba34055609 start_thread (libpthread.so.0 + 0x8609)
                #6  0x00007fba342e4133 __clone (libc.so.6 + 0x11f133)
                
                Stack trace of thread 5371:
                #0  0x00007fba342dd73d syscall (libc.so.6 + 0x11873d)
                #1  0x00007fba34458746 g_cond_wait_until (libglib-2.0.so.0 + 0x9f746)
                #2  0x00007fba343db581 n/a (libglib-2.0.so.0 + 0x22581)
                #3  0x00007fba344354ca n/a (libglib-2.0.so.0 + 0x7c4ca)
                #4  0x00007fba34434ad1 n/a (libglib-2.0.so.0 + 0x7bad1)
                #5  0x00007fba34055609 start_thread (libpthread.so.0 + 0x8609)
                #6  0x00007fba342e4133 __clone (libc.so.6 + 0x11f133)

GNU gdb (Ubuntu 9.2-0ubuntu1~20.04.1) 9.2
Copyright (C) 2020 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Type "show copying" and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
    <http://www.gnu.org/software/gdb/documentation/>.

For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from /usr/bin/thunar...
(No debugging symbols found in /usr/bin/thunar)
[New LWP 5367]
[New LWP 5368]
[New LWP 5370]
[New LWP 5369]
[New LWP 5371]
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
Core was generated by `thunar'.
Program terminated with signal SIGSEGV, Segmentation fault.
#0  0x00007fba34429623 in g_slice_alloc () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
[Current thread is 1 (Thread 0x7fba32f69a80 (LWP 5367))]
(gdb) bt
#0  0x00007fba34429623 in g_slice_alloc () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
#1  0x00007fba34429aae in g_slice_alloc0 () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007fba34956535 in gdk_event_new () from /usr/lib/x86_64-linux-gnu/libgdk-3.so.0
#3  0x00007fba349892a0 in ?? () from /usr/lib/x86_64-linux-gnu/libgdk-3.so.0
#4  0x00007fba349510e4 in gdk_display_get_event () from /usr/lib/x86_64-linux-gnu/libgdk-3.so.0
#5  0x00007fba349890e6 in ?? () from /usr/lib/x86_64-linux-gnu/libgdk-3.so.0
#6  0x00007fba3440b17d in g_main_context_dispatch () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
#7  0x00007fba3440b400 in ?? () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
#8  0x00007fba3440b4a3 in g_main_context_iteration () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
#9  0x00007fba34624fe5 in g_application_run () from /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0
#10 0x000056202a095471 in ?? ()
#11 0x00007fba341e9083 in __libc_start_main (main=0x56202a0953c0, argc=1, argv=0x7fff8ff70018, init=<optimized out>, fini=<optimized out>, rtld_fini=<optimized out>, stack_end=0x7fff8ff70008)
    at ../csu/libc-start.c:308
#12 0x000056202a0955ae in ?? ()
7fba342dd73d syscall (libc.so.6 + 0x11873d)
                #1  0x00007fba34458746 g_cond_wait_until (libglib-2.0.so.0 + 0x9f746)
                #2  0x00007fba343db581 n/a (libglib-2.0.so.0 + 0x22581)
                #3  0x00007fba344354ca n/a (libglib-2.0.so.0 + 0x7c4ca)
                #4  0x00007fba34434ad1 n/a (libglib-2.0.so.0 + 0x7bad1)
                #5  0x00007fba34055609 start_thread (libpthread.so.0 + 0x8609)
                #6  0x00007fba342e4133 __clone (libc.so.6 + 0x11f133)
                
                Stack trace of thread 5369:
                #0  0x00007fba342d799f __GI___poll (libc.so.6 + 0x11299f)
                #1  0x00007fba3440b36e n/a (libglib-2.0.so.0 + 0x5236e)
                #2  0x00007fba3440b6f3 g_main_loop_run (libglib-2.0.so.0 + 0x526f3)
                #3  0x00007fba34660f8a n/a (libgio-2.0.so.0 + 0x11ef8a)
                #4  0x00007fba34434ad1 n/a (libglib-2.0.so.0 + 0x7bad1)
                #5  0x00007fba34055609 start_thread (libpthread.so.0 + 0x8609)
                #6  0x00007fba342e4133 __clone (libc.so.6 + 0x11f133)
                
                Stack trace of thread 5371:
                #0  0x00007fba342dd73d syscall (libc.so.6 + 0x11873d)
                #1  0x00007fba34458746 g_cond_wait_until (libglib-2.0.so.0 + 0x9f746)
                #2  0x00007fba343db581 n/a (libglib-2.0.so.0 + 0x22581)
                #3  0x00007fba344354ca n/a (libglib-2.0.so.0 + 0x7c4ca)
                #4  0x00007fba34434ad1 n/a (libglib-2.0.so.0 + 0x7bad1)
                #5  0x00007fba34055609 start_thread (libpthread.so.0 + 0x8609)
                #6  0x00007fba342e4133 __clone (libc.so.6 + 0x11f133)

GNU gdb (Ubuntu 9.2-0ubuntu1~20.04.1) 9.2
Copyright (C) 2020 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Type "show copying" and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
    <http://www.gnu.org/software/gdb/documentation/>.

For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from /usr/bin/thunar...
(No debugging symbols found in /usr/bin/thunar)
[New LWP 5367]
[New LWP 5368]
[New LWP 5370]
[New LWP 5369]
[New LWP 5371]
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
Core was generated by `thunar'.
Program terminated with signal SIGSEGV, Segmentation fault.
#0  0x00007fba34429623 in g_slice_alloc () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
[Current thread is 1 (Thread 0x7fba32f69a80 (LWP 5367))]
(gdb) bt
#0  0x00007fba34429623 in g_slice_alloc () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
#1  0x00007fba34429aae in g_slice_alloc0 () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007fba34956535 in gdk_event_new () from /usr/lib/x86_64-linux-gnu/libgdk-3.so.0
#3  0x00007fba349892a0 in ?? () from /usr/lib/x86_64-linux-gnu/libgdk-3.so.0
#4  0x00007fba349510e4 in gdk_display_get_event () from /usr/lib/x86_64-linux-gnu/libgdk-3.so.0
#5  0x00007fba349890e6 in ?? () from /usr/lib/x86_64-linux-gnu/libgdk-3.so.0
#6  0x00007fba3440b17d in g_main_context_dispatch () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
#7  0x00007fba3440b400 in ?? () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
#8  0x00007fba3440b4a3 in g_main_context_iteration () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
#9  0x00007fba34624fe5 in g_application_run () from /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0
#10 0x000056202a095471 in ?? ()
#11 0x00007fba341e9083 in __libc_start_main (main=0x56202a0953c0, argc=1, argv=0x7fff8ff70018, init=<optimized out>, fini=<optimized out>, rtld_fini=<optimized out>, stack_end=0x7fff8ff70008)
    at ../csu/libc-start.c:308
#12 0x000056202a0955ae in ?? ()
```

Not sure where to take it from here.

---

### Post by ActionParsnip on 2023-01-20
Do other file managers like PCManFM run OK?

---

### Post by BarnOwl on 2023-01-20
> **ActionParsnip said:**
> Do other file managers like PCManFM run OK?

Thanks for the reply.  Yes, PCManFM works but, not my favorite.  Besides, I'm a bit concerned that something else will be affected.

---

### Post by TheFu on 2023-01-20
Have you tried reinstalling thunar?
Also, if files in your HOME aren't all owned by the current userid, that can cause some programs to crash.

For example, if root owns some files, bad things can happen. Use this command
```
find $HOME  -user root
```
to find files owned by root. Those need to be fixed.  Similarly, if any other userid owns files under the wrong userid HOME, that can be bad too.

Backups need more than just the data. file file is just 50% of what a good backup contains.  The restore needs to include the owner, group, permissions, ACLs, and xattrs too.  This is why using a good backup tool and not just a simple "copy" is needed for proper backups.  All backup tools aren't equal either. Some don't handle all those things or don't handle them correctly.

---

### Post by ajgreeny on 2023-01-20
I can't remember exactly where it is but in your hidden .config/xfce4 folder i think there will be a configuration file for thunar, thunarrc? not sure of the name but I suspect you will find it.
See if you can find it and rename it as a backup using  terminal, then restart thunar.

---

### Post by BarnOwl on 2023-01-20
> **TheFu said:**
> Have you tried reinstalling thunar?
Also, if files in your HOME aren't all owned by the current userid, that can cause some programs to crash.

For example, if root owns some files, bad things can happen. Use this command
```
find $HOME  -user root
```
to find files owned by root. Those need to be fixed.  Similarly, if any other userid owns files under the wrong userid HOME, that can be bad too.

Backups need more than just the data. file file is just 50% of what a good backup contains.  The restore needs to include the owner, group, permissions, ACLs, and xattrs too.  This is why using a good backup tool and not just a simple "copy" is needed for proper backups.  All backup tools aren't equal either. Some don't handle all those things or don't handle them correctly.

Thanks for the reply.  Nothing owned by root in my home directory.  As far as the back up goes.  It was an rsync -av to an empty partition.  I think that accomplishes everything you are talking about.  I do have a BackInTime backup of the whole thing as well but, at it's base, that's just rsync.

> **ajgreeny said:**
> I can't remember exactly where it is but in your hidden .config/xfce4 folder i think there will be a configuration file for thunar, thunarrc? not sure of the name but I suspect you will find it.
See if you can find it and rename it as a backup using  terminal, then restart thunar.

Thanks for replying.  I found and deleted those.  Didn't change anything.

---

### Post by TheFu on 2023-01-21
> **BarnOwl said:**
> Thanks for the reply.  Nothing owned by root in my home directory.  As far as the back up goes.  It was an rsync -av to an empty partition.  I think that accomplishes everything you are talking about.  I do have a BackInTime backup of the whole thing as well but, at it's base, that's just rsync. 

That should work, provided the target file system is native Linux, not some foreign file system like NTFS or exFAT.
But you should be aware that rsync+hardlink backup tools only retain the most recent owner, group, permissions.  It is usually fine, but sometimes, over months, different projects will change their group and ownership to improve security. These changes are lost, so if you need to restore any version from before the modifications happened, you're sorta screwed.  For desktops, this is much, much, less important. OTOH, if you run server software on the desktop, it becomes more likely to cause issues.

I learned about the limitation the hard way. ;(

---

### Post by BarnOwl on 2023-01-22
> **TheFu said:**
> That should work, provided the target file system is native Linux, not some foreign file system like NTFS or exFAT.
But you should be aware that rsync+hardlink backup tools only retain the most recent owner, group, permissions.  It is usually fine, but sometimes, over months, different projects will change their group and ownership to improve security. These changes are lost, so if you need to restore any version from before the modifications happened, you're sorta screwed.  For desktops, this is much, much, less important. OTOH, if you run server software on the desktop, it becomes more likely to cause issues.

I learned about the limitation the hard way. ;(

I actually worked as a DBA in a corporate environment.  So, I'm aware of what you're talking about but, this is a single user system with an ext4 filesystem except for the EFI partition.  I don't think my backup's to blame.  I'm going to try something else that may fix it.  I'll post back if it does.

---

