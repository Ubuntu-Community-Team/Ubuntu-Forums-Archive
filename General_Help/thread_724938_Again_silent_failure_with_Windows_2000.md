---
title: "Again silent failure with Windows 2000"
date: 2008-03-15
forum: General Help
---

### Post by steve196 on 2008-03-15
Alpha 453 again fails to start and generates no error message.
Here is Windbg output
```

Microsoft (R) Windows Debugger Version 6.8.0004.0 X86
Copyright (c) Microsoft Corporation. All rights reserved.

CommandLine: J:\Wubi-8.04-alpha-rev453.exe
Symbol search path is: *** Invalid ***
****************************************************************************
* Symbol loading may be unreliable without a symbol search path.           *
* Use .symfix to have the debugger choose a symbol path.                   *
* After setting your symbol path, use .reload to refresh symbol locations. *
****************************************************************************
Executable search path is: 
ModLoad: 00400000 00457000   image00400000
ModLoad: 77f80000 77ffd000   ntdll.dll
ModLoad: 7c570000 7c624000   F:\WINNT\system32\KERNEL32.dll
ModLoad: 77e10000 77e6f000   F:\WINNT\system32\USER32.dll
ModLoad: 77f40000 77f7c000   F:\WINNT\system32\GDI32.dll
ModLoad: 782f0000 78538000   F:\WINNT\system32\SHELL32.dll
ModLoad: 7c2d0000 7c332000   F:\WINNT\system32\ADVAPI32.DLL
ModLoad: 77d30000 77d9f000   F:\WINNT\system32\RPCRT4.DLL
ModLoad: 70a70000 70ad6000   F:\WINNT\system32\SHLWAPI.DLL
ModLoad: 78000000 78045000   F:\WINNT\system32\msvcrt.dll
ModLoad: 71710000 71794000   F:\WINNT\system32\COMCTL32.DLL
ModLoad: 7ce20000 7cf0f000   F:\WINNT\system32\ole32.dll
ModLoad: 77820000 77827000   F:\WINNT\system32\VERSION.dll
ModLoad: 759b0000 759b6000   F:\WINNT\system32\LZ32.DLL
(540.5f4): Break instruction exception - code 80000003 (first chance)
eax=00000000 ebx=00131f04 ecx=00000009 edx=00000000 esi=7ffdf000 edi=00131f90
eip=77f813b1 esp=0012f984 ebp=0012fc98 iopl=0         nv up ei pl nz na po nc
cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00000202
*** ERROR: Symbol file could not be found.  Defaulted to export symbols for ntdll.dll - 
ntdll!DbgBreakPoint:
77f813b1 cc              int     3
0:000> g
ModLoad: 6e420000 6e426000   F:\WINNT\system32\INDICDLL.dll
ModLoad: 75e60000 75e7a000   F:\WINNT\system32\IMM32.dll
ModLoad: 719b0000 719b8000   F:\WINNT\system32\SHFOLDER.dll
ModLoad: 779b0000 77a4c000   F:\WINNT\system32\OLEAUT32.DLL
ModLoad: 775a0000 77626000   F:\WINNT\system32\CLBCATQ.DLL
ModLoad: 77840000 7787e000   F:\WINNT\system32\cscui.dll
ModLoad: 770c0000 770e3000   F:\WINNT\system32\CSCDLL.DLL
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 70c00000 70c08000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\test64.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10005000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\UserInfo.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 772b0000 7731d000   F:\WINNT\system32\RichEd20.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10005000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\nsExec.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10009000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\InstallOptions.dll
ModLoad: 76b30000 76b6e000   F:\WINNT\system32\comdlg32.dll
HEAP[Wubi-8.04-alpha-rev453.exe]: Invalid Address specified to RtlFreeHeap( 130000, 18aee8 )
(540.5f4): Break instruction exception - code 80000003 (first chance)
eax=0018aee0 ebx=0018aee0 ecx=0012f748 edx=0012f4e2 esi=00130000 edi=0018aee0
eip=77f813b1 esp=0012f6c8 ebp=0012f6cc iopl=0         nv up ei pl nz na po nc
cs=001b  ss=0023  ds=0023  es=0023  fs=0038  gs=0000             efl=00000202
ntdll!DbgBreakPoint:
77f813b1 cc              int     3
0:000> g
HEAP[Wubi-8.04-alpha-rev453.exe]: Invalid Address specified to RtlFreeHeap( 130000, 18bf00 )
(540.5f4): Break instruction exception - code 80000003 (first chance)
eax=0018bef8 ebx=0018bef8 ecx=0012f748 edx=0012f4e2 esi=00130000 edi=0018bef8
eip=77f813b1 esp=0012f6c8 ebp=0012f6cc iopl=0         nv up ei pl nz na po nc
cs=001b  ss=0023  ds=0023  es=0023  fs=0038  gs=0000             efl=00000202
ntdll!DbgBreakPoint:
77f813b1 cc              int     3
0:000> g
HEAP[Wubi-8.04-alpha-rev453.exe]: Invalid Address specified to RtlFreeHeap( 130000, 18cf18 )
(540.5f4): Break instruction exception - code 80000003 (first chance)
eax=0018cf10 ebx=0018cf10 ecx=0012f748 edx=0012f4e2 esi=00130000 edi=0018cf10
eip=77f813b1 esp=0012f6c8 ebp=0012f6cc iopl=0         nv up ei pl nz na po nc
cs=001b  ss=0023  ds=0023  es=0023  fs=0038  gs=0000             efl=00000202
ntdll!DbgBreakPoint:
77f813b1 cc              int     3
0:000> g
HEAP[Wubi-8.04-alpha-rev453.exe]: Invalid Address specified to RtlFreeHeap( 130000, 18e5c0 )
(540.5f4): Break instruction exception - code 80000003 (first chance)
eax=0018e5b8 ebx=0018e5b8 ecx=0012f748 edx=0012f4e2 esi=00130000 edi=0018e5b8
eip=77f813b1 esp=0012f6c8 ebp=0012f6cc iopl=0         nv up ei pl nz na po nc
cs=001b  ss=0023  ds=0023  es=0023  fs=0038  gs=0000             efl=00000202
ntdll!DbgBreakPoint:
77f813b1 cc              int     3

```

---

### Post by steve196 on 2008-03-15
Again in the debugger it runs. I made a few more gos with the same error message, and then suddenly it continued. Without the debugger it does not continue.

---

### Post by steve196 on 2008-03-15
This is the complete log:

```

Microsoft (R) Windows Debugger Version 6.8.0004.0 X86
Copyright (c) Microsoft Corporation. All rights reserved.

CommandLine: J:\Wubi-8.04-alpha-rev453.exe
Symbol search path is: *** Invalid ***
****************************************************************************
* Symbol loading may be unreliable without a symbol search path.           *
* Use .symfix to have the debugger choose a symbol path.                   *
* After setting your symbol path, use .reload to refresh symbol locations. *
****************************************************************************
Executable search path is: 
ModLoad: 00400000 00457000   image00400000
ModLoad: 77f80000 77ffd000   ntdll.dll
ModLoad: 7c570000 7c624000   F:\WINNT\system32\KERNEL32.dll
ModLoad: 77e10000 77e6f000   F:\WINNT\system32\USER32.dll
ModLoad: 77f40000 77f7c000   F:\WINNT\system32\GDI32.dll
ModLoad: 782f0000 78538000   F:\WINNT\system32\SHELL32.dll
ModLoad: 7c2d0000 7c332000   F:\WINNT\system32\ADVAPI32.DLL
ModLoad: 77d30000 77d9f000   F:\WINNT\system32\RPCRT4.DLL
ModLoad: 70a70000 70ad6000   F:\WINNT\system32\SHLWAPI.DLL
ModLoad: 78000000 78045000   F:\WINNT\system32\msvcrt.dll
ModLoad: 71710000 71794000   F:\WINNT\system32\COMCTL32.DLL
ModLoad: 7ce20000 7cf0f000   F:\WINNT\system32\ole32.dll
ModLoad: 77820000 77827000   F:\WINNT\system32\VERSION.dll
ModLoad: 759b0000 759b6000   F:\WINNT\system32\LZ32.DLL
(540.5f4): Break instruction exception - code 80000003 (first chance)
eax=00000000 ebx=00131f04 ecx=00000009 edx=00000000 esi=7ffdf000 edi=00131f90
eip=77f813b1 esp=0012f984 ebp=0012fc98 iopl=0         nv up ei pl nz na po nc
cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00000202
*** ERROR: Symbol file could not be found.  Defaulted to export symbols for ntdll.dll - 
ntdll!DbgBreakPoint:
77f813b1 cc              int     3
0:000> g
ModLoad: 6e420000 6e426000   F:\WINNT\system32\INDICDLL.dll
ModLoad: 75e60000 75e7a000   F:\WINNT\system32\IMM32.dll
ModLoad: 719b0000 719b8000   F:\WINNT\system32\SHFOLDER.dll
ModLoad: 779b0000 77a4c000   F:\WINNT\system32\OLEAUT32.DLL
ModLoad: 775a0000 77626000   F:\WINNT\system32\CLBCATQ.DLL
ModLoad: 77840000 7787e000   F:\WINNT\system32\cscui.dll
ModLoad: 770c0000 770e3000   F:\WINNT\system32\CSCDLL.DLL
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 70c00000 70c08000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\test64.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10005000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\UserInfo.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 772b0000 7731d000   F:\WINNT\system32\RichEd20.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10005000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\nsExec.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10009000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\InstallOptions.dll
ModLoad: 76b30000 76b6e000   F:\WINNT\system32\comdlg32.dll
HEAP[Wubi-8.04-alpha-rev453.exe]: Invalid Address specified to RtlFreeHeap( 130000, 18aee8 )
(540.5f4): Break instruction exception - code 80000003 (first chance)
eax=0018aee0 ebx=0018aee0 ecx=0012f748 edx=0012f4e2 esi=00130000 edi=0018aee0
eip=77f813b1 esp=0012f6c8 ebp=0012f6cc iopl=0         nv up ei pl nz na po nc
cs=001b  ss=0023  ds=0023  es=0023  fs=0038  gs=0000             efl=00000202
ntdll!DbgBreakPoint:
77f813b1 cc              int     3
0:000> g
HEAP[Wubi-8.04-alpha-rev453.exe]: Invalid Address specified to RtlFreeHeap( 130000, 18bf00 )
(540.5f4): Break instruction exception - code 80000003 (first chance)
eax=0018bef8 ebx=0018bef8 ecx=0012f748 edx=0012f4e2 esi=00130000 edi=0018bef8
eip=77f813b1 esp=0012f6c8 ebp=0012f6cc iopl=0         nv up ei pl nz na po nc
cs=001b  ss=0023  ds=0023  es=0023  fs=0038  gs=0000             efl=00000202
ntdll!DbgBreakPoint:
77f813b1 cc              int     3
0:000> g
HEAP[Wubi-8.04-alpha-rev453.exe]: Invalid Address specified to RtlFreeHeap( 130000, 18cf18 )
(540.5f4): Break instruction exception - code 80000003 (first chance)
eax=0018cf10 ebx=0018cf10 ecx=0012f748 edx=0012f4e2 esi=00130000 edi=0018cf10
eip=77f813b1 esp=0012f6c8 ebp=0012f6cc iopl=0         nv up ei pl nz na po nc
cs=001b  ss=0023  ds=0023  es=0023  fs=0038  gs=0000             efl=00000202
ntdll!DbgBreakPoint:
77f813b1 cc              int     3
0:000> g
HEAP[Wubi-8.04-alpha-rev453.exe]: Invalid Address specified to RtlFreeHeap( 130000, 18e5c0 )
(540.5f4): Break instruction exception - code 80000003 (first chance)
eax=0018e5b8 ebx=0018e5b8 ecx=0012f748 edx=0012f4e2 esi=00130000 edi=0018e5b8
eip=77f813b1 esp=0012f6c8 ebp=0012f6cc iopl=0         nv up ei pl nz na po nc
cs=001b  ss=0023  ds=0023  es=0023  fs=0038  gs=0000             efl=00000202
ntdll!DbgBreakPoint:
77f813b1 cc              int     3
0:000> g
HEAP[Wubi-8.04-alpha-rev453.exe]: Invalid Address specified to RtlFreeHeap( 130000, 18f5d8 )
(540.5f4): Break instruction exception - code 80000003 (first chance)
eax=0018f5d0 ebx=0018f5d0 ecx=0012f748 edx=0012f4e2 esi=00130000 edi=0018f5d0
eip=77f813b1 esp=0012f6c8 ebp=0012f6cc iopl=0         nv up ei pl nz na po nc
cs=001b  ss=0023  ds=0023  es=0023  fs=0038  gs=0000             efl=00000202
ntdll!DbgBreakPoint:
77f813b1 cc              int     3
0:000> g
HEAP[Wubi-8.04-alpha-rev453.exe]: Invalid Address specified to RtlFreeHeap( 130000, 1905f0 )
(540.5f4): Break instruction exception - code 80000003 (first chance)
eax=001905e8 ebx=001905e8 ecx=0012f748 edx=0012f4e2 esi=00130000 edi=001905e8
eip=77f813b1 esp=0012f6c8 ebp=0012f6cc iopl=0         nv up ei pl nz na po nc
cs=001b  ss=0023  ds=0023  es=0023  fs=0038  gs=0000             efl=00000202
ntdll!DbgBreakPoint:
77f813b1 cc              int     3
0:000> g
ModLoad: 02870000 02875000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\tooltips.dll
ModLoad: 02890000 02895000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\tooltips.dll
ModLoad: 028b0000 028b5000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\tooltips.dll
ModLoad: 028d0000 028d5000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\tooltips.dll
ModLoad: 02900000 02905000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\tooltips.dll
ModLoad: 02920000 02925000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\tooltips.dll
ModLoad: 02940000 02945000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\tooltips.dll
ModLoad: 02960000 02965000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\tooltips.dll
ModLoad: 02990000 02995000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\tooltips.dll
ModLoad: 061f0000 06205000   F:\WINNT\system32\SSSensor.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10005000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\nsExec.dll
ModLoad: 10000000 10005000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\Dialer.dll
ModLoad: 63000000 63095000   F:\WINNT\system32\wininet.dll
ModLoad: 7c740000 7c7c7000   F:\WINNT\system32\CRYPT32.dll
ModLoad: 77430000 77440000   F:\WINNT\system32\MSASN1.DLL
ModLoad: 774e0000 77513000   F:\WINNT\system32\RASAPI32.DLL
ModLoad: 774c0000 774d1000   F:\WINNT\system32\RASMAN.DLL
ModLoad: 75030000 75044000   F:\WINNT\system32\WS2_32.DLL
ModLoad: 75020000 75028000   F:\WINNT\system32\WS2HELP.DLL
ModLoad: 77530000 77552000   F:\WINNT\system32\TAPI32.DLL
ModLoad: 77830000 7783e000   F:\WINNT\system32\RTUTILS.DLL
ModLoad: 75ab0000 75ab5000   F:\WINNT\system32\sensapi.dll
ModLoad: 7c0f0000 7c151000   F:\WINNT\system32\USERENV.DLL
ModLoad: 7cdc0000 7ce10000   F:\WINNT\system32\netapi32.dll
ModLoad: 7c340000 7c34f000   F:\WINNT\system32\Secur32.dll
ModLoad: 77bf0000 77c01000   F:\WINNT\system32\NTDSAPI.dll
ModLoad: 77980000 779a4000   F:\WINNT\system32\DNSAPI.DLL
ModLoad: 75050000 75058000   F:\WINNT\system32\WSOCK32.dll
ModLoad: 77950000 7797a000   F:\WINNT\system32\WLDAP32.DLL
ModLoad: 751c0000 751c6000   F:\WINNT\system32\NETRAP.dll
ModLoad: 75150000 7515f000   F:\WINNT\system32\SAMLIB.dll
ModLoad: 68680000 686d8000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\metadl.dll
ModLoad: 74fd0000 74fee000   F:\WINNT\system32\msafd.dll
ModLoad: 75010000 75017000   F:\WINNT\System32\wshtcpip.dll
ModLoad: 782c0000 782cc000   F:\WINNT\System32\rnr20.dll
ModLoad: 77340000 77353000   F:\WINNT\system32\iphlpapi.dll
ModLoad: 77520000 77525000   F:\WINNT\system32\ICMP.DLL
ModLoad: 77320000 77337000   F:\WINNT\system32\MPRAPI.DLL
ModLoad: 773b0000 773df000   F:\WINNT\system32\ACTIVEDS.DLL
ModLoad: 77380000 773a3000   F:\WINNT\system32\ADSLDPC.DLL
ModLoad: 77880000 7790e000   F:\WINNT\system32\SETUPAPI.DLL
ModLoad: 77360000 77379000   F:\WINNT\system32\DHCPCSVC.DLL
ModLoad: 777e0000 777e8000   F:\WINNT\System32\winrnr.dll
ModLoad: 777f0000 777f5000   F:\WINNT\system32\rasadhlp.dll
ModLoad: 68680000 686d8000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\metadl.dll
ModLoad: 68680000 686d8000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\metadl.dll
ModLoad: 10000000 10005000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\nsExec.dll
ModLoad: 68680000 686d8000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\metadl.dll
ModLoad: 10000000 10005000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\nsExec.dll
ModLoad: 10000000 10005000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\nsExec.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 04d20000 04f24000   F:\WINNT\system32\MSI.DLL
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 1001e000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\mkpasswd.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\System.dll
ModLoad: 61c00000 61c08000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\diskimage.dll
ModLoad: 61c00000 61c08000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\diskimage.dll
ModLoad: 61c00000 61c08000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\diskimage.dll
ModLoad: 10000000 10009000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\InstallOptions.dll
ModLoad: 76b30000 76b6e000   F:\WINNT\system32\comdlg32.dll
eax=00000001 ebx=00000000 ecx=7ffde1dc edx=00000000 esi=77f8ee04 edi=00000000
eip=77f8ee0f esp=0012fd60 ebp=0012fe28 iopl=0         nv up ei pl zr na pe nc
cs=001b  ss=0023  ds=0023  es=0023  fs=0038  gs=0000             efl=00000246
ntdll!ZwTerminateProcess+0xb:
77f8ee0f c20800          ret     8

```

---

### Post by steve196 on 2008-03-15
After successfully running it through the debugger it has still the old errors:
* ro has to be changed to rw manually in menu.lst for it to work
* During update Synaptic tries and predictably fails to create a link on the fat32 host partition and subsequently leaves stuff unconfigured.

---

### Post by ago on 2008-03-15
> **steve196 said:**
> 
* ro has to be changed to rw manually in menu.lst for it to work
That is next on my agenda:
[https://bugs.launchpad.net/wubi/+bug/201750](https://bugs.launchpad.net/wubi/+bug/201750)

> * During update Synaptic tries and predictably fails to create a link on the fat32 host partition and subsequently leaves stuff unconfigured.
That should have been fixed, can you try with today daily ISO?

Re crash, is that reproducible? Can you provide the windows logs? They are in you %temp% folder

---

### Post by steve196 on 2008-03-16
I have uninstalled without backing up the .iso . Now silent failure does not happen. I have no log of the silent failure, because it was overwritten by the successful run inside the debugger.

---

### Post by steve196 on 2008-03-16
Tried again, because before it had found an old .iso in its own directory. Now the failure happened again.

```
============ Installer ============
PLUGINSDIR=F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsg6.tmp
detect_all
Parsing cmdline "J:\Wubi-8.04-alpha-rev453.exe" 
debug=, 32bit=, cdboot=
arch=i386
DetectCD
      Is Valid CD J:
CDInfo cleared
      Is Valid CD I:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD J:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
isInstallationDrive E:\ubuntu
isInstallationDrive F:\ubuntu
isInstallationDrive G:\ubuntu
isInstallationDrive H:\ubuntu
isInstallationDrive J:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
FreeSpace in D: is 12698
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
Found BackupFolder D:\ubuntu-backup
GMT=1
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=9c6fbf74e7fb42c
ComputerName=9C6FBF74E7FB42C
EnvUsername=Administrator
UserDomain=9C6FBF74E7FB42C
UserInfoName=Administrator
UserProfileFolder=F:\Documents and Settings\Administrator.9C6FBF74E7FB42C
UserProfileName=Administrator 
============ Installer ============
PLUGINSDIR=F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nse8.tmp
detect_all
Parsing cmdline "J:\Wubi-8.04-alpha-rev453.exe" 
debug=, 32bit=, cdboot=
arch=i386
DetectCD
      Is Valid CD J:
CDInfo cleared
      Is Valid CD I:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD J:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
isInstallationDrive E:\ubuntu
isInstallationDrive F:\ubuntu
isInstallationDrive G:\ubuntu
isInstallationDrive H:\ubuntu
isInstallationDrive J:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
FreeSpace in D: is 12698
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
Found BackupFolder D:\ubuntu-backup
GMT=1
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=9c6fbf74e7fb42c
ComputerName=9C6FBF74E7FB42C
EnvUsername=Administrator
UserDomain=9C6FBF74E7FB42C
UserInfoName=Administrator
UserProfileFolder=F:\Documents and Settings\Administrator.9C6FBF74E7FB42C
UserProfileName=Administrator 
============ Installer ============
PLUGINSDIR=F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nszA.tmp
detect_all
Parsing cmdline "J:\Wubi-8.04-alpha-rev453.exe" 
debug=, 32bit=, cdboot=
arch=i386
DetectCD
      Is Valid CD J:
CDInfo cleared
      Is Valid CD I:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD J:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
isInstallationDrive E:\ubuntu
isInstallationDrive F:\ubuntu
isInstallationDrive G:\ubuntu
isInstallationDrive H:\ubuntu
isInstallationDrive J:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
FreeSpace in D: is 12698
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
Found BackupFolder D:\ubuntu-backup
GMT=1
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=9c6fbf74e7fb42c
ComputerName=9C6FBF74E7FB42C
EnvUsername=Administrator
UserDomain=9C6FBF74E7FB42C
UserInfoName=Administrator
UserProfileFolder=F:\Documents and Settings\Administrator.9C6FBF74E7FB42C
UserProfileName=Administrator 
============ Installer ============
PLUGINSDIR=F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nslC.tmp
detect_all
Parsing cmdline "J:\Wubi-8.04-alpha-rev453.exe" 
debug=, 32bit=, cdboot=
arch=i386
DetectCD
      Is Valid CD J:
CDInfo cleared
      Is Valid CD I:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD J:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
isInstallationDrive E:\ubuntu
isInstallationDrive F:\ubuntu
isInstallationDrive G:\ubuntu
isInstallationDrive H:\ubuntu
isInstallationDrive J:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
FreeSpace in D: is 12698
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
Found BackupFolder D:\ubuntu-backup
GMT=1
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=9c6fbf74e7fb42c
ComputerName=9C6FBF74E7FB42C
EnvUsername=Administrator
UserDomain=9C6FBF74E7FB42C
UserInfoName=Administrator
UserProfileFolder=F:\Documents and Settings\Administrator.9C6FBF74E7FB42C
UserProfileName=Administrator 
============ Installer ============
PLUGINSDIR=F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nszE.tmp
detect_all
Parsing cmdline J:\Wubi-8.04-alpha-rev453.exe
debug=, 32bit=, cdboot=
arch=i386
DetectCD
      Is Valid CD J:
CDInfo cleared
      Is Valid CD I:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD J:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
isInstallationDrive E:\ubuntu
isInstallationDrive F:\ubuntu
isInstallationDrive G:\ubuntu
isInstallationDrive H:\ubuntu
isInstallationDrive J:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
FreeSpace in D: is 12698
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
Found BackupFolder D:\ubuntu-backup
GMT=1
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=9c6fbf74e7fb42c
ComputerName=9C6FBF74E7FB42C
EnvUsername=Administrator
UserDomain=9C6FBF74E7FB42C
UserInfoName=Administrator
UserProfileFolder=F:\Documents and Settings\Administrator.9C6FBF74E7FB42C
UserProfileName=Administrator 
ShowMainPage
Making drive list
Drive & Path name 1732; Volume name festplottn; Max #/chars in vol name 1614732; Volume Serial # -1979884213; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT; File System Name Size HDD
Skipping drive C:, not enough free space 771 <= {MinSizeMB}
Drive & Path name 1732; Volume name BISSLGRESSA; Max #/chars in vol name 1614736; Volume Serial # 946748791; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Adding drive D:
Drive & Path name 1732; Volume name DRIVE_E; Max #/chars in vol name 1614740; Volume Serial # 742184440; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT; File System Name Size HDD
Skipping drive E:, not enough free space 48 <= {MinSizeMB}
Drive & Path name 1732; Volume name DRIVE_I; Max #/chars in vol name 1614744; Volume Serial # -62015557; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Skipping drive F:, not enough free space 211 <= {MinSizeMB}
Drive & Path name 1732; Volume name drive_g; Max #/chars in vol name 1614748; Volume Serial # -2010230431; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Skipping drive G:, not enough free space 169 <= {MinSizeMB}
Drive & Path name 1732; Volume name NEW VOLUME; Max #/chars in vol name 1614752; Volume Serial # 543681005; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Skipping drive H:, not enough free space 845 <= {MinSizeMB}
Drive & Path name 1732; Volume name ext; Max #/chars in vol name 1614760; Volume Serial # -666414389; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Skipping drive J:, not enough free space 3252 <= {MinSizeMB}
Drive list = D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 8
PopulateDistroList
DetectIso
      IsValidIso ispoath=D:\ubuntu-backup\hardy-desktop-i386.iso
      ExtractIsoInfo
      F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nszE.tmp\7z.exe e -y -i!.disk\info -oF:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp D:\ubuntu-backup\hardy-desktop-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Alpha i386 (20080222)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Alpha 
      GetDistroInfo distrfullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Alpha i386 (20080222)
AddDistroToList Ubuntu-i386
AddDistroToList Ubuntu-amd64
AddDistroToList Kubuntu-i386
AddDistroToList Kubuntu-amd64
AddDistroToList Kubuntu-KDE4-i386
AddDistroToList Kubuntu-KDE4-amd64
AddDistroToList Xubuntu-i386
AddDistroToList Xubuntu-amd64
DistroList = Ubuntu|Kubuntu|Kubuntu-KDE4|Xubuntu
PopulateLanguageListBox
      GetDistroInfo distrfullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
============ Installer ============
PLUGINSDIR=F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp
detect_all
Parsing cmdline J:\Wubi-8.04-alpha-rev453.exe
debug=, 32bit=, cdboot=
arch=i386
DetectCD
      Is Valid CD J:
CDInfo cleared
      Is Valid CD I:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD J:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
isInstallationDrive E:\ubuntu
isInstallationDrive F:\ubuntu
isInstallationDrive G:\ubuntu
isInstallationDrive H:\ubuntu
isInstallationDrive J:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
FreeSpace in D: is 12698
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
Found BackupFolder D:\ubuntu-backup
GMT=1
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=9c6fbf74e7fb42c
ComputerName=9C6FBF74E7FB42C
EnvUsername=Administrator
UserDomain=9C6FBF74E7FB42C
UserInfoName=Administrator
UserProfileFolder=F:\Documents and Settings\Administrator.9C6FBF74E7FB42C
UserProfileName=Administrator 
ShowMainPage
Making drive list
Drive & Path name 1732; Volume name festplottn; Max #/chars in vol name 1614732; Volume Serial # -1979884213; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT; File System Name Size HDD
Skipping drive C:, not enough free space 771 <= {MinSizeMB}
Drive & Path name 1732; Volume name BISSLGRESSA; Max #/chars in vol name 1614736; Volume Serial # 946748791; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Adding drive D:
Drive & Path name 1732; Volume name DRIVE_E; Max #/chars in vol name 1614740; Volume Serial # 742184440; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT; File System Name Size HDD
Skipping drive E:, not enough free space 48 <= {MinSizeMB}
Drive & Path name 1732; Volume name DRIVE_I; Max #/chars in vol name 1614744; Volume Serial # -62015557; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Skipping drive F:, not enough free space 208 <= {MinSizeMB}
Drive & Path name 1732; Volume name drive_g; Max #/chars in vol name 1614748; Volume Serial # -2010230431; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Skipping drive G:, not enough free space 169 <= {MinSizeMB}
Drive & Path name 1732; Volume name NEW VOLUME; Max #/chars in vol name 1614752; Volume Serial # 543681005; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Skipping drive H:, not enough free space 845 <= {MinSizeMB}
Drive & Path name 1732; Volume name ext; Max #/chars in vol name 1614760; Volume Serial # -666414389; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Skipping drive J:, not enough free space 3252 <= {MinSizeMB}
Drive list = D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 8
PopulateDistroList
DetectIso
      IsValidIso ispoath=D:\ubuntu-backup\hardy-desktop-i386.iso
      ExtractIsoInfo
      F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\7z.exe e -y -i!.disk\info -oF:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp D:\ubuntu-backup\hardy-desktop-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Alpha i386 (20080222)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Alpha 
      GetDistroInfo distrfullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Alpha i386 (20080222)
AddDistroToList Ubuntu-i386
AddDistroToList Ubuntu-amd64
AddDistroToList Kubuntu-i386
AddDistroToList Kubuntu-amd64
AddDistroToList Kubuntu-KDE4-i386
AddDistroToList Kubuntu-KDE4-amd64
AddDistroToList Xubuntu-i386
AddDistroToList Xubuntu-amd64
DistroList = Ubuntu|Kubuntu|Kubuntu-KDE4|Xubuntu
PopulateLanguageListBox
      GetDistroInfo distrfullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrfullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
CreateInstallationFolders
MakeUninstall
Created D:\ubuntu\Uninstall.exe
Created F:\WINNT\Uninstall.exe
Created reg key 1
Created reg key 2
CopyDistFolders
GetIso
DetectCD
      Is Valid CD J:
CDInfo cleared
      Is Valid CD I:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD J:
CDInfo cleared
No CD found
DetectIso
      IsValidIso ispoath=D:\ubuntu-backup\hardy-desktop-i386.iso
      ExtractIsoInfo
      F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsq11.tmp\7z.exe e -y -i!.disk\info -oF:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp D:\ubuntu-backup\hardy-desktop-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Alpha i386 (20080222)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Alpha 
      GetDistroInfo distrfullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Alpha i386 (20080222)
Using D:\ubuntu-backup\hardy-desktop-i386.iso
Checking/Downloading Ubuntu-8.04
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
get_md5 http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg md5=
Download status=The requested URL returned error: 404
Error downloading http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg, The req
Trying remote metalink2: http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink
get_md5 http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS.gpg md5=
Download status=success:D:\ubuntu\install\MD5SUMS.gpg
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS md5=
Download status=success:D:\ubuntu\install\MD5SUMS
      Verifying signature D:\ubuntu\install\MD5SUMS.asc
0; gpgv: Signature made 02/28/08 21:54:35 W. Europe Standard Time using DSA key ID E907875D
gpgv: Good signature from "Agostino Russo (ago) <agostino.russo@gmail.com>"
; ; ; 
      Parsing D:\ubuntu\install\MD5SUMS
Found md5 7623756fc4bf51c1512d807ea195b671
Downloading: trymefirst=D:\ubuntu-backup\hardy-desktop-i386.iso url=http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink md5=7623756fc4bf51c1512d807ea195b671
Download status=success:D:\ubuntu\install\hardy-desktop-i386.iso
ISO file hardy-desktop-i386.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=D:\ubuntu\install\hardy-desktop-i386.iso, cddrive=
Extracting with 7z kernel/initrd from D:\ubuntu\install\hardy-desktop-i386.iso
UncompressFilesPriorInstall
Drive & Path name D:\ubuntu\install\hardy-desktop-i386.iso; Volume name BISSLGRESSA; Max #/chars in vol name ; Volume Serial # 946748791; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size J:
rootSize=3000 homesize=0, swapsize=1000, usrsize=4000
Drive & Path name D:\ubuntu\install\hardy-desktop-i386.iso; Volume name BISSLGRESSA; Max #/chars in vol name ; Volume Serial # 946748791; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size J:
rootSize=3000 homesize=0, swapsize=1000, usrsize=4000
AllocFile filename=D:\ubuntu\disks\root.disk size=3000
AllocFile filename=D:\ubuntu\disks\home.disk size=0
AllocFile filename=D:\ubuntu\disks\swap.disk size=1000
AllocFile filename=D:\ubuntu\disks\usr.disk size=4000
UncompressFilesAfterInstall
Installation completed successfully!
============ Installer ============
PLUGINSDIR=F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsm5.tmp
detect_all
Parsing cmdline "J:\Wubi-8.04-alpha-rev453.exe" 
debug=, 32bit=, cdboot=
arch=i386
DetectCD
      Is Valid CD J:
CDInfo cleared
      Is Valid CD I:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD J:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
Found InstallationDrive D:\ubuntu
AlreadyInstalled=true OldInstallationDrive=D: InstallCompleted=true
FreeSpace in D: is 5040
DetectBackupFolder
Found BackupFolder D:\ubuntu-backup
GMT=1
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=9c6fbf74e7fb42c
ComputerName=9C6FBF74E7FB42C
EnvUsername=Administrator
UserDomain=9C6FBF74E7FB42C
UserInfoName=Administrator
UserProfileFolder=F:\Documents and Settings\Administrator.9C6FBF74E7FB42C
UserProfileName=Administrator 
ShowMainPage
Existing installation detected, calling old uninstaller and quitting.
============ Uninstaller ============
PLUGINSDIR=F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsc8.tmp
============ Installer ============
PLUGINSDIR=F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nstA.tmp
detect_all
Parsing cmdline "J:\Wubi-8.04-alpha-rev453.exe" 
debug=, 32bit=, cdboot=
arch=i386
DetectCD
      Is Valid CD J:
CDInfo cleared
      Is Valid CD I:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD J:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
Found InstallationDrive D:\ubuntu
AlreadyInstalled=true OldInstallationDrive=D: InstallCompleted=true
FreeSpace in D: is 5040
DetectBackupFolder
Found BackupFolder D:\ubuntu-backup
GMT=1
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=9c6fbf74e7fb42c
ComputerName=9C6FBF74E7FB42C
EnvUsername=Administrator
UserDomain=9C6FBF74E7FB42C
UserInfoName=Administrator
UserProfileFolder=F:\Documents and Settings\Administrator.9C6FBF74E7FB42C
UserProfileName=Administrator 
ShowMainPage
Existing installation detected, calling old uninstaller and quitting.
============ Uninstaller ============
PLUGINSDIR=F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nseD.tmp
un.install
un.BackupIso
un.CleanBcd
un.RemoveInstallationFolder D:\ubuntu
un.CleanThisDrive C:\
un.CleanConfig.sys C:\
un.CleanThisDrive D:\
un.CleanThisDrive E:\
un.CleanConfig.sys E:\
un.CleanThisDrive F:\
un.CleanThisDrive G:\
un.CleanThisDrive H:\
un.CleanThisDrive J:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
un.RemoveUninstallers F:\WINNT\Uninstall.exe
============ Installer ============
PLUGINSDIR=F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsx11.tmp
detect_all
Parsing cmdline "J:\Wubi-8.04-alpha-rev453.exe" 
debug=, 32bit=, cdboot=
arch=i386
DetectCD
      Is Valid CD J:
CDInfo cleared
      Is Valid CD I:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD J:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
isInstallationDrive E:\ubuntu
isInstallationDrive F:\ubuntu
isInstallationDrive G:\ubuntu
isInstallationDrive H:\ubuntu
isInstallationDrive J:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
FreeSpace in D: is 13392
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
Found BackupFolder D:\ubuntu-backup
GMT=1
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=9c6fbf74e7fb42c
ComputerName=9C6FBF74E7FB42C
EnvUsername=Administrator
UserDomain=9C6FBF74E7FB42C
UserInfoName=Administrator
UserProfileFolder=F:\Documents and Settings\Administrator.9C6FBF74E7FB42C
UserProfileName=Administrator 
ShowMainPage
Making drive list
Drive & Path name 1732; Volume name festplottn; Max #/chars in vol name 1596260; Volume Serial # -1979884213; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT; File System Name Size HDD
Skipping drive C:, not enough free space 771 <= {MinSizeMB}
Drive & Path name 1732; Volume name BISSLGRESSA; Max #/chars in vol name 1596264; Volume Serial # 946748791; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Adding drive D:
Drive & Path name 1732; Volume name DRIVE_E; Max #/chars in vol name 1596268; Volume Serial # 742184440; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT; File System Name Size HDD
Skipping drive E:, not enough free space 48 <= {MinSizeMB}
Drive & Path name 1732; Volume name DRIVE_I; Max #/chars in vol name 1596272; Volume Serial # -62015557; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Skipping drive F:, not enough free space 165 <= {MinSizeMB}
Drive & Path name 1732; Volume name drive_g; Max #/chars in vol name 1596276; Volume Serial # -2010230431; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Skipping drive G:, not enough free space 169 <= {MinSizeMB}
Drive & Path name 1732; Volume name NEW VOLUME; Max #/chars in vol name 1596280; Volume Serial # 543681005; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Skipping drive H:, not enough free space 845 <= {MinSizeMB}
Drive & Path name 1732; Volume name ext; Max #/chars in vol name 1596288; Volume Serial # -666414389; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Skipping drive J:, not enough free space 3252 <= {MinSizeMB}
Drive list = D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 8
PopulateDistroList
DetectIso
      IsValidIso ispoath=J:\fluxbuntu-7.10-installer-i386.iso
      ExtractIsoInfo
      F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsx11.tmp\7z.exe e -y -i!.disk\info -oF:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp J:\fluxbuntu-7.10-installer-i386.iso
      IsValid Fluxbuntu 7.10 "Gutsy Gibbon" - Release Candidate i386 (20071026)

      cdversion=7.10 cddistro=Fluxbuntu cdarch=Candidate cdcodename=Gutsy Gibbon cdsubversion=Release 
      GetDistroInfo distrfullname=Fluxbuntu-i386 distro= cddistro=Fluxbuntu cdarch=Candidate arch=i386
      ->metalinkURL=
      ->isoKernel=
      ->distroVersion=
no distroversion
CDInfo cleared
      IsValidIso ispoath=J:\hardy-desktop-i386.iso
      ExtractIsoInfo
      F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsx11.tmp\7z.exe e -y -i!.disk\info -oF:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp J:\hardy-desktop-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Alpha i386 (20080222)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Alpha 
      GetDistroInfo distrfullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Alpha i386 (20080222)
AddDistroToList Ubuntu-i386
AddDistroToList Ubuntu-amd64
AddDistroToList Kubuntu-i386
AddDistroToList Kubuntu-amd64
AddDistroToList Kubuntu-KDE4-i386
AddDistroToList Kubuntu-KDE4-amd64
AddDistroToList Xubuntu-i386
AddDistroToList Xubuntu-amd64
DistroList = Ubuntu|Kubuntu|Kubuntu-KDE4|Xubuntu
PopulateLanguageListBox
      GetDistroInfo distrfullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrfullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
CreateInstallationFolders
MakeUninstall
Created D:\ubuntu\Uninstall.exe
Created F:\WINNT\Uninstall.exe
Created reg key 1
Created reg key 2
CopyDistFolders
GetIso
DetectCD
      Is Valid CD J:
CDInfo cleared
      Is Valid CD I:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD J:
CDInfo cleared
No CD found
DetectIso
      IsValidIso ispoath=J:\fluxbuntu-7.10-installer-i386.iso
      ExtractIsoInfo
      F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsx11.tmp\7z.exe e -y -i!.disk\info -oF:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp J:\fluxbuntu-7.10-installer-i386.iso
      IsValid Fluxbuntu 7.10 "Gutsy Gibbon" - Release Candidate i386 (20071026)

      cdversion=7.10 cddistro=Fluxbuntu cdarch=Candidate cdcodename=Gutsy Gibbon cdsubversion=Release 
      GetDistroInfo distrfullname=Ubuntu-i386 distro=Ubuntu cddistro=Fluxbuntu cdarch=Candidate arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
different distro Ubuntu != Fluxbuntu
CDInfo cleared
      IsValidIso ispoath=J:\hardy-desktop-i386.iso
      ExtractIsoInfo
      F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsx11.tmp\7z.exe e -y -i!.disk\info -oF:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp J:\hardy-desktop-i386.iso
      IsValid Ubuntu 8.04 "Hardy Heron" - Alpha i386 (20080222)
      cdversion=8.04 cddistro=Ubuntu cdarch=i386 cdcodename=Hardy Heron cdsubversion=Alpha 
      GetDistroInfo distrfullname=Ubuntu-i386 distro=Ubuntu cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Alpha i386 (20080222)
Copying J:\hardy-desktop-i386.iso -> D:\ubuntu\install\hardy-desktop-i386.iso
Checking/Downloading Ubuntu-8.04
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
get_md5 http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg md5=
Download status=The requested URL returned error: 404
Error downloading http://wubi-installer.org/metalinks/8.04-final/MD5SUMS.gpg, The req
Trying remote metalink2: http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink
get_md5 http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS.gpg md5=
Download status=success:D:\ubuntu\install\MD5SUMS.gpg
Downloading: trymefirst= url=http://wubi-installer.org/metalinks/8.04/MD5SUMS md5=
Download status=success:D:\ubuntu\install\MD5SUMS
      Verifying signature D:\ubuntu\install\MD5SUMS.asc
0; gpgv: Signature made 02/28/08 21:54:35 W. Europe Standard Time using DSA key ID E907875D
gpgv: Good signature from "Agostino Russo (ago) <agostino.russo@gmail.com>"
; ; ; 
      Parsing D:\ubuntu\install\MD5SUMS
Found md5 7623756fc4bf51c1512d807ea195b671
Downloading: trymefirst=D:\ubuntu\install\hardy-desktop-i386.iso url=http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink md5=7623756fc4bf51c1512d807ea195b671
Download status=success:D:\ubuntu\install\hardy-desktop-i386.iso
ISO file hardy-desktop-i386.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=D:\ubuntu\install\hardy-desktop-i386.iso, cddrive=
Extracting with 7z kernel/initrd from D:\ubuntu\install\hardy-desktop-i386.iso
UncompressFilesPriorInstall
Drive & Path name D:\ubuntu\install\hardy-desktop-i386.iso; Volume name BISSLGRESSA; Max #/chars in vol name ; Volume Serial # 946748791; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size J:
rootSize=3000 homesize=0, swapsize=1000, usrsize=4000
Drive & Path name D:\ubuntu\install\hardy-desktop-i386.iso; Volume name BISSLGRESSA; Max #/chars in vol name ; Volume Serial # 946748791; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size J:
rootSize=3000 homesize=0, swapsize=1000, usrsize=4000
AllocFile filename=D:\ubuntu\disks\root.disk size=3000
AllocFile filename=D:\ubuntu\disks\home.disk size=0
AllocFile filename=D:\ubuntu\disks\swap.disk size=1000
AllocFile filename=D:\ubuntu\disks\usr.disk size=4000
UncompressFilesAfterInstall
Installation completed successfully!
============ Installer ============
PLUGINSDIR=F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsi41.tmp
detect_all
Parsing cmdline "J:\Wubi-8.04-alpha-rev453.exe" 
debug=, 32bit=, cdboot=
arch=i386
DetectCD
      Is Valid CD J:
CDInfo cleared
      Is Valid CD I:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD J:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
Found InstallationDrive D:\ubuntu
AlreadyInstalled=true OldInstallationDrive=D: InstallCompleted=true
FreeSpace in D: is 5057
DetectBackupFolder
Found BackupFolder D:\ubuntu-backup
GMT=1
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=9c6fbf74e7fb42c
ComputerName=9C6FBF74E7FB42C
EnvUsername=Administrator
UserDomain=9C6FBF74E7FB42C
UserInfoName=Administrator
UserProfileFolder=F:\Documents and Settings\Administrator.9C6FBF74E7FB42C
UserProfileName=Administrator 
ShowMainPage
Existing installation detected, calling old uninstaller and quitting.
============ Uninstaller ============
PLUGINSDIR=F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsy44.tmp
un.install
un.BackupIso
un.CleanBcd
un.RemoveInstallationFolder D:\ubuntu
un.CleanThisDrive C:\
un.CleanConfig.sys C:\
un.CleanThisDrive D:\
un.CleanThisDrive E:\
un.CleanConfig.sys E:\
un.CleanThisDrive F:\
un.CleanThisDrive G:\
un.CleanThisDrive H:\
un.CleanThisDrive J:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
un.RemoveUninstallers F:\WINNT\Uninstall.exe
============ Installer ============
PLUGINSDIR=F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsu48.tmp
detect_all
Parsing cmdline "J:\Wubi-8.04-alpha-rev453.exe" 
debug=, 32bit=, cdboot=
arch=i386
DetectCD
      Is Valid CD J:
CDInfo cleared
      Is Valid CD I:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD J:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
isInstallationDrive E:\ubuntu
isInstallationDrive F:\ubuntu
isInstallationDrive G:\ubuntu
isInstallationDrive H:\ubuntu
isInstallationDrive J:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
FreeSpace in D: is 13392
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
Found BackupFolder D:\ubuntu-backup
GMT=1
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=9c6fbf74e7fb42c
ComputerName=9C6FBF74E7FB42C
EnvUsername=Administrator
UserDomain=9C6FBF74E7FB42C
UserInfoName=Administrator
UserProfileFolder=F:\Documents and Settings\Administrator.9C6FBF74E7FB42C
UserProfileName=Administrator 
ShowMainPage
Making drive list
Drive & Path name 1732; Volume name festplottn; Max #/chars in vol name 1596260; Volume Serial # -1979884213; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT; File System Name Size HDD
Skipping drive C:, not enough free space 771 <= {MinSizeMB}
Drive & Path name 1732; Volume name BISSLGRESSA; Max #/chars in vol name 1596264; Volume Serial # 946748791; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Adding drive D:
Drive & Path name 1732; Volume name DRIVE_E; Max #/chars in vol name 1596268; Volume Serial # 742184440; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT; File System Name Size HDD
Skipping drive E:, not enough free space 48 <= {MinSizeMB}
Drive & Path name 1732; Volume name DRIVE_I; Max #/chars in vol name 1596272; Volume Serial # -62015557; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Skipping drive F:, not enough free space 164 <= {MinSizeMB}
Drive & Path name 1732; Volume name drive_g; Max #/chars in vol name 1596276; Volume Serial # -2010230431; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Skipping drive G:, not enough free space 169 <= {MinSizeMB}
Drive & Path name 1732; Volume name NEW VOLUME; Max #/chars in vol name 1596280; Volume Serial # 543681005; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Skipping drive H:, not enough free space 845 <= {MinSizeMB}
Drive & Path name 1732; Volume name ext; Max #/chars in vol name 1596288; Volume Serial # -666414389; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Skipping drive J:, not enough free space 3252 <= {MinSizeMB}
Drive list = D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 8
PopulateDistroList
DetectIso
      IsValidIso ispoath=J:\fluxbuntu-7.10-installer-i386.iso
      ExtractIsoInfo
      F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsu48.tmp\7z.exe e -y -i!.disk\info -oF:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp J:\fluxbuntu-7.10-installer-i386.iso
      IsValid Fluxbuntu 7.10 "Gutsy Gibbon" - Release Candidate i386 (20071026)

      cdversion=7.10 cddistro=Fluxbuntu cdarch=Candidate cdcodename=Gutsy Gibbon cdsubversion=Release 
      GetDistroInfo distrfullname=Fluxbuntu-i386 distro= cddistro=Fluxbuntu cdarch=Candidate arch=i386
      ->metalinkURL=
      ->isoKernel=
      ->distroVersion=
no distroversion
CDInfo cleared
     
Could not find F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\info
      IsValid 
no cdinfo
CDInfo cleared
      IsValidIso ispoath=J:\ubuntu-7.10-alternate-i386.iso
      ExtractIsoInfo
      F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsu48.tmp\7z.exe e -y -i!.disk\info -oF:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp J:\ubuntu-7.10-alternate-i386.iso
      IsValid Ubuntu 7.10 "Gutsy Gibbon" - Release i386 (20071016.1)
      cdversion=7.10 cddistro=Ubuntu cdarch=i386 cdcodename=Gutsy Gibbon cdsubversion=Release 
      GetDistroInfo distrfullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
different version 8.04 != 7.10
CDInfo cleared
      IsValidIso ispoath=J:\ubuntu-7.10-desktop-i386.iso
      ExtractIsoInfo
      F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsu48.tmp\7z.exe e -y -i!.disk\info -oF:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp J:\ubuntu-7.10-desktop-i386.iso
      IsValid Ubuntu 7.10 "Gutsy Gibbon" - Release i386 (20071016)
      cdversion=7.10 cddistro=Ubuntu cdarch=i386 cdcodename=Gutsy Gibbon cdsubversion=Release 
      GetDistroInfo distrfullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
different version 8.04 != 7.10
CDInfo cleared
AddDistroToList Ubuntu-i386
============ Installer ============
PLUGINSDIR=F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsv4E.tmp
detect_all
Parsing cmdline "J:\Wubi-8.04-alpha-rev453.exe" 
debug=, 32bit=, cdboot=
arch=i386
DetectCD
      Is Valid CD J:
CDInfo cleared
      Is Valid CD I:
CDInfo cleared
      Is Valid CD C:
CDInfo cleared
      Is Valid CD D:
CDInfo cleared
      Is Valid CD E:
CDInfo cleared
      Is Valid CD F:
CDInfo cleared
      Is Valid CD G:
CDInfo cleared
      Is Valid CD H:
CDInfo cleared
      Is Valid CD J:
CDInfo cleared
No CD found
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
isInstallationDrive E:\ubuntu
isInstallationDrive F:\ubuntu
isInstallationDrive G:\ubuntu
isInstallationDrive H:\ubuntu
isInstallationDrive J:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
FreeSpace in D: is 13392
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
Found BackupFolder D:\ubuntu-backup
GMT=1
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=9c6fbf74e7fb42c
ComputerName=9C6FBF74E7FB42C
EnvUsername=Administrator
UserDomain=9C6FBF74E7FB42C
UserInfoName=Administrator
UserProfileFolder=F:\Documents and Settings\Administrator.9C6FBF74E7FB42C
UserProfileName=Administrator 
ShowMainPage
Making drive list
Drive & Path name 1732; Volume name festplottn; Max #/chars in vol name 1596260; Volume Serial # -1979884213; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT; File System Name Size HDD
Skipping drive C:, not enough free space 771 <= {MinSizeMB}
Drive & Path name 1732; Volume name BISSLGRESSA; Max #/chars in vol name 1596264; Volume Serial # 946748791; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Adding drive D:
Drive & Path name 1732; Volume name DRIVE_E; Max #/chars in vol name 1596268; Volume Serial # 742184440; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT; File System Name Size HDD
Skipping drive E:, not enough free space 48 <= {MinSizeMB}
Drive & Path name 1732; Volume name DRIVE_I; Max #/chars in vol name 1596272; Volume Serial # -62015557; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Skipping drive F:, not enough free space 161 <= {MinSizeMB}
Drive & Path name 1732; Volume name drive_g; Max #/chars in vol name 1596276; Volume Serial # -2010230431; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Skipping drive G:, not enough free space 169 <= {MinSizeMB}
Drive & Path name 1732; Volume name NEW VOLUME; Max #/chars in vol name 1596280; Volume Serial # 543681005; Max #/chars in dir/file names 255; File System Flags 6; File System Type FAT32; File System Name Size HDD
Skipping drive H:, not enough free space 845 <= {MinSizeMB}
Drive & Path name 1732; Volume name ext; Max #/chars in vol name 1596288; Volume Serial # -666414389; Max #/chars in dir/file names 255; File System Flags 459007; File System Type NTFS; File System Name Size HDD
Skipping drive J:, not enough free space 3252 <= {MinSizeMB}
Drive list = D:
ChangeInstallationDrive to D:
ChangeInstallationSize to 8
PopulateDistroList
DetectIso
      IsValidIso ispoath=J:\fluxbuntu-7.10-installer-i386.iso
      ExtractIsoInfo
      F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsv4E.tmp\7z.exe e -y -i!.disk\info -oF:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp J:\fluxbuntu-7.10-installer-i386.iso
      IsValid Fluxbuntu 7.10 "Gutsy Gibbon" - Release Candidate i386 (20071026)

      cdversion=7.10 cddistro=Fluxbuntu cdarch=Candidate cdcodename=Gutsy Gibbon cdsubversion=Release 
      GetDistroInfo distrfullname=Fluxbuntu-i386 distro= cddistro=Fluxbuntu cdarch=Candidate arch=i386
      ->metalinkURL=
      ->isoKernel=
      ->distroVersion=
no distroversion
CDInfo cleared
     
Could not find F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\info
      IsValid 
no cdinfo
CDInfo cleared
      IsValidIso ispoath=J:\ubuntu-7.10-alternate-i386.iso
      ExtractIsoInfo
      F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsv4E.tmp\7z.exe e -y -i!.disk\info -oF:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp J:\ubuntu-7.10-alternate-i386.iso
      IsValid Ubuntu 7.10 "Gutsy Gibbon" - Release i386 (20071016.1)
      cdversion=7.10 cddistro=Ubuntu cdarch=i386 cdcodename=Gutsy Gibbon cdsubversion=Release 
      GetDistroInfo distrfullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
different version 8.04 != 7.10
CDInfo cleared
      IsValidIso ispoath=J:\ubuntu-7.10-desktop-i386.iso
      ExtractIsoInfo
      F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsv4E.tmp\7z.exe e -y -i!.disk\info -oF:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp J:\ubuntu-7.10-desktop-i386.iso
      IsValid Ubuntu 7.10 "Gutsy Gibbon" - Release i386 (20071016)
      cdversion=7.10 cddistro=Ubuntu cdarch=i386 cdcodename=Gutsy Gibbon cdsubversion=Release 
      GetDistroInfo distrfullname=Ubuntu-i386 distro= cddistro=Ubuntu cdarch=i386 arch=i386
      ->metalinkURL=http://wubi-installer.org/metalinks/8.04-final/ubuntu-desktop-i386.iso.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.04
different version 8.04 != 7.10
CDInfo cleared
AddDistroToList Ubuntu-i386

```

---

### Post by ago on 2008-03-16
Can you change the extensions of all the 7.10 isos and try again?

---

### Post by steve196 on 2008-03-16
I think, you found it. I just moved all cd images to a subdirectory and now wubi starts normally.

---

