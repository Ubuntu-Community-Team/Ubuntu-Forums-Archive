---
title: "mplayer plug-in for firefox"
date: 2007-02-01
forum: General Help
---

### Post by blacklobo on 2007-02-01
I am trying to install the mplayer plug-in on Ubuntu 6.10 for use in Firefox.  I was not able to find the mplayer plug-in for Firefox in the Repositories.  So I have been trying to install it from the source code.  I was able to do the ./configure but now the make is getting a bunch of errors.  Can someone point me in the right direction?  Below is the information I get when I run the make.



make
g++ -c -o plugin.o -Wall -g -O2   -g -O2  -DXP_UNIX -DMOZ_X11 -I/usr/include/firefox/java -I/usr/include/firefox/plugin -I/usr/include/firefox -I/usr/include/firefox/xpcom -I/usr/include/firefox/string -I/usr/include/firefox/nspr   -I/usr/include/firefox -Iinclude -fPIC  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DGTK_ENABLED   Source/plugin.cpp
In file included from Source/plugin.h:55,
                 from Source/plugin.cpp:37:
Source/plugin-setup.h:4:27: error: X11/Intrinsic.h: No such file or directory
Source/plugin-setup.h:5:28: error: X11/StringDefs.h: No such file or directory
include/pluginbase.h:55: warning: ‘class nsPluginInstanceBase’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsISupportsBase.h:80: warning: ‘class nsISupports’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsIProgrammingLanguage.h:32: warning: ‘class nsIProgrammingLanguage’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsIClassInfo.h:33: warning: ‘class nsIClassInfo’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:25: warning: ‘class nsIScriptableWMPPlugin’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:120: warning: ‘class nsIScriptableMplayerPlugin’ has virtual functions but non-virtual destructor
Source/nsScriptablePeer.h:56: warning: ‘class nsClassInfoMixin’ has virtual functions but non-virtual destructor
Source/plugin-setup.h:132: error: ‘Widget’ does not name a type
Source/plugin-setup.h:203: error: variable or field ‘DrawUI’ declared void
Source/plugin-setup.h:203: error: ‘Widget’ was not declared in this scope
Source/plugin-setup.h:203: error: expected primary-expression before ‘*’ token
Source/plugin-setup.h:203: error: ‘instance’ was not declared in this scope
Source/plugin-setup.h:203: error: expected primary-expression before ‘char’
Source/plugin-setup.h:204: error: expected primary-expression before ‘int’
Source/plugin-setup.h:204: error: expected primary-expression before ‘int’
Source/plugin-setup.h:204: error: initializer expression list treated as compound expression
Source/plugin-setup.h:206: warning: ‘RedrawCB’ initialized and declared ‘extern’
Source/plugin-setup.h:206: error: variable or field ‘RedrawCB’ declared void
Source/plugin-setup.h:206: error: ‘Widget’ was not declared in this scope
Source/plugin-setup.h:206: error: ‘XtPointer’ was not declared in this scope
Source/plugin-setup.h:207: error: ‘XtPointer’ was not declared in this scope
Source/plugin-setup.h:207: error: initializer expression list treated as compound expression
Source/plugin.h:173: error: ‘Widget’ does not name a type
/usr/include/firefox/nsIServiceManager.h:40: warning: ‘class nsIServiceManager’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsIMemory.h:58: warning: ‘class nsIMemory’ has virtual functions but non-virtual destructor
Source/plugin.cpp: In function ‘NPError NS_PluginInitialize()’:
Source/plugin.cpp:101: warning: dereferencing type-punned pointer will break strict-aliasing rules
Source/plugin.cpp: In constructor ‘nsPluginInstance::nsPluginInstance(NPP_t*)’:
Source/plugin.cpp:207: error: ‘widget’ was not declared in this scope
make: *** [plugin.o] Error 1

---

### Post by david_2001 on 2007-02-01
Here's the easiest and most straightforward answer ;-):  The package you need is called "mozilla-mplayer" and it's in the multiverse repository.

---

### Post by blacklobo on 2007-02-01
I tried installing that package but it looks like it was installed for the browser "Mozilla"  I know Firfox is based on Mozilla, however the package did not show up in the firefox add-ons.  That is why I am trying to install the source code. ...

---

### Post by blacklobo on 2007-02-02
I tried reinstalling the mplayer plug-in.  But I am still do not see it in Firefox as an addon.  I did a locate and found what I understand as all the files in the correct location I have copied them below.  Anyone have a thought as to what I am doing wrong?


/usr/lib/firefox/plugins/mplayerplug-in-gmp.xpt
/usr/lib/firefox/plugins/mplayerplug-in-gmp.so
/usr/lib/firefox/plugins/mplayerplug-in-rm.xpt
/usr/lib/firefox/plugins/mplayerplug-in-rm.so
/usr/lib/firefox/plugins/mplayerplug-in-qt.xpt
/usr/lib/firefox/plugins/mplayerplug-in-qt.so
/usr/lib/firefox/plugins/mplayerplug-in-wmp.xpt
/usr/lib/firefox/plugins/mplayerplug-in-wmp.so
/usr/lib/firefox/plugins/mplayerplug-in.xpt
/usr/lib/firefox/plugins/mplayerplug-in.so

---

### Post by nix4me on 2007-02-02
It is not a firefox addon.  It only pops up when you click a streaming media link.

nix4me

---

### Post by blacklobo on 2007-02-02
Okay then my follow up question is.  Any ideas why I cannot stream audio off a site that in there FAQs says:
"Question: How do I stream if I am a LINUX user?
Answer: You can download the mplayer plug-in for Firefox.
http://www.linux-sxs.org/multimedia/mplayermozplug.html"

---

### Post by david_2001 on 2007-02-02
> **blacklobo said:**
> I tried reinstalling the mplayer plug-in.  But I am still do not see it in Firefox as an addon.  I did a locate and found what I understand as all the files in the correct location I have copied them below.  Anyone have a thought as to what I am doing wrong?


/usr/lib/firefox/plugins/mplayerplug-in-gmp.xpt
/usr/lib/firefox/plugins/mplayerplug-in-gmp.so
[Cut]

There is a well known clash between the mplayer plugin and the totem plugin that is installed by default in Ubuntu.  If you type "about:plugins" (without the quotes) into firefox's location bar to bring up the installed plugins page you'll probably find entries for both and, if so, you'll be able to see that they both cover many of the same file types.  The easiest way to disable the totem plugin is to delete the links from /usr/lib/firefox/plugins:
> libtotem-basic-plugin.so
libtotem-basic-plugin.xpt
libtotem-complex-plugin.so
libtotem-complex-plugin.xpt
libtotem-gmp-plugin.so
libtotem-gmp-plugin.xpt
libtotem-mully-plugin.so
libtotem-mully-plugin.xpt
libtotem-narrowspace-plugin.so
libtotem-narrowspace-plugin.xpt
Is that FAQ you followed the one at [95.7 BEN FM]("http://www.957benfm.com/streaming.shtml")?  It links to installation instructions that will only work if mplayer was also compiled from source and all of the compilation dependencies are present.

---

### Post by blacklobo on 2007-02-02
Thank you, thank you, thank you.

Taking out the links to the totem plugin did the trick.

---

