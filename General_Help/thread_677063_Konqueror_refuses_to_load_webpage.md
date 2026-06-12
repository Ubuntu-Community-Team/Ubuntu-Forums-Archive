---
title: "Konqueror refuses to load webpage"
date: 2008-01-24
forum: General Help
---

### Post by sageb1 on 2008-01-24
Konqueror fails and prints on window:
An error occurred while loading [http://ubuntuforums.org/showthread.php?t=674438&highlight=cpu:](http://ubuntuforums.org/showthread.php?t=674438&highlight=cpu:)
The process for the [http://ubuntuforums.org](http://ubuntuforums.org) protocol died unexpectedly.

Konqueror does create the crashlog to save up URLs loaded at time of crash.

I also attached a recent .xsession-errors log to this entry.

=== .xsession-errors ===
.Failed to connect to socket /tmp/fam-sageb1-
kbuildsycoca running...
konqueror: WARNING: Unknown class KJS::KJSDebugWin in session saved data!
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)

---

### Post by sageb1 on 2008-01-24
Most bugs related to konqueror and also to firefox and opera have been traced back to javascript on bugs.kde.org

[http://bugs.kde.org/buglist.cgi?short_desc_type=allwordssubstr&short_desc=kjs&long_desc_type=allwordssubstr&long_desc=kjs&bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bugidtype=include&bug_id=&votes=&emailassigned_to1=1&emailtype1=substring&email1=&emailassigned_to2=1&emailreporter2=1&emailcc2=1&emailtype2=substring&email2=&changedin=&chfieldfrom=&chfieldto=Now&chfieldvalue=&order=Reuse+same+sort+as+last+time&cmdtype=doit](http://bugs.kde.org/buglist.cgi?short_desc_type=allwordssubstr&short_desc=kjs&long_desc_type=allwordssubstr&long_desc=kjs&bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bugidtype=include&bug_id=&votes=&emailassigned_to1=1&emailtype1=substring&email1=&emailassigned_to2=1&emailreporter2=1&emailcc2=1&emailtype2=substring&email2=&changedin=&chfieldfrom=&chfieldto=Now&chfieldvalue=&order=Reuse+same+sort+as+last+time&cmdtype=doit)

---

### Post by sageb1 on 2008-01-24
Re: QFont::setPixelSize:  Pixel size <= 0 (0) error

Here is the definition of the object in QFont class from the source author at
[http://doc.trolltech.com/3.3//qfont.html#setPixelSize](http://doc.trolltech.com/3.3//qfont.html#setPixelSize)

void QFont::setPixelSize ( int pixelSize ) 
 Sets the font size to pixelSize pixels. 
 Using this function makes the font device dependent. Use setPointSize() or setPointSizeFloat() to set the size of the font in a device independent manner.

This explains the following error: 

X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0

which maybe associated with :
QFont::setPixelSize: Pixel size <= 0 (0)

The error happens because setPixelSize is never prevented from using a Pixel size of 0 or lesser than 0. This means QFont::setPointlSize should be set to default for the particular application based on config settings for it.

The following sources are affected:

/usr/share/doc/kde/HTML/en/kdelibs-apidocs/kate/html/katefont_8cpp-source.html
/usr/share/doc/kde/HTML/en/kdelibs-apidocs/kate/html/katefont_8h-source.html
/usr/share/doc/kde/HTML/en/kdelibs-apidocs/kdeui/html/kfontcombo_8cpp-source.html
/usr/share/doc/kde/HTML/en/kdelibs-apidocs/kdeui/html/kfontdialog_8cpp-source.html
/usr/share/doc/kde/HTML/en/kdelibs-apidocs/kdeui/html/kfontdialog_8h-source.html
/usr/share/doc/kde/HTML/en/kdelibs-apidocs/kdeui/html/kfontrequester_8cpp-source.html
/usr/share/doc/kde/HTML/en/kdelibs-apidocs/kdeui/html/kfontrequester_8h-source.html
/usr/share/doc/kde/HTML/en/koffice-apidocs/lib/html/fontedit_8cpp-source.html
/usr/share/doc/kde/HTML/en/koffice-apidocs/lib/html/fontstyle_8cc-source.html
/usr/share/doc/kde/HTML/en/koffice-apidocs/lib/html/fontstyle_8h-source.html

---

### Post by sageb1 on 2008-01-24
(edited:deleted original text)
/usr/share/doc/kde/HTML/en/kdelibs-apidocs/kdeui/html/kfontcombo_8cpp-source.html appears to be where the problem is,

kfontcombo.cpp
there is probably a check for pointsize of 0 hence the error.

---

