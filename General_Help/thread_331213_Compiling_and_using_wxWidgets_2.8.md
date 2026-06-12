---
title: "Compiling and using wxWidgets 2.8"
date: 2007-01-04
forum: General Help
---

### Post by Prism on 2007-01-04
Since there is at least one known problem with wxWidgets 2.6 (a bug which cause aMule to [crash when a search tab is closed]("http://forum.amule.org/thread.php?threadid=11834&sid=9524f8415c0a67dd953bcdf7a6ef9d6a")), and because I have some other problems and I suspect wxWidgets to be the faulty component, I decided to use the recently released version 2.8.

I looked for an official repository, but in the wxWidgets site the only Edgy repo is for amd64. Therefore, I had no choice but compiling it myself. I downloaded the source code, and executed:
```
./configure --prefix=/usr --with-gtk --enable-unicode --disable-compat24 --enable-optimise
make
sudo make install
sudo ldconfig
```

And nothing seems to have changed. aMule still crashes, for example.
[FONT="Courier New"]sudo ldconfig -v | grep wx[/FONT] shows this, meaning that not everything has been updated.

```
ldconfig: Can't stat /lib64: No such file or directory
        libwx_gtk2u_richtext-2.8.so.0 -> libwx_gtk2u_richtext-2.8.so.0.0.0
        libwx_gtk2u_aui-2.8.so.0 -> libwx_gtk2u_aui-2.8.so.0.0.0
        libwx_gtk2u_xrc-2.8.so.0 -> libwx_gtk2u_xrc-2.8.so.0.0.0
        libwx_baseu_xml-2.8.so.0 -> libwx_baseu_xml-2.8.so.0.0.0
        libwx_gtk2u_qa-2.8.so.0 -> libwx_gtk2u_qa-2.8.so.0.0.0
        libwx_gtk2u_html-2.8.so.0 -> libwx_gtk2u_html-2.8.so.0.0.0
        libwx_gtk2u_adv-2.8.so.0 -> libwx_gtk2u_adv-2.8.so.0.0.0
        libwx_gtk2u_core-2.8.so.0 -> libwx_gtk2u_core-2.8.so.0.0.0
        libwx_baseu_net-2.8.so.0 -> libwx_baseu_net-2.8.so.0.0.0
        libwx_baseu-2.8.so.0 -> libwx_baseu-2.8.so.0.0.0
        libwwwxml.so.0 -> libwwwxml.so.0.1.0
        libwx_gtk_xrc-2.4.so.1 -> libwx_gtk_xrc-2.4.so.1.0.0
        libwx_gtk_stc-2.4.so.1 -> libwx_gtk_stc-2.4.so.1.0.0
        libwx_gtk_plot-2.4.so.1 -> libwx_gtk_plot-2.4.so.1.0.0
        libwx_gtk_ogl-2.4.so.1 -> libwx_gtk_ogl-2.4.so.1.0.0
        libwx_gtk_net-2.4.so.1 -> libwx_gtk_net-2.4.so.1.0.0
        libwx_gtk_mmedia-2.4.so.1 -> libwx_gtk_mmedia-2.4.so.1.0.0
        libwx_gtk_gizmos-2.4.so.1 -> libwx_gtk_gizmos-2.4.so.1.0.0
        libwx_gtk_fl-2.4.so.1 -> libwx_gtk_fl-2.4.so.1.0.0
        libwx_gtk_dcsvg-2.4.so.1 -> libwx_gtk_dcsvg-2.4.so.1.0.0
        libwx_gtk_canvas-2.4.so.1 -> libwx_gtk_canvas-2.4.so.1.0.0
        libwx_gtk2u_mmedia-2.6.so.0 -> libwx_gtk2u_mmedia-2.6.so.0.3.1
        libwx_gtk-2.4.so.1 -> libwx_gtk-2.4.so.1.0.0
        libwx_gtk_gl-2.4.so.1 -> libwx_gtk_gl-2.4.so.1.0.0
        libwx_gtk2u_xrc-2.6.so.0 -> libwx_gtk2u_xrc-2.6.so.0.3.1
        libwx_gtk2u_svg-2.6.so.0 -> libwx_gtk2u_svg-2.6.so.0.3.1
        libwx_gtk2u_stc-2.6.so.0 -> libwx_gtk2u_stc-2.6.so.0.3.1
        libwx_gtk2u_qa-2.6.so.0 -> libwx_gtk2u_qa-2.6.so.0.3.1
        libwx_gtk2u_plot-2.6.so.0 -> libwx_gtk2u_plot-2.6.so.0.3.1
        libwx_gtk2u_ogl-2.6.so.0 -> libwx_gtk2u_ogl-2.6.so.0.3.1
        libwx_gtk2u_media-2.6.so.0 -> libwx_gtk2u_media-2.6.so.0.3.1
        libwx_gtk2u_html-2.6.so.0 -> libwx_gtk2u_html-2.6.so.0.3.1
        libwx_gtk2u_gl-2.6.so.0 -> libwx_gtk2u_gl-2.6.so.0.3.1
        libwx_gtk2u_gizmos_xrc-2.6.so.0 -> libwx_gtk2u_gizmos_xrc-2.6.so.0.3.1
        libwx_gtk2u_gizmos-2.6.so.0 -> libwx_gtk2u_gizmos-2.6.so.0.3.1
        libwx_gtk2u_fl-2.6.so.0 -> libwx_gtk2u_fl-2.6.so.0.3.1
        libwx_gtk2u_deprecated-2.6.so.0 -> libwx_gtk2u_deprecated-2.6.so.0.3.1
        libwx_gtk2u_core-2.6.so.0 -> libwx_gtk2u_core-2.6.so.0.3.1
        libwx_gtk2u_animate-2.6.so.0 -> libwx_gtk2u_animate-2.6.so.0.3.1
        libwx_gtk2u_adv-2.6.so.0 -> libwx_gtk2u_adv-2.6.so.0.3.1
        libwx_baseu_xml-2.6.so.0 -> libwx_baseu_xml-2.6.so.0.3.1
        libwx_baseu_net-2.6.so.0 -> libwx_baseu_net-2.6.so.0.3.1
        libwx_baseu-2.6.so.0 -> libwx_baseu-2.6.so.0.3.1
```

What did I miss here? How should I compile wxWidgets correctly?

Thanks in advance. :)

---

### Post by Prism on 2007-01-05
Anyone please?

---

### Post by heldal on 2007-01-08
You have probably compiled and installed the new libraries correctly. It's just that old applications may link to a specific version. Use "ldd <binary-program>" to check. In the case of aMule there's a patch for version 2.1.3 that is necessary to make it compile and run with wxwidgets 2.8.x (see [www.amule.org)](www.amule.org)). I.e. you must also compile and link aMule to the new libraries to make it work.

IMHO it is also a bad idea to replace or install new versions of libraries in /usr unless the version supplied with the distribution can be removed. In this case it is better to use /usr/local (or other alternative) as install-prefix for the locally compiled wxwidgets, as well as other applications built on top of this version of the library.

//per

---

### Post by ivangotoy on 2007-01-21
wxwidgets ,no matter what release is, doesn't work fine when more than one version is installed (i will try to gather essential info from sites i used and they worked for my unmoded ubuntu 6.10 edgy)
 
1. checking for double wxWidgets installation :
ls -l /usr/bin/wx*
ls -l /usr/local/bin/wx*

only one line should point to wx contents

2. "make uninstall" command in sources directory didn't always helped me remove wxwidgets so : forcing the wxwidgets removal is done with : 

rm -f  /usr/bin/wx*
rm -rf /usr/lib/wx
rm -f  /usr/lib/libwx*
rm -f  /usr/local/bin/wx*
rm -rf /usr/local/lib/wx
rm -f  /usr/local/lib/libwx*
ldconfig

wxWidgets reminds after installation that ldconfig as root should be executed 
i declare amule stopped the search tab crash after wxgtk 2.8 upgrade

---

