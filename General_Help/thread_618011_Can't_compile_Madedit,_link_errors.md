---
title: "Can't compile Madedit, link errors"
date: 2007-11-19
forum: General Help
---

### Post by D-- on 2007-11-19
Hi, I've been trying all day to compile Madedit, a hex editor. I am aware the author makes a Debian package available, but there are some UI changes I would like to make to get it to fit better with my system.

The Madedit page is located at [http://madedit.sourceforge.net/](http://madedit.sourceforge.net/). I am using the 0.2.8 code, but have also tested this with 0.2.7. The following link errors occurred with both wxWidgets 2.6 and 2.8. My current output is taken from 2.8.

```
g++  -g -O2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12   -I./xpressive    -o madedit  madedit-MadAboutDialog.o madedit-MadConvEncDialog.o madedit-MadEditApp.o madedit-MadEditFrame.o madedit-MadFindInFilesDialog.o madedit-MadHighlightingDialog.o madedit-MadOptionsDialog.o madedit-MadPlugin.o madedit-MadPrintout.o madedit-MadReplaceDialog.o madedit-MadSearchDialog.o madedit-MadSortDialog.o madedit-MadUtils.o madedit-MadWordCountDialog.o madedit-caret_new.o madedit-clipbrd_gtk.o madedit-MadEdit.o madedit-MadEditAdvanced.o madedit-MadEditBasic.o madedit-MadEditCommand.o madedit-MadEditSearch.o madedit-MadEdit_gtk.o madedit-MadEncoding.o madedit-MadLines.o madedit-MadSyntax.o madedit-MadUndo.o madedit-TradSimp.o madedit-auibook.o madedit-dockart.o madedit-floatpane.o madedit-framemanager.o madedit-tabmdi.o madedit-CharDistribution.o madedit-JpCntx.o madedit-LangBulgarianModel.o madedit-LangCyrillicModel.o madedit-LangGreekModel.o madedit-LangHebrewModel.o madedit-LangHungarianModel.o madedit-LangThaiModel.o madedit-nsBig5Prober.o madedit-nsCharSetProber.o madedit-nsEscCharsetProber.o madedit-nsEscSM.o madedit-nsEUCJPProber.o madedit-nsEUCKRProber.o madedit-nsEUCTWProber.o madedit-nsGB2312Prober.o madedit-nsHebrewProber.o madedit-nsLatin1Prober.o madedit-nsMBCSGroupProber.o madedit-nsMBCSSM.o madedit-nsSBCharSetProber.o madedit-nsSBCSGroupProber.o madedit-nsSJISProber.o madedit-nsUniversalDetector.o madedit-nsUTF8Prober.o madedit-impl.o  -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXcomposite -lXdamage -lpango-1.0 -lcairo -lX11 -lXfixes -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -pthread   -lwx_gtk2u_aui-2.8 -lwx_gtk2u_xrc-2.8 -lwx_gtk2u_qa-2.8 -lwx_gtk2u_html-2.8 -lwx_gtk2u_adv-2.8 -lwx_gtk2u_core-2.8 -lwx_baseu_xml-2.8 -lwx_baseu_net-2.8 -lwx_baseu-2.8 
madedit-MadAboutDialog.o: In function `~wxString':
/usr/include/wx-2.8/wx/string.h:243: undefined reference to `free'
madedit-MadAboutDialog.o: In function `wxStringData::Unlock()':
/usr/include/wx-2.8/wx/string.h:243: undefined reference to `free'
madedit-MadAboutDialog.o: In function `~wxString':
/usr/include/wx-2.8/wx/string.h:243: undefined reference to `free'
madedit-MadAboutDialog.o: In function `~wxStringBase':
/usr/include/wx-2.8/wx/string.h:243: undefined reference to `free'
madedit-MadAboutDialog.o: In function `~wxString':
/usr/include/wx-2.8/wx/string.h:243: undefined reference to `free'
madedit-MadAboutDialog.o:/usr/include/wx-2.8/wx/string.h:243: more undefined references to `free' follow
/usr/bin/ld: madedit: hidden symbol `free' isn't defined
/usr/bin/ld: final link failed: Nonrepresentable section on output
collect2: ld returned 1 exit status
make[2]: *** [madedit] Error 1
make[2]: Leaving directory `/home/d/Desktop/madedit-0.2.8'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/d/Desktop/madedit-0.2.8'
make: *** [all] Error 2
```

The link in question here in wxWidgets is:

```
238: #if defined(__VISUALC__) && defined(_MT) && !defined(_DLL)
239:   void  Unlock() { if ( !IsEmpty() && --nRefs == 0) Free();  }
240:   // we must not inline deallocation since allocation is not inlined
241:   void  Free();
242: #else
243:   void  Unlock() { if ( !IsEmpty() && --nRefs == 0) free(this);  }
244: #endif
```

Does anyone have any ideas on how to fix this and get Madedit to compile?

Edit: God damn the wxWidgets project. It STILL isn't working with gcc 4.0 and the bug was reported and fixed in CVS in **2005**. Doing an apt-get install gcc-3.4 g++-3.4 then hacking the Makefile to use these resulted in a perfect build.

---

