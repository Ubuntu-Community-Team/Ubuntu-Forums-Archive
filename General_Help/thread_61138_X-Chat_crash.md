---
title: "X-Chat crash"
date: 2005-08-30
forum: General Help
---

### Post by LokeDK on 2005-08-30
Hello,
I'm having some problems with X-Chat 2.4.3.
When I go to the X-Chat menu push on "Load Plugin or Script", it crashes. I don't even get the file dialog. Just in the same second i push on "Load Plugin or Script" it crashed.
I've been looking on X-Chat's website how to debug ([http://xchat.org/gdb/](http://xchat.org/gdb/)) and I've done it. But I was told that they could not help me, since it was a Ubuntu package, and not their official...
But well I hope the debugging is usefull.
Oh and by the way - I've also tried reinstall and re-configure.. no luck.
Thanks in advance  :smile: 

(gdb) run
Starting program: /usr/bin/xchat
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1217386048 (LWP 20099)]
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[New Thread -1223930960 (LWP 20104)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1217386048 (LWP 20099)]
0xb73715ed in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
(gdb) bt
#0  0xb73715ed in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
#1  0xb79d22bf in pthread_mutex_lock () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7a4a779 in g_mem_chunk_new () from /usr/lib/libglib-2.0.so.0
#3  0xb7a45b0b in g_main_context_add_poll () from /usr/lib/libglib-2.0.so.0
#4  0xb7a42356 in g_main_context_unref () from /usr/lib/libglib-2.0.so.0
#5  0xb7a42477 in g_main_context_new () from /usr/lib/libglib-2.0.so.0
#6  0xb65e6c99 in link_init () from /usr/lib/libORBit-2.so.0
#7  0xb65c93d3 in giop_init () from /usr/lib/libORBit-2.so.0
#8  0xb65ccb01 in CORBA_ORB_init () from /usr/lib/libORBit-2.so.0
#9  0xb6610e35 in bonobo_activation_orb_init ()
   from /usr/lib/libbonobo-activation.so.4
#10 0xb6610d03 in bonobo_activation_init ()
   from /usr/lib/libbonobo-activation.so.4
#11 0xb66c8cd6 in gnome_vfs_init () from /usr/lib/libgnomevfs-2.so.0
#12 0xb68bc2c8 in fs_module_init ()
   from /usr/lib/gtk-2.0/2.4.0/filesystems/libgnome-vfs.so
#13 0xb7de641f in _gtk_file_system_module_get_type ()
   from /usr/lib/libgtk-x11-2.0.so.0
#14 0xb7bec2c2 in g_type_module_use () from /usr/lib/libgobject-2.0.so.0
#15 0xb7de650a in _gtk_file_system_module_get_type ()
   from /usr/lib/libgtk-x11-2.0.so.0
#16 0xb7de65f6 in _gtk_file_system_create () from /usr/lib/libgtk-x11-2.0.so.0
#17 0xb7dd76db in _gtk_file_chooser_default_get_type ()
---Type <return> to continue, or q <return> to quit---
   from /usr/lib/libgtk-x11-2.0.so.0
#18 0xb7bd53da in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#19 0xb7dd7267 in _gtk_file_chooser_default_get_type ()
   from /usr/lib/libgtk-x11-2.0.so.0
#20 0xb7bd4a9a in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#21 0xb7bd50c9 in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#22 0xb7bd47b0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
#23 0xb7ddb4b4 in _gtk_file_chooser_default_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#24 0xb7ddc796 in gtk_file_chooser_widget_get_type ()
   from /usr/lib/libgtk-x11-2.0.so.0
#25 0xb7bd4a9a in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#26 0xb7bd5212 in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#27 0xb7bd47b0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
#28 0xb7dcfc1f in gtk_file_chooser_dialog_get_type ()
   from /usr/lib/libgtk-x11-2.0.so.0
#29 0xb7bd4a9a in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#30 0xb7bd50c9 in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#31 0xb7bd47b0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
#32 0xb7dcfeca in gtk_file_chooser_dialog_get_type ()
   from /usr/lib/libgtk-x11-2.0.so.0
#33 0xb7dcff4f in gtk_file_chooser_dialog_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
---Type <return> to continue, or q <return> to quit---
#34 0x0805d358 in ?? ()
#35 0x080a0920 in _IO_stdin_used ()
#36 0x00000000 in ?? ()
#37 0x00000000 in ?? ()
#38 0x0809bc72 in _IO_stdin_used ()
#39 0xfffffffa in ?? ()
#40 0x0809d469 in _IO_stdin_used ()
#41 0xfffffffd in ?? ()
#42 0x00000000 in ?? ()
#43 0x080a0920 in _IO_stdin_used ()
#44 0x0810a440 in ?? ()
#45 0x08068520 in ?? ()
#46 0xb7bfa708 in ?? () from /usr/lib/libgobject-2.0.so.0
#47 0x083217d0 in ?? ()
#48 0x08321638 in ?? ()
#49 0xbfffee88 in ?? ()
#50 0x0806860e in ?? ()
#51 0x080a0920 in _IO_stdin_used ()
#52 0x08068520 in ?? ()
#53 0x0810a440 in ?? ()
#54 0x00000000 in ?? ()
#55 0x00000004 in ?? ()
#56 0x083217d0 in ?? ()
---Type <return> to continue, or q <return> to quit---
#57 0xbfffeea8 in ?? ()
#58 0xb7be2c9a in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
Previous frame inner to this frame (corrupt stack?)
(gdb)

---

### Post by arnieboy on 2005-08-30
I am not on my ubuntu box right now, so we will have to do it a little slowly. can u paste the contents of
```
ls -a $HOME/.xchat
```
?

---

### Post by LokeDK on 2005-08-30
22:19:45 [loke@orion][~] $ ls ~/.xchat2/
colors.conf  ignore.conf       notify.conf     slap.py     xchat.conf
downloads    keybindings.conf  servlist_.conf  sound.conf  xmms-control.so
22:29:55 [loke@orion][~] $

(There is only .xchat2)

---

### Post by arnieboy on 2005-08-30
[QUOTE=LokeDK]22:19:45 [loke@orion][~] $ ls ~/.xchat2/
colors.conf  ignore.conf       notify.conf     slap.py     xchat.conf
downloads    keybindings.conf  servlist_.conf  sound.conf  xmms-control.so
22:29:55 [loke@orion][~] $

(There is only .xchat2)[/QUOTE]
delete xchat.conf (or move it to your desktop) and try starting xchat again.

---

### Post by LokeDK on 2005-08-30
No result - it still does the same.

---

### Post by arnieboy on 2005-08-30
[QUOTE=LokeDK]No result - it still does the same.[/QUOTE]
well if I had been on my ubuntu box, i would have read the contents of these config files and helped u quicker. However, what i would suggest is that u try moving these conf files one by one to see which one is causing the crash so that when xchat2 recreates it in your home folder, it wont have the bug anymore.

---

### Post by LokeDK on 2005-08-30
Thanks a lot for your help.
I did a mv ~/.xchat2 ~/.xchat2_backup
And well now it works with a clean xchat.
Though I hate that I have to start from beginning again.

---

### Post by arnieboy on 2005-08-30
[QUOTE=LokeDK]Thanks a lot for your help.
I did a mv ~/.xchat2 ~/.xchat2_backup
And well now it works with a clean xchat.
Though I hate that I have to start from beginning again.[/QUOTE]
u dont have to start from the beginning again if u are a wee bit interested in getting to the root of the crash. just replace the conf files from ur backup one by one on to $HOME/.xchat2/ 
replace one and start xchat2 and see if it crashes or not. it wont even take u a minute to know which conf file was causing the crash. so that u can actually open it next time and edit it and make the damn thing work flawlessly. :)

---

### Post by Manganic on 2007-07-08
> **arnieboy said:**
> u dont have to start from the beginning again if u are a wee bit interested in getting to the root of the crash. just replace the conf files from ur backup one by one on to $HOME/.xchat2/ 
replace one and start xchat2 and see if it crashes or not. it wont even take u a minute to know which conf file was causing the crash. so that u can actually open it next time and edit it and make the damn thing work flawlessly. :)

I'm running into this as well, except I can't find the xchat.conf file anywhere on my system.

I try to go to /home/usr/.xchat and it just doesn't exist.

??! HELP?

---

### Post by zmjjmz on 2008-02-25
It's /home/<user>/.xchat2 not .xchat

---

