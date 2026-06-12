---
title: "rev395 starts but rev 398 not"
date: 2008-02-07
forum: General Help
---

### Post by steve196 on 2008-02-07
After several issues with wubi 8.4 rev395 i have uninstalled and tried to install rev 398.
rev 398 does not start and silently fails while 395 still starts up normally. I have had the same issue with 395 and fixed it by emptying the temp directory. But that did not work with 398.

============ Installer ============
PLUGINSDIR=F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nst41.tmp
detect_all
Parsing cmdline "J:\Wubi-8.04-alpha-rev398.exe" 
DetectProcessorArchitecture
arch=i386
DetectCD
isvalidcd I:\
isvalidcd C:\
isvalidcd D:\
isvalidcd E:\
isvalidcd F:\
isvalidcd G:\
isvalidcd H:\
isvalidcd J:\
DetectCD Finished cddrive=
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
isInstallationDrive E:\ubuntu
isInstallationDrive F:\ubuntu
isInstallationDrive G:\ubuntu
isInstallationDrive H:\ubuntu
isInstallationDrive J:\ubuntu
CheckFreeSpace D:
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
Found BackupFolder D:\ubuntu-backup
DetectGMT
DetectCountry
DetectLocale
DetectLayoutCode
DetectTimeZone
DetectDomain
DetectHostName
DetectComputerName
DetectUserName
DetectUserDomain
DetectUserInfoName
DetectUserProfileFolder
DetectUserProfileName
UserProfileName=Administrator

---

### Post by steve196 on 2008-02-08
rev 397 and 396 do not start either.

---

### Post by ago on 2008-02-08
Steve I have a couple of pending changes then I will be on it. Best way would be to chat over w/e so that I can send you patched versions the fly. Debugging this trials is a bit of a pain. In the meantime, you can use windbg.exe though. That will provide useful info.

[http://www.microsoft.com/whdc/devtools/debugging/installx86.mspx](http://www.microsoft.com/whdc/devtools/debugging/installx86.mspx)
c:\pogram files\Debugging Tools\windbg > file > open executable
keep hitting F5 until it gets to the point where it crashes
I will recompile with debug symbols later on

Send me a PM if you wish.

---

### Post by steve196 on 2008-02-08
Thank you!
Running this under the debugger actually solved the problem (no idea why). rev398 started normally and i have been able to install. I have not tested yet if the installed system can boot.
Here is what the debugger says:
```

Microsoft (R) Windows Debugger Version 6.8.0004.0 X86
Copyright (c) Microsoft Corporation. All rights reserved.

CommandLine: J:\Wubi-8.04-alpha-rev398.exe
Symbol search path is: *** Invalid ***
****************************************************************************
* Symbol loading may be unreliable without a symbol search path.           *
* Use .symfix to have the debugger choose a symbol path.                   *
* After setting your symbol path, use .reload to refresh symbol locations. *
****************************************************************************
Executable search path is: 
ModLoad: 00400000 00450000   image00400000
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
(520.228): Break instruction exception - code 80000003 (first chance)
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
ModLoad: 779b0000 77a4b000   F:\WINNT\system32\OLEAUT32.DLL
ModLoad: 775a0000 77626000   F:\WINNT\system32\CLBCATQ.DLL
ModLoad: 77840000 7787e000   F:\WINNT\system32\cscui.dll
ModLoad: 770c0000 770e3000   F:\WINNT\system32\CSCDLL.DLL
ModLoad: 65200000 65208000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\test64.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10005000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\UserInfo.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 772b0000 7731d000   F:\WINNT\system32\RichEd20.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 65340000 6534e000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\locate.dll
ModLoad: 10000000 10005000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\nsExec.dll
(520.228): Access violation - code c0000005 (first chance)
First chance exceptions are reported before any exception handling.
This exception may be expected and handled.
eax=feeefeee ebx=00000000 ecx=00000000 edx=00000000 esi=00187104 edi=00000000
eip=77f88216 esp=0012f594 ebp=0012f5f4 iopl=0         nv up ei ng nz na pe nc
cs=001b  ss=0023  ds=0023  es=0023  fs=0038  gs=0000             efl=00010286
ntdll!RtlpWaitForCriticalSection+0x60:
77f88216 ff4010          inc     dword ptr [eax+10h]  ds:0023:feeefefe=????????
0:000> g
HEAP[Wubi-8.04-alpha-rev398.exe]: HEAP: Free Heap block 1870e8 modified at 187108 after it was freed
(520.228): Break instruction exception - code 80000003 (first chance)
eax=001870e8 ebx=00000004 ecx=0012eef8 edx=0012eb32 esi=00130000 edi=001870e8
eip=77f813b1 esp=0012ed0c ebp=0012ed10 iopl=0         nv up ei pl nz na po nc
cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00000202
ntdll!DbgBreakPoint:
77f813b1 cc              int     3
0:000> g
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10009000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\InstallOptions.dll
ModLoad: 76b30000 76b6e000   F:\WINNT\system32\comdlg32.dll
HEAP[Wubi-8.04-alpha-rev398.exe]: Invalid Address specified to RtlFreeHeap( 130000, 170540 )
(520.228): Break instruction exception - code 80000003 (first chance)
eax=00170538 ebx=00170538 ecx=0012f748 edx=0012f4e2 esi=00130000 edi=00170538
eip=77f813b1 esp=0012f6c8 ebp=0012f6cc iopl=0         nv up ei pl nz na po nc
cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00000202
ntdll!DbgBreakPoint:
77f813b1 cc              int     3
0:000> g
HEAP[Wubi-8.04-alpha-rev398.exe]: Invalid Address specified to RtlFreeHeap( 130000, 171558 )
(520.228): Break instruction exception - code 80000003 (first chance)
eax=00171550 ebx=00171550 ecx=0012f748 edx=0012f4e2 esi=00130000 edi=00171550
eip=77f813b1 esp=0012f6c8 ebp=0012f6cc iopl=0         nv up ei pl nz na po nc
cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00000202
ntdll!DbgBreakPoint:
77f813b1 cc              int     3
0:000> g
HEAP[Wubi-8.04-alpha-rev398.exe]: Invalid Address specified to RtlFreeHeap( 130000, 172570 )
(520.228): Break instruction exception - code 80000003 (first chance)
eax=00172568 ebx=00172568 ecx=0012f748 edx=0012f4e2 esi=00130000 edi=00172568
eip=77f813b1 esp=0012f6c8 ebp=0012f6cc iopl=0         nv up ei pl nz na po nc
cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00000202
ntdll!DbgBreakPoint:
77f813b1 cc              int     3
0:000> g
HEAP[Wubi-8.04-alpha-rev398.exe]: Invalid Address specified to RtlFreeHeap( 130000, 173b80 )
(520.228): Break instruction exception - code 80000003 (first chance)
eax=00173b78 ebx=00173b78 ecx=0012f748 edx=0012f4e2 esi=00130000 edi=00173b78
eip=77f813b1 esp=0012f6c8 ebp=0012f6cc iopl=0         nv up ei pl nz na po nc
cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00000202
ntdll!DbgBreakPoint:
77f813b1 cc              int     3
0:000> g
HEAP[Wubi-8.04-alpha-rev398.exe]: Invalid Address specified to RtlFreeHeap( 130000, 174bc8 )
(520.228): Break instruction exception - code 80000003 (first chance)
eax=00174bc0 ebx=00174bc0 ecx=0012f748 edx=0012f4e2 esi=00130000 edi=00174bc0
eip=77f813b1 esp=0012f6c8 ebp=0012f6cc iopl=0         nv up ei pl nz na po nc
cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00000202
ntdll!DbgBreakPoint:
77f813b1 cc              int     3
0:000> g
HEAP[Wubi-8.04-alpha-rev398.exe]: Invalid Address specified to RtlFreeHeap( 130000, 175c10 )
(520.228): Break instruction exception - code 80000003 (first chance)
eax=00175c08 ebx=00175c08 ecx=0012f748 edx=0012f4e2 esi=00130000 edi=00175c08
eip=77f813b1 esp=0012f6c8 ebp=0012f6cc iopl=0         nv up ei pl nz na po nc
cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00000202
ntdll!DbgBreakPoint:
77f813b1 cc              int     3
0:000> g
ModLoad: 02750000 02755000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\ToolTips.dll
ModLoad: 02770000 02775000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\ToolTips.dll
ModLoad: 02790000 02795000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\ToolTips.dll
ModLoad: 027b0000 027b5000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\ToolTips.dll
ModLoad: 027e0000 027e5000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\ToolTips.dll
ModLoad: 02800000 02805000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\ToolTips.dll
ModLoad: 02820000 02825000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\ToolTips.dll
ModLoad: 02840000 02845000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\ToolTips.dll
ModLoad: 02870000 02875000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\ToolTips.dll
ModLoad: 061f0000 06205000   F:\WINNT\system32\SSSensor.dll
ModLoad: 65900000 6590a000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\textreplace.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 65340000 6534e000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\locate.dll
ModLoad: 10000000 10005000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\nsExec.dll
(520.458): Access violation - code c0000005 (first chance)
First chance exceptions are reported before any exception handling.
This exception may be expected and handled.
eax=feeefeee ebx=00000000 ecx=00000000 edx=00000000 esi=001872f4 edi=00000000
eip=77f88216 esp=031af930 ebp=031af990 iopl=0         nv up ei ng nz na pe nc
cs=001b  ss=0023  ds=0023  es=0023  fs=0038  gs=0000             efl=00010286
ntdll!RtlpWaitForCriticalSection+0x60:
77f88216 ff4010          inc     dword ptr [eax+10h]  ds:0023:feeefefe=????????
0:002> g
ModLoad: 10000000 10005000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\Dialer.dll
ModLoad: 63000000 63095000   F:\WINNT\system32\wininet.dll
ModLoad: 7c740000 7c7c7000   F:\WINNT\system32\CRYPT32.dll
ModLoad: 77430000 77440000   F:\WINNT\system32\MSASN1.DLL
HEAP[Wubi-8.04-alpha-rev398.exe]: HEAP: Free Heap block 1872d8 modified at 1872f8 after it was freed
(520.458): Break instruction exception - code 80000003 (first chance)
eax=001872d8 ebx=00000010 ecx=031aeedc edx=031aeb16 esi=00000038 edi=001872d8
eip=77f813b1 esp=031aecf0 ebp=031aecf4 iopl=0         nv up ei pl nz na po nc
cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00000202
ntdll!DbgBreakPoint:
77f813b1 cc              int     3
0:002> g
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
ModLoad: 68680000 686d6000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\metadl.dll
ModLoad: 77570000 775a0000   F:\WINNT\system32\WINMM.DLL
ModLoad: 759c0000 759c7000   F:\WINNT\system32\mmdrv.dll
ModLoad: 10000000 10005000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\nsExec.dll
ModLoad: 10000000 10005000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\nsExec.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 044d0000 046d4000   F:\WINNT\system32\MSI.DLL
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 1001e000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\mkpasswd.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 10000000 10006000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\System.dll
ModLoad: 6eb00000 6eb09000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\diskimage.dll
ModLoad: 6eb00000 6eb09000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\diskimage.dll
ModLoad: 6eb00000 6eb09000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\diskimage.dll
ModLoad: 10000000 10009000   F:\DOCUME~1\ADMINI~1.9C6\LOCALS~1\Temp\nsrF.tmp\InstallOptions.dll
ModLoad: 76b30000 76b6e000   F:\WINNT\system32\comdlg32.dll
eax=05010000 ebx=00000000 ecx=20010101 edx=00000000 esi=77f8ee04 edi=00000000
eip=77f8ee0f esp=0012fd60 ebp=0012fe28 iopl=0         nv up ei pl zr na pe nc
cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00000246
ntdll!ZwTerminateProcess+0xb:
77f8ee0f c20800          ret     8

```

---

### Post by steve196 on 2008-02-08
It works.
I had to again replace hd0,0 with hd1,3 and ro with rw in menu.lst.
After an update including a new kernel only the old kernel actually works. The new one ends in an emergency boot prompt (but the updated menu.lst had the partitions right only the rw was changed back to ro). 
But now i have a system that works.

---

### Post by ago on 2008-02-09
Hmm would like to know more about those crashes...

---

