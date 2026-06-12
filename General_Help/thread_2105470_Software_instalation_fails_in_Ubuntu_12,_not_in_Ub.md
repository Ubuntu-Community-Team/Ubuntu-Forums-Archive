---
title: "Software instalation fails in Ubuntu 12, not in Ubuntu 10"
date: 2013-01-16
forum: General Help
---

### Post by goldstein2034 on 2013-01-16
Hello Ubuntu gurus, 

First of all, thank you for your help. 

I installed (with no problems) MARS, Scientific Software based on ROOT, scientific software from CERN, based on C++ in my Ubuntu 10.04 computer. Both ROOT and MARS installation processes go smoothly (with the tipical ./configure -> make -> make install).

The problem I am finding is that following this same process with Ubuntu 12.04, installs without problems ROOT but in MARS installation, while linking libraries (after compiling everything) it just throws a huge number of undefined references. 

I tryed with different GCC versions, different kernels, different everything! but it was impossible...

Is there any simple difference between Ubuntu 10 & 12 which I need to take into account to modify the Makefile configuration¿?

I am not that experiences, so sorry if my question seems to wide...

Thank you!

---

### Post by dino99 on 2013-01-16
you might focus on the needed/used language(s) by MARS : itself or some dependencies probably need something else than gcc compatible version, but maybe also python, ...

without the output errors, its hard to answer better. Cant you debug it ?

---

### Post by goldstein2034 on 2013-01-16
When I make, it promts (first, all compilations already performed, and while linking, it dies):

```
Calling make in mcalib
 Calling make in mcamera
 Calling make in mcta
 Calling make in mdata
 Calling make in mdisp
 Calling make in mfbase
 Calling make in mfileio
 Calling make in mfilter
 Calling make in mflux
 Calling make in mgeom
 Calling make in mgui
 Calling make in mhbase
 Calling make in mhcalib
 Calling make in mhflux
 Calling make in mhft
 Calling make in mhist
 Calling make in mhistmc
 Calling make in mhvstime
 Calling make in mimage
 Calling make in mjobs
 Calling make in mmain
 Calling make in mmc
 Calling make in mmccamera
 Calling make in mmontecarlo
 Calling make in mmuon
 Calling make in monline
 Calling make in mpedestal
 Calling make in mpointing
 Calling make in mpulsar
 Calling make in mranforest
 Calling make in mraw
 Calling make in mreflector
 Calling make in mreport
 Calling make in msignal
 Calling make in mskyplot
 Calling make in msorcerer
 Calling make in msql
 Calling make in mstarcam
 Calling make in msupercuts
 Calling make in mtools
 Calling make in mtrigger
 Calling make in mtruee
 Linking shared object libmars.so ...
 Linking ape ...
ape.o: In function `Usage()':
ape.cc:(.text+0x9): undefined reference to `gLog'
ape.cc:(.text+0x2a): undefined reference to `typeinfo for MLog'
ape.cc:(.text+0x50): undefined reference to `gLog'
ape.cc:(.text+0x8e): undefined reference to `gLog'
ape.cc:(.text+0xfa): undefined reference to `gLog'
ape.cc:(.text+0x166): undefined reference to `gLog'
ape.cc:(.text+0x1db): undefined reference to `gLog'
ape.o:ape.cc:(.text+0x22a): more undefined references to `gLog' follow
ape.o: In function `main':
ape.cc:(.text+0x4dd): undefined reference to `MArgs::MArgs(int, char**, bool)'
ape.cc:(.text+0x4f1): undefined reference to `TString::TString(char const*)'
ape.cc:(.text+0x51a): undefined reference to `MArgs::HasOnly(TString) const'
ape.cc:(.text+0x53b): undefined reference to `TString::TString(char const*)'
ape.cc:(.text+0x564): undefined reference to `MArgs::HasOnly(TString) const'
ape.cc:(.text+0x599): undefined reference to `TString::TString(char const*)'
ape.cc:(.text+0x5c2): undefined reference to `MArgs::HasOnly(TString) const'
ape.cc:(.text+0x5d1): undefined reference to `TString::~TString()'
ape.cc:(.text+0x5e3): undefined reference to `TString::~TString()'
ape.cc:(.text+0x60f): undefined reference to `TString::~TString()'
ape.cc:(.text+0x61c): undefined reference to `TString::~TString()'
ape.cc:(.text+0x63e): undefined reference to `TString::TString(char const*)'
ape.cc:(.text+0x653): undefined reference to `MArgs::HasOnlyAndRemove(TString)'
ape.cc:(.text+0x662): undefined reference to `TString::~TString()'
ape.cc:(.text+0x66f): undefined reference to `MArgs::GetNumOptions() const'
ape.cc:(.text+0x680): undefined reference to `gLog'
ape.cc:(.text+0x6b4): undefined reference to `MArgs::Print(char const*) const'
ape.cc:(.text+0x6bb): undefined reference to `gLog'
ape.cc:(.text+0x6d6): undefined reference to `MArgs::GetNumArguments() const'
ape.cc:(.text+0x6ed): undefined reference to `gLog'
ape.cc:(.text+0x72c): undefined reference to `MArgs::GetArgumentStr(int) const'
ape.cc:(.text+0x733): undefined reference to `gSystem'
ape.cc:(.text+0x772): undefined reference to `gLog'
ape.cc:(.text+0x79a): undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, TString const&)'
ape.cc:(.text+0x7ea): undefined reference to `TFile::TFile(char const*, char const*, char const*, int)'
ape.cc:(.text+0x806): undefined reference to `typeinfo for MAnalysisProblems'
ape.cc:(.text+0x80b): undefined reference to `TBuffer::GetClass(std::type_info const&)'
ape.cc:(.text+0x83d): undefined reference to `typeinfo for TTree'
ape.cc:(.text+0x842): undefined reference to `TBuffer::GetClass(std::type_info const&)'
ape.cc:(.text+0x870): undefined reference to `typeinfo for MAnalysisProblems'
ape.cc:(.text+0x875): undefined reference to `TClass::GetClass(std::type_info const&, bool, bool)'
ape.cc:(.text+0x88a): undefined reference to `typeinfo for MAnalysisProblems'
ape.cc:(.text+0x88f): undefined reference to `TDataType::GetType(std::type_info const&)'
ape.cc:(.text+0x8cf): undefined reference to `gLog'
ape.cc:(.text+0x8f7): undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, TString const&)'
ape.cc:(.text+0x938): undefined reference to `gLog'
ape.cc:(.text+0x960): undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, TString const&)'
ape.cc:(.text+0xa0e): undefined reference to `gLog'
ape.cc:(.text+0xa46): undefined reference to `gLog'
ape.cc:(.text+0xa7e): undefined reference to `gLog'
ape.cc:(.text+0xaa3): undefined reference to `gLog'
ape.cc:(.text+0xabd): undefined reference to `TFile::Close(char const*)'
ape.cc:(.text+0xada): undefined reference to `TFile::~TFile()'
ape.cc:(.text+0xaee): undefined reference to `TString::~TString()'
ape.cc:(.text+0xb10): undefined reference to `MArgs::~MArgs()'
ape.cc:(.text+0xb4c): undefined reference to `TString::~TString()'
ape.cc:(.text+0xb63): undefined reference to `TString::~TString()'
ape.cc:(.text+0xb75): undefined reference to `TString::~TString()'
ape.cc:(.text+0xb84): undefined reference to `TFile::~TFile()'
ape.cc:(.text+0xb96): undefined reference to `TString::~TString()'
ape.cc:(.text+0xba8): undefined reference to `MArgs::~MArgs()'
ape.o: In function `_GLOBAL__sub_I_ape.cc':
ape.cc:(.text+0xbe6): undefined reference to `TVersionCheck::TVersionCheck(int)'
ape.o: In function `TArrayI::operator[](int) const':
ape.cc:(.text._ZNK7TArrayIixEi[TArrayI::operator[](int) const]+0x29): undefined reference to `TArray::OutOfBoundsError(char const*, int) const'
ape.o: In function `operator<<(std::basic_ostream<char, std::char_traits<char> >&, _Debug)':
ape.cc:(.text._ZlsRSo6_Debug[operator<<(std::basic_ostream<char, std::char_traits<char> >&, _Debug)]+0x2f): undefined reference to `typeinfo for MLog'
collect2: ld devolvió el estado de salida 1
make: *** [ape] Error 1
```






If I debug (sorry because its in spanish):


.............................(this for every folder).............................
```
Este programa fue construido para x86_64-pc-linux-gnu
Leyendo makefiles...
Actualizando los objetivos finales....
 El archivo «all» no existe.
Se debe reconstruir el objetivo «all».
Se reconstruyó con éxito el archivo objetivo «all».
    Se reconstruyó con éxito el archivo objetivo «msignal.a».
     El archivo «mskyplot.a» no existe.
    Se debe reconstruir el objetivo «mskyplot.a».
 Calling make in mskyplot
GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
Este es software libre; consulte en el código fuente las condiciones de copia.
NO hay garantía; ni siquiera para MERCANTIBILIDAD o EL CUMPLIMIENTO DE
ALGÚN PROPÓSITO PARTICULAR.

.............................(this for every folder).............................


Este programa fue construido para x86_64-pc-linux-gnu
Leyendo makefiles...
Actualizando los objetivos finales....
 El archivo «all» no existe.
Se debe reconstruir el objetivo «all».
Se reconstruyó con éxito el archivo objetivo «all».
    Se reconstruyó con éxito el archivo objetivo «mtruee.a».
   La dependencia «manalysis.a» del blanco «libmars.so» no existe.
   La dependencia «mastro.a» del blanco «libmars.so» no existe.
   La dependencia «mbadpixels.a» del blanco «libmars.so» no existe.
   La dependencia «mbase.a» del blanco «libmars.so» no existe.
   La dependencia «mcalib.a» del blanco «libmars.so» no existe.
   La dependencia «mcamera.a» del blanco «libmars.so» no existe.
   La dependencia «mcta.a» del blanco «libmars.so» no existe.
   La dependencia «mdata.a» del blanco «libmars.so» no existe.
   La dependencia «mdisp.a» del blanco «libmars.so» no existe.
   La dependencia «mfbase.a» del blanco «libmars.so» no existe.
   La dependencia «mfileio.a» del blanco «libmars.so» no existe.
   La dependencia «mfilter.a» del blanco «libmars.so» no existe.
   La dependencia «mflux.a» del blanco «libmars.so» no existe.
   La dependencia «mgeom.a» del blanco «libmars.so» no existe.
   La dependencia «mgui.a» del blanco «libmars.so» no existe.
   La dependencia «mhbase.a» del blanco «libmars.so» no existe.
   La dependencia «mhcalib.a» del blanco «libmars.so» no existe.
   La dependencia «mhflux.a» del blanco «libmars.so» no existe.
   La dependencia «mhft.a» del blanco «libmars.so» no existe.
   La dependencia «mhist.a» del blanco «libmars.so» no existe.
   La dependencia «mhistmc.a» del blanco «libmars.so» no existe.
   La dependencia «mhvstime.a» del blanco «libmars.so» no existe.
   La dependencia «mimage.a» del blanco «libmars.so» no existe.
   La dependencia «mjobs.a» del blanco «libmars.so» no existe.
   La dependencia «mmain.a» del blanco «libmars.so» no existe.
   La dependencia «mmc.a» del blanco «libmars.so» no existe.
   La dependencia «mmccamera.a» del blanco «libmars.so» no existe.
   La dependencia «mmontecarlo.a» del blanco «libmars.so» no existe.
   La dependencia «mmuon.a» del blanco «libmars.so» no existe.
   La dependencia «monline.a» del blanco «libmars.so» no existe.
   La dependencia «mpedestal.a» del blanco «libmars.so» no existe.
   La dependencia «mpointing.a» del blanco «libmars.so» no existe.
   La dependencia «mpulsar.a» del blanco «libmars.so» no existe.
   La dependencia «mranforest.a» del blanco «libmars.so» no existe.
   La dependencia «mraw.a» del blanco «libmars.so» no existe.
   La dependencia «mreflector.a» del blanco «libmars.so» no existe.
   La dependencia «mreport.a» del blanco «libmars.so» no existe.
   La dependencia «msignal.a» del blanco «libmars.so» no existe.
   La dependencia «mskyplot.a» del blanco «libmars.so» no existe.
   La dependencia «msorcerer.a» del blanco «libmars.so» no existe.
   La dependencia «msql.a» del blanco «libmars.so» no existe.
   La dependencia «mstarcam.a» del blanco «libmars.so» no existe.
   La dependencia «msupercuts.a» del blanco «libmars.so» no existe.
   La dependencia «mtools.a» del blanco «libmars.so» no existe.
   La dependencia «mtrigger.a» del blanco «libmars.so» no existe.
   La dependencia «mtruee.a» del blanco «libmars.so» no existe.
  Se debe reconstruir el objetivo «libmars.so».
 Linking shared object libmars.so ...
  Se reconstruyó con éxito el archivo objetivo «libmars.so».
   El archivo «ape» no existe.
  Se debe reconstruir el objetivo «ape».
 Linking ape ...
ape.o: In function `Usage()':
ape.cc:(.text+0x9): undefined reference to `gLog'
ape.cc:(.text+0x2a): undefined reference to `typeinfo for MLog'
ape.cc:(.text+0x50): undefined reference to `gLog'
ape.cc:(.text+0x8e): undefined reference to `gLog'
ape.cc:(.text+0xfa): undefined reference to `gLog'
ape.cc:(.text+0x166): undefined reference to `gLog'
ape.cc:(.text+0x1db): undefined reference to `gLog'
ape.o:ape.cc:(.text+0x22a): more undefined references to `gLog' follow
ape.o: In function `main':
ape.cc:(.text+0x4dd): undefined reference to `MArgs::MArgs(int, char**, bool)'
ape.cc:(.text+0x4f1): undefined reference to `TString::TString(char const*)'
ape.cc:(.text+0x51a): undefined reference to `MArgs::HasOnly(TString) const'
ape.cc:(.text+0x53b): undefined reference to `TString::TString(char const*)'
ape.cc:(.text+0x564): undefined reference to `MArgs::HasOnly(TString) const'
ape.cc:(.text+0x599): undefined reference to `TString::TString(char const*)'
ape.cc:(.text+0x5c2): undefined reference to `MArgs::HasOnly(TString) const'
ape.cc:(.text+0x5d1): undefined reference to `TString::~TString()'
ape.cc:(.text+0x5e3): undefined reference to `TString::~TString()'
ape.cc:(.text+0x60f): undefined reference to `TString::~TString()'
ape.cc:(.text+0x61c): undefined reference to `TString::~TString()'
ape.cc:(.text+0x63e): undefined reference to `TString::TString(char const*)'
ape.cc:(.text+0x653): undefined reference to `MArgs::HasOnlyAndRemove(TString)'
ape.cc:(.text+0x662): undefined reference to `TString::~TString()'
ape.cc:(.text+0x66f): undefined reference to `MArgs::GetNumOptions() const'
ape.cc:(.text+0x680): undefined reference to `gLog'
ape.cc:(.text+0x6b4): undefined reference to `MArgs::Print(char const*) const'
ape.cc:(.text+0x6bb): undefined reference to `gLog'
ape.cc:(.text+0x6d6): undefined reference to `MArgs::GetNumArguments() const'
ape.cc:(.text+0x6ed): undefined reference to `gLog'
ape.cc:(.text+0x72c): undefined reference to `MArgs::GetArgumentStr(int) const'
ape.cc:(.text+0x733): undefined reference to `gSystem'
ape.cc:(.text+0x772): undefined reference to `gLog'
ape.cc:(.text+0x79a): undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, TString const&)'
ape.cc:(.text+0x7ea): undefined reference to `TFile::TFile(char const*, char const*, char const*, int)'
ape.cc:(.text+0x806): undefined reference to `typeinfo for MAnalysisProblems'
ape.cc:(.text+0x80b): undefined reference to `TBuffer::GetClass(std::type_info const&)'
ape.cc:(.text+0x83d): undefined reference to `typeinfo for TTree'
ape.cc:(.text+0x842): undefined reference to `TBuffer::GetClass(std::type_info const&)'
ape.cc:(.text+0x870): undefined reference to `typeinfo for MAnalysisProblems'
ape.cc:(.text+0x875): undefined reference to `TClass::GetClass(std::type_info const&, bool, bool)'
ape.cc:(.text+0x88a): undefined reference to `typeinfo for MAnalysisProblems'
ape.cc:(.text+0x88f): undefined reference to `TDataType::GetType(std::type_info const&)'
ape.cc:(.text+0x8cf): undefined reference to `gLog'
ape.cc:(.text+0x8f7): undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, TString const&)'
ape.cc:(.text+0x938): undefined reference to `gLog'
ape.cc:(.text+0x960): undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, TString const&)'
ape.cc:(.text+0xa0e): undefined reference to `gLog'
ape.cc:(.text+0xa46): undefined reference to `gLog'
ape.cc:(.text+0xa7e): undefined reference to `gLog'
ape.cc:(.text+0xaa3): undefined reference to `gLog'
ape.cc:(.text+0xabd): undefined reference to `TFile::Close(char const*)'
ape.cc:(.text+0xada): undefined reference to `TFile::~TFile()'
ape.cc:(.text+0xaee): undefined reference to `TString::~TString()'
ape.cc:(.text+0xb10): undefined reference to `MArgs::~MArgs()'
ape.cc:(.text+0xb4c): undefined reference to `TString::~TString()'
ape.cc:(.text+0xb63): undefined reference to `TString::~TString()'
ape.cc:(.text+0xb75): undefined reference to `TString::~TString()'
ape.cc:(.text+0xb84): undefined reference to `TFile::~TFile()'
ape.cc:(.text+0xb96): undefined reference to `TString::~TString()'
ape.cc:(.text+0xba8): undefined reference to `MArgs::~MArgs()'
ape.o: In function `_GLOBAL__sub_I_ape.cc':
ape.cc:(.text+0xbe6): undefined reference to `TVersionCheck::TVersionCheck(int)'
ape.o: In function `TArrayI::operator[](int) const':
ape.cc:(.text._ZNK7TArrayIixEi[TArrayI::operator[](int) const]+0x29): undefined reference to `TArray::OutOfBoundsError(char const*, int) const'
ape.o: In function `operator<<(std::basic_ostream<char, std::char_traits<char> >&, _Debug)':
ape.cc:(.text._ZlsRSo6_Debug[operator<<(std::basic_ostream<char, std::char_traits<char> >&, _Debug)]+0x2f): undefined reference to `typeinfo for MLog'
collect2: ld devolvió el estado de salida 1
make: *** [ape] Error 1
```

---

