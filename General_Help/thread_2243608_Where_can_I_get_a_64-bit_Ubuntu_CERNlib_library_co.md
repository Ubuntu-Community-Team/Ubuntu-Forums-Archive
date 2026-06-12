---
title: "Where can I get a 64-bit Ubuntu CERNlib library compatible with i386 and gfortran?"
date: 2014-09-10
forum: General Help
---

### Post by alice5 on 2014-09-10
I would like to run gfortran with the -m32 flag as my fortran code is in the f77 version, so I also need CERNlib libraries to be i386 compatible. I have downloaded Ubuntu packages: cernlib, [COLOR=#333333][FONT=Helvetica Neue]lib32gfortran-4.8-dev, and gcc-multilib.[/FONT][/COLOR]

I also downloaded libmathlib.a and libkernlib.a from [http://cernlib.web.cern.ch/cernlib/version.html](http://cernlib.web.cern.ch/cernlib/version.html), but all of the versions, be it 2006 or 2004, give me these errors:


    $ gfortran -m32 -O -o out10 MBpart1ep0.f -L. -lmathlib -lkernlib -Lcuba

    /tmp/ccs5Njbz.o: In function `MAIN__':
    MBpart1ep0.f: (.text+0x82): undefined reference to `cuhre_'
    //usr/local/lib/libmathlib.a(cgamma64.o): In function `wgamma_':
    cgamma64.F: (.text+0xd1): undefined reference to `s_wsfi'
    cgamma64.F: (.text+0xe5): undefined reference to `do_fio'
    cgamma64.F: (.text+0xea): undefined reference to `e_wsfi'
    cgamma64.F: (.text+0x424): undefined reference to `z_log'
    cgamma64.F: (.text+0x47e): undefined reference to `z_exp'
    cgamma64.F: (.text+0x522): undefined reference to `z_sin'
    //usr/local/lib/libmathlib.a(wpsipg.o): In function `wpsipg_':
    wpsipg.F: (.text+0x97): undefined reference to `s_wsfi'
    wpsipg.F: (.text+0xa7): undefined reference to `do_fio'
    wpsipg.F: (.text+0xac): undefined reference to `e_wsfi'
    wpsipg.F: (.text+0x1b4): undefined reference to `s_wsfi'
    wpsipg.F: (.text+0x1c8): undefined reference to `do_fio'
    wpsipg.F: (.text+0x1cd): undefined reference to `e_wsfi'
    wpsipg.F: (.text+0x8e7): undefined reference to `z_log'
    //usr/local/lib/libmathlib.a(mtlprt.o): In function `mtlprt_':
    mtlprt.F: (.text+0x20): undefined reference to `s_cmp'
    mtlprt.F: (.text+0x90): undefined reference to `s_wsfe'
    mtlprt.F: (.text+0xa0): undefined reference to `do_fio'
    mtlprt.F: (.text+0xb3): undefined reference to `do_fio'
    mtlprt.F: (.text+0xc2): undefined reference to `do_fio'
    mtlprt.F: (.text+0xd6): undefined reference to `do_fio'
    mtlprt.F: (.text+0xdb): undefined reference to `e_wsfe'
    mtlprt.F: (.text+0xfe): undefined reference to `s_wsfe'
    mtlprt.F: (.text+0x10e): undefined reference to `do_fio'
    mtlprt.F: (.text+0x121): undefined reference to `do_fio'
    mtlprt.F: (.text+0x130): undefined reference to `do_fio'
    mtlprt.F: (.text+0x144): undefined reference to `do_fio'
    mtlprt.F: (.text+0x149): undefined reference to `e_wsfe'
    //usr/local/lib/libmathlib.a(mtlset.o): In function `__g77_masterfun_mtlset':
    mtlset.F: (.text+0x38): undefined reference to `s_cmp'
    mtlset.F: (.text+0x5d): undefined reference to `s_cmp'
    mtlset.F: (.text+0xa7): undefined reference to `s_cmp'
    mtlset.F: (.text+0x11a): undefined reference to `s_cmp'
    mtlset.F: (.text+0x137): undefined reference to `s_wsfe'
    mtlset.F: (.text+0x147): undefined reference to `do_fio'
    mtlset.F: (.text+0x14c): undefined reference to `e_wsfe'
    mtlset.F: (.text+0x1d7): undefined reference to `s_wsfe'
    mtlset.F: (.text+0x1f6): undefined reference to `do_fio'
    mtlset.F: (.text+0x1fb): undefined reference to `e_wsfe'
    mtlset.F: (.text+0x21e): undefined reference to `s_wsfe'
    mtlset.F: (.text+0x23d): undefined reference to `do_fio'
    mtlset.F: (.text+0x242): undefined reference to `e_wsfe'
    collect2: error: ld returned 1 exit status

---

### Post by alice5 on 2014-09-10
This is what solved my problem: [http://askubuntu.com/questions/522526/how-to-get-gfortran-to-work-with-i386-i-have-undefined-reference-errors-how](http://askubuntu.com/questions/522526/how-to-get-gfortran-to-work-with-i386-i-have-undefined-reference-errors-how)  I didn't even need to get i386! I could just use the 64-bit version. :)

---

