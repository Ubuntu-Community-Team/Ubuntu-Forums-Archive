---
title: "Installation and or wireless question: make error swscanner"
date: 2007-08-06
forum: General Help
---

### Post by hops33n on 2007-08-06
After realizing the scan crash error with swscanner, I found to download and install the svn trunk.  I configured and installed xorg-dev, libqt3-mt-dev, kdelibs-dev, libjpeg-progs, libiw-dev and libshp-dev.  When I went to make, I errored and then installed automake1.9.  Now when I make I get this long listing:


root@frafl2sflt3:/home/user/My_Docs/trunk# make
make  all-recursive
make[1]: Entering directory `/home/user/My_Docs/trunk'
Making all in doc
make[2]: Entering directory `/home/user/My_Docs/trunk/doc'
make[3]: Entering directory `/home/user/My_Docs/trunk/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/user/My_Docs/trunk/doc'
make[2]: Leaving directory `/home/user/My_Docs/trunk/doc'
Making all in icons
make[2]: Entering directory `/home/user/My_Docs/trunk/icons'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/user/My_Docs/trunk/icons'
Making all in man
make[2]: Entering directory `/home/user/My_Docs/trunk/man'
make[3]: Entering directory `/home/user/My_Docs/trunk/man'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/user/My_Docs/trunk/man'
make[2]: Leaving directory `/home/user/My_Docs/trunk/man'
Making all in po
make[2]: Entering directory `/home/user/My_Docs/trunk/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/user/My_Docs/trunk/po'
Making all in sounds
make[2]: Entering directory `/home/user/My_Docs/trunk/sounds'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/user/My_Docs/trunk/sounds'
Making all in src
make[2]: Entering directory `/home/user/My_Docs/trunk/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common -Wno-non-virtual-dtor -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.cpp; \
        then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
In file included from mainwindow.h:23,
                 from main.cpp:22:
frmconfig.h:24:23: error: dlgConfig.h: No such file or directory
In file included from gpserial.h:36,
                 from myevents.h:25,
                 from mainwindow.h:27,
                 from main.cpp:22:
frmconfigini.h:24:26: error: dlgConfigIni.h: No such file or directory
In file included from mainwindow.h:32,
                 from main.cpp:22:
frmutils.h:41:22: error: dlgUtils.h: No such file or directory
In file included from mainwindow.h:36,
                 from main.cpp:22:
frmsignalchart.h:29:28: error: dlgSignalChart.h: No such file or directory
frmconfig.h:57: error: ISO C++ forbids declaration of &#8216;dlgConfig&#8217; with no type
frmconfig.h:57: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
/usr/include/kde/kdialogbase.h: In member function &#8216;QLabel* frmconfig::getlblEssid()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfig.h:72: error: within this context
frmconfig.h:72: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h: In member function &#8216;QLabel* frmconfig::getlblMAC()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfig.h:73: error: within this context
frmconfig.h:73: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h: In member function &#8216;QCheckBox* frmconfig::getchkWEP()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfig.h:74: error: within this context
frmconfig.h:74: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h: In member function &#8216;QLineEdit* frmconfig::gettxtKey()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfig.h:75: error: within this context
frmconfig.h:75: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h: In member function &#8216;QComboBox* frmconfig::getcmbKeyLength()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfig.h:76: error: within this context
frmconfig.h:76: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h: In member function &#8216;QLineEdit* frmconfig::gettxtIP1()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfig.h:77: error: within this context
frmconfig.h:77: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h: In member function &#8216;QLineEdit* frmconfig::gettxtIP2()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfig.h:78: error: within this context
frmconfig.h:78: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h: In member function &#8216;QLineEdit* frmconfig::gettxtIP3()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfig.h:79: error: within this context
frmconfig.h:79: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h: In member function &#8216;QLineEdit* frmconfig::gettxtIP4()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfig.h:80: error: within this context
frmconfig.h:80: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h: In member function &#8216;QLineEdit* frmconfig::gettxtMask1()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfig.h:81: error: within this context
frmconfig.h:81: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h: In member function &#8216;QLineEdit* frmconfig::gettxtMask2()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfig.h:82: error: within this context
frmconfig.h:82: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h: In member function &#8216;QLineEdit* frmconfig::gettxtMask3()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfig.h:83: error: within this context
frmconfig.h:83: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h: In member function &#8216;QLineEdit* frmconfig::gettxtMask4()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfig.h:84: error: within this context
frmconfig.h:84: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h: In member function &#8216;QLineEdit* frmconfig::gettxtGat1()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfig.h:85: error: within this context
frmconfig.h:85: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h: In member function &#8216;QLineEdit* frmconfig::gettxtGat2()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfig.h:86: error: within this context
frmconfig.h:86: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h: In member function &#8216;QLineEdit* frmconfig::gettxtGat3()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfig.h:87: error: within this context
frmconfig.h:87: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h: In member function &#8216;QLineEdit* frmconfig::gettxtGat4()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfig.h:88: error: within this context
frmconfig.h:88: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h: In member function &#8216;QGroupBox* frmconfig::getfrmGate()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfig.h:89: error: within this context
frmconfig.h:89: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h: In member function &#8216;QGroupBox* frmconfig::getfrmDhcp()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfig.h:90: error: within this context
frmconfig.h:90: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h: In member function &#8216;QLineEdit* frmconfig::gettxtDhcpClient()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfig.h:91: error: within this context
frmconfig.h:91: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h: In member function &#8216;QLineEdit* frmconfig::gettxtScript()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfig.h:92: error: within this context
frmconfig.h:92: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
frmconfigini.h: At global scope:
frmconfigini.h:44: error: ISO C++ forbids declaration of &#8216;dlgConfigIni&#8217; with no type
frmconfigini.h:44: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
/usr/include/kde/kdialogbase.h: In member function &#8216;QComboBox* frmConfigIni::getCmbParity()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfigini.h:50: error: within this context
frmconfigini.h:50: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h: In member function &#8216;QComboBox* frmConfigIni::getCmbStop()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfigini.h:51: error: within this context
frmconfigini.h:51: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h: In member function &#8216;QComboBox* frmConfigIni::getCmbBits()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfigini.h:52: error: within this context
frmconfigini.h:52: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h: In member function &#8216;QComboBox* frmConfigIni::getCmbBaud()&#8217;:
/usr/include/kde/kdialogbase.h:1629: error: &#8216;KDialogBase::KDialogBasePrivate* const KDialogBase::d&#8217; is private
frmconfigini.h:53: error: within this context
frmconfigini.h:53: error: invalid use of undefined type &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
/usr/include/kde/kdialogbase.h:1628: error: forward declaration of &#8216;struct KDialogBase::KDialogBasePrivate&#8217;
frmutils.h: At global scope:
frmutils.h:56: error: ISO C++ forbids declaration of &#8216;dlgUtils&#8217; with no type
frmutils.h:56: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
frmsignalchart.h:43: error: ISO C++ forbids declaration of &#8216;dlgSignalChart&#8217; with no type
frmsignalchart.h:43: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
frmsignalchart.h: In member function &#8216;void frmSignalChart::setMAC(QString)&#8217;:
frmsignalchart.h:52: error: &#8216;dlgwidget&#8217; was not declared in this scope
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/user/My_Docs/trunk/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/user/My_Docs/trunk'
make: *** [all] Error 2


Any ideas? If you need anymore info let me know. Thanks in advance.

---

