---
title: "Anaglyph Compiz Plugin for Hardy Heron"
date: 2008-05-28
forum: General Help
---

### Post by HornedBeast on 2008-05-28
Hi.

I've followed all the guides I could find on here, but couldn't figure out how to install this plugin.

I tried doing it the way the Compiz-Fusion site suggested, but it doesn't build properly.

Does anyone have a deb package, or a work source that does compile properly?

Thanks in advance.

Andy

---

### Post by PmDematagoda on 2008-05-28
What error do you get while building? Also, how were you trying to install the plugin?

---

### Post by HornedBeast on 2008-05-28
I'm following this guide here:

[http://forum.compiz-fusion.org/showthread.php?p=56851](http://forum.compiz-fusion.org/showthread.php?p=56851)

Says it for the exact version of Ubuntu and Compiz im running. I've installed all the packages it asked for, everything!

Heres what happens when I do "make".

```
compiling : build/anaglyph_options.c -> build/anaglyph_options.loIn file included from build/anaglyph_options.c:19:
build/anaglyph_options.h:23: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
build/anaglyph_options.h:65: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
build/anaglyph_options.h:69: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
build/anaglyph_options.h:81: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;anaglyphGetDesaturate&#8217;
build/anaglyph_options.h:85: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;anaglyphGetMipmaps&#8217;
build/anaglyph_options.c:25: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
build/anaglyph_options.c:26: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;anaglyphOptionsVTable&#8217;
build/anaglyph_options.c:44: error: array type has incomplete element type
build/anaglyph_options.c:50: error: array type has incomplete element type
build/anaglyph_options.c: In function &#8216;anaglyphGetWindowToggleKeyOption&#8217;:
build/anaglyph_options.c:56: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:58: warning: control reaches end of non-void function
build/anaglyph_options.c: In function &#8216;anaglyphSetWindowToggleKeyNotify&#8217;:
build/anaglyph_options.c:62: error: dereferencing pointer to incomplete type
build/anaglyph_options.c: In function &#8216;anaglyphGetScreenToggleKeyOption&#8217;:
build/anaglyph_options.c:68: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:70: warning: control reaches end of non-void function
build/anaglyph_options.c: In function &#8216;anaglyphSetScreenToggleKeyNotify&#8217;:
build/anaglyph_options.c:74: error: dereferencing pointer to incomplete type
build/anaglyph_options.c: In function &#8216;anaglyphGetWindowToggleButtonOption&#8217;:
build/anaglyph_options.c:80: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:82: warning: control reaches end of non-void function
build/anaglyph_options.c: In function &#8216;anaglyphSetWindowToggleButtonNotify&#8217;:
build/anaglyph_options.c:86: error: dereferencing pointer to incomplete type
build/anaglyph_options.c: In function &#8216;anaglyphGetScreenToggleButtonOption&#8217;:
build/anaglyph_options.c:92: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:94: warning: control reaches end of non-void function
build/anaglyph_options.c: In function &#8216;anaglyphSetScreenToggleButtonNotify&#8217;:
build/anaglyph_options.c:98: error: dereferencing pointer to incomplete type
build/anaglyph_options.c: At top level:
build/anaglyph_options.c:102: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
build/anaglyph_options.c: In function &#8216;anaglyphGetAnaglyphMatchOption&#8217;:
build/anaglyph_options.c:110: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:110: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:112: warning: control reaches end of non-void function
build/anaglyph_options.c: In function &#8216;anaglyphSetAnaglyphMatchNotify&#8217;:
build/anaglyph_options.c:116: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:116: error: dereferencing pointer to incomplete type
build/anaglyph_options.c: At top level:
build/anaglyph_options.c:120: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
build/anaglyph_options.c: In function &#8216;anaglyphGetExcludeMatchOption&#8217;:
build/anaglyph_options.c:128: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:128: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:130: warning: control reaches end of non-void function
build/anaglyph_options.c: In function &#8216;anaglyphSetExcludeMatchNotify&#8217;:
build/anaglyph_options.c:134: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:134: error: dereferencing pointer to incomplete type
build/anaglyph_options.c: In function &#8216;anaglyphGetOffset&#8217;:
build/anaglyph_options.c:140: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:140: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:142: warning: control reaches end of non-void function
build/anaglyph_options.c: In function &#8216;anaglyphGetOffsetOption&#8217;:
build/anaglyph_options.c:146: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:146: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:148: warning: control reaches end of non-void function
build/anaglyph_options.c: In function &#8216;anaglyphSetOffsetNotify&#8217;:
build/anaglyph_options.c:152: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:152: error: dereferencing pointer to incomplete type
build/anaglyph_options.c: In function &#8216;anaglyphGetDesktopOffset&#8217;:
build/anaglyph_options.c:158: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:158: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:160: warning: control reaches end of non-void function
build/anaglyph_options.c: In function &#8216;anaglyphGetDesktopOffsetOption&#8217;:
build/anaglyph_options.c:164: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:164: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:166: warning: control reaches end of non-void function
build/anaglyph_options.c: In function &#8216;anaglyphSetDesktopOffsetNotify&#8217;:
build/anaglyph_options.c:170: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:170: error: dereferencing pointer to incomplete type
build/anaglyph_options.c: At top level:
build/anaglyph_options.c:174: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;anaglyphGetDesaturate&#8217;
build/anaglyph_options.c: In function &#8216;anaglyphGetDesaturateOption&#8217;:
build/anaglyph_options.c:182: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:182: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:184: warning: control reaches end of non-void function
build/anaglyph_options.c: In function &#8216;anaglyphSetDesaturateNotify&#8217;:
build/anaglyph_options.c:188: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:188: error: dereferencing pointer to incomplete type
build/anaglyph_options.c: At top level:
build/anaglyph_options.c:192: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;anaglyphGetMipmaps&#8217;
build/anaglyph_options.c: In function &#8216;anaglyphGetMipmapsOption&#8217;:
build/anaglyph_options.c:200: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:200: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:202: warning: control reaches end of non-void function
build/anaglyph_options.c: In function &#8216;anaglyphSetMipmapsNotify&#8217;:
build/anaglyph_options.c:206: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:206: error: dereferencing pointer to incomplete type
build/anaglyph_options.c: In function &#8216;anaglyphGetDisplayOption&#8217;:
build/anaglyph_options.c:212: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:214: warning: control reaches end of non-void function
build/anaglyph_options.c: In function &#8216;anaglyphGetScreenOption&#8217;:
build/anaglyph_options.c:218: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:218: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:220: warning: control reaches end of non-void function
build/anaglyph_options.c: At top level:
build/anaglyph_options.c:222: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;anaglyphOptionsDisplayOptionInfo&#8217;
build/anaglyph_options.c:229: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;anaglyphOptionsSetDisplayOption&#8217;
build/anaglyph_options.c: In function &#8216;anaglyphOptionsGetDisplayOptions&#8217;:
build/anaglyph_options.c:282: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:285: warning: control reaches end of non-void function
build/anaglyph_options.c: At top level:
build/anaglyph_options.c:287: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;anaglyphOptionsScreenOptionInfo&#8217;
build/anaglyph_options.c:296: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;anaglyphOptionsSetScreenOption&#8217;
build/anaglyph_options.c: In function &#8216;anaglyphOptionsGetScreenOptions&#8217;:
build/anaglyph_options.c:365: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:365: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:368: warning: control reaches end of non-void function
build/anaglyph_options.c: At top level:
build/anaglyph_options.c:370: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;anaglyphOptionsInitScreen&#8217;
build/anaglyph_options.c: In function &#8216;anaglyphOptionsFiniScreen&#8217;:
build/anaglyph_options.c:394: error: &#8216;anaglyphPluginVTable&#8217; undeclared (first use in this function)
build/anaglyph_options.c:394: error: (Each undeclared identifier is reported only once
build/anaglyph_options.c:394: error: for each function it appears in.)
build/anaglyph_options.c:395: warning: &#8216;return&#8217; with a value, in function returning void
build/anaglyph_options.c:397: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:397: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:400: warning: implicit declaration of function &#8216;compFiniScreenOptions&#8217;
build/anaglyph_options.c:400: warning: nested extern declaration of &#8216;compFiniScreenOptions&#8217;
build/anaglyph_options.c: At top level:
build/anaglyph_options.c:405: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;anaglyphOptionsInitDisplay&#8217;
build/anaglyph_options.c: In function &#8216;anaglyphOptionsFiniDisplay&#8217;:
build/anaglyph_options.c:435: error: &#8216;anaglyphPluginVTable&#8217; undeclared (first use in this function)
build/anaglyph_options.c:436: warning: &#8216;return&#8217; with a value, in function returning void
build/anaglyph_options.c:438: error: dereferencing pointer to incomplete type
build/anaglyph_options.c:440: warning: implicit declaration of function &#8216;freeScreenPrivateIndex&#8217;
build/anaglyph_options.c:440: warning: nested extern declaration of &#8216;freeScreenPrivateIndex&#8217;
build/anaglyph_options.c:442: warning: implicit declaration of function &#8216;compFiniDisplayOptions&#8217;
build/anaglyph_options.c:442: warning: nested extern declaration of &#8216;compFiniDisplayOptions&#8217;
build/anaglyph_options.c: At top level:
build/anaglyph_options.c:447: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;anaglyphOptionsInit&#8217;
build/anaglyph_options.c: In function &#8216;anaglyphOptionsFini&#8217;:
build/anaglyph_options.c:464: error: &#8216;anaglyphPluginVTable&#8217; undeclared (first use in this function)
build/anaglyph_options.c:465: warning: &#8216;return&#8217; with a value, in function returning void
build/anaglyph_options.c:468: warning: implicit declaration of function &#8216;freeDisplayPrivateIndex&#8217;
build/anaglyph_options.c:468: warning: nested extern declaration of &#8216;freeDisplayPrivateIndex&#8217;
build/anaglyph_options.c: At top level:
build/anaglyph_options.c:479: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
```


Hope that helps!

Andy

---

### Post by crhylove on 2008-08-01
Ok, that's all nice, but does somebody have .deb yet?  Thanks in advance!

---

### Post by soliac on 2008-09-14
I have attached the plugin. You just need to decompress it into your home directory & CompizConfig Settings Manager should recognise a new "Anaglyph" plugin. It is just two files inside a ".compiz" folder, so a deb seems overkill to me.

---

### Post by grafias3787 on 2008-10-18
All seems fine, I placed the files as should, I see the Anaglyph option in CompizConfig Settings Manager, but when I check the box to enable it, it de-selects by itself... is there something I'm missing?

---

### Post by Corianton on 2009-01-13
For those of you getting this error, please go to [http://forum.compiz-fusion.org/showthread.php?p=68054]("http://forum.compiz-fusion.org/showthread.php?p=68054"), assuming you are using ubuntu ibex 8.10.  The guide on that page worked for me.  If you are using an earlier version, go here: [http://forum.compiz-fusion.org/showthread.php?p=56851]("http://forum.compiz-fusion.org/showthread.php?p=56851").  Good luck

---

