---
title: "Gnome rdp hosed"
date: 2008-04-01
forum: General Help
---

### Post by jramey on 2008-04-01
After running the latest update on mar31 Gnome RDP blows up with cannot connect to database
2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux


:/usr/sbin$ sudo gnome-rdp
Stacktrace:

  at (wrapper managed-to-native) Mono.Data.SqliteClient.Sqlite.sqlite_compile (intptr,intptr,intptr&,intptr&,intptr&) <0x00004>
  at (wrapper managed-to-native) Mono.Data.SqliteClient.Sqlite.sqlite_compile (intptr,intptr,intptr&,intptr&,intptr&) <0xffffffff>
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (intptr,intptr&,intptr&) <0x0009e>
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (System.Data.CommandBehavior,bool,int&) <0x000da>
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (System.Data.CommandBehavior) <0x0001d>
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader () <0x0000f>
  at Mono.Data.SqliteClient.SqliteCommand.System.Data.IDbCommand.ExecuteReader () <0x0000d>
  at GnomeRDP.Sqlite.Query (string) <0x00047>
  at GnomeRDP.Configuration.CheckDatabaseVersion () <0x0007c>
  at GnomeRDP.MainApp.InitializeComponent () <0x00140>
  at GnomeRDP.MainApp..ctor (string[]) <0x000d5>
  at GnomeRDP.MainApp.Main (string[]) <0x00019>
  at (wrapper runtime-invoke) System.Object.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

        /usr/bin/mono [0x8194ca6]
        /usr/bin/mono [0x81770ed]
        [0xffffe440]
        /usr/lib/libsqlite.so.0(sqlite_compile+0x35) [0xb5263c35]
        [0xb5433a79]
        [0xb5433967]
        [0xb5432b03]
        [0xb54327ee]
        [0xb54327b8]
        [0xb543278e]
        [0xb54325e8]
        [0xb54284b5]
        [0xb55394c9]
        [0xb7422f9e]
        [0xb7422862]
        [0xb74227d5]
        /usr/bin/mono [0x8176f50]
        /usr/bin/mono(mono_runtime_invoke+0x27) [0x80b0b2f]
        /usr/bin/mono(mono_runtime_exec_main+0x142) [0x80b5383]
        /usr/bin/mono(mono_runtime_run_main+0x27e) [0x80b5631]
        /usr/bin/mono(mono_jit_exec+0xbd) [0x805a4cb]
        /usr/bin/mono [0x805a5a8]
        /usr/bin/mono(mono_main+0x1683) [0x805bdc9]
        /usr/bin/mono [0x8059636]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d30050]
        /usr/bin/mono [0x80595b1]

Debug info from gdb:

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1211005232 (LWP 6105)]
[New Thread -1220408432 (LWP 6107)]
[New Thread -1214645360 (LWP 6106)]
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
0xffffe410 in __kernel_vsyscall ()
  3 Thread -1214645360 (LWP 6106)  0xffffe410 in __kernel_vsyscall ()
  2 Thread -1220408432 (LWP 6107)  0xffffe410 in __kernel_vsyscall ()
  1 Thread -1211005232 (LWP 6105)  0xffffe410 in __kernel_vsyscall ()

Thread 3 (Thread -1214645360 (LWP 6106)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e959f6 in ?? () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0811bc9f in ?? ()
#3  0xb799f3ac in ?? ()
#4  0x00000000 in ?? ()

Thread 2 (Thread -1220408432 (LWP 6107)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e92676 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08120dde in ?? ()
#3  0xb790a1dc in ?? ()
#4  0xb790a1c4 in ?? ()
#5  0xb7e90541 in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
#6  0x081210eb in ?? ()
#7  0xb790a1dc in ?? ()
#8  0xb790a1c4 in ?? ()
#9  0x00000000 in ?? ()

Thread 1 (Thread -1211005232 (LWP 6105)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7de62a1 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7f05780 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7f05b4c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x08194d84 in ?? ()
#5  0xb7bd5844 in ?? ()
#6  0xb7bd582c in ?? ()
#7  0xb7bd5828 in ?? ()
#8  0xb7bd5824 in ?? ()
#9  0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.

---

### Post by tuskenraider on 2008-04-22
unfortunatly the only way i have found around this error is to either delete the old ~/.gnome-rdp.db or rename it...  

tho if you do this, you will have to re-enter all of your remote connection info...  ie: computer username password ect....   

enjoy. :lolflag:

tusken

---

### Post by starbugx on 2008-04-25
Here is a way to read the old .gnome-rdp.db
I hope it will help to restore the lost information!


```

starbugx@ubuntu:~$ sqlite3 ~/.gnome-rdp.db
SQLite version 3.4.2
Enter ".help" for instructions
sqlite> .output gnome-rdp.db.txt
sqlite> select * from session;
sqlite> .exit
starbugx@ubuntu:~$ grep "\." gnome-rdp.db.txt | awk -F"|" '{print $4 " " $6 " "  $7 " " $8}'

```

Output:

Severname IP-Address Username Password

The other way to make gnome-rdp working is to change the link from the libsqlite.so.0 while starting gnome-rdp so it is forced to use libsqlite3.so.0.
Use the following startscript for gnome-rdp instead of gnome-rdp:

```

#!/bin/bash
gksudo mv /usr/lib/libsqlite.so.0 /usr/lib/libsqlite.so.0_
gnome-rdp&
sleep 1
gksudo mv /usr/lib/libsqlite.so.0_ /usr/lib/libsqlite.so.0

```

After that change the starter in Menubar:

System/Preferences/Main Menu
/Internet
Gnome-RDP rightclick Properties
Change Command-Field from "gnome-rdp" to the path an scriptname
For example /home/username/grdp.sh

---

### Post by bensode on 2008-04-29
> **starbugx said:**
> 
The other way to make gnome-rdp working is to change the link from the libsqlite.so.0 while starting gnome-rdp so it is forced to use libsqlite3.so.0.
Use the following startscript for gnome-rdp instead of gnome-rdp:

```

#!/bin/bash
gksudo mv /usr/lib/libsqlite.so.0 /usr/lib/libsqlite.so.0_
gnome-rdp&
sleep 1
gksudo mv /usr/lib/libsqlite.so.0_ /usr/lib/libsqlite.so.0

```



Great little work around.  I just did a fresh install of 8.04 and turned green when I couldn't start gnome-rdp after just copying the .db file over.  Anyone have any suggestions on a proper "fix" so that there is no risk of losing libsqlite.so if for any reason this shell script bombs?  I know that deleting the file and creating a fresh one will do the trick but I have about 200 hosts, most of which are setup differently.

---

