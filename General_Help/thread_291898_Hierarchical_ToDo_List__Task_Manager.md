---
title: "Hierarchical ToDo List / Task Manager"
date: 2006-11-03
forum: General Help
---

### Post by pt123 on 2006-11-03
Is there a free hierarchical ToDo List / Task Manager?

Like a treelike structure, where you can have main tasks and within
them you have sub-tasks?

There is a great free (source code is provided to like) program on Windows called : ToDoList which does this.
[http://www.abstractspoon.com/index.htm](http://www.abstractspoon.com/index.htm)

Sadly this program doesn't work on Wine](*,)

---

### Post by reclusivemonkey on 2006-11-03
> **pt123 said:**
> Is there a free hierarchical ToDo List / Task Manager?

Like a treelike structure, where you can have main tasks and within
them you have sub-tasks?

There is a great free (source code is provided to like) program on Windows called : ToDoList which does this.
[http://www.abstractspoon.com/index.htm](http://www.abstractspoon.com/index.htm)

Sadly this program doesn't work on Wine](*,)

There is a wonderful application that does this, but it seem to be only on the Zaurus;

[http://iqnotes.berlios.de/](http://iqnotes.berlios.de/)

It may compile though if you have all the qt stuff installed. Have you tried searching the repos?

---

### Post by pt123 on 2006-11-05
Thanks but it doesn't look fully functional as the Windows ToDoList app. 

I will see if there is a way to get people at Wine to fix the errors this application causes.

---

### Post by pt123 on 2007-07-06
Found a way to get ToDoList to work in WINE

1) Copy MSXML3.dll and MSXML3R.dll from WindowsXP installation (usually in C:\Windows\System32) to system32 folder in WINE (usually /home/username/.wine/drive_c/windows/system32 )

Or you can download the file from sites like these:
[http://www.dll-files.com/dllindex/dll-files.shtml](http://www.dll-files.com/dllindex/dll-files.shtml)

2) Run winecfg and override MSXML3 as native. It is in the Libraries tab

3) Manually register msxml3.dll using regsvr32 by typing this in terminal
wine regsvr32 msxml3.dll

-------------
It is pretty functional the right click menu doesn't work well. But those commands can be accessed using the top file menu.

When you run it the first time it will ask you where it should save the settings to, chose an INI file option not the registry.

---

### Post by itmanvn on 2007-11-07
> **pt123 said:**
> Found a way to get ToDoList to work in WINE

1) Copy MSXML3.dll and MSXML3R.dll from WindowsXP installation (usually in C:\Windows\System32) to system32 folder in WINE (usually /home/username/.wine/drive_c/windows/system32 )

Or you can download the file from sites like these:
[http://www.dll-files.com/dllindex/dll-files.shtml](http://www.dll-files.com/dllindex/dll-files.shtml)

2) Run winecfg and override MSXML3 as native. It is in the Libraries tab

3) Manually register msxml3.dll using regsvr32 by typing this in terminal
wine regsvr32 msxml3.dll

-------------
It is pretty functional the right click menu doesn't work well. But those commands can be accessed using the top file menu.

When you run it the first time it will ask you where it should save the settings to, chose an INI file option not the registry.

Still not work on Ubuntu 7.10 :(

---

### Post by pt123 on 2007-11-18
can you post the error message you are getting?

That would be very helpful

---

### Post by itmanvn on 2007-11-20
> **pt123 said:**
> can you post the error message you are getting?

That would be very helpful

```
itmanvn@itmanvn:~/.wine/drive_c/Program Files/todolist$ wine ToDoList.exe 
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
wine: Call from 0x456522 to unimplemented function MFC42.DLL.6475, aborting
wine: Unimplemented function MFC42.DLL.6475 called at address 0x456522 (thread 0009), starting debugger...
Unhandled exception: unimplemented function MFC42.DLL.6475 called in 32-bit code (0x7bc42cfc).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc42cfc ESP:0034fd9c EBP:0034fe00 EFLAGS:00200206(   - 00      - -IP1)
 EAX:0000194b EBX:7bc8443c ECX:004b8270 EDX:7ee7c2f4
 ESI:0034fda8 EDI:004ab8b8
Stack dump:
0x0034fd9c:  7ee61fc4 0034fdd0 7ee47593 80000100
0x0034fdac:  00000001 00000000 00456522 00000002
0x0034fdbc:  004a8d34 0000194b 7ee61fc4 7ee61fc4
0x0034fdcc:  004ab60c 0034fe00 7ee3e02a 0000000d
0x0034fddc:  004569b5 0034fde8 004b8000 fa987654
0x0034fdec:  40e33ddf 00000000 7ee61fc4 7ee61fc4
Backtrace:
=>1 0x7bc42cfc stub_entry_point+0x4c(dll=0x4a8d34, name=0x194b) [/build/buildd/wine-0.9.46/dlls/ntdll/loader.c:189] in ntdll (0x0034fe00)
  2 0x00456522 in todolist (+0x56522) (0x0034fe58)
  3 0x0047f928 in todolist (+0x7f928) (0x0034ff08)
  4 0x7b874c7e start_process+0xee(arg=0x0) [/build/buildd/wine-0.9.46/dlls/kernel32/process.c:839] in kernel32 (0x0034ffe8)
  5 0xb7de99d7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7bc42cfc stub_entry_point+0x4c [/build/buildd/wine-0.9.46/dlls/ntdll/loader.c:189] in ntdll: subl     $4,%esp
Unable to open file '/build/buildd/wine-0.9.46/dlls/ntdll/loader.c'
Modules:
Module  Address                 Debug info      Name (61 modules)
PE        400000-  4e0000       Export          todolist
PE      5f400000-5f4ed000       Deferred        mfc42
ELF     7b800000-7b929000       Dwarf           kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Dwarf           ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e339000-7e36b000       Deferred        uxtheme<elf>
  \-PE  7e340000-7e36b000       \               uxtheme
ELF     7e3f5000-7e3fa000       Deferred        libxfixes.so.3
ELF     7e3fa000-7e403000       Deferred        libxcursor.so.1
ELF     7e415000-7e4b5000       Deferred        libgl.so.1
ELF     7e4b5000-7e4ba000       Deferred        libxdmcp.so.6
ELF     7e4ba000-7e5ab000       Deferred        libx11.so.6
ELF     7e5ab000-7e5b9000       Deferred        libxext.so.6
ELF     7e5b9000-7e5be000       Deferred        libxxf86vm.so.1
ELF     7e5be000-7e5d6000       Deferred        libice.so.6
ELF     7e5d6000-7e5de000       Deferred        libsm.so.6
ELF     7e5de000-7e669000       Deferred        winex11<elf>
  \-PE  7e5f0000-7e669000       \               winex11
ELF     7e72e000-7e74e000       Deferred        libexpat.so.1
ELF     7e74e000-7e779000       Deferred        libfontconfig.so.1
ELF     7e779000-7e78e000       Deferred        libz.so.1
ELF     7e78e000-7e7fe000       Deferred        libfreetype.so.6
ELF     7e7fe000-7e89c000       Deferred        oleaut32<elf>
  \-PE  7e810000-7e89c000       \               oleaut32
ELF     7e89c000-7e8af000       Deferred        libresolv.so.2
ELF     7e8b3000-7e8b9000       Deferred        libxrandr.so.2
ELF     7e8b9000-7e8c1000       Deferred        libxrender.so.1
ELF     7e8c1000-7e8df000       Deferred        iphlpapi<elf>
  \-PE  7e8d0000-7e8df000       \               iphlpapi
ELF     7e8df000-7e938000       Deferred        rpcrt4<elf>
  \-PE  7e8f0000-7e938000       \               rpcrt4
ELF     7e938000-7e9d9000       Deferred        ole32<elf>
  \-PE  7e950000-7e9d9000       \               ole32
ELF     7e9d9000-7ea97000       Deferred        comctl32<elf>
  \-PE  7e9e0000-7ea97000       \               comctl32
ELF     7ea97000-7eaf0000       Deferred        shlwapi<elf>
  \-PE  7eab0000-7eaf0000       \               shlwapi
ELF     7eaf0000-7ebf3000       Deferred        shell32<elf>
  \-PE  7eb00000-7ebf3000       \               shell32
ELF     7ebf3000-7ed31000       Deferred        user32<elf>
  \-PE  7ec10000-7ed31000       \               user32
ELF     7ed31000-7ed7a000       Deferred        advapi32<elf>
  \-PE  7ed40000-7ed7a000       \               advapi32
ELF     7ed7a000-7ee15000       Deferred        gdi32<elf>
  \-PE  7ed90000-7ee15000       \               gdi32
ELF     7ee15000-7ee7d000       Deferred        msvcrt<elf>
  \-PE  7ee30000-7ee7d000       \               msvcrt
ELF     7ef9c000-7efa7000       Deferred        libnss_files.so.2
ELF     7efa7000-7efb1000       Deferred        libnss_nis.so.2
ELF     7efb1000-7efc9000       Deferred        libnsl.so.1
ELF     7efc9000-7efee000       Deferred        libm.so.6
ELF     7efee000-7eff1000       Deferred        libxau.so.6
ELF     b7c60000-b7c69000       Deferred        libnss_compat.so.2
ELF     b7c69000-b7c6d000       Deferred        libdl.so.2
ELF     b7c6d000-b7db7000       Deferred        libc.so.6
ELF     b7db7000-b7dcf000       Deferred        libpthread.so.0
ELF     b7de2000-b7ef6000       Dwarf           libwine.so.1
ELF     b7ef6000-b7f03000       Deferred        xvnkb.so.0.2.9
ELF     b7f06000-b7f22000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\todolist\ToDoList.exe
        00000009    0 <==
wine: Call from 0x456522 to unimplemented function MFC42.DLL.6475, aborting
wine: Call from 0x456522 to unimplemented function MFC42.DLL.6475, aborting

```

---

### Post by pt123 on 2007-11-21
do you have the mfc42.dll file in the system32 folder?

/home/yourusernamepar/.wine/drive_c/windows/system32

also what version of wine are you using?

---

### Post by itmanvn on 2007-11-21
> **pt123 said:**
> 1. do you have the mfc42.dll file in the system32 folder?

/home/yourusernamepar/.wine/drive_c/windows/system32

2. also what version of wine are you using?

1. yup
2. wine-0.9.46

help me pls :(

---

### Post by pt123 on 2007-11-23
I am using wine-0.9.49

but I am sure todo list was working for me on  0.9.46

what version of todolist are you running?
Also try running the app. like this.
```

wine "c:\Program Files\ToDoList\ToDoList.exe"

```

Are you running Wine on a virtual desktop like me?

And finally what is file size of your MFC42.dll file

---

### Post by itmanvn on 2007-11-23
> **pt123 said:**
> I am using wine-0.9.49

but I am sure todo list was working for me on  0.9.46

what version of todolist are you running?
Also try running the app. like this.
```

wine "c:\Program Files\ToDoList\ToDoList.exe"

```

Are you running Wine on a virtual desktop like me?

And finally what is file size of your MFC42.dll file

Hi pt123,

I've just upgraded to lastest version of Wine 0.9.49 but still not work for me

MFC42.DLL: 918.3 KB (940304 bytes) - 1997-08-05 09:18:50

Could you send me your todolist and mfc42.dll? I can't live without todolist :mad:

---

### Post by pt123 on 2007-11-23
What version is your todolist?

mine is:4.10.7

Anyway my MFC is 1004KB

it is attached below

---

### Post by itmanvn on 2007-11-23
> **pt123 said:**
> What version is your todolist?

mine is:4.10.7

Anyway my MFC is 1004KB

it is attached below

Great !!!!!!! It's work for me now: Todolist v5.3 [http://www.abstractspoon.com/todolist_beta_exe.zip](http://www.abstractspoon.com/todolist_beta_exe.zip)
With your MFC42.DLL. You are my hero :lolflag:

---

### Post by pt123 on 2007-11-24
Good to hear, on 5.3 do the right click menus work, because on 4.9 they dont?

---

### Post by bargol on 2008-01-21
Hello,

I tried 5.3 and 5.4, but i get always the same error.
Can anyone help?

```

$ wine ToDoList.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:winhttp:WinHttpCheckPlatform stub
wine: Unhandled page fault on read access to 0x00000020 at address 0x407602 (thread 0009), starting debugger...
WineDbg starting on pid 0008
Unhandled exception: page fault on read access to 0x00000020 in 32-bit code (0x00407602).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00407602 ESP:0033a0dc EBP:0033a0fc EFLAGS:00010202(   - 00      - -RI1)
 EAX:0033a0ec EBX:00000014 ECX:0033a20c EDX:00000119
 ESI:0033a20c EDI:00000000
Stack dump:
0x0033a0dc:  0033a0ec fffffef1 00000000 0033a1b8
0x0033a0ec:  00711fb0 0033a1b8 00711fb0 0033a0e8
0x0033a0fc:  0033a174 004076cf 00000000 00000000
0x0033a10c:  00000119 0000000a fffffef1 00000001
0x0033a11c:  0033a150 0033a160 004485e2 00000000
0x0033a12c:  0033a160 00000001 0000000a 00000000
Backtrace:
=>1 0x00407602 in todolist (+0x7602) (0x0033a0fc)
  2 0x004076cf in todolist (+0x76cf) (0x0033a174)
  3 0x0044819b in todolist (+0x4819b) (0x0033a22c)
  4 0x0044810b in todolist (+0x4810b) (0x0033a2c0)
  5 0x73dd1b9b in mfc42 (+0x1b9b) (0x0033a2e0)
  6 0x73dd1b05 in mfc42 (+0x1b05) (0x0033a340)
  7 0x73dd1a58 in mfc42 (+0x1a58) (0x0033a360)
  8 0x73e6847d in mfc42 (+0x9847d) (0x0033a38c)
  10 0x7ed0447e WINPROC_wrapper+0x34e() in user32 (0x0033a3fc)
  11 0x7ed06cd6 in user32 (+0xa6cd6) (0x0033b4fc)
  12 0x7ed09a3f in user32 (+0xa9a3f) (0x0033b53c)
  13 0x7ecd17be in user32 (+0x717be) (0x0033b5ac)
  14 0x7ecd470f in user32 (+0x7470f) (0x0033b60c)
  15 0x7ecd4bca SendMessageW+0x4c() in user32 (0x0033b66c)
  16 0x7ec9b051 in user32 (+0x3b051) (0x0033b72c)
  17 0x7ec9c127 DefWindowProcA+0xb0() in user32 (0x0033b76c)
  18 0x7ec9a52a DefDlgProcA+0x17d() in user32 (0x0033b79c)
  19 0x7ed0414a WINPROC_wrapper+0x1a() in user32 (0x0033b7cc)
  20 0x7ed0447e WINPROC_wrapper+0x34e() in user32 (0x0033b80c)
  21 0x7ed09d38 CallWindowProcA+0x5d() in user32 (0x0033b84c)
  22 0x73dd216b in mfc42 (+0x216b) (0x0033b86c)
  23 0x73dd1bb2 in mfc42 (+0x1bb2) (0x0033b888)
  24 0x73dd1b05 in mfc42 (+0x1b05) (0x0033b8e8)
  25 0x73dd1a58 in mfc42 (+0x1a58) (0x0033b908)
  26 0x73e6847d in mfc42 (+0x9847d) (0x0033b934)
  27 0x7ed0414a WINPROC_wrapper+0x1a() in user32 (0x0033b964)
  28 0x7ed0447e WINPROC_wrapper+0x34e() in user32 (0x0033b9a4)
  29 0x7ed06cd6 in user32 (+0xa6cd6) (0x0033caa4)
  30 0x7ed09a3f in user32 (+0xa9a3f) (0x0033cae4)
  31 0x7ecd17be in user32 (+0x717be) (0x0033cb54)
  32 0x7ecd470f in user32 (+0x7470f) (0x0033cbb4)
  33 0x7ecd4bca SendMessageW+0x4c() in user32 (0x0033cc14)
  34 0x7ed0223e in user32 (+0xa223e) (0x0033cd94)
  35 0x7ed02b03 SetWindowPos+0xd2() in user32 (0x0033ce14)
  36 0x7ed03598 MoveWindow+0x64() in user32 (0x0033ce54)
  37 0x73e2eef8 in mfc42 (+0x5eef8) (0x0033ce74)
  38 0x00436af6 in todolist (+0x36af6) (0x0033cec4)
  39 0x004478a6 in todolist (+0x478a6) (0x0033cef8)
  40 0x0046b2d7 in todolist (+0x6b2d7) (0x0033cf24)
  41 0x0046b24d in todolist (+0x6b24d) (0x0033cf54)
  42 0x004658db in todolist (+0x658db) (0x0033cf78)
  43 0x00463194 in todolist (+0x63194) (0x0033cfc4)
  44 0x73dd1e91 in mfc42 (+0x1e91) (0x0033d040)
  45 0x73dd1b9b in mfc42 (+0x1b9b) (0x0033d060)
  46 0x73dd1b05 in mfc42 (+0x1b05) (0x0033d0c0)
  47 0x73dd1a58 in mfc42 (+0x1a58) (0x0033d0e0)
  48 0x73e6847d in mfc42 (+0x9847d) (0x0033d10c)
  49 0x7ed0414a WINPROC_wrapper+0x1a() in user32 (0x0033d13c)
  50 0x7ed0447e WINPROC_wrapper+0x34e() in user32 (0x0033d17c)
  51 0x7ed09b5c in user32 (+0xa9b5c) (0x0033d1bc)
  52 0x7ecd17be in user32 (+0x717be) (0x0033d22c)
  53 0x7ecd470f in user32 (+0x7470f) (0x0033d28c)
  54 0x7ecd4b77 SendMessageA+0x53() in user32 (0x0033d2ec)
  55 0x7e885bd6 X11DRV_CreateWindow+0xb2e() in winex11 (0x0033d48c)
  56 0x7ecfc89b in user32 (+0x9c89b) (0x0033d6cc)
  57 0x7ecfe0bb CreateWindowExA+0xb3() in user32 (0x0033d92c)
  58 0x73ddbba4 in mfc42 (+0xbba4) (0x0033d99c)
  59 0x73ddd94d in mfc42 (+0xd94d) (0x0033d9dc)
  60 0x73ddd726 in mfc42 (+0xd726) (0x0033da1c)
  61 0x00462eb8 in todolist (+0x62eb8) (0x0033fe48)
  62 0x73ddcf74 in mfc42 (+0xcf74) (0x0033ff08)
  63 0x7b86eb3d in kernel32 (+0x4eb3d) (0x0033ffe8)
  64 0xb7e3a1cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x00407602: pushl       0x20(%edi)
Wine-dbg>

```

---

### Post by pt123 on 2008-01-21
what version is your mfc & wine?

---

### Post by bargol on 2008-01-22
Hi,

i used the given mfc from this thread with wine-0.9.53 from the [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) source.

I hope you can help me. This software rocks for me.

---

### Post by pt123 on 2008-01-23
mine is 4.10.7, 
how are you running it what command are you giving to run the application?

I am running it by this command
wine "c:\Program Files\ToDoList\ToDoList.exe"

I have placed the .exe file in the ~/.wine//drive_c/Program Files/ToDoList
Folder

Not sure if it helps

---

### Post by itmanvn on 2008-04-29
Hi all, I recenty found a very cool program called ZIM, google it :D

---

### Post by pt123 on 2008-04-29
Zim (wiki) doesn't not do tasks.

---

### Post by frodeflintstone on 2008-06-11
Hello to all,

I just installed wine(0.9.59) + the mfc file from this thread + the msxml3 files from my windows xp box + the lates todolist (5.5.6).  Everything works except when i want to save the todolist.  I get an error saying that it contains characters that cannot be saved and I need to remove them before I can save it.  


Ok, so i was halfway through typing this post when i remembered that i had another version of todolist (5.5.2).  I copied it over and it works fine.

maybe this will help someone.

---

### Post by frodeflintstone on 2008-06-11
Oh,  I also copied over the following files from my xp machine (which may have fixed the problem):


msxml.dll
msxml2.dll
msxml2r.dll
msxml3.dll
msxml3r.dll
msxml4.dll
msxml4r.dll
msxml6.dll
msxml6r.dll
msxmlr.dll

As mentioned, I have no idea if they fixed the issue.

Hope this helps.

-r

---

