---
title: "ccsloader.bin fails: undefined symbol: initPAnsiStrings"
date: 2014-08-10
forum: General Help
---

### Post by tom130 on 2014-08-10
Hi all,

I am trying to debug a problem that I have been working on for several days. I want to run a program called ccsloader.bin. This program accessess a programmer connected to USB and loads PIC microcontrollers. It is a 32-bit program and my system is a 64 bit installation.

 The problem:

[/opt/picc]$./ccsloader.bin
./ccsloader.bin: symbol lookup error: ./ccsloader.bin: undefined symbol: initPAnsiStrings
[/opt/picc]$

Having search the forums I determined the problem has something to do with the libborqt.so, or lack thereof. I made sure I had that one installed.

Library is found and it's 32 bit:

[/opt/picc]$readelf -a /lib/i386-linux-gnu/libborqt-6.9-qt2.3.so|head
ELF Header:
  Magic:   7f 45 4c 46 01 01 01 00 00 00 00 00 00 00 00 00
  Class:                             ELF32
  Data:                              2's complement, little endian
  Version:                           1 (current)
  OS/ABI:                            UNIX - System V
  ABI Version:                       0
  Type:                              DYN (Shared object file)
  Machine:                           Intel 80386
  Version:                           0x1


I verified the library contains the missing symbol:

[/opt/picc]$readelf -a /lib/i386-linux-gnu/libborqt-6.9-qt2.3.so | grep AnsiString
007295f4  00068106 R_386_GLOB_DAT    0072a0f0   copyCharsToPAnsiString
007295f8  0010ad06 R_386_GLOB_DAT    0072a0f4   charsOfPAnsiString
00729600  0022e406 R_386_GLOB_DAT    0072a0fc   finalPAnsiString
007295fc  00362506 R_386_GLOB_DAT    0072a0f8   initPAnsiString
   272: 002637c4    68 FUNC    GLOBAL DEFAULT   17 initPAnsiStrings
  1665: 0072a0f0     4 OBJECT  GLOBAL DEFAULT   27 copyCharsToPAnsiString
  4269: 0072a0f4     4 OBJECT  GLOBAL DEFAULT   27 charsOfPAnsiString
  8932: 0072a0fc     4 OBJECT  GLOBAL DEFAULT   27 finalPAnsiString
 13861: 0072a0f8     4 OBJECT  GLOBAL DEFAULT   27 initPAnsiString

**The string is indeed in the library.

The library is opened and found:

strace ccsloader.bin

<snip>

open("/lib/i386-linux-gnu/libborqt-6.9-qt2.3.so", O_RDONLY|O_CLOEXEC) = 6
read(6, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20|%\0004\0\0\0"..., 512) = 512
fstat64(6, {st_mode=S_IFREG|0644, st_size=7526184, ...}) = 0
mmap2(NULL, 7532556, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 6, 0) = 0xfffffffff69ac000
mmap2(0xf6ffa000, 905216, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 6, 0x64d000) = 0xfffffffff6ffa000
mmap2(0xf70d7000, 16396, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xfffffffff7

BUT....

writev(2, [{"ccsloader.bin", 13}, {": ", 2}, {"symbol lookup error", 19}, {": ", 2}, {"ccsloader.bin", 13}, {": ", 2}, {"undefined symbol: initPAnsiStrin"..., 34}, {"", 0}, {"", 0}, {"\n", 1}], 10ccsloader.bin: symbol lookup error: ccsloader.bin: undefined symbol: initPAnsiStrings
) = 86
exit_group(127)                         = ?
+++ exited with 127 +++


Sigh. I suppose I could try a jailed 32-bit chroot but at this point I have lost all confidence that anything I try will work. 

Thanks to anyone who has any ideas....

Tom

---

