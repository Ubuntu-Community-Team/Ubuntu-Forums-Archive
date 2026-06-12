---
title: "Installation of Gaussian 09 in ubuntu"
date: 2015-08-26
forum: General Help
---

### Post by karthi.mku.physici on 2015-08-26
Dear Friends,

I am J. Karthikeyan, research scholar from CSIR-Central Electrochemical Research Institute, India. I am doing my PhD there. Two years before, We bought Gaussian 09 software for redhat OS. but now we use only ubuntu in all our workstation. I am trying to install Gaussian in ubuntu machine which is having pgfortran as instructed in the forum ([http://ubuntuforums.org/showthread.php?p=12171054](http://ubuntuforums.org/showthread.php?p=12171054)). but I am getting error in c[COLOR=#000000]ompilation[/COLOR] step. 

When i give the following command

```
./bsd/bldg09 2>&1 | tee make.log
```

I am getting the error like this.. Please help me to solve this problem.. Thanks in advance.

```

uname -a
Linux Einstein4 3.2.0-55-generic #85-Ubuntu SMP Wed Oct 2 12:29:27 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
set makeflag = 
set makename = make
setenv TMPDIR .
setenv LC_COLLATE C
setenv LANG C
if ( ( == ) || ( == all ) ) then
@ dolink = 1
@ delexe = 1
@ doutil = 1
@ resutil = 0
@ dohermes = 0
else if ( ( == nolink ) || ( == utilonly ) ) then
@ doprof = 0
@ doamd64 = 0
@ doip4 = 0
@ doip3 = 0
@ dop1 = 0
@ dop2 = 0
@ doi4 = 0
@ noomp = 0
@ ibm = 0
@ ia64 = 0
@ em64t = 0
@ mac32 = 0
@ small = 0
@ istanbul = 0
@ nehalem = 0
@ dop5 = 0
@ fjsparc = 0
if ( == small ) then
if ( == medium ) then
if ( == prof ) then
if ( == ibmp1 ) then
if ( == ibmp2 ) then
if ( ( == ibmp5 ) || ( == ibmp6 ) ) then
if ( == i4 ) then
if ( == ia64 ) then
if ( == ia32p4 ) then
if ( == ia32p3 ) then
if ( == x86-64 ) then
if ( == em64t ) then
if ( == mac32 ) then
if ( == istanbul ) then
if ( == nehalem ) then
if ( == fjsparc ) then
if ( == noomp ) then
if ( 0 && ( ! 1 ) ) then
set utilname=util.a
endif
if ( 1 ) then
touch delete_me.exe
rm -f -r delete_me.exe
endif
set machflag = 
if ( `hostname` == sun4 ) then
hostname
if ( -e /usr/convex/bin/cc ) then
if ( -e /opt/FSUNf90/bin/fcc ) then
if ( 0 ) then
if ( 0 ) then
set zzz = `which ifort`
which ifort
ifort: Command not found.
if ( 1 ) unsetenv LD_LIBRARY_PATH
unsetenv LD_LIBRARY_PATH
setenv NPES 1
cc -o gau-machine bsd/machine.c
cc: error: bsd/machine.c: No such file or directory
cc: fatal error: no input files
compilation terminated.
unsetenv NPES
endif
set x = `./gau-machine`
./gau-machine
echo machine type is amd64
machine type is amd64
set CWD=`pwd`
pwd
setenv PATH /usr/local/g09:/usr/local/g09/bsd:/opt/pgi/linux86-64/11.8/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/wien/w2w:/opt/wien/util:/opt/wien/wplot:/opt/wien/woptic:/opt/wannier90-1.2::/usr/local/g09/bsd:/usr/local/g09/local:/usr/local/g09/extras:/usr/local/g09:/opt/wien/w2w:/opt/wien/util:/opt/wien/wplot:/opt/wien/woptic:/opt/wannier90-1.2::/usr/local/g09/bsd:/usr/local/g09/local:/usr/local/g09/extras:/usr/local/g09
if ( ! ( 1 ) ) setenv g09root /usr/local
source /usr/local/g09/bsd/g09.login
if ( 1 ) then
set gr=/usr/local
else
setenv GAUSS_EXEDIR /usr/local/g09/bsd:/usr/local/g09/local:/usr/local/g09/extras:/usr/local/g09
setenv GAUSS_LEXEDIR /usr/local/g09/linda-exe
setenv GAUSS_ARCHDIR /usr/local/g09/arch
setenv GAUSS_BSDDIR /usr/local/g09/bsd
setenv GV_DIR /usr/local/gv
if ( -e /usr/local/gv/gview.app ) then
alias gv /usr/local/gv/gview.csh
endif
if ( ! 1 ) setenv PGI /usr/pgi
if ( ! 0 ) then
foreach y ( linux86-64 linux86 )
foreach x ( 11.8 11.6 11.5 10.5 9.0-4 8.0-6 7.2-5 7.1-5 7.1-4 7.1-3 7.1-2 7.1-1 )
if ( -e /opt/pgi/linux86-64/11.8 ) then
setenv PGIDIR /opt/pgi/linux86-64/11.8
goto PGIDONE
endif
if ( 1 ) then
setenv PATH /usr/local/g09:/usr/local/g09/bsd:/opt/pgi/linux86-64/11.8/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/wien/w2w:/opt/wien/util:/opt/wien/wplot:/opt/wien/woptic:/opt/wannier90-1.2::/usr/local/g09/bsd:/usr/local/g09/local:/usr/local/g09/extras:/usr/local/g09:/opt/wien/w2w:/opt/wien/util:/opt/wien/wplot:/opt/wien/woptic:/opt/wannier90-1.2::/usr/local/g09/bsd:/usr/local/g09/local:/usr/local/g09/extras:/usr/local/g09:/usr/local/g09/bsd:/usr/local/g09/local:/usr/local/g09/extras:/usr/local/g09
else
if ( 0 ) then
if ( 0 ) then
setenv PERLLIB /usr/local/g09/bsd
endif
rehash
setenv _DSM_BARRIER SHM
setenv _RLD_ARGS -log /dev/null
if ( 0 ) then
if ( 0 ) then
setenv LD_LIBRARY_PATH /usr/local/g09/bsd:/usr/local/g09/local:/usr/local/g09/extras:/usr/local/g09:/usr/local/gv/lib
endif
setenv G09BASIS /usr/local/g09/basis
set gman=/usr/local/g09/bsd
if ( 1 ) then
setenv MANPATH /usr/local/g09/bsd::/opt/pgi/linux86-64/11.8/man
endif
alias sl /usr/local/g09/tests/searchlog.csh
set mname = `set-mflags x`
set-mflags x
./gau-hname: Command not found.
set mflags = `set-mflags`
set-mflags
./gau-hname: Command not found.
alias mg make -f bsd/g09.make 
if ( -e /usr/local/g09/bsd/setup-make ) then
source /usr/local/g09/bsd/setup-make
set mach = `gau-hname`
gau-hname
set xname = /usr/local/g09
set mstr = make
set dimstr = 
set mflags = 
if ( 0 ) unsetenv LINDA_CC
if ( -e /usr/local/g09/small.flag ) set dimstr = GAUDIM=10
if ( -e /usr/local/g09/medium.flag ) set dimstr = GAUDIM=200
if ( ( em64t == ibm_rs6k_aix ) || ( em64t == ibm_rs6k_linux ) || ( em64t == ibm_rs6k_osx ) ) then
if ( em64t == alpha-osf1 ) then
if ( em64t == alpha-linux ) then
if ( em64t == cray1 ) then
if ( ( em64t == i386 ) || ( em64t == amd64 ) || ( em64t == em64t ) || ( em64t == i386-mac64 ) || ( em64t == i386-mac32 ) ) then
if ( -e /usr/local/g09/ia32p3.flag ) then
if ( em64t == i386 ) then
if ( em64t == amd64 ) then
if ( em64t == em64t ) then
if ( -e /usr/local/g09/nehalem.flag ) then
set fcname = FCN='pgf77 -Bstatic_pgi'
set fcflag = FC='-mp=nonuma -tp nehalem-64 -i8 -r8 -mcmodel=medium'
set blas = BLAS='' UTIL_NAME='{util,bsd/libf77blas-corei764sse3,bsd/libatlas-corei764sse3}.a' MACHTY=nehalem-64 GAULIBU=util.a I8FLAG=-i8 R8FLAG=-r8 MMODEL='-mcmodel=medium' OPTOI= I8CPP1=-DI64 I8CPP2=-DP64 I8CPP3=-DPACK64 I8CPP4=-DUSE_I2 NJSEC=-DDEFJSEC=512 XGEMMINI=-DXGEMM_INIT
set lfort = pgf77 -Bstatic_pgi -mp=nonuma -tp nehalem-64 -i8 -r8 -mcmodel=medium
else
else if ( em64t == i386-mac64 ) then
set fcflagp = 
set fc2flag = FC2='-lpthread -lm -lc'
setenv LINDA_FORTRAN pgf77 -Bstatic_pgi -mp=nonuma -tp nehalem-64 -i8 -r8 -mcmodel=medium
setenv POSTFL_FORTRAN pgf77 -Bstatic_pgi -mp=nonuma -tp nehalem-64 -i8 -r8 -mcmodel=medium
setenv LINDA_FORTRAN_LINK pgf77 -Bstatic_pgi -mp=nonuma -tp nehalem-64 -i8 -r8 -mcmodel=medium
set blasp = BLAS='' UTIL_NAME='{util,bsd/libf77blas-corei764sse3,bsd/libatlas-corei764sse3}.a' MACHTY=nehalem-64 GAULIBU=util.a I8FLAG=-i8 R8FLAG=-r8 MMODEL='-mcmodel=medium' OPTOI= I8CPP1=-DI64 I8CPP2=-DP64 I8CPP3=-DPACK64 I8CPP4=-DUSE_I2 NJSEC=-DDEFJSEC=512 XGEMMINI=-DXGEMM_INIT
set pstr = -p
else if ( em64t == sun_solaris2 ) then
alias mk make GAU_DIR=/usr/local/g09 BLAS='' UTIL_NAME='{util,bsd/libf77blas-corei764sse3,bsd/libatlas-corei764sse3}.a' MACHTY=nehalem-64 GAULIBU=util.a I8FLAG=-i8 R8FLAG=-r8 MMODEL='-mcmodel=medium' OPTOI= I8CPP1=-DI64 I8CPP2=-DP64 I8CPP3=-DPACK64 I8CPP4=-DUSE_I2 NJSEC=-DDEFJSEC=512 XGEMMINI=-DXGEMM_INIT FCN='pgf77 -Bstatic_pgi' FC='-mp=nonuma -tp nehalem-64 -i8 -r8 -mcmodel=medium' FC2='-lpthread -lm -lc'
alias mkp make GAU_DIRA=/usr/local/g09/prof UTIL_NAME=profutil.a BLAS='' UTIL_NAME='{util,bsd/libf77blas-corei764sse3,bsd/libatlas-corei764sse3}.a' MACHTY=nehalem-64 GAULIBU=util.a I8FLAG=-i8 R8FLAG=-r8 MMODEL='-mcmodel=medium' OPTOI= I8CPP1=-DI64 I8CPP2=-DP64 I8CPP3=-DPACK64 I8CPP4=-DUSE_I2 NJSEC=-DDEFJSEC=512 XGEMMINI=-DXGEMM_INIT FCN='pgf77 -Bstatic_pgi' FC2='-lpthread -lm -lc' PROFFLAG=-p UPROFFLAG=-p
alias mkno make GAU_DIR=/usr/local/g09 BLAS='' UTIL_NAME='{util,bsd/libf77blas-corei764sse3,bsd/libatlas-corei764sse3}.a' MACHTY=nehalem-64 GAULIBU=util.a I8FLAG=-i8 R8FLAG=-r8 MMODEL='-mcmodel=medium' OPTOI= I8CPP1=-DI64 I8CPP2=-DP64 I8CPP3=-DPACK64 I8CPP4=-DUSE_I2 NJSEC=-DDEFJSEC=512 XGEMMINI=-DXGEMM_INIT FCN='pgf77 -Bstatic_pgi' FC='-mp=nonuma -tp nehalem-64 -i8 -r8 -mcmodel=medium' FC2='-lpthread -lm -lc' PROFFLAG='-g -O0' UPROFFLAG='-g -O0'
alias gt g09 -exedir=l1:exe-dir:/usr/local/g09/bsd:/usr/local/g09/local:/usr/local/g09/extras:/usr/local/g09
alias gtl g09 -exedir=l1:linda-exe:exe-dir:/usr/local/g09/linda-exe:/usr/local/g09/bsd:/usr/local/g09/local:/usr/local/g09/extras:/usr/local/g09
alias gtlx g09 -exedir=/mf/frisch/working/l1:/mf/frisch/working/linda-exe:/mf/frisch/working/exe-dir:/usr/local/g09/linda-exe:/usr/local/g09/bsd:/usr/local/g09/local:/usr/local/g09/extras:/usr/local/g09
alias ngt nohup `alias gt`
alias gt
alias ngtl nohup `alias gtl`
alias gtl
alias mkf make -f /usr/local/g09/bsd/g09.make
endif
if ( -e `which gau-machine` ) then
which gau-machine
set mach = `./gau-machine`
./gau-machine
else
if ( amd64 == necsx ) then
if ( amd64 == sgi ) then
if ( amd64 == ia64 ) then
if ( amd64 == crayx1 ) then
if ( amd64 == ibm_rs6k_linux ) then
setenv PGI_TERM trace,abort
set xtmp = /usr/local/g09/tests/search.csh
alias ss /usr/local/g09/tests/search.csh log ia64
alias si /usr/local/g09/tests/search.csh log ibm
set unl = /usr/local/g09/bsd/gau-unlimit
if ( -e /usr/local/g09/bsd/gau-unlimit ) then
source /usr/local/g09/bsd/gau-unlimit
set x = `./gau-machine`
./gau-machine
if ( ( amd64 != cray1 ) && ( amd64 != cray2 ) && ( amd64 != crayt3e ) && ( amd64 != hp700 ) && ( amd64 != necsx ) && ( amd64 != convex_spp ) && ( amd64 != hi_ux ) && ( amd64 != hi_osf ) && ( amd64 != i386-win32 ) ) then
unlimit datasize
if ( ( amd64 != sun_solaris2 ) && ( amd64 != amd_solaris2 ) && ( amd64 != intel_solaris2 ) && ( amd64 != i386 ) && ( amd64 != gp7kf ) ) unlimit memoryuse
unlimit memoryuse
limit coredumpsize 0
limit: coredumpsize: Can't set limit

```

---

### Post by dino99 on 2015-08-26
here is a howto related to installing into Ubuntu Precise

[https://www.quora.com/Can-Gaussian09-be-installed-in-Ubuntu-11?share=1](https://www.quora.com/Can-Gaussian09-be-installed-in-Ubuntu-11?share=1)

when glancing at your compile log, i'm seeing some 'no file found' so you need first to check for there path/installation (gfortran ?)
and avoid using 'reserved' word like 'make' found at the log top

[http://www.gaussian.com/g_tech/g_ur/m_running.htm](http://www.gaussian.com/g_tech/g_ur/m_running.htm)

---

### Post by Bucky Ball on 2015-08-26
*Thread moved to **General Help**.*

Welcome. The ***Installations and Upgrade*** section is for installation and upgrades to the operating system. :)

---

