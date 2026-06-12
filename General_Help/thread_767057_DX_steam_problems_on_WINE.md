---
title: "DX steam problems on WINE"
date: 2008-04-25
forum: General Help
---

### Post by torrent478 on 2008-04-25
Hello everyone, I'm new here and I need a little bit of help.

I'm running WINE 0.9.59 on Ubuntu 7.04

For starters I'm trying to get steam games to work on wine. I can get steam installed, and I log in fine. but when I go to launch a game it says "the latest version of Microsoft DirectX is needed to play this game"

So I look around the internet on how to installed dx on wine and I find this:
[http://wine-review.blogspot.com/2008/03/directx-90c-march-2008-redistributable.html](http://wine-review.blogspot.com/2008/03/directx-90c-march-2008-redistributable.html)

I follow the instructions here perfectly, but when I go to install DXSETUP.exe It stalls on the initializing step and I get this readout:

```

daniel@ubuntu:~/dx$ wine DXSETUP.exe
fixme:spoolsv:serv_main (0 (nil))
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
wine: Call from 0x7b840fd8 to unimplemented function softpub.dll.SoftpubInitialize, aborting
wine: Unimplemented function softpub.dll.SoftpubInitialize called at address 0x7b840fd8 (thread 001f), starting debugger...
WineDbg starting on pid 0008
Unhandled exception: unimplemented function softpub.dll.SoftpubInitialize called in 32-bit code (0x7b841052).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b841052 ESP:7e498fa8 EBP:7e49900c EFLAGS:00000212(   - 00      - -IA1)
 EAX:7b82c181 EBX:7b8ac8a0 ECX:00000000 EDX:7e499024
 ESI:7e499024 EDI:7e499214
Stack dump:
0x7e498fa8:  7e499024 00000008 7bc39855 80000100
0x7e498fb8:  00000001 00000000 7b840fd8 00000002
0x7e498fc8:  7e65db94 7e65dd5e 00000000 7bc8643c
0x7e498fd8:  00000000 7e498fec 7bc39990 00000000
0x7e498fe8:  7e2141c8 7e498ffc 7ee6dcbf 00000000
0x7e498ff8:  00142d00 7e49903c 7b840fe2 7e2141c8
Backtrace:
=>1 0x7b841052 RaiseException+0x7a() in kernel32 (0x7e49900c)
  2 0x7e65db41 in softpub (+0xdb41) (0x7e49902c)
  3 0x7e65d8e0 in softpub (+0xd8e0) (0x7e49908c)
  4 0x7e20ef92 in wintrust (+0xef92) (0x7e4990dc)
  5 0x7e20f23d WinVerifyTrust+0x1db() in wintrust (0x7e4991ac)
  6 0x007c55ce in dsetup32 (+0x155ce) (0x7e499430)
  7 0x007bd105 in dsetup32 (+0xd105) (0x7e499564)
  8 0x007bd390 in dsetup32 (+0xd390) (0x7e499790)
  9 0x007c910d in dsetup32 (+0x1910d) (0x7e4999d0)
  10 0x00685088 in dsetup (+0x5088) (0x7e4999f0)
  11 0x010053a5 in dxsetup (+0x53a5) (0x7e499a08)
  12 0x7bc684ce call_thread_entry_point+0xe() in ntdll (0x7e499a18)
  13 0x7bc69285 in ntdll (+0x59285) (0x7e499ac8)
  14 0x7bc69d2c NtQueueApcThread() in ntdll (0x7e49a3c8)
  15 0xb7dd731b start_thread+0xcb() in libpthread.so.0 (0x7e49a4b8)
  16 0xb7d5f57e __clone+0x5e() in libc.so.6 (0x00000000)
0x7b841052 RaiseException+0x7a in kernel32: subl        $4,%esp 
```


Ive also tried installing dx9 with wine-doors but that hasnt seemed to work either


So.... is there any way I can get dx9 to work? am I doing something wrong on the install step of dx? Or is there possibly any way to trick steam into thinking that I am running dx9?


Thanks for the help in advanced.

---

### Post by roderick on 2008-04-25
You do not need to install directx in wine as it provides it's own dll's for this purpose.

Was there a more specific error from steam? Did the game require directx 10 or was it 9 or earlier? 

I believe the error you are experiencing is a windows 2000 issue. If you installed steam and have the os type (in winecfg) as windows 2000, then steam gets messed up. 

Try wiping out the  .wine dir and starting from scratch.

You should run winecfg immediately before doing anything with steam or any games. Ensure you setup the os as XP and then install steam. 

Try reading up on wine at [http://www.winehq.org](http://www.winehq.org) for some additional help.

---

