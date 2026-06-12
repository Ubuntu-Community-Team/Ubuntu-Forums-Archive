---
title: "WebKit Nightly"
date: 2008-06-19
forum: General Help
---

### Post by sekinto on 2008-06-19
Okay, so I wanted to use the WebKit nightly so I downloaded the source from webkit.org. I compiled it and everything, does anyone know how to use it?

---

### Post by CalderCoalson on 2008-06-21
I'm attempting this right now.  Will keep you posted.

[EDIT 1]`
1. Install dependencies:
```
sudo apt-get install bison flex gperf libglib2.0-dev libicu-dev libpango1.0-dev libgtk2.0-dev libxml2-dev libcurl3-dev libsqlite3-dev libxslt-dev
```
2. 'cd' to WebKit source directory
3. Run ```
sudo ./autogen.sh
```
4. Run ```
sudo make install
```

DISCLAIMER: I'm posting this now, but my computer still isn't done installing.  It's been hard at work now for the last 15 minutes, and I suspect that it's going to succeed.  ;-)
[/EDIT]

[EDIT2]
Should have knocked on wood.  It didn't work: install failed with error 2.  More info later.
[/EDIT]

---

### Post by x1a4 on 2008-06-21
Hi,

What do you mean by wanting to use it?  WebKit is a web browser engine, used by developers who write web browsers.  Epiphany, for example, is slowly moving away from Gecko (Mozilla's engine) and is going to be using WebKit.  If you want to use WebKit, download Epiphany source and compile it to use WebKit instead of Gecko. 

If you're writing your own web browser simply call the WebKit APIs in your code.

---

### Post by CalderCoalson on 2008-06-21
I think you still need to have WebKit compiled and installed to run Epiphany, because of these instructions: [http://live.gnome.org/WebKitGtk](http://live.gnome.org/WebKitGtk)

---

### Post by CalderCoalson on 2008-06-21
I'm testing this now, but you can probably just install the libwebkitgtk1d package in the universe repository...

---

### Post by CalderCoalson on 2008-06-21
1. Get dependencies: ```
sudo apt-get install libwebkitgtk-dev libgnome-desktop-dev libdbus-glib-1-dev libglade2-dev

```

2. Download the Epiphany source: [http://ftp.gnome.org/pub/GNOME/sources/epiphany/2.22/epiphany-2.22.0.tar.bz2](http://ftp.gnome.org/pub/GNOME/sources/epiphany/2.22/epiphany-2.22.0.tar.bz2)

3. Unzip and cd to source dir

4. Configure: ```
./configure
```

5. Install: ```
sudo make && sudo make install
```



I hope that works for you, it didn't for me.  Apparently, you need to have installed webkit from source, because it failed saying dependency "webkit-1.0" was not met.  If I figure this out later, I'll make sure to post.

---

### Post by indecisive on 2008-08-06
When I try to compile webkit, I get these errors:

In file included from WebCore/plugins/gtk/PluginViewGtk.cpp:63:
WebCore/plugins/gtk/gtk2xtbin.h:44:27: error: X11/Intrinsic.h: No such file or directory
In file included from WebCore/plugins/gtk/PluginViewGtk.cpp:63:
WebCore/plugins/gtk/gtk2xtbin.h:78: error: ‘Widget’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:79: error: ‘Widget’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:104: error: ‘String’ has not been declared
WebCore/plugins/gtk/gtk2xtbin.h:113: error: ‘XtTranslations’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:114: error: ‘XtBoundActions’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:120: error: ‘Widget’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:121: error: ‘WidgetClass’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:122: error: ‘Widget’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:124: error: ‘Boolean’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:125: error: ‘XtCallbackList’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:126: error: ‘XtPointer’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:127: error: ‘Position’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:128: error: ‘Dimension’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:129: error: ‘Dimension’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:130: error: ‘Boolean’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:131: error: ‘Boolean’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:132: error: ‘Boolean’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:133: error: ‘XtEventTable’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:135: error: ‘XtTranslations’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:136: error: ‘Pixel’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:138: error: ‘WidgetList’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:139: error: ‘Cardinal’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:140: error: ‘String’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:144: error: ‘Cardinal’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:145: error: ‘Pixel’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:147: error: ‘Boolean’ does not name a type
WebCore/plugins/gtk/gtk2xtbin.h:148: error: ‘Boolean’ does not name a type
WebCore/plugins/gtk/PluginViewGtk.cpp: In member function ‘NPError WebCore::PluginView::getValue(NPNVariable, void*)’:
WebCore/plugins/gtk/PluginViewGtk.cpp:391: error: ‘XtDisplayToApplicationContext’ was not declared in this scope
make[1]: *** [WebCore/plugins/gtk/libWebCore_la-PluginViewGtk.lo] Error 1
make[1]: Leaving directory `/home/user1/WebKit-r35542'
make: *** [all] Error 2

Does anyone have similar problems?

---

### Post by indecisive on 2008-08-08
After downloading a newer nightly build (WebKit-r35636), I received the following error when running ./autogen.sh:

checking for XT... configure: error: Package requirements (xt) were not met:

No package 'xt' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XT_CFLAGS
and XT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

After searching the repositories, I found one package named xt (some program to show where on the globe a packet is sent with traceroute), which (evidently) was not what WebKit wanted.

Can anyone help?

---

### Post by indecisive on 2008-08-13
I have solved this problem by just updating to the latest WebKit svn repository.

---

### Post by lalitarora on 2009-03-25
Hi All,

I have built latest webkit source as available on SVN and able to launch GTKLauncher App. But it is not opening default url ("http://www.google.com").

To confirm source problem, I tried the building Nightly build source. But encountered the same problem.

Do I need to set proxy settings in the source or it is automatically taken from environment variable "http_proxy".

Please let me know if someone has encountered this problem or how to make it work.

Lalit

---

### Post by lalitarora on 2009-03-26
Dear All,

Please let me know how to enable libsoup as http_backend for latest nightly build WebKitt-r41944.

Regards,
Lalit Arora

---

### Post by mebunto on 2011-03-02
It's a bit late in the day but you needed the package libxt-dev I've just done it today ....

---

### Post by feel_IT on 2011-04-14
hi
i also want to get into webkit. please tell me what is next thing to do if you know.

---

