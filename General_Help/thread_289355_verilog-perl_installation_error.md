---
title: "verilog-perl installation error"
date: 2006-10-30
forum: General Help
---

### Post by duramp1 on 2006-10-30
Hi,

 I am trying to install verilog-perl-2.361 in kubuntu 6.06. but I am getting the following error. Anyone know what I am doing wrong?

thanks,
duram

----------------------------------------------------------------
user8@tronix:~/data_transfer/verilator/Verilog-Perl-2.361$ perl Makefile.PL
Checking if your kit is complete...
Looks good
Writing Makefile for Verilog::Preproc::lib
Writing Makefile for Verilog::Preproc
Writing Makefile for Verilog::Language

user8@tronix:~/data_transfer/verilator/Verilog-Perl-2.361$ make
Skip blib/lib/Verilog/Netlist/Cell.pm (unchanged)
Skip blib/lib/Verilog/Netlist/Net.pm (unchanged)
Skip blib/lib/Verilog/Getopt.pm (unchanged)
Skip blib/lib/Verilog/Parse.pm (unchanged)
Skip blib/lib/Verilog/Netlist/Port.pm (unchanged)
Skip blib/lib/Verilog/Language.pm (unchanged)
Skip blib/lib/Verilog/Netlist/Pin.pm (unchanged)
Skip blib/lib/Verilog/Netlist.pm (unchanged)
Skip blib/lib/Verilog/Netlist/Subclass.pm (unchanged)
Skip blib/lib/Verilog/Netlist/File.pm (unchanged)
Skip blib/lib/Verilog/Parser.pm (unchanged)
Skip blib/lib/Verilog/Netlist/Module.pm (unchanged)
Skip blib/lib/Verilog/SigParser.pm (unchanged)
make[1]: Entering directory `/home/user8/data_transfer/verilator/Verilog-Perl-2.361/Preproc'
Skip ../blib/lib/Verilog/Preproc.pm (unchanged)
cd src && make  example
make[2]: Entering directory `/home/user8/data_transfer/verilator/Verilog-Perl-2.361/Preproc/src'
g++ -c   -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"\" -DXS_VERSION=\"\" -fPIC "-I/usr/lib/perl/5.8/CORE"   example.cpp
g++ -c   -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"\" -DXS_VERSION=\"\" -fPIC "-I/usr/lib/perl/5.8/CORE"   VPreproc.cpp
g++ -c   -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"\" -DXS_VERSION=\"\" -fPIC "-I/usr/lib/perl/5.8/CORE"   VFileLine.cpp
flex  -oVPreprocLex.cpp VPreprocLex.l
g++ -c   -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"\" -DXS_VERSION=\"\" -fPIC "-I/usr/lib/perl/5.8/CORE"   VPreprocLex.cpp
VPreprocLex.l: In member function ‘void VPreprocLex::unputString(const char*)’:
VPreprocLex.l:177: error: ‘yytext_ptr’ was not declared in this scope
make[2]: *** [VPreprocLex.o] Error 1
make[2]: Leaving directory `/home/user8/data_transfer/verilator/Verilog-Perl-2.361/Preproc/src'
make[1]: *** [src/VFileLine.o] Error 2
make[1]: Leaving directory `/home/user8/data_transfer/verilator/Verilog-Perl-2.361/Preproc'
make: *** [subdirs] Error 2

---

