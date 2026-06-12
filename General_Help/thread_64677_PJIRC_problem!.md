---
title: "PJIRC problem!"
date: 2005-09-11
forum: General Help
---

### Post by nemesa on 2005-09-11
Hi!

I would like to use PJIRC to manage IRC connection(through html) to my site.
There is some bug, but I don't know which is the wrong element...

So Firefox crashes when I open any HTML pages uses PJIRC Java applet.
(i.e. [www.pjirc.com/demo.php](www.pjirc.com/demo.php))

I use Firefox 1.0.6(manually installed) and Jre 1.5.0_04 (manually installed).
On Windows (with the same versions above) works...
With jre 1.4.2 it works (on my ubuntu box)...

Please help!!

---

### Post by pgabriel on 2005-09-22
Just a me-too here. 
This is the first java applet that crashes the browser, others that i use work fine. I suspect Firefox because this used to work before on Ubuntu than the upgrade to a new version 1.0.3 or something generated this error. 
At some point the applet requests authorization from the user and I think this is the point when crashes.

My environment is:
 
Firefox 1.0.6 - Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.10) Gecko/20050725 Firefox/1.0.6 (Ubuntu package 1.0.6)
$ java -version
java version "1.5.0_01"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_01-b08)
Java HotSpot(TM) Client VM (build 1.5.0_01-b08, mixed mode, sharing)

It dies with:
```

# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb1ae0d3b, pid=10120, tid=2971663280
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_01-b08 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x2ed3b]
#

Stack: [0xb117f000,0xb1200000),  sp=0xb11fec34,  free space=511k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libfontmanager.so+0x2ed3b]
C  [libfontmanager.so+0x34efe]
C  [libfontmanager.so+0x35286]
C  [libfontmanager.so+0x376c2]
C  [libfontmanager.so+0x35aca]
C  [libfontmanager.so+0x35fe2]
C  [libfontmanager.so+0x225db]
C  [libfontmanager.so+0x2433c]
C  [libfontmanager.so+0x46270]  Java_sun_font_FileFont_getGlyphImage+0x120
j  sun.font.FileFont.getGlyphImage(JI)J+0
j  sun.font.FileFontStrike.getGlyphImagePtr(I)J+62
j  sun.font.FileFontStrike.getGlyphAdvance(I)F+59
j  sun.font.FileFontStrike.getCodePointAdvance(I)F+9
j  sun.font.FontDesignMetrics.handleCharWidth(I)F+5
j  sun.font.FontDesignMetrics.getLatinCharWidth(C)F+16
j  sun.font.FontDesignMetrics.stringWidth(Ljava/lang/String;)I+36

```

---

### Post by SWAT on 2005-10-05
I have exactly the same problem. I'm also using the newest version of Firefox and Java (apt-get style), but when the pjIRC applet loads it crashes, together with Firefox. It works fine on Windows though.... Let's fix this :)

---

### Post by alras on 2005-10-06
I use blackdown java version 1.4.2-02 from the repositories and that seems to work ok. with the applet.

---

### Post by FuzzyShoting on 2006-09-26
I have been working on this problem for quite some time ago.
The debugger might say that its having problems with libfontmanager.so 
The problem though is an earlier upgrade in the gtk2-engines of ubuntu.
I've confirmed this in Ubuntu Hoary, and this is still present in Ubuntu Dapper Drake.

It got broke since the security update of Ubuntu Hoary, which as the version is unknown. The version coming with the ISO installation was alright.

What was changed?

- Should be moved to Dapper, since this problem is still present!

---

### Post by geofff on 2006-10-12
Another me-too
I'm using latest release of Firefox updated automatically on Dapper. Firefox not only aborts when I'm loading some pages such as [www.chat386.com](www.chat386.com) but can cut out half way through reading stuff on other sites when I wouldn't have thought anything active was happening. If there's any info I can supply that might be useful please let me know. 
Wish you luck in solving this.

Geofff

---

### Post by Itaku on 2008-03-30
i get 
Unable to connect : java.security.AccessControlException : access denied (java.net.SocketPermission irc.jungelirc.net resolve) 
how do i fix that?

---

