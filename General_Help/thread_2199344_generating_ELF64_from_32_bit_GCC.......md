---
title: "generating ELF64 from 32 bit GCC......"
date: 2014-01-13
forum: General Help
---

### Post by aditya.mahesh.shar on 2014-01-13
Hi
can we generate amd X86-64  ELF file from a gcc 32-bit compiler.

I mean, my compiler by default generate this ELF -

aditya@gayatrimata:~/Templates/programs/c++$ readelf -a ucf
ELF Header:
  Magic:   7f 45 4c 46 01 01 01 00 00 00 00 00 00 00 00 00 
  Class:                             ELF32
  Data:                              2's complement, little endian
  Version:                           1 (current)
  OS/ABI:                            UNIX - System V
  ABI Version:                       0
  Type:                              EXEC (Executable file)
  Machine:                           Intel 80386
  Version:                           0x1
  Entry point address:               0x8048610
  Start of program headers:          52 (bytes into file)
  Start of section headers:          4504 (bytes into file)
  Flags:                             0x0
  Size of this header:               52 (bytes)
  Size of program headers:           32 (bytes)
  Number of program headers:         9
  Size of section headers:           40 (bytes)
  Number of section headers:         31
  Section header string table index: 28





,But I want this ELF file to be generated from my gcc -

aditya@gayatrimata:~/Templates/programs/c++$ readelf -a test
ELF Header:
  Magic:   7f 45 4c 46 02 01 01 00 00 00 00 00 00 00 00 00 
  Class:                             ELF64
  Data:                              2's complement, little endian
  Version:                           1 (current)
  OS/ABI:                            UNIX - System V
  ABI Version:                       0
  Type:                              EXEC (Executable file)
  Machine:                           Advanced Micro Devices X86-64
  Version:                           0x1
  Entry point address:               0x400810
  Start of program headers:          64 (bytes into file)
  Start of section headers:          6712 (bytes into file)
  Flags:                             0x0
  Size of this header:               64 (bytes)
  Size of program headers:           56 (bytes)
  Number of program headers:         9
  Size of section headers:           64 (bytes)
  Number of section headers:         42
  Section header string table index: 39


Please suggest suitable answer.

---

