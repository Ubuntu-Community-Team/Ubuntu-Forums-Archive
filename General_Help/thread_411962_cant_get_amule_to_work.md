---
title: "cant get amule to work"
date: 2007-04-17
forum: General Help
---

### Post by xhaos on 2007-04-17
i am trying to use amuled (deamon) but when i try to run it as user i get this result that i cant. when i sudo it i get the following

> amuled: OnInit - starting timer
Initialising aMule
Checking if there is an instance already running...
No other instances are running.
        aMule Version: aMuled 2.1.3 using wxGTK2 v2.6.3 (Unicoded)

Terminated after throwing an instance of 'CInvalidStateEx'
        what(): CRunTimeException::CInvalidStateException: CFile: Cannot get length of closed file.
        backtrace:
[2] wxAppTraits::~wxAppTraits() in amuled [0x806ec9d]
[3] wxEntry(int&, wchar_t**) in /usr/lib/libwx_baseu-2.6.so.0[0xb7932f0d]
[4] wxEntry(int&, char**) in /usr/lib/libwx_baseu-2.6.so.0[0xb7932f76]
[5] ?? in amuled [0x8068510]
[6] __libc_start_main in /lib/tls/i686/cmov/libc.so.6[0xb76918cc]
[7] wxAppConsole::Initialize(int&, wchar_t**) in amuled[0x8067e81]

Aborted (core dumped)


what goes on?
furthermore i just cant  get it to connect even though i have setup my router properly (firewall/nat) anyone else had such problems?

---

### Post by wormite on 2007-04-23
Having the same problem here.

---

### Post by vorondil on 2007-11-05
I had the same deal on 7.10.  I nuked ~/.aMule, and it started working again.

---

### Post by NoruoW on 2007-11-05
on 7.10 amule works for me, later on ubuntu studio 7.10 don't - 
when i replaced ubuntu studio /.aMule directory whith the working 7.10 version /.aMule, it start work too

---

