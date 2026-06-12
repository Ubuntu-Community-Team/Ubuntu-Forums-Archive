---
title: "crosstool-ng build fail on ubuntu 14.04 destop 32 bits"
date: 2015-01-12
forum: General Help
---

### Post by uPatrick on 2015-01-12
I build crosstool-ng version 1.9.3 on ubuntu 32 bits destop 14.04, I get the following error

=================================================================


[00:02] / 
[INFO ]  Extracting and patching toolchain components
00:04] / 
[ERROR]    configure.in:294: error: automatic de-ANSI-fication support has been removed
[00:06] / 
[ERROR]    aclocal: error: echo failed with exit status: 1
[00:06] / 
[ERROR]    Build failed in step 'Extracting and patching toolchain components'
[00:06] / 
[ERROR]    Error happened in '/home/patrick/embedded-arm/crosstool-ng/crosstool-ng-1.9.3/scripts/functions' in function 'CT_DoExecLog' (line unknown, sorry)
[00:06] / 
[ERROR]          called from '/home/patrick/embedded-arm/crosstool-ng/crosstool-ng-1.9.3/scripts/build/companion_libs/mpfr.sh' at line # 36 in function 'do_mpfr_extract'
[00:06] / 
[ERROR]          called from '/home/patrick/embedded-arm/crosstool-ng/crosstool-ng-1.9.3/scripts/crosstool-NG.sh' at line # 559 in function 'main'
[00:06] / 
[ERROR]    Look at '/home/patrick/x-tools/arm-cortex_a8-linux-gnueabi/build.log' for more info on this error.
[00:06] / 
[ERROR]  (elapsed: 0:05.27)

on the script mpfr.sh, I change line 36 but no help same error
            if [ ! -f .autoreconf.ct-ng ]; then
                CT_DoLog DEBUG "Running autoreconf"
                CT_DoExecLog ALL autoreconf
                touch .autoreconf.ct-ng
            fi
change to ===>
            if [ ! -f .autoreconf.ct-ng ]; then
                CT_DoLog DEBUG "Running autoreconf"
                CT_DoExecLog ALL autoreconf -fi
                touch .autoreconf.ct-ng
            fi



Any help ?

Patrick

---

