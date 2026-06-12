---
title: "Program removed, but still there"
date: 2020-06-24
forum: General Help
---

### Post by eddugo on 2020-06-24
Hello again;

I resurrected an old Dell inspiron 15 with Ubuntu Mate 20.04.  I loaded a program (flrig) and forgot to first load the dependencies.  Of course the program doesn't work properly so I tried to uninstall using terminal.  Terminal says it is not found as does synaptic.  I removed the file from hidden files in Home too.  When I go to terminal and type "flrig", the program starts - even though teminal say it's not there.  I tried to find it with "find “/” flrig" - no results.  I manually checked /bin/, /usr/bin/ - can't find it.  Where is it and how do i remove it?  Thank you in advance for your help.

ed@ed-Inspiron:~$ find “/” flrig
find: ‘“/”’: No such file or directory
find: ‘flrig’: No such file or directory

---

### Post by dragonfly41 on 2020-06-24
I have a Dell. Just curious I ran ```
sudo locate flrig
``` and found two hits (but neither executable).

[FONT=monospace][COLOR=#000000]~/_CUBIC/desktop/squashfs-root/var/lib/app-info/icons/ubuntu-bionic-universe/64x64/flrig_flrig.png[/COLOR]
/var/lib/app-info/icons/ubuntu-bionic-universe/64x64/flrig_flrig.png

[/FONT]

---

### Post by Impavidus on 2020-06-24
How did you install flrig? If you installed from the repositories (official or PPA), dependencies are installed automatically. When you remove a package, the files it stored in your home directory are not removed. You have to do so manually. Further, some config files don't get removed, unless you purge the package instead of normal removal.

In your find command you mixed up straight quote characters ( " ' ) with curly quote characters ( “ ” ‘ ’ ). The curly quote characters have no special meaning to the shell or to find, so it looks for a directory that has those in its name.

**find** is a versatile command. Read the man page.

---

### Post by eddugo on 2020-06-24
dragonfly 41

This is what I get with locate.  Other then what is in Downloads - can those files just be deleted or do they have to be uninstalled?

```
/home/ed/Downloads/flrig-1.3.50/src/graphics/.deps/flrig-images.Po
/home/ed/Downloads/flrig-1.3.50/src/graphics/.deps/flrig-pixmaps.Po
/home/ed/Downloads/flrig-1.3.50/src/images/P100.xbm
/home/ed/Downloads/flrig-1.3.50/src/images/P200.xbm
/home/ed/Downloads/flrig-1.3.50/src/images/P200log.xbm
/home/ed/Downloads/flrig-1.3.50/src/images/P25.xbm
/home/ed/Downloads/flrig-1.3.50/src/images/P5.xbm
/home/ed/Downloads/flrig-1.3.50/src/images/P50.xbm
/home/ed/Downloads/flrig-1.3.50/src/images/S60.xbm
/home/ed/Downloads/flrig-1.3.50/src/images/SWR.xbm
/home/ed/Downloads/flrig-1.3.50/src/images/alc.xbm
/home/ed/Downloads/flrig-1.3.50/src/include/AOR5K.h
/home/ed/Downloads/flrig-1.3.50/src/include/DELTA-II.h
/home/ed/Downloads/flrig-1.3.50/src/include/FT1000.h
/home/ed/Downloads/flrig-1.3.50/src/include/FT1000MP.h
/home/ed/Downloads/flrig-1.3.50/src/include/FT100D.h
/home/ed/Downloads/flrig-1.3.50/src/include/FT2000.h
/home/ed/Downloads/flrig-1.3.50/src/include/FT450.h
/home/ed/Downloads/flrig-1.3.50/src/include/FT450D.h
/home/ed/Downloads/flrig-1.3.50/src/include/FT5000.h
/home/ed/Downloads/flrig-1.3.50/src/include/FT747.h
/home/ed/Downloads/flrig-1.3.50/src/include/FT767.h
/home/ed/Downloads/flrig-1.3.50/src/include/FT817.h
/home/ed/Downloads/flrig-1.3.50/src/include/FT847.h
/home/ed/Downloads/flrig-1.3.50/src/include/FT857D.h
/home/ed/Downloads/flrig-1.3.50/src/include/FT890.h
/home/ed/Downloads/flrig-1.3.50/src/include/FT891.h
/home/ed/Downloads/flrig-1.3.50/src/include/FT900.h
/home/ed/Downloads/flrig-1.3.50/src/include/FT920.h
/home/ed/Downloads/flrig-1.3.50/src/include/FT950.h
/home/ed/Downloads/flrig-1.3.50/src/include/FT990.h
/home/ed/Downloads/flrig-1.3.50/src/include/FT990a.h
/home/ed/Downloads/flrig-1.3.50/src/include/FT991.h
/home/ed/Downloads/flrig-1.3.50/src/include/FT991A.h
/home/ed/Downloads/flrig-1.3.50/src/include/FTdx101D.h
/home/ed/Downloads/flrig-1.3.50/src/include/FTdx1200.h
/home/ed/Downloads/flrig-1.3.50/src/include/FTdx3000.h
/home/ed/Downloads/flrig-1.3.50/src/include/FTdx9000.h
/home/ed/Downloads/flrig-1.3.50/src/include/Fl_SigBar.h
/home/ed/Downloads/flrig-1.3.50/src/include/FreqControl.h
/home/ed/Downloads/flrig-1.3.50/src/include/IC7000.h
/home/ed/Downloads/flrig-1.3.50/src/include/IC703.h
/home/ed/Downloads/flrig-1.3.50/src/include/IC706MKIIG.h
/home/ed/Downloads/flrig-1.3.50/src/include/IC7100.h
/home/ed/Downloads/flrig-1.3.50/src/include/IC718.h
/home/ed/Downloads/flrig-1.3.50/src/include/IC7200.h
/home/ed/Downloads/flrig-1.3.50/src/include/IC728.h
/home/ed/Downloads/flrig-1.3.50/src/include/IC7300.h
/home/ed/Downloads/flrig-1.3.50/src/include/IC735.h
/home/ed/Downloads/flrig-1.3.50/src/include/IC7410.h
/home/ed/Downloads/flrig-1.3.50/src/include/IC746.h
/home/ed/Downloads/flrig-1.3.50/src/include/IC756.h
/home/ed/Downloads/flrig-1.3.50/src/include/IC756PRO2.h
/home/ed/Downloads/flrig-1.3.50/src/include/IC756PRO3.h
/home/ed/Downloads/flrig-1.3.50/src/include/IC7600.h
/home/ed/Downloads/flrig-1.3.50/src/include/IC7610.h
/home/ed/Downloads/flrig-1.3.50/src/include/IC7700.h
/home/ed/Downloads/flrig-1.3.50/src/include/IC7800.h
/home/ed/Downloads/flrig-1.3.50/src/include/IC7851.h
/home/ed/Downloads/flrig-1.3.50/src/include/IC910.h
/home/ed/Downloads/flrig-1.3.50/src/include/IC9100.h
/home/ed/Downloads/flrig-1.3.50/src/include/IC9700.h
/home/ed/Downloads/flrig-1.3.50/src/include/ICF8101.h
/home/ed/Downloads/flrig-1.3.50/src/include/ICbase.h
/home/ed/Downloads/flrig-1.3.50/src/include/K2.h
/home/ed/Downloads/flrig-1.3.50/src/include/K3.h
/home/ed/Downloads/flrig-1.3.50/src/include/K3_ui.h
/home/ed/Downloads/flrig-1.3.50/src/include/KENWOOD.h
/home/ed/Downloads/flrig-1.3.50/src/include/KX3.h
/home/ed/Downloads/flrig-1.3.50/src/include/KX3_ui.h
/home/ed/Downloads/flrig-1.3.50/src/include/PCR1000.h
/home/ed/Downloads/flrig-1.3.50/src/include/RAY152.h
/home/ed/Downloads/flrig-1.3.50/src/include/TS140.h
/home/ed/Downloads/flrig-1.3.50/src/include/TS2000.h
/home/ed/Downloads/flrig-1.3.50/src/include/TS450S.h
/home/ed/Downloads/flrig-1.3.50/src/include/TS480HX.h
/home/ed/Downloads/flrig-1.3.50/src/include/TS480SAT.h
/home/ed/Downloads/flrig-1.3.50/src/include/TS570.h
/home/ed/Downloads/flrig-1.3.50/src/include/TS590S.h
/home/ed/Downloads/flrig-1.3.50/src/include/TS590SG.h
/home/ed/Downloads/flrig-1.3.50/src/include/TS790.h
/home/ed/Downloads/flrig-1.3.50/src/include/TS850.h
/home/ed/Downloads/flrig-1.3.50/src/include/TS870S.h
/home/ed/Downloads/flrig-1.3.50/src/include/TS890S.h
/home/ed/Downloads/flrig-1.3.50/src/include/TS940S.h
/home/ed/Downloads/flrig-1.3.50/src/include/TS950.h
/home/ed/Downloads/flrig-1.3.50/src/include/TS990.h
/home/ed/Downloads/flrig-1.3.50/src/include/TT516.h
/home/ed/Downloads/flrig-1.3.50/src/include/TT538.h
/home/ed/Downloads/flrig-1.3.50/src/include/TT550.h
/home/ed/Downloads/flrig-1.3.50/src/include/TT563.h
/home/ed/Downloads/flrig-1.3.50/src/include/TT566.h
/home/ed/Downloads/flrig-1.3.50/src/include/TT588.h
/home/ed/Downloads/flrig-1.3.50/src/include/TT599.h
/home/ed/Downloads/flrig-1.3.50/src/include/ValueSlider.h
/home/ed/Downloads/flrig-1.3.50/src/include/combo.h
/home/ed/Downloads/flrig-1.3.50/src/include/compat-mingw.h
/home/ed/Downloads/flrig-1.3.50/src/include/compat.h
/home/ed/Downloads/flrig-1.3.50/src/include/debug.h
/home/ed/Downloads/flrig-1.3.50/src/include/dialogs.h
/home/ed/Downloads/flrig-1.3.50/src/include/fileselect.h
/home/ed/Downloads/flrig-1.3.50/src/include/flinput2.h
/home/ed/Downloads/flrig-1.3.50/src/include/flrigrc.h
/home/ed/Downloads/flrig-1.3.50/src/include/flslider2.h
/home/ed/Downloads/flrig-1.3.50/src/include/font_browser.h
/home/ed/Downloads/flrig-1.3.50/src/include/generic.h
/home/ed/Downloads/flrig-1.3.50/src/include/gettext.h
/home/ed/Downloads/flrig-1.3.50/src/include/hspinner.h
/home/ed/Downloads/flrig-1.3.50/src/include/icons.h
/home/ed/Downloads/flrig-1.3.50/src/include/images.h
/home/ed/Downloads/flrig-1.3.50/src/include/mingw.h
/home/ed/Downloads/flrig-1.3.50/src/include/pixmaps.h
/home/ed/Downloads/flrig-1.3.50/src/include/pl_tones.h
/home/ed/Downloads/flrig-1.3.50/src/include/ptt.h
/home/ed/Downloads/flrig-1.3.50/src/include/rig.h
/home/ed/Downloads/flrig-1.3.50/src/include/rig_io.h
/home/ed/Downloads/flrig-1.3.50/src/include/rigbase.h
/home/ed/Downloads/flrig-1.3.50/src/include/rigpanel.h
/home/ed/Downloads/flrig-1.3.50/src/include/rigs.h
/home/ed/Downloads/flrig-1.3.50/src/include/serial.h
/home/ed/Downloads/flrig-1.3.50/src/include/socket.h
/home/ed/Downloads/flrig-1.3.50/src/include/socket_io.h
/home/ed/Downloads/flrig-1.3.50/src/include/status.h
/home/ed/Downloads/flrig-1.3.50/src/include/support.h
/home/ed/Downloads/flrig-1.3.50/src/include/threads.h
/home/ed/Downloads/flrig-1.3.50/src/include/timeops.h
/home/ed/Downloads/flrig-1.3.50/src/include/tod_clock.h
/home/ed/Downloads/flrig-1.3.50/src/include/trace.h
/home/ed/Downloads/flrig-1.3.50/src/include/ui.h
/home/ed/Downloads/flrig-1.3.50/src/include/util.h
/home/ed/Downloads/flrig-1.3.50/src/include/xml_server.h
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps
/home/ed/Downloads/flrig-1.3.50/src/rigs/.dirstamp
/home/ed/Downloads/flrig-1.3.50/src/rigs/AOR5K.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/DELTA-II.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FT1000.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FT1000MP.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FT100D.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FT2000.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FT450.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FT450D.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FT5000.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FT747.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FT767.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FT817.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FT847.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FT857D.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FT890.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FT891.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FT900.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FT920.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FT950.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FT990.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FT990a.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FT991.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FT991A.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FTdx101D.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FTdx1200.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FTdx3000.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/FTdx9000.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/IC7000.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/IC703.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/IC706MKIIG.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/IC7100.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/IC718.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/IC7200.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/IC728.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/IC7300.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/IC735.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/IC7410.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/IC746.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/IC756.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/IC756PRO2.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/IC756PRO3.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/IC7600.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/IC7610.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/IC7700.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/IC7800.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/IC7851.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/IC910.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/IC9100.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/IC9700.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/ICF8101.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/ICbase.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/K2.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/K3.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/KENWOOD.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/KX3.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/PCR1000.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/RAY152.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/TS140.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/TS2000.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/TS450S.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/TS480HX.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/TS480SAT.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/TS570.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/TS590S.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/TS590SG.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/TS790.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/TS850.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/TS870S.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/TS890S.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/TS940S.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/TS950.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/TS990.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/TT516.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/TT538.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/TT550.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/TT563.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/TT566.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/TT588.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/TT599.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-AOR5K.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-DELTA-II.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FT1000.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FT1000MP.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FT100D.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FT2000.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FT450.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FT450D.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FT5000.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FT747.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FT767.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FT817.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FT847.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FT857D.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FT890.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FT891.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FT900.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FT920.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FT950.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FT990.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FT990a.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FT991.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FT991A.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FTdx101D.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FTdx1200.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FTdx3000.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-FTdx9000.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-IC7000.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-IC703.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-IC706MKIIG.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-IC7100.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-IC718.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-IC7200.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-IC728.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-IC7300.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-IC735.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-IC7410.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-IC746.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-IC756.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-IC756PRO2.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-IC756PRO3.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-IC7600.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-IC7610.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-IC7700.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-IC7800.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-IC7851.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-IC910.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-IC9100.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-IC9700.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-ICF8101.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-ICbase.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-K2.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-K3.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-KENWOOD.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-KX3.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-PCR1000.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-RAY152.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-TS140.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-TS2000.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-TS450S.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-TS480HX.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-TS480SAT.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-TS570.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-TS590S.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-TS590SG.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-TS790.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-TS850.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-TS870S.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-TS890S.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-TS940S.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-TS950.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-TS990.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-TT516.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-TT538.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-TT550.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-TT563.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-TT566.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-TT588.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-TT599.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-rigbase.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/flrig-rigs.o
/home/ed/Downloads/flrig-1.3.50/src/rigs/rigbase.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/rigs.cxx
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/.dirstamp
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-AOR5K.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-DELTA-II.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FT1000.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FT1000MP.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FT100D.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FT2000.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FT450.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FT450D.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FT5000.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FT747.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FT767.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FT817.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FT847.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FT857D.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FT890.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FT891.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FT900.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FT920.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FT950.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FT990.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FT990a.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FT991.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FT991A.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FTdx101D.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FTdx1200.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FTdx3000.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-FTdx9000.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-IC7000.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-IC703.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-IC706MKIIG.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-IC7100.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-IC718.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-IC7200.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-IC728.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-IC7300.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-IC735.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-IC7410.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-IC746.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-IC756.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-IC756PRO2.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-IC756PRO3.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-IC7600.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-IC7610.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-IC7700.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-IC7800.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-IC7851.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-IC910.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-IC9100.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-IC9700.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-ICF8101.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-ICbase.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-K2.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-K3.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-KENWOOD.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-KX3.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-PCR1000.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-RAY152.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-TS140.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-TS2000.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-TS450S.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-TS480HX.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-TS480SAT.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-TS570.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-TS590S.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-TS590SG.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-TS790.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-TS850.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-TS870S.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-TS890S.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-TS940S.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-TS950.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-TS990.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-TT516.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-TT538.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-TT550.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-TT563.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-TT566.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-TT588.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-TT599.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-rigbase.Po
/home/ed/Downloads/flrig-1.3.50/src/rigs/.deps/flrig-rigs.Po
/home/ed/Downloads/flrig-1.3.50/src/server/.deps
/home/ed/Downloads/flrig-1.3.50/src/server/.dirstamp
/home/ed/Downloads/flrig-1.3.50/src/server/flrig-xml_server.o
/home/ed/Downloads/flrig-1.3.50/src/server/xml_server.cxx
/home/ed/Downloads/flrig-1.3.50/src/server/.deps/.dirstamp
/home/ed/Downloads/flrig-1.3.50/src/server/.deps/flrig-xml_server.Po
/home/ed/Downloads/flrig-1.3.50/src/support/.deps
/home/ed/Downloads/flrig-1.3.50/src/support/.dirstamp
/home/ed/Downloads/flrig-1.3.50/src/support/debug.cxx
/home/ed/Downloads/flrig-1.3.50/src/support/dialogs.cxx
/home/ed/Downloads/flrig-1.3.50/src/support/flrig-debug.o
/home/ed/Downloads/flrig-1.3.50/src/support/flrig-dialogs.o
/home/ed/Downloads/flrig-1.3.50/src/support/flrig-ptt.o
/home/ed/Downloads/flrig-1.3.50/src/support/flrig-rig_io.o
/home/ed/Downloads/flrig-1.3.50/src/support/flrig-serial.o
/home/ed/Downloads/flrig-1.3.50/src/support/flrig-socket.o
/home/ed/Downloads/flrig-1.3.50/src/support/flrig-socket_io.o
/home/ed/Downloads/flrig-1.3.50/src/support/flrig-status.o
/home/ed/Downloads/flrig-1.3.50/src/support/flrig-support.o
/home/ed/Downloads/flrig-1.3.50/src/support/flrig-threads.o
/home/ed/Downloads/flrig-1.3.50/src/support/flrig-timeops.o
/home/ed/Downloads/flrig-1.3.50/src/support/flrig-tod_clock.o
/home/ed/Downloads/flrig-1.3.50/src/support/flrig-trace.o
/home/ed/Downloads/flrig-1.3.50/src/support/flrig-util.o
/home/ed/Downloads/flrig-1.3.50/src/support/mingw.c
/home/ed/Downloads/flrig-1.3.50/src/support/ptt.cxx
/home/ed/Downloads/flrig-1.3.50/src/support/rig_io.cxx
/home/ed/Downloads/flrig-1.3.50/src/support/serial.cxx
/home/ed/Downloads/flrig-1.3.50/src/support/socket.cxx
/home/ed/Downloads/flrig-1.3.50/src/support/socket_io.cxx
/home/ed/Downloads/flrig-1.3.50/src/support/status.cxx
/home/ed/Downloads/flrig-1.3.50/src/support/support.cxx
/home/ed/Downloads/flrig-1.3.50/src/support/threads.cxx
/home/ed/Downloads/flrig-1.3.50/src/support/timeops.cxx
/home/ed/Downloads/flrig-1.3.50/src/support/tod_clock.cxx
/home/ed/Downloads/flrig-1.3.50/src/support/trace.cxx
/home/ed/Downloads/flrig-1.3.50/src/support/util.cxx
/home/ed/Downloads/flrig-1.3.50/src/support/.deps/.dirstamp
/home/ed/Downloads/flrig-1.3.50/src/support/.deps/flrig-debug.Po
/home/ed/Downloads/flrig-1.3.50/src/support/.deps/flrig-dialogs.Po
/home/ed/Downloads/flrig-1.3.50/src/support/.deps/flrig-mingw.Po
/home/ed/Downloads/flrig-1.3.50/src/support/.deps/flrig-ptt.Po
/home/ed/Downloads/flrig-1.3.50/src/support/.deps/flrig-rig_io.Po
/home/ed/Downloads/flrig-1.3.50/src/support/.deps/flrig-serial.Po
/home/ed/Downloads/flrig-1.3.50/src/support/.deps/flrig-socket.Po
/home/ed/Downloads/flrig-1.3.50/src/support/.deps/flrig-socket_io.Po
/home/ed/Downloads/flrig-1.3.50/src/support/.deps/flrig-status.Po
/home/ed/Downloads/flrig-1.3.50/src/support/.deps/flrig-support.Po
/home/ed/Downloads/flrig-1.3.50/src/support/.deps/flrig-threads.Po
/home/ed/Downloads/flrig-1.3.50/src/support/.deps/flrig-timeops.Po
/home/ed/Downloads/flrig-1.3.50/src/support/.deps/flrig-tod_clock.Po
/home/ed/Downloads/flrig-1.3.50/src/support/.deps/flrig-trace.Po
/home/ed/Downloads/flrig-1.3.50/src/support/.deps/flrig-util.Po
/home/ed/Downloads/flrig-1.3.50/src/widgets/.deps
/home/ed/Downloads/flrig-1.3.50/src/widgets/.dirstamp
/home/ed/Downloads/flrig-1.3.50/src/widgets/Fl_SigBar.cxx
/home/ed/Downloads/flrig-1.3.50/src/widgets/FreqControl.cxx
/home/ed/Downloads/flrig-1.3.50/src/widgets/ValueSlider.cxx
/home/ed/Downloads/flrig-1.3.50/src/widgets/combo.cxx
/home/ed/Downloads/flrig-1.3.50/src/widgets/flinput2.cxx
/home/ed/Downloads/flrig-1.3.50/src/widgets/flrig-Fl_SigBar.o
/home/ed/Downloads/flrig-1.3.50/src/widgets/flrig-FreqControl.o
/home/ed/Downloads/flrig-1.3.50/src/widgets/flrig-ValueSlider.o
/home/ed/Downloads/flrig-1.3.50/src/widgets/flrig-combo.o
/home/ed/Downloads/flrig-1.3.50/src/widgets/flrig-flinput2.o
/home/ed/Downloads/flrig-1.3.50/src/widgets/flrig-flslider2.o
/home/ed/Downloads/flrig-1.3.50/src/widgets/flrig-font_browser.o
/home/ed/Downloads/flrig-1.3.50/src/widgets/flrig-hspinner.o
/home/ed/Downloads/flrig-1.3.50/src/widgets/flrig-pl_tones.o
/home/ed/Downloads/flrig-1.3.50/src/widgets/flslider2.cxx
/home/ed/Downloads/flrig-1.3.50/src/widgets/font_browser.cxx
/home/ed/Downloads/flrig-1.3.50/src/widgets/hspinner.cxx
/home/ed/Downloads/flrig-1.3.50/src/widgets/pl_tones.cxx
/home/ed/Downloads/flrig-1.3.50/src/widgets/.deps/.dirstamp
/home/ed/Downloads/flrig-1.3.50/src/widgets/.deps/flrig-Fl_SigBar.Po
/home/ed/Downloads/flrig-1.3.50/src/widgets/.deps/flrig-FreqControl.Po
/home/ed/Downloads/flrig-1.3.50/src/widgets/.deps/flrig-ValueSlider.Po
/home/ed/Downloads/flrig-1.3.50/src/widgets/.deps/flrig-combo.Po
/home/ed/Downloads/flrig-1.3.50/src/widgets/.deps/flrig-flinput2.Po
/home/ed/Downloads/flrig-1.3.50/src/widgets/.deps/flrig-flslider2.Po
/home/ed/Downloads/flrig-1.3.50/src/widgets/.deps/flrig-font_browser.Po
/home/ed/Downloads/flrig-1.3.50/src/widgets/.deps/flrig-hspinner.Po
/home/ed/Downloads/flrig-1.3.50/src/widgets/.deps/flrig-pl_tones.Po
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/.deps
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/.dirstamp
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/XmlRpc.h
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/XmlRpcBase64.h
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/XmlRpcClient.cpp
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/XmlRpcClient.h
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/XmlRpcDispatch.cpp
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/XmlRpcDispatch.h
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/XmlRpcException.h
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/XmlRpcMutex.cpp
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/XmlRpcMutex.h
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/XmlRpcServer.cpp
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/XmlRpcServer.h
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/XmlRpcServerConnection.cpp
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/XmlRpcServerConnection.h
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/XmlRpcServerMethod.cpp
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/XmlRpcServerMethod.h
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/XmlRpcSocket.cpp
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/XmlRpcSocket.h
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/XmlRpcSource.cpp
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/XmlRpcSource.h
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/XmlRpcUtil.cpp
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/XmlRpcUtil.h
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/XmlRpcValue.cpp
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/XmlRpcValue.h
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/flrig-XmlRpcClient.o
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/flrig-XmlRpcDispatch.o
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/flrig-XmlRpcMutex.o
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/flrig-XmlRpcServer.o
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/flrig-XmlRpcServerConnection.o
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/flrig-XmlRpcServerMethod.o
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/flrig-XmlRpcSocket.o
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/flrig-XmlRpcSource.o
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/flrig-XmlRpcUtil.o
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/flrig-XmlRpcValue.o
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/.deps/.dirstamp
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/.deps/flrig-XmlRpcClient.Po
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/.deps/flrig-XmlRpcDispatch.Po
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/.deps/flrig-XmlRpcMutex.Po
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/.deps/flrig-XmlRpcServer.Po
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/.deps/flrig-XmlRpcServerConnection.Po
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/.deps/flrig-XmlRpcServerMethod.Po
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/.deps/flrig-XmlRpcSocket.Po
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/.deps/flrig-XmlRpcSource.Po
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/.deps/flrig-XmlRpcUtil.Po
/home/ed/Downloads/flrig-1.3.50/src/xmlrpcpp/.deps/flrig-XmlRpcValue.Po
/usr/local/bin/flrig
/usr/local/share/applications/flrig.desktop
/usr/local/share/pixmaps/flrig.xpm
/var/cache/apt/archives/flrig_1.3.49-1build1_amd64.deb
ed@ed-Inspiron:~$
```

---

### Post by eddugo on 2020-06-24
Impervidus

I actually installed it twice as I thought it was gone the first time. I used tar.gz.  I still get"no such file or directory" using the correct command characters.  i did remove the folder from Home hidden files.  Above is a read out from "locate"

---

### Post by eddugo on 2020-06-24
/usr/local/bin/ -- has one item that says 103.5MB on disk, but I do't know how to remove??

---

### Post by Impavidus on 2020-06-24
So you installed it once from the repositories (the package is still in /apt/cache/apt/archives), but removed that. Then you installed from source and put the resulting program in /usr/local. Which is the appropriate place for manually installed stuff.

Unless you really need version 1.3.50, I strongly suggest you take the version from the repository (which is version 1.3.49, possibly with some bugfixes backported). If something goes wrong when installing from the repository, let's try and fix that. Installing from source is the last resort.

---

### Post by dragonfly41 on 2020-06-24
Remember if using ```
sudo locate
``` to apply the command ```
sudo updatedb
``` from time to time to update the file index. It takes a number of minutes to complete the indexing. Otherwise the locate might give misleading results.

---

### Post by eddugo on 2020-06-24
Is it possible to remove it from /USR/local?  If I can't uninstall is there a way to disable it? add a extra letter to the file name???

---

### Post by dragonfly41 on 2020-06-24
Yes you can if you are concerned about deleting/removing ..

/usr/local/bin/flrig
/usr/local/share/applications/flrig.desktop

can be edited to this ..

/usr/local/bin/_flrig
/usr/local/share/applications/_flrig.desktop

to knock them out.

---

### Post by ajgreeny on 2020-06-24
It looks as if you installed this package perhaps by using source code and compiling it as most of what  you show in post #4 appears to be source code in Downloads in your home?

If I'm  correct did you use a final "make install" command? You would have made life easier had you used checkinstall as that creates a .deb package and installs it, allowing removal with the more normal "sudo apt remove" command.  Just out of interest what does command
which flrig
show as output?

However this may all be worrying over nothing and assuming this program does not cause any problems you could simply leave it where it is but remove all the source code in Downloads.

---

### Post by eddugo on 2020-06-25
ed@ed-Inspiron:~$ which flrig
/usr/local/bin/flrig
ed@ed-Inspiron:~$

---

### Post by ajgreeny on 2020-06-25
Source code installed applications for which you used ***make install*** as the final command can often (should really be always, but that is not so in every case) be uninstalled by navigating to the source folder and running ***make uninstall*** using sudo in the case of Ubuntu.  That assumes you have not already removed all the source code from your system, of course.

Worth trying I think, then installing the package from the repos.

---

### Post by eddugo on 2020-06-25
ajgreeny

Thank you for the info

I going to remove the source code, install the program from the repos.  When I started using Ubuntu 13 years ago, (Ubuntu 7.04) any specialized program had to be installed using a tar.gz.  i guess I didn't change with the times.  thanks again for you help.  I learned a lot in the past 3 days.  I'll mark it solved.

---

### Post by eddugo on 2020-06-25
Drgonfly 41
Thank you for the info

I going to remove the source code, install the program from the repos.  When I started using Ubuntu 13 years ago, (Ubuntu 7.04) any specialized program had to be installed using a tar.gz.  i guess I didn't change with the times.  thanks again for you help.  I learned a lot in the past 3 days.  I'll mark it solved.

---

### Post by eddugo on 2020-06-25
Impavidus

Thank you for the info

I going to remove the source code, install the program from the repos.  When I started using Ubuntu 13 years ago, (Ubuntu 7.04) any specialized program had to be installed using a tar.gz.  i guess I didn't change with the times.  thanks again for you help.  I learned a lot in the past 3 days.  I'll mark it solved.

---

