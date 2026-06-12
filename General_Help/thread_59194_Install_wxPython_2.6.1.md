---
title: "Install wxPython 2.6.1"
date: 2005-08-23
forum: General Help
---

### Post by waffen on 2005-08-23
Hello,
Im newbie with Linux, I need this version of wxPython, in the repository only found 2.5.3, is too old, and my Boa/Spe IDEs need v 2.6.1

I tried compiled from source but its action fail. ](*,) 

Please any help? 

Thanks in advance!!

---

### Post by Zotova on 2005-08-23
What error(s) did you get when trying to compile from source?

---

### Post by waffen on 2005-08-23
Yes, copy & paste from my console:

Later 1.30 hrs compiling....

../../.././bk-deps g++ -c -o stcdll_XPM.o -D__WXGTK__     -I../../../../contrib/src/stc/../../include -I../../../../contrib/src/stc/scintilla/include -I../../../../contrib/src/stc/scintilla/src -D__WX__ -DSCI_LEXER -DLINK_LEXERS -DWXUSINGDLL -DWXMAKINGDLL_STC -fPIC -DPIC -D__WXDEBUG__ -I../../../lib/wx/include/gtk2-unicode-debug-2.6 -I../../../../include -DXTHREADS -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D_LARGEFILE_SOURCE=1 -I/usr/X11R6/include -O2 -pthread -I/usr/include/SDL -D_REENTRANT -Wall -Wno-ctor-dtor-privacy ../../../../contrib/src/stc/scintilla/src/XPM.cxx
g++ -shared -fPIC -o ../../../lib/libwx_gtk2ud_stc-2.6.so.0.0.0  stcdll_PlatWX.o stcdll_ScintillaWX.o stcdll_stc.o stcdll_AutoComplete.o stcdll_CallTip.o stcdll_CellBuffer.o stcdll_ContractionState.o stcdll_Document.o stcdll_DocumentAccessor.o stcdll_Editor.o stcdll_ExternalLexer.o stcdll_Indicator.o stcdll_KeyMap.o stcdll_KeyWords.o stcdll_LexAPDL.o stcdll_LexAU3.o stcdll_LexAVE.o stcdll_LexAda.o stcdll_LexAsm.o stcdll_LexAsn1.o stcdll_LexBaan.o stcdll_LexBash.o stcdll_LexBullant.o stcdll_LexCLW.o stcdll_LexCPP.o stcdll_LexCSS.o stcdll_LexConf.o stcdll_LexCrontab.o stcdll_LexEScript.o stcdll_LexEiffel.o stcdll_LexErlang.o stcdll_LexForth.o stcdll_LexFortran.o stcdll_LexGui4Cli.o stcdll_LexHTML.o stcdll_LexKix.o stcdll_LexLisp.o stcdll_LexLout.o stcdll_LexLua.o stcdll_LexMMIXAL.o stcdll_LexMPT.o stcdll_LexMSSQL.o stcdll_LexMatlab.o stcdll_LexMetapost.o stcdll_LexNsis.o stcdll_LexOthers.o stcdll_LexPB.o stcdll_LexPOV.o stcdll_LexPS.o stcdll_LexPascal.o stcdll_LexPerl.o stcdll_LexPython.o stcdll_LexRuby.o stcdll_LexSQL.o stcdll_LexScriptol.o stcdll_LexSpecman.o stcdll_LexTeX.o stcdll_LexVB.o stcdll_LexVHDL.o stcdll_LexVerilog.o stcdll_LexYAML.o stcdll_LineMarker.o stcdll_PropSet.o stcdll_RESearch.o stcdll_ScintillaBase.o stcdll_Style.o stcdll_StyleContext.o stcdll_UniConversion.o stcdll_ViewStyle.o stcdll_WindowAccessor.o stcdll_XPM.o -pthread   -L/usr/X11R6/lib    -L../../../lib   -Wl,-soname,libwx_gtk2ud_stc-2.6.so.0   -lwx_gtk2ud-2.6 -lwxtiffd-2.6 -lwxjpegd-2.6 -lwxpngd-2.6   -lwxregexud-2.6  -pthread   -L/usr/X11R6/lib -Wl,--version-script,../../../version-script -lz -ldl -lm  -pthread -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0 -lXinerama
(cd ../../../lib/; rm -f libwx_gtk2ud_stc-2.6.so libwx_gtk2ud_stc-2.6.so.0; ln -s libwx_gtk2ud_stc-2.6.so.0.0.0 libwx_gtk2ud_stc-2.6.so.0; ln -s libwx_gtk2ud_stc-2.6.so.0 libwx_gtk2ud_stc-2.6.so)
make: Leaving directory `/usr/src/rpm/BUILD/wxPython-src-2.6.1.0/bld/contrib/src/stc'
+ cd /usr/src/rpm/BUILD/wxPython-src-2.6.1.0/wxPython
+ /usr/bin/python2.4 setup.py WXPORT=gtk2 UNICODE=1 EP_ADD_OPTS=1 NO_SCRIPTS=1 'WX_CONFIG=/usr/src/rpm/BUILD/wxPython-src-2.6.1.0/bld/wx-config --no_rpath' build_ext --rpath=/usr/lib/wxPython-2.6.1.0-gtk2-unicode/lib build
Preparing CORE...
Preparing GLCANVAS...
Preparing STC...
Preparing GIZMOS...
Preparing ANIMATE...
running build_ext
error: invalid Python installation: unable to open /usr/lib/python2.4/config/Makefile (Is a directory)
error: Bad exit status from /var/tmp/rpm-tmp.42016 (%build)


RPM build errors:
    Bad exit status from /var/tmp/rpm-tmp.42016 (%build)

This is the command:
root@Laptop-Ubuntu:/home/mario/MisDownloads/Linux/Programas/wxPython # sudo rpmbuild --rebuild --define 'pyver 2.4' wxPython2.6-2.6.1.0-1.src.rpm

I follow the instructions form this website: [http://www.bitpim.org/developer.html](http://www.bitpim.org/developer.html)

Thanks in advance!!!  ](*,) 


[QUOTE=Zotova]What error(s) did you get when trying to compile from source?[/QUOTE]

---

### Post by waffen on 2005-09-01
> **waffen]Yes, copy & paste from my console:

Later 1.30 hrs compiling....

../../.././bk-deps g++ -c -o stcdll_XPM.o -D__WXGTK__     -I../../../../contrib/src/stc/../../include -I../../../../contrib/src/stc/scintilla/include -I../../../../contrib/src/stc/scintilla/src -D__WX__ -DSCI_LEXER -DLINK_LEXERS -DWXUSINGDLL -DWXMAKINGDLL_STC -fPIC -DPIC -D__WXDEBUG__ -I../../../lib/wx/include/gtk2-unicode-debug-2.6 -I../../../../include -DXTHREADS -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D_LARGEFILE_SOURCE=1 -I/usr/X11R6/include -O2 -pthread -I/usr/include/SDL -D_REENTRANT -Wall -Wno-ctor-dtor-privacy ../../../../contrib/src/stc/scintilla/src/XPM.cxx
g++ -shared -fPIC -o ../../../lib/libwx_gtk2ud_stc-2.6.so.0.0.0  stcdll_PlatWX.o stcdll_ScintillaWX.o stcdll_stc.o stcdll_AutoComplete.o stcdll_CallTip.o stcdll_CellBuffer.o stcdll_ContractionState.o stcdll_Document.o stcdll_DocumentAccessor.o stcdll_Editor.o stcdll_ExternalLexer.o stcdll_Indicator.o stcdll_KeyMap.o stcdll_KeyWords.o stcdll_LexAPDL.o stcdll_LexAU3.o stcdll_LexAVE.o stcdll_LexAda.o stcdll_LexAsm.o stcdll_LexAsn1.o stcdll_LexBaan.o stcdll_LexBash.o stcdll_LexBullant.o stcdll_LexCLW.o stcdll_LexCPP.o stcdll_LexCSS.o stcdll_LexConf.o stcdll_LexCrontab.o stcdll_LexEScript.o stcdll_LexEiffel.o stcdll_LexErlang.o stcdll_LexForth.o stcdll_LexFortran.o stcdll_LexGui4Cli.o stcdll_LexHTML.o stcdll_LexKix.o stcdll_LexLisp.o stcdll_LexLout.o stcdll_LexLua.o stcdll_LexMMIXAL.o stcdll_LexMPT.o stcdll_LexMSSQL.o stcdll_LexMatlab.o stcdll_LexMetapost.o stcdll_LexNsis.o stcdll_LexOthers.o stcdll_LexPB.o stcdll_LexPOV.o stcdll_LexPS.o stcdll_LexPascal.o stcdll_LexPerl.o stcdll_LexPython.o stcdll_LexRuby.o stcdll_LexSQL.o stcdll_LexScriptol.o stcdll_LexSpecman.o stcdll_LexTeX.o stcdll_LexVB.o stcdll_LexVHDL.o stcdll_LexVerilog.o stcdll_LexYAML.o stcdll_LineMarker.o stcdll_PropSet.o stcdll_RESearch.o stcdll_ScintillaBase.o stcdll_Style.o stcdll_StyleContext.o stcdll_UniConversion.o stcdll_ViewStyle.o stcdll_WindowAccessor.o stcdll_XPM.o -pthread   -L/usr/X11R6/lib    -L../../../lib   -Wl,-soname,libwx_gtk2ud_stc-2.6.so.0   -lwx_gtk2ud-2.6 -lwxtiffd-2.6 -lwxjpegd-2.6 -lwxpngd-2.6   -lwxregexud-2.6  -pthread   -L/usr/X11R6/lib -Wl,--version-script,../../../version-script -lz -ldl -lm  -pthread -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0 -lXinerama
(cd ../../../lib/ said:**
> http://www.bitpim.org/developer.html[/url]

Thanks in advance!!!  ](*,)
 Solution:

I missed install this package: Python2.4-Dev.

---

