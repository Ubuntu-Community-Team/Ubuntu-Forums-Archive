---
title: "errors trying to install mplayerplug-in from source"
date: 2007-02-26
forum: General Help
---

### Post by noalternative on 2007-02-26
Ok, I am trying to follow the instructions in the [mplayerplugin for Opera howto.]("http://ubuntuforums.org/showthread.php?t=185547&page=2")


Anway, I didn't seem to get any errors during the actual compiling phase.  Here is the output.

> root@ubuntu:~/mplayerplug-in# ./configure --enable-x  --with-gecko-sdk=/usr/loca                                                             l/gecko-sdk1.6
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to run the C preprocessor... gcc -E
checking for X... no
checking for egrep... grep -E
checking for ANSI C header files... no
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking X11/Xlib.h usability... no
checking X11/Xlib.h presence... no
checking for X11/Xlib.h... no
checking X11/Intrinsic.h usability... no
checking X11/Intrinsic.h presence... no
checking for X11/Intrinsic.h... no
checking X11/StringDefs.h usability... no
checking X11/StringDefs.h presence... no
checking for X11/StringDefs.h... no
checking for sys/stat.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for an ANSI C-conforming const... yes
checking whether time.h and sys/time.h may both be included... yes
checking for pid_t... yes
checking for size_t... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... no
checking for unistd.h... (cached) yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... no
checking for vfork... no
checking for memset... no
checking for strcasecmp... no
checking for strchr... no
checking for strdup... no
checking for strncasecmp... no
checking for strstr... no
checking for strrchr... no
checking for snprintf... no
checking for mkfifo... no
checking for dup2... no
checking for gettimeofday... no
checking for strerror... no
checking for strtol... no
checking for memmem... no
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking return type of signal handlers... void
checking X11/xpm.h usability... no
checking X11/xpm.h presence... no
checking for X11/xpm.h... no
checking for DPMSQueryExtension in -lXdpms... no
checking for X11/extensions/dpms.h... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged

but when I entered "make" I seemed to run into problems.

> root@ubuntu:~/mplayerplug-in# make
g++ -c -Wall -g -O2   -g -O2  -DXP_UNIX -DMOZ_X11 -I/usr/local/gecko-sdk1.6 -I/u                                                             sr/local/gecko-sdk1.6/xpcom/include  -I/usr/local/gecko-sdk1.6/nspr/include -I/u                                                             sr/local/gecko-sdk1.6/string/include  -I/usr/local/gecko-sdk1.6/plugin/include -                                                             I/usr/local/gecko-sdk1.6/java/include -DGECKOSDK_ENABLED -Iinclude -fPIC -DXPCOM                                                             _GLUE -DMOZILLA_STRICT_API   -DX_ENABLED  Source/plugin.cpp
In file included from include/npplat.h:41,
                 from include/pluginbase.h:41,
                 from Source/plugin.h:53,
                 from Source/plugin.cpp:37:
/usr/local/gecko-sdk1.6/plugin/include/npapi.h:119:24: error: X11/Xlib.h: No suc                                                             h file or directory
/usr/local/gecko-sdk1.6/plugin/include/npapi.h:120:25: error: X11/Xutil.h: No su                                                             ch file or directory
In file included from Source/plugin.h:55,
                 from Source/plugin.cpp:37:
Source/plugin-setup.h:4:27: error: X11/Intrinsic.h: No such file or directory
Source/plugin-setup.h:5:28: error: X11/StringDefs.h: No such file or directory
/usr/local/gecko-sdk1.6/plugin/include/npapi.h:315: error: ISO C++ forbids decla                                                             ration of &#8216;Display&#8217; with no type
/usr/local/gecko-sdk1.6/plugin/include/npapi.h:315: error: expected &#8216;;&#8217; befo                                                             re &#8216;*&#8217; token
/usr/local/gecko-sdk1.6/plugin/include/npapi.h:316: error: ISO C++ forbids decla                                                             ration of &#8216;Visual&#8217; with no type
/usr/local/gecko-sdk1.6/plugin/include/npapi.h:316: error: expected &#8216;;&#8217; befo                                                             re &#8216;*&#8217; token
/usr/local/gecko-sdk1.6/plugin/include/npapi.h:317: error: &#8216;Colormap&#8217; does n                                                             ot name a type
/usr/local/gecko-sdk1.6/plugin/include/npapi.h:488: error: &#8216;XEvent&#8217; does not                                                              name a type
/usr/local/gecko-sdk1.6/plugin/include/npapi.h:498: error: &#8216;Region&#8217; does not                                                              name a type
/usr/local/gecko-sdk1.6/plugin/include/npapi.h:693: error: &#8216;NPRegion&#8217; has no                                                             t been declared
/usr/local/gecko-sdk1.6/plugin/include/npupp.h:1031: error: &#8216;NPRegion&#8217; has n                                                             ot been declared
include/pluginbase.h:55: warning: &#8216;class nsPluginInstanceBase&#8217; has virtual f                                                             unctions but non-virtual destructor
/usr/local/gecko-sdk1.6/xpcom/include/nsISupportsBase.h:80: warning: &#8216;class ns                                                             ISupports&#8217; has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:25: warning: &#8216;class nsIScriptableWMPPlugin                                                             &#8217; has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:120: warning: &#8216;class nsIScriptableMplayerP                                                             lugin&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk1.6/xpcom/include/nsIProgrammingLanguage.h:32: warning: &#8216;c                                                             lass nsIProgrammingLanguage&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk1.6/xpcom/include/nsIClassInfo.h:33: warning: &#8216;class nsICl                                                             
assInfo&#8217; has virtual functions but non-virtual destructor
Source/nsScriptablePeer.h:56: warning: &#8216;class nsClassInfoMixin&#8217; has virtual                                                              functions but non-virtual destructor
Source/plugin-setup.h:109: error: &#8216;Widget&#8217; does not name a type
Source/plugin-setup.h:169: error: variable or field &#8216;DrawUI&#8217; declared void
Source/plugin-setup.h:169: error: &#8216;Widget&#8217; was not declared in this scope
Source/plugin-setup.h:169: error: expected primary-expression before &#8216;*&#8217; tok                                                             en
Source/plugin-setup.h:169: error: &#8216;instance&#8217; was not declared in this scope
Source/plugin-setup.h:169: error: expected primary-expression before &#8216;char&#8217;
Source/plugin-setup.h:170: error: expected primary-expression before &#8216;int&#8217;
Source/plugin-setup.h:170: error: expected primary-expression before &#8216;int&#8217;
Source/plugin-setup.h:170: error: initializer expression list treated as compoun                                                             d expression
Source/plugin-setup.h:171: warning: &#8216;FreeUI&#8217; initialized and declared &#8216;ext                                                             ern&#8217;
Source/plugin-setup.h:171: error: variable or field &#8216;FreeUI&#8217; declared void
Source/plugin-setup.h:171: error: &#8216;Display&#8217; was not declared in this scope
Source/plugin-setup.h:171: error: &#8216;dpy&#8217; was not declared in this scope
Source/plugin-setup.h:171: error: expected primary-expression before &#8216;*&#8217; tok                                                             en
Source/plugin-setup.h:171: error: &#8216;instance&#8217; was not declared in this scope
Source/plugin-setup.h:171: error: initializer expression list treated as compoun                                                             d expression
Source/plugin-setup.h:172: warning: &#8216;RedrawCB&#8217; initialized and declared &#8216;e                                                             xtern&#8217;
Source/plugin-setup.h:172: error: variable or field &#8216;RedrawCB&#8217; declared void
Source/plugin-setup.h:172: error: &#8216;Widget&#8217; was not declared in this scope
Source/plugin-setup.h:172: error: &#8216;XtPointer&#8217; was not declared in this scope
Source/plugin-setup.h:173: error: &#8216;XtPointer&#8217; was not declared in this scope
Source/plugin-setup.h:173: error: initializer expression list treated as compoun                                                             d expression
Source/plugin-setup.h:205: error: &#8216;XEvent&#8217; has not been declared
Source/plugin.h:158: error: &#8216;Window&#8217; does not name a type
Source/plugin.h:159: error: &#8216;Window&#8217; does not name a type
Source/plugin.h:160: error: ISO C++ forbids declaration of &#8216;Display&#8217; with no                                                              type
Source/plugin.h:160: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
Source/plugin.h:161: error: &#8216;Widget&#8217; does not name a type
Source/plugin.h:268: error: ISO C++ forbids declaration of &#8216;XFontStruct&#8217; wit                                                             h no type
Source/plugin.h:268: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
Source/plugin.h:269: error: &#8216;Pixmap&#8217; does not name a type
Source/plugin.h:270: error: &#8216;Pixmap&#8217; does not name a type
Source/plugin.h:271: error: &#8216;Pixmap&#8217; does not name a type
Source/plugin.h:272: error: &#8216;Pixmap&#8217; does not name a type
Source/plugin.h:273: error: &#8216;Pixmap&#8217; does not name a type
Source/plugin.h:274: error: &#8216;Pixmap&#8217; does not name a type
Source/plugin.h:275: error: &#8216;Pixmap&#8217; does not name a type
Source/plugin.h:276: error: &#8216;Pixmap&#8217; does not name a type
Source/plugin.h:277: error: &#8216;Pixmap&#8217; does not name a type
Source/plugin.h:278: error: &#8216;Pixmap&#8217; does not name a type
/usr/local/gecko-sdk1.6/xpcom/include/nsIServiceManager.h:40: warning: &#8216;class                                                              nsIServiceManager&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk1.6/xpcom/include/nsIMemory.h:54: warning: &#8216;class nsIMemor                                                             y&#8217; has virtual functions but non-virtual destructor
Source/plugin.cpp: In constructor &#8216;nsPluginInstance::nsPluginInstance(NPP_t*)                                                             :
Source/plugin.cpp:187: error: &#8216;widget&#8217; was not declared in this scope
Source/plugin.cpp:188: error: &#8216;display&#8217; was not declared in this scope
Source/plugin.cpp:189: error: &#8216;window&#8217; was not declared in this scope
Source/plugin.cpp:190: error: &#8216;player_window&#8217; was not declared in this scope
Source/plugin.cpp:226: error: &#8216;font&#8217; was not declared in this scope
Source/plugin.cpp:227: error: &#8216;logo&#8217; was not declared in this scope
Source/plugin.cpp:227: error: &#8216;Pixmap&#8217; was not declared in this scope
Source/plugin.cpp:227: error: expected `;' before &#8216;__null&#8217;
Source/plugin.cpp:228: error: &#8216;logomask&#8217; was not declared in this scope
Source/plugin.cpp:228: error: expected `;' before &#8216;__null&#8217;
Source/plugin.cpp:229: error: &#8216;progress_left&#8217; was not declared in this scope
Source/plugin.cpp:229: error: expected `;' before &#8216;__null&#8217;
Source/plugin.cpp:230: error: &#8216;progress_leftmask&#8217; was not declared in this s                                                             cope
Source/plugin.cpp:230: error: expected `;' before &#8216;__null&#8217;
Source/plugin.cpp:231: error: &#8216;progress_middle&#8217; was not declared in this sco                                                             pe
Source/plugin.cpp:231: error: expected `;' before &#8216;__null&#8217;
Source/plugin.cpp:232: error: &#8216;progress_middlemask&#8217; was not declared in this                                                              scope
Source/plugin.cpp:232: error: expected `;' before &#8216;__null&#8217;
Source/plugin.cpp:233: error: &#8216;progress_right&#8217; was not declared in this scop                                                             e
Source/plugin.cpp:233: error: expected `;' before &#8216;__null&#8217;
Source/plugin.cpp:234: error: &#8216;progress_rightmask&#8217; was not declared in this                                                              scope
Source/plugin.cpp:234: error: expected `;' before &#8216;__null&#8217;
Source/plugin.cpp:235: error: &#8216;progress_fill&#8217; was not declared in this scope
Source/plugin.cpp:235: error: expected `;' before &#8216;__null&#8217;
Source/plugin.cpp:236: error: &#8216;progress_fillmask&#8217; was not declared in this s                                                             cope
Source/plugin.cpp:236: error: expected `;' before &#8216;__null&#8217;
Source/plugin.cpp: In member function &#8216;virtual void nsPluginInstance::shut()                                                             :
Source/plugin.cpp:327: error: &#8216;Display&#8217; was not declared in this scope
Source/plugin.cpp:327: error: expected primary-expression before &#8216;)&#8217; token
Source/plugin.cpp:327: error: &#8216;FreeUI&#8217; cannot be used as a function
Source/plugin.cpp: In member function &#8216;virtual NPError nsPluginInstance::SetWi                                                             ndow(NPWindow*)&#8217;:
Source/plugin.cpp:561: error: &#8216;GC&#8217; was not declared in this scope
Source/plugin.cpp:561: error: expected `;' before &#8216;black_gc&#8217;
Source/plugin.cpp:562: error: &#8216;XGCValues&#8217; was not declared in this scope
Source/plugin.cpp:562: error: expected `;' before &#8216;values&#8217;
Source/plugin.cpp:582: error: &#8216;Window&#8217; was not declared in this scope
Source/plugin.cpp:582: error: expected `)' before &#8216;window&#8217;
Source/plugin.cpp:585: error: &#8216;window&#8217; was not declared in this scope
Source/plugin.cpp:593: error: &#8216;values&#8217; was not declared in this scope
Source/plugin.cpp:594: error: &#8216;struct NPSetWindowCallbackStruct&#8217; has no memb                                                             er named &#8216;display&#8217;
Source/plugin.cpp:594: error: &#8216;struct NPSetWindowCallbackStruct&#8217; has no memb                                                             er named &#8216;display&#8217;
Source/plugin.cpp:594: error: &#8216;DefaultScreen&#8217; was not declared in this scope
Source/plugin.cpp:594: error: &#8216;BlackPixel&#8217; was not declared in this scope
Source/plugin.cpp:595: error: &#8216;black_gc&#8217; was not declared in this scope
Source/plugin.cpp:596: error: &#8216;struct NPSetWindowCallbackStruct&#8217; has no memb                                                             er named &#8216;display&#8217;
Source/plugin.cpp:596: error: &#8216;Window&#8217; was not declared in this scope
Source/plugin.cpp:596: error: &#8216;GCForeground&#8217; was not declared in this scope
Source/plugin.cpp:597: error: &#8216;XCreateGC&#8217; was not declared in this scope
Source/plugin.cpp:601: error: &#8216;struct NPSetWindowCallbackStruct&#8217; has no memb                                                             er named &#8216;display&#8217;
Source/plugin.cpp:601: error: expected `)' before &#8216;aWindow&#8217;
Source/plugin.cpp:602: error: &#8216;XDrawString&#8217; was not declared in this scope
Source/plugin.cpp:603: error: &#8216;struct NPSetWindowCallbackStruct&#8217; has no memb                                                             er named &#8216;display&#8217;
Source/plugin.cpp:603: error: &#8216;XFreeGC&#8217; was not declared in this scope
Source/plugin.cpp:616: error: &#8216;widget&#8217; was not declared in this scope
Source/plugin.cpp:617: error: &#8216;Display&#8217; was not declared in this scope
Source/plugin.cpp:617: error: expected primary-expression before &#8216;)&#8217; token
Source/plugin.cpp:618: error: &#8216;Window&#8217; was not declared in this scope
Source/plugin.cpp:618: error: &#8216;XtWindowToWidget&#8217; was not declared in this sc                                                             ope
Source/plugin.cpp:620: error: &#8216;ExposureMask&#8217; was not declared in this scope
Source/plugin.cpp:621: error: &#8216;XtEventHandler&#8217; was not declared in this scop                                                             e
Source/plugin.cpp:621: error: &#8216;XtAddEventHandler&#8217; was not declared in this s                                                             cope
Source/plugin.cpp:623: error: &#8216;display&#8217; was not declared in this scope
Source/plugin.cpp:623: error: &#8216;struct NPSetWindowCallbackStruct&#8217; has no memb                                                             er named &#8216;display&#8217;
Source/plugin.cpp:627: error: &#8216;window&#8217; was not declared in this scope
Source/plugin.cpp:627: error: expected `;' before &#8216;aWindow&#8217;
Source/plugin.cpp: In member function &#8216;virtual NPError nsPluginInstance::DestroyStream(NPStream*, NPError)&#8217;:
Source/plugin.cpp:1121: error: &#8216;widget&#8217; was not declared in this scope
Source/plugin.cpp:1121: error: &#8216;DrawUI&#8217; cannot be used as a function
Source/plugin.cpp: In member function &#8216;virtual int32 nsPluginInstance::Write(N                                                             PStream*, int32, int32, void*)&#8217;:
Source/plugin.cpp:1498: error: &#8216;widget&#8217; was not declared in this scope
Source/plugin.cpp:1501: error: &#8216;DrawUI&#8217; cannot be used as a function
Source/plugin.cpp:1522: error: &#8216;widget&#8217; was not declared in this scope
Source/plugin.cpp:1525: error: &#8216;DrawUI&#8217; cannot be used as a function
make: *** [plugin.o] Error 1
root@ubuntu:~/mplayerplug-in# 

Any help on this?  I have never been able to compile anything and I sure wish Ubuntu would handle this problem with apt-get.

---

### Post by Maestro23 on 2007-02-26
.

---

### Post by noalternative on 2007-02-26
kick!:confused:

---

### Post by berserker on 2007-03-24
Do you have libxt-dev installed?

```
sudo apt-get install libxt-dev
```

HTH

---

### Post by gottferdamnt on 2007-07-19
> **berserker said:**
> Do you have libxt-dev installed?

```
sudo apt-get install libxt-dev
```

HTH

Thank berserker :)

---

### Post by nujnxrzkppmvoc on 2008-04-29
> **berserker said:**
> Do you have libxt-dev installed?

```
sudo apt-get install libxt-dev
```

HTH

Allah raz&#122;&#305; olsun hocam çok büyük yard&#100;&#305;m&#109;&#305;n dokundu ne desek azd&#100;&#305;r

If you didn't understand Turkish, I mean God bless you ;)

---

