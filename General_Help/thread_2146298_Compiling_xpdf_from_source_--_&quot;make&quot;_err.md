---
title: "Compiling xpdf from source -- &quot;make&quot; errors"
date: 2013-05-18
forum: General Help
---

### Post by chellrose on 2013-05-18
The xpdf package available from the Ubuntu repositories (for 12.04) crashes with a segfault on startup.  I've found several bug reports on this, and the consensus seems to be either:
1) Downgrade libpoppler to v.19, or
2) Compile xpdf from source using the package available from [http://www.foolabs.com/xpdf/download.html](http://www.foolabs.com/xpdf/download.html)

I seem to have libpoppler19 already, so I'm trying to compile from source.  Initially "configure" was complaining that it couldn't find FreeType; I've got FreeType6 installed (by default, I think).  After some more digging, I found that it wanted FreeType2.  So I installed that and then the configure process seemed to work.  However, ```
make
``` resulted in a whole pile of warnings and an error message.

```

XPDFViewer.cc:1806:54: error: invalid conversion from ‘const char*’ to ‘char*’ [-fpermissive]
/usr/include/Xm/Xm.h:1477:22: error:   initializing argument 1 of ‘unsigned char* XmStringCreateLocalized(char*)’ [-fpermissive]
XPDFViewer.cc:3397:64: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings]
XPDFViewer.cc: In member function ‘void XPDFViewer::setupPrintDialog()’:
XPDFViewer.cc:3453:43: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings]
XPDFViewer.cc: In member function ‘void XPDFViewer::cmdRun(GString**, int, XEvent*)’:
XPDFViewer.cc:1210:28: warning: ignoring return value of ‘int system(const char*)’, declared with attribute warn_unused_result [-Wunused-result]
make[1]: *** [XPDFViewer.o] Error 1
make: *** [all] Error 2

```

(along with a whole pile of similar warnings about deprecated conversion from string constant to char*.)  Not surprisingly, ```
sudo make install
``` then fails.

Can anyone tell me how I might fix this?

---

### Post by andrew.46 on 2013-05-18
A good first step might be to assemble all of the dependencies needed to compile xpdf and the easiest way to do this is:

```
sudo apt-get build-dep xpdf
```

and then recompile and see if many of the errors vanish. Perhaps also you should be using *checkinstall* to create and install your final package.

---

### Post by mc4man on 2013-05-18
Both the 12.04 repo source (3.02+) & 3.03 can be built & will apparently work without segfaulting. Whether it works fully or without some 'unseen' issue don't know & not inclined to pursue.
(Debian/Ubuntu apply a host of patches, with those patches fully applied to the 3.02 source it either fails to build or segfaults. Likely caused by one or 2 of the patches. Whether any of those patches is useful can be tested but time consuming, ect.

Just to note - 
 FreeType6 is the package name of FreeType2, the location of the libs is where the configure script can't find.
Also the repo source builds off of lesstif2-dev, here I substituted libmotif-dev

So for 3.03 you can try - 
sudo apt-get build-dep xpdf
Then install libmotif-dev which will remove lesstif2-dev (you can try with  lesstif2-dev first if desired
Also you may want to install libt1-dev 

For the ./configure use something like this, (this is for a 32 bit install, adjust blue for 64 bit, the includes may not be needed, doesn't hurt
```
./configure --with-freetype2-includes=/usr/include/freetype2 --with-freetype2-library=usr/lib/[COLOR="#0000CD"]i386-linux-gnu[/COLOR]
```
Also note that there is no "sudo make uninstall" available for the source so maybe consider checkinstall

The source will not install a .desktop, if needed then in ~/.local/share/applications use this - ( if an icon is desired then full path to one in the Icon= line or place attached in /usr/share/pixmaps folder
```
[Desktop Entry]
Name=xpdf
GenericName=PDF viewer
Comment=View PDF files
Exec=xpdf %U
Icon=xpdf
Terminal=false
Type=Application
MimeType=application/pdf;
Categories=Viewer;Graphics;
```

Also note see these warnings when run from terminal, whether an issue don't know
> xpdf '/home/doug/Documents/sample.pdf' Warning: Cannot convert string "-*-helvetica-medium-r-normal--12-*-*-*-*-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-*-courier-medium-r-normal--12-*-*-*-*-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-*-times-bold-i-normal--20-*-*-*-*-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-*-times-medium-r-normal--16-*-*-*-*-*-iso8859-1" to type FontStruct

Attached icon & text of configure

---

### Post by chellrose on 2013-05-22
Thanks.  I ran ```
sudo apt-get build-dep xpdf
```, apparently successfully.  I also used the options to configure suggested by mc4man.  It still complains that it can't find FreeType.  The result of ```
make
``` is
```

cd goo; make
make[1]: Entering directory `/home/rachel/Downloads/xpdf-3.03/goo'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/rachel/Downloads/xpdf-3.03/goo'
cd fofi; make
make[1]: Entering directory `/home/rachel/Downloads/xpdf-3.03/fofi'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/rachel/Downloads/xpdf-3.03/fofi'
cd splash; make
make[1]: Entering directory `/home/rachel/Downloads/xpdf-3.03/splash'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/rachel/Downloads/xpdf-3.03/splash'
cd xpdf; make all-no-x
make[1]: Entering directory `/home/rachel/Downloads/xpdf-3.03/xpdf'
make[1]: Nothing to be done for `all-no-x'.
make[1]: Leaving directory `/home/rachel/Downloads/xpdf-3.03/xpdf'

```

Compiling via ```
sudo checkinstall
``` appears to be successful... it says that it has created and installed the Debian package.  However, 
```

~$ xpdf
The program 'xpdf' is currently not installed.  You can install it by typing:
sudo apt-get install xpdf

```

I've tried it with lesstif2-dev and with libmotif-dev, both with the same results.  I even tried ```
sudo dpkg -i xpdf_3.03-1_i386.deb
``` on the .deb file that the checkinstall process generated.  I can't find an xpdf executable in any obscure directories, either.

---

