---
title: "Freedom error in Ubuntu 7.04 !"
date: 2007-05-19
forum: General Help
---

### Post by mruser on 2007-05-19
I waw trying to install one of my .tar files named as "Freedom" foranalysis of  my experimental data.

I tried following commands:

tar -zxvf Freedom23Aug03.tgz
cd Freedom
make
make install
cp X Freedom /home/user

[COLOR="Red"]
_The output of all the commands (it gave error) is as below_[/COLOR]

Freedom/Files/CFG/CAM/
Freedom/Files/CFG/DSP/
Freedom/Files/CFG/ERD/
Freedom/Files/CFG/ERD/CFG/
Freedom/Files/CFG/ERD/CFG/x.ERD
Freedom/Files/CFG/ERD/CFG/Al.erd
Freedom/Files/CFG/ERD/CFG/DLC.ERD
Freedom/Files/CFG/ERD/CFG/ECR.ERD
Freedom/Files/CFG/ERD/SIM/
Freedom/Files/CFG/ERD/CMPND/
Freedom/Files/CFG/ERD/CMPND/ERDAT.DAT
Freedom/Files/CFG/ERD/CMPND/erdat.c
Freedom/Files/CFG/ERD/CMPND/COMPOUNDS.DAT
Freedom/Files/CFG/ERD/CMPND/IMPURITIES.DAT
Freedom/Files/CFG/GON/
Freedom/Files/CFG/GON/chnag.gon
Freedom/Files/CFG/GTE/
Freedom/Files/CFG/LIN/
Freedom/Files/SPC/
Freedom/Files/SPC/ONED/
Freedom/Files/SPC/ONED/oned.ONE
Freedom/Files/SPC/ALL/
Freedom/Files/SPC/TWOD/
Freedom/Files/FIT/
Freedom/Files/MAT/
Freedom/Files/DAT/
Freedom/hira.dat
Freedom/Makefile
Freedom/Source/
Freedom/Source/Client/
Freedom/Source/Client/autofit.c
Freedom/Source/Client/sca_init.c
Freedom/Source/Client/sca_init.h
Freedom/Source/Client/calc.y
Freedom/Source/Client/calc.h
Freedom/Source/Client/calc.c
Freedom/Source/Client/update.c
Freedom/Source/Client/typedefs.h
Freedom/Source/Client/widgets.h
Freedom/Source/Client/widgets.c
Freedom/Source/Client/freedom.h
Freedom/Source/Client/freedom.c
Freedom/Source/Client/shared.c
Freedom/Source/Client/erda.h
Freedom/Source/Client/erda.c
Freedom/Source/Client/project.c
Freedom/Source/Client/project.h
Freedom/Source/Client/process.c
Freedom/Source/Client/tdccal.c
Freedom/Source/Client/matproc.c
Freedom/Source/Client/filebox.h
Freedom/Source/Client/filebox.c
Freedom/Source/Client/erdat.c
Freedom/Source/Client/gated.c
Freedom/Source/Client/list_cfg.h
Freedom/Source/Client/list_cfg.c
Freedom/Source/Client/disp_cfg.h
Freedom/Source/Client/disp_cfg.c
Freedom/Source/Client/evt_sel.h
Freedom/Source/Client/evt_sel.c
Freedom/Source/Client/erdasch.c
Freedom/Source/Client/fit_cfg.h
Freedom/Source/Client/fit_cfg.c
Freedom/Source/Client/XFreedom
Freedom/Source/Client/Makefile
Freedom/Source/Client/select.c
Freedom/Source/Client/select.h
Freedom/Source/Client/linear.c
Freedom/Source/Client/help.c
Freedom/Source/Client/bit_cfg.h
Freedom/Source/Client/bit_cfg.c
Freedom/Source/Client/col_cfg.h
Freedom/Source/Client/col_cfg.c
Freedom/Source/Client/cal_cfg.h
Freedom/Source/Client/cal_cfg.c
Freedom/Source/Client/cvt_type.c
Freedom/Source/Client/fit.c
Freedom/Source/Client/config.c
Freedom/Source/Client/config.h
Freedom/Source/Client/erdawids.c
Freedom/Source/Client/message.h
Freedom/Source/Client/message.c
Freedom/Source/Client/zoommark.c
Freedom/Source/Client/twod.c
Freedom/Source/Client/manipulate.c
Freedom/Source/Client/globals.h
Freedom/Source/Client/cfg_wids.c
Freedom/Source/Client/routines.h
Freedom/Source/Client/lp_form.c
Freedom/Source/Client/grids.c
Freedom/Source/Client/main_wid.c
Freedom/Source/Client/contour.c
Freedom/Source/Client/file.c
Freedom/Source/Client/print.c
Freedom/Source/Client/print.h
Freedom/Source/Client/iso.c
Freedom/Source/Client/hist.c
Freedom/Source/Client/xbits.c
Freedom/Source/Client/ovr_zero.c
Freedom/Source/Client/socket.c
Freedom/Source/Client/calib.c
Freedom/Source/Client/user_cfg.c
Freedom/Source/Client/user_cfg.h
Freedom/Source/Client/sing_cfg.c
Freedom/Source/Client/sing_cfg.h
Freedom/Source/Client/serv_cmd.c
Freedom/Source/Client/serv_cmd.h
Freedom/Source/Client/common.h
Freedom/Source/Client/chimin.c
Freedom/Source/Client/erdaprof.c
Freedom/Source/Client/receive.c
Freedom/Source/Client/gonio.h
Freedom/Source/Client/gonio.c
Freedom/Source/Client/init.c
Freedom/Source/Client/erdacalc.h
Freedom/Source/Client/erdacalc.c
Freedom/Source/Client/modscale.c
Freedom/Source/Client/fit_wids.c
Freedom/Source/Client/tickbits.c
Freedom/Source/Client/scroll.c
Freedom/Source/Client/layout.c
Freedom/Source/Client/calc.tab.c
Freedom/Source/Client/hira.c
Freedom/Source/Client/hira.dat
Freedom/Source/Client/gates
Freedom/Source/Client/userproc.c
Freedom/Source/Client/.erda.c.swp
Freedom/Source/Examine/
Freedom/Source/Examine/se.f
Freedom/Source/Examine/all_load.c
Freedom/Source/Examine/read2d.c
Freedom/Source/Examine/read1d.c
Freedom/Source/Examine/shmtes.c
Freedom/Source/Examine/tst.c
Freedom/Source/Examine/Makefile
Freedom/Source/Examine/dserv.h
Freedom/Source/Examine/mtes1.c
Freedom/Source/Examine/nsc2free.c
Freedom/Source/Examine/load_all.c
Freedom/Source/Examine/exam.c
Freedom/Source/Examine/eof_remo.c
Freedom/Source/Examine/split.c
Freedom/Source/Examine/common.h
Freedom/Source/Examine/tapescan.c
Freedom/Source/Examine/ets.c
Freedom/Source/Examine/gen_free.c
Freedom/Source/Examine/oned.c
Freedom/Source/Examine/freegen.c
Freedom/Source/Examine/store.c
Freedom/Source/Examine/eof_remo
Freedom/Source/Examine/exam.o
Freedom/Source/Examine/exam
Freedom/Source/Examine/eof_remo.o
Freedom/Source/Server.Offline/
Freedom/Source/Server.Offline/read.c
Freedom/Source/Server.Offline/Makefile
Freedom/Source/Server.Offline/dserv.h
Freedom/Source/Server.Offline/replay.c
Freedom/Source/Server.Offline/replay.h
Freedom/Source/Server.Offline/dlib.c
Freedom/Source/Server.Offline/shmem.c
Freedom/Source/Server.Offline/common.h
Freedom/Source/Server.Offline/conv.c
Freedom/Source/Server.LP/
Freedom/Source/Server.LP/common.h
Freedom/Source/Server.LP/dlib.c
Freedom/Source/Server.LP/dserv.c
Freedom/Source/Server.LP/dserv.h
Freedom/Source/Server.LP/file.h
Freedom/Source/Server.LP/lip.c
Freedom/Source/Server.LP/makefile
Freedom/Source/Server.LP/scaler.c
Freedom/Source/Server.LP/shmem.c
Freedom/Source/Server.LP/single.c
Freedom/Source/Server.LP/status.c
Freedom/Source/Server.LP/store.c
Freedom/Source/Drivers/
Freedom/Source/Drivers/hmcc2.0.c
Freedom/Source/Drivers/hmcc2.4.c
Freedom/Source/Drivers/Makefile
Freedom/Source/Drivers/kscc.c
Freedom/Source/Drivers/kscc.h
Freedom/Source/Drivers/go4
Freedom/Source/Drivers/hmcc.o
Freedom/Source/Drivers/x~
Freedom/Source/GatedEvent/
Freedom/Source/GatedEvent/common.h
Freedom/Source/GatedEvent/dserv.h
Freedom/Source/GatedEvent/Makefile
Freedom/Source/GatedEvent/gates
Freedom/Source/GatedEvent/gatedEvent.c
Freedom/Source/GatedEvent/gatedEvent.c.OLD
Freedom/Source/GatedEvent/gatedList.c
Freedom/Source/GatedEvent/gatedEvent
Freedom/Source/GatedEvent/gatedList
Freedom/Source/Server.LowCost/
Freedom/Source/Server.LowCost/Makefile
Freedom/Source/Server.LowCost/TEST/
Freedom/Source/Server.LowCost/TEST/tesds.c
Freedom/Source/Server.LowCost/TEST/hmtes.c
Freedom/Source/Server.LowCost/TEST/camio.c
Freedom/Source/Server.LowCost/TEST/evtes.c
Freedom/Source/Server.LowCost/TEST/common.h
Freedom/Source/Server.LowCost/TEST/exam.c
Freedom/Source/Server.LowCost/common.h
Freedom/Source/Server.LowCost/dlib.c
Freedom/Source/Server.LowCost/dserv.c
Freedom/Source/Server.LowCost/dserv.conf
Freedom/Source/Server.LowCost/dserv.h
Freedom/Source/Server.LowCost/go
Freedom/Source/Server.LowCost/go4
Freedom/Source/Server.LowCost/hmcc2.0.c
Freedom/Source/Server.LowCost/hmcc2.4.c
Freedom/Source/Server.LowCost/lip.c
Freedom/Source/Server.LowCost/scaler.c
Freedom/Source/Server.LowCost/shmem.c
Freedom/Source/Server.LowCost/single.c
Freedom/Source/Server.LowCost/status.c
Freedom/Source/Server.LowCost/store.c
Freedom/XFreedom
user@user-laptop:~$ cd Freedom
user@user-laptop:~/Freedom$ make
cd Source/Client ; make 
make[1]: Entering directory `/home/user/Freedom/Source/Client'
gcc -Wall -g   -c -o autofit.o autofit.c
In file included from freedom.h:3,
                 from autofit.c:1:
globals.h:4:19: error: stdio.h: No such file or directory
globals.h:5:21: error: sys/ipc.h: No such file or directory
globals.h:6:21: error: sys/shm.h: No such file or directory
globals.h:7:20: error: unistd.h: No such file or directory
In file included from freedom.h:4,
                 from autofit.c:1:
typedefs.h:4:27: error: X11/Intrinsic.h: No such file or directory
typedefs.h:5:28: error: X11/StringDefs.h: No such file or directory
In file included from freedom.h:4,
                 from autofit.c:1:
typedefs.h:20: error: expected specifier-qualifier-list before â&#8364;&#732;Widgetâ&#8364;&#8482;
typedefs.h:27: error: expected specifier-qualifier-list before â&#8364;&#732;Widgetâ&#8364;&#8482;
typedefs.h:60: error: expected specifier-qualifier-list before â&#8364;&#732;Booleanâ&#8364;&#8482;
typedefs.h:84: error: expected specifier-qualifier-list before â&#8364;&#732;Pixelâ&#8364;&#8482;
typedefs.h:116: error: expected specifier-qualifier-list before â&#8364;&#732;Dimensionâ&#8364;&#8482;
typedefs.h:130: error: expected specifier-qualifier-list before â&#8364;&#732;XtAppContextâ&#8364;&#8482;
typedefs.h:156: error: expected specifier-qualifier-list before â&#8364;&#732;Widgetâ&#8364;&#8482;
typedefs.h:172: error: expected specifier-qualifier-list before â&#8364;&#732;FILEâ&#8364;&#8482;
In file included from autofit.c:1:
freedom.h:6:18: error: time.h: No such file or directory
In file included from autofit.c:1:
freedom.h:15: error: expected specifier-qualifier-list before â&#8364;&#732;Stringâ&#8364;&#8482;
In file included from freedom.h:267,
                 from autofit.c:1:
routines.h:8: warning: parameter names (without types) in function declaration
routines.h:9: warning: parameter names (without types) in function declaration
routines.h:14: warning: parameter names (without types) in function declaration
routines.h:18: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;intâ&#8364;&#8482;
routines.h:39: warning: parameter names (without types) in function declaration
routines.h:40: warning: parameter names (without types) in function declaration
routines.h:41: warning: parameter names (without types) in function declaration
routines.h:47: warning: parameter names (without types) in function declaration
routines.h:48: warning: parameter names (without types) in function declaration
routines.h:49: warning: parameter names (without types) in function declaration
routines.h:50: warning: parameter names (without types) in function declaration
routines.h:60: warning: parameter names (without types) in function declaration
routines.h:66: warning: parameter names (without types) in function declaration
routines.h:67: warning: parameter names (without types) in function declaration
routines.h:68: warning: parameter names (without types) in function declaration
routines.h:79: warning: parameter names (without types) in function declaration
routines.h:83: warning: parameter names (without types) in function declaration
routines.h:84: warning: parameter names (without types) in function declaration
routines.h:85: warning: parameter names (without types) in function declaration
routines.h:86: warning: parameter names (without types) in function declaration
routines.h:87: warning: parameter names (without types) in function declaration
routines.h:88: warning: parameter names (without types) in function declaration
routines.h:89: warning: parameter names (without types) in function declaration
routines.h:90: warning: parameter names (without types) in function declaration
routines.h:93: warning: parameter names (without types) in function declaration
routines.h:94: warning: parameter names (without types) in function declaration
routines.h:104: warning: parameter names (without types) in function declaration
routines.h:105: warning: parameter names (without types) in function declaration
routines.h:106: warning: parameter names (without types) in function declaration
routines.h:107: warning: parameter names (without types) in function declaration
routines.h:110: warning: parameter names (without types) in function declaration
routines.h:113: warning: parameter names (without types) in function declaration
routines.h:114: warning: parameter names (without types) in function declaration
routines.h:115: warning: parameter names (without types) in function declaration
routines.h:116: warning: parameter names (without types) in function declaration
routines.h:117: warning: parameter names (without types) in function declaration
routines.h:126: warning: parameter names (without types) in function declaration
routines.h:127: warning: parameter names (without types) in function declaration
routines.h:128: warning: parameter names (without types) in function declaration
routines.h:129: warning: parameter names (without types) in function declaration
routines.h:130: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;Widgetâ&#8364;&#8482;
routines.h:131: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;Widgetâ&#8364;&#8482;
routines.h:132: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;Widgetâ&#8364;&#8482;
routines.h:136: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;XtPointerâ&#8364;&#8482;
routines.h:145: warning: parameter names (without types) in function declaration
routines.h:146: warning: parameter names (without types) in function declaration
routines.h:147: warning: parameter names (without types) in function declaration
routines.h:148: warning: parameter names (without types) in function declaration
routines.h:149: warning: parameter names (without types) in function declaration
routines.h:150: warning: parameter names (without types) in function declaration
routines.h:151: warning: parameter names (without types) in function declaration
routines.h:152: warning: parameter names (without types) in function declaration
routines.h:153: warning: parameter names (without types) in function declaration
routines.h:154: warning: parameter names (without types) in function declaration
routines.h:155: warning: parameter names (without types) in function declaration
routines.h:160: warning: parameter names (without types) in function declaration
routines.h:167: warning: parameter names (without types) in function declaration
routines.h:172: warning: parameter names (without types) in function declaration
routines.h:173: warning: parameter names (without types) in function declaration
routines.h:175: warning: parameter names (without types) in function declaration
routines.h:176: warning: parameter names (without types) in function declaration
routines.h:177: warning: parameter names (without types) in function declaration
routines.h:178: warning: parameter names (without types) in function declaration
routines.h:179: warning: parameter names (without types) in function declaration
routines.h:180: warning: parameter names (without types) in function declaration
routines.h:184: warning: parameter names (without types) in function declaration
routines.h:191: warning: parameter names (without types) in function declaration
routines.h:192: warning: parameter names (without types) in function declaration
routines.h:193: warning: parameter names (without types) in function declaration
routines.h:194: warning: parameter names (without types) in function declaration
routines.h:195: warning: parameter names (without types) in function declaration
routines.h:196: warning: parameter names (without types) in function declaration
routines.h:197: warning: parameter names (without types) in function declaration
routines.h:198: warning: parameter names (without types) in function declaration
routines.h:206: warning: parameter names (without types) in function declaration
routines.h:207: warning: parameter names (without types) in function declaration
routines.h:210: warning: parameter names (without types) in function declaration
routines.h:216: warning: parameter names (without types) in function declaration
routines.h:217: warning: parameter names (without types) in function declaration
routines.h:224: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;intâ&#8364;&#8482;
routines.h:225: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;intâ&#8364;&#8482;
routines.h:231: warning: parameter names (without types) in function declaration
routines.h:232: warning: parameter names (without types) in function declaration
routines.h:233: warning: parameter names (without types) in function declaration
routines.h:247: warning: parameter names (without types) in function declaration
routines.h:248: error: expected â&#8364;&#732;=â&#8364;&#8482;, â&#8364;&#732;,â&#8364;&#8482;, â&#8364;&#732;;â&#8364;&#8482;, â&#8364;&#732;asmâ&#8364;&#8482; or â&#8364;&#732;__attribute__â&#8364;&#8482; before â&#8364;&#732;my_popâ&#8364;&#8482;
routines.h:251: warning: parameter names (without types) in function declaration
routines.h:256: warning: parameter names (without types) in function declaration
routines.h:276: warning: parameter names (without types) in function declaration
routines.h:277: warning: parameter names (without types) in function declaration
routines.h:296: warning: parameter names (without types) in function declaration
routines.h:300: warning: parameter names (without types) in function declaration
routines.h:301: warning: parameter names (without types) in function declaration
routines.h:302: warning: parameter names (without types) in function declaration
routines.h:303: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;Widgetâ&#8364;&#8482;
routines.h:304: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;Widgetâ&#8364;&#8482;
routines.h:305: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;Widgetâ&#8364;&#8482;
routines.h:308: warning: parameter names (without types) in function declaration
routines.h:309: warning: parameter names (without types) in function declaration
routines.h:310: warning: parameter names (without types) in function declaration
routines.h:311: warning: parameter names (without types) in function declaration
routines.h:312: warning: parameter names (without types) in function declaration
routines.h:318: warning: parameter names (without types) in function declaration
routines.h:319: warning: parameter names (without types) in function declaration
routines.h:320: warning: parameter names (without types) in function declaration
routines.h:321: warning: parameter names (without types) in function declaration
routines.h:322: warning: parameter names (without types) in function declaration
routines.h:323: warning: parameter names (without types) in function declaration
routines.h:324: warning: parameter names (without types) in function declaration
routines.h:325: warning: parameter names (without types) in function declaration
routines.h:329: warning: parameter names (without types) in function declaration
routines.h:330: warning: parameter names (without types) in function declaration
routines.h:331: warning: parameter names (without types) in function declaration
routines.h:332: warning: parameter names (without types) in function declaration
routines.h:350: warning: parameter names (without types) in function declaration
routines.h:351: warning: parameter names (without types) in function declaration
routines.h:355: warning: parameter names (without types) in function declaration
routines.h:356: warning: parameter names (without types) in function declaration
routines.h:357: warning: parameter names (without types) in function declaration
routines.h:358: warning: parameter names (without types) in function declaration
routines.h:359: warning: parameter names (without types) in function declaration
routines.h:360: warning: parameter names (without types) in function declaration
routines.h:366: warning: parameter names (without types) in function declaration
routines.h:367: warning: parameter names (without types) in function declaration
routines.h:371: warning: parameter names (without types) in function declaration
routines.h:373: warning: parameter names (without types) in function declaration
routines.h:374: warning: parameter names (without types) in function declaration
routines.h:375: warning: parameter names (without types) in function declaration
routines.h:376: warning: parameter names (without types) in function declaration
routines.h:377: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;Booleanâ&#8364;&#8482;
routines.h:378: warning: parameter names (without types) in function declaration
routines.h:379: warning: parameter names (without types) in function declaration
routines.h:380: warning: parameter names (without types) in function declaration
routines.h:381: warning: parameter names (without types) in function declaration
routines.h:382: warning: parameter names (without types) in function declaration
routines.h:383: warning: parameter names (without types) in function declaration
routines.h:384: warning: parameter names (without types) in function declaration
routines.h:385: warning: parameter names (without types) in function declaration
routines.h:386: warning: parameter names (without types) in function declaration
routines.h:387: warning: parameter names (without types) in function declaration
routines.h:388: warning: parameter names (without types) in function declaration
routines.h:389: warning: parameter names (without types) in function declaration
routines.h:390: warning: parameter names (without types) in function declaration
routines.h:400: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;intâ&#8364;&#8482;
routines.h:401: warning: parameter names (without types) in function declaration
routines.h:405: warning: parameter names (without types) in function declaration
routines.h:406: warning: parameter names (without types) in function declaration
routines.h:419: warning: parameter names (without types) in function declaration
routines.h:420: warning: parameter names (without types) in function declaration
routines.h:421: warning: parameter names (without types) in function declaration
routines.h:422: warning: parameter names (without types) in function declaration
routines.h:423: warning: parameter names (without types) in function declaration
routines.h:428: warning: parameter names (without types) in function declaration
routines.h:429: warning: parameter names (without types) in function declaration
routines.h:437: warning: parameter names (without types) in function declaration
routines.h:438: warning: parameter names (without types) in function declaration
routines.h:439: warning: parameter names (without types) in function declaration
routines.h:441: warning: parameter names (without types) in function declaration
routines.h:449: warning: parameter names (without types) in function declaration
routines.h:450: warning: parameter names (without types) in function declaration
routines.h:455: warning: parameter names (without types) in function declaration
routines.h:456: warning: parameter names (without types) in function declaration
routines.h:457: warning: parameter names (without types) in function declaration
routines.h:476: warning: parameter names (without types) in function declaration
autofit.c:4:18: error: math.h: No such file or directory
autofit.c:5:20: error: malloc.h: No such file or directory
autofit.c:6:20: error: stdlib.h: No such file or directory
autofit.c: In function â&#8364;&#732;find_peaksâ&#8364;&#8482;:
autofit.c:113: warning: implicit declaration of function â&#8364;&#732;memsetâ&#8364;&#8482;
autofit.c:113: warning: incompatible implicit declaration of built-in function â&#8364;&#732;memsetâ&#8364;&#8482;
autofit.c: In function â&#8364;&#732;auto_fitâ&#8364;&#8482;:
autofit.c:126: error: expected declaration specifiers before â&#8364;&#732;Widgetâ&#8364;&#8482;
autofit.c:127: error: expected declaration specifiers before â&#8364;&#732;XtPointerâ&#8364;&#8482;
autofit.c:128: error: expected declaration specifiers before â&#8364;&#732;XtPointerâ&#8364;&#8482;
autofit.c:143: error: â&#8364;&#732;FILEâ&#8364;&#8482; undeclared (first use in this function)
autofit.c:143: error: (Each undeclared identifier is reported only once
autofit.c:143: error: for each function it appears in.)
autofit.c:143: error: â&#8364;&#732;fpâ&#8364;&#8482; undeclared (first use in this function)
autofit.c:147: warning: implicit declaration of function â&#8364;&#732;memcpyâ&#8364;&#8482;
autofit.c:147: warning: incompatible implicit declaration of built-in function â&#8364;&#732;memcpyâ&#8364;&#8482;
autofit.c:147: error: â&#8364;&#732;DISPâ&#8364;&#8482; has no member named â&#8364;&#732;markâ&#8364;&#8482;
autofit.c:149: error: â&#8364;&#732;DISPâ&#8364;&#8482; has no member named â&#8364;&#732;ViewPortâ&#8364;&#8482;
autofit.c:149: error: too many arguments to function â&#8364;&#732;use_max_errorâ&#8364;&#8482;
autofit.c:152: error: â&#8364;&#732;DISPâ&#8364;&#8482; has no member named â&#8364;&#732;markâ&#8364;&#8482;
autofit.c:153: error: â&#8364;&#732;DISPâ&#8364;&#8482; has no member named â&#8364;&#732;ViewPortâ&#8364;&#8482;
autofit.c:153: error: too many arguments to function â&#8364;&#732;use_max_errorâ&#8364;&#8482;
autofit.c:157: error: â&#8364;&#732;Trueâ&#8364;&#8482; undeclared (first use in this function)
autofit.c:158: error: â&#8364;&#732;Falseâ&#8364;&#8482; undeclared (first use in this function)
autofit.c:159: error: â&#8364;&#732;NULLâ&#8364;&#8482; undeclared (first use in this function)
autofit.c:159: error: too many arguments to function â&#8364;&#732;supply_dataâ&#8364;&#8482;
autofit.c:162: warning: implicit declaration of function â&#8364;&#732;XFlushâ&#8364;&#8482;
autofit.c:162: error: â&#8364;&#732;DISPâ&#8364;&#8482; has no member named â&#8364;&#732;dispâ&#8364;&#8482;
autofit.c:172: warning: implicit declaration of function â&#8364;&#732;sqrtâ&#8364;&#8482;
autofit.c:172: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sqrtâ&#8364;&#8482;
autofit.c:184: warning: implicit declaration of function â&#8364;&#732;chdirâ&#8364;&#8482;
autofit.c:185: warning: implicit declaration of function â&#8364;&#732;getcwdâ&#8364;&#8482;
autofit.c:186: warning: implicit declaration of function â&#8364;&#732;strcatâ&#8364;&#8482;
autofit.c:186: warning: incompatible implicit declaration of built-in function â&#8364;&#732;strcatâ&#8364;&#8482;
autofit.c:187: warning: implicit declaration of function â&#8364;&#732;fopenâ&#8364;&#8482;
autofit.c:187: error: expected expression before â&#8364;&#732;)â&#8364;&#8482; token
autofit.c:188: error: â&#8364;&#732;DISPâ&#8364;&#8482; has no member named â&#8364;&#732;ViewPortâ&#8364;&#8482;
autofit.c:188: error: too many arguments to function â&#8364;&#732;use_max_errorâ&#8364;&#8482;
autofit.c:189: error: â&#8364;&#732;DISPâ&#8364;&#8482; has no member named â&#8364;&#732;markâ&#8364;&#8482;
autofit.c:195: warning: incompatible implicit declaration of built-in function â&#8364;&#732;memsetâ&#8364;&#8482;
autofit.c:197: warning: implicit declaration of function â&#8364;&#732;fprintfâ&#8364;&#8482;
autofit.c:197: warning: incompatible implicit declaration of built-in function â&#8364;&#732;fprintfâ&#8364;&#8482;
autofit.c:213: error: â&#8364;&#732;DISPâ&#8364;&#8482; has no member named â&#8364;&#732;markâ&#8364;&#8482;
autofit.c:215: error: â&#8364;&#732;DISPâ&#8364;&#8482; has no member named â&#8364;&#732;markâ&#8364;&#8482;
autofit.c:215: error: â&#8364;&#732;DISPâ&#8364;&#8482; has no member named â&#8364;&#732;markâ&#8364;&#8482;
autofit.c:216: error: â&#8364;&#732;DISPâ&#8364;&#8482; has no member named â&#8364;&#732;markâ&#8364;&#8482;
autofit.c:216: error: â&#8364;&#732;DISPâ&#8364;&#8482; has no member named â&#8364;&#732;markâ&#8364;&#8482;
autofit.c:226: error: â&#8364;&#732;DISPâ&#8364;&#8482; has no member named â&#8364;&#732;markâ&#8364;&#8482;
autofit.c:226: error: â&#8364;&#732;DISPâ&#8364;&#8482; has no member named â&#8364;&#732;markâ&#8364;&#8482;
autofit.c:230: error: â&#8364;&#732;DISPâ&#8364;&#8482; has no member named â&#8364;&#732;markâ&#8364;&#8482;
autofit.c:230: error: â&#8364;&#732;DISPâ&#8364;&#8482; has no member named â&#8364;&#732;markâ&#8364;&#8482;
autofit.c:233: error: too many arguments to function â&#8364;&#732;supply_dataâ&#8364;&#8482;
autofit.c:255: warning: implicit declaration of function â&#8364;&#732;sprintfâ&#8364;&#8482;
autofit.c:255: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
autofit.c:256: warning: implicit declaration of function â&#8364;&#732;XtVaSetValuesâ&#8364;&#8482;
autofit.c:256: error: â&#8364;&#732;DISPâ&#8364;&#8482; has no member named â&#8364;&#732;FormLabelâ&#8364;&#8482;
autofit.c:256: error: â&#8364;&#732;XtNlabelâ&#8364;&#8482; undeclared (first use in this function)
autofit.c:257: warning: implicit declaration of function â&#8364;&#732;XSyncâ&#8364;&#8482;
autofit.c:257: error: â&#8364;&#732;DISPâ&#8364;&#8482; has no member named â&#8364;&#732;dispâ&#8364;&#8482;
autofit.c:261: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
autofit.c:262: error: â&#8364;&#732;DISPâ&#8364;&#8482; has no member named â&#8364;&#732;FormLabelâ&#8364;&#8482;
autofit.c:263: error: â&#8364;&#732;DISPâ&#8364;&#8482; has no member named â&#8364;&#732;dispâ&#8364;&#8482;
autofit.c:264: error: â&#8364;&#732;DISPâ&#8364;&#8482; has no member named â&#8364;&#732;dispâ&#8364;&#8482;
autofit.c:270: error: â&#8364;&#732;DISPâ&#8364;&#8482; has no member named â&#8364;&#732;ViewPortâ&#8364;&#8482;
autofit.c:270: error: too many arguments to function â&#8364;&#732;use_max_errorâ&#8364;&#8482;
autofit.c:294: warning: implicit declaration of function â&#8364;&#732;fcloseâ&#8364;&#8482;
autofit.c:296: warning: incompatible implicit declaration of built-in function â&#8364;&#732;sprintfâ&#8364;&#8482;
autofit.c:298: error: â&#8364;&#732;DISPâ&#8364;&#8482; has no member named â&#8364;&#732;ViewPortâ&#8364;&#8482;
autofit.c:298: error: too many arguments to function â&#8364;&#732;use_max_errorâ&#8364;&#8482;
autofit.c:300: error: â&#8364;&#732;DISPâ&#8364;&#8482; has no member named â&#8364;&#732;markâ&#8364;&#8482;
make[1]: *** [autofit.o] Error 1
make[1]: Leaving directory `/home/user/Freedom/Source/Client'
make: *** [all] Error 2
user:(@user-laptop:~/Freedom$

---

### Post by heimo on 2007-05-19
Sorry, no answer - but just a polite request to put that long output inside code tags (# sign in message editor), so that page isn't so long. Example below - see how it puts scrollable window around the output:


```

Freedom/Files/CFG/ERD/CMPND/ERDAT.DAT
Freedom/Files/CFG/ERD/CMPND/erdat.c
Freedom/Files/CFG/ERD/CMPND/COMPOUNDS.DAT
Freedom/Files/CFG/ERD/CMPND/IMPURITIES.DAT
Freedom/Files/CFG/GON/
Freedom/Files/CFG/GON/chnag.gon
Freedom/Files/CFG/GTE/
Freedom/Files/CFG/LIN/
Freedom/Files/SPC/
Freedom/Files/SPC/ONED/
Freedom/Files/SPC/ONED/oned.ONE
Freedom/Files/SPC/ALL/
Freedom/Files/SPC/TWOD/
Freedom/Files/FIT/
Freedom/Files/MAT/
Freedom/Files/DAT/
Freedom/hira.dat
Freedom/Makefile
Freedom/Source/
Freedom/Source/Client/
Freedom/Source/Client/autofit.c
Freedom/Source/Client/sca_init.c
Freedom/Source/Client/sca_init.h
Freedom/Source/Client/calc.y
Freedom/Source/Client/calc.h
Freedom/Source/Client/calc.c
Freedom/Source/Client/update.c
Freedom/Source/Client/typedefs.h
Freedom/Source/Client/widgets.h
Freedom/Source/Client/widgets.c
Freedom/Source/Client/freedom.h
Freedom/Source/Client/freedom.c
Freedom/Source/Client/shared.c
Freedom/Source/Client/erda.h
Freedom/Source/Client/erda.c
Freedom/Source/Client/project.c
Freedom/Source/Client/project.h
Freedom/Source/Client/process.c
Freedom/Source/Client/tdccal.c
Freedom/Source/Client/matproc.c
Freedom/Source/Client/filebox.h
Freedom/Source/Client/filebox.c
Freedom/Source/Client/erdat.c
Freedom/Source/Client/gated.c
Freedom/Source/Client/list_cfg.h
Freedom/Source/Client/list_cfg.c
Freedom/Source/Client/disp_cfg.h
Freedom/Source/Client/disp_cfg.c
```

---

### Post by mrsurf on 2007-05-23
Hey,

I am also having similar kind of problem. Is it something relqated to do with X11 or X org. I have installed from repo. But still it gives error. As I was using this in FC6 & it worked fine. Since I have moved to Ubantu how it will work in this one

---

### Post by DoktorSeven on 2007-05-23
Given it doesn't know about stdio.h and unistd.h, you might not have the basic development stuff installed:

**sudo apt-get install build-essential**

As for the X11 errors:the package libxt-dev seems to have it.

If it shows it can't find a header (.h) file, find it with apt-file (**sudo apt-get install apt-file**, then **sudo apt-file update**, then **apt-file search *filename*** -- **apt-file search StringDefs.h** as an example).

---

