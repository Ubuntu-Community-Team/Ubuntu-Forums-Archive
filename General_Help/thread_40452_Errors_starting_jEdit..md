---
title: "Errors starting jEdit."
date: 2005-06-09
forum: General Help
---

### Post by Goophy on 2005-06-09
When I try to run jEdit on this computer it just throws up some errors I really don't get.

```
[error] main: Exception in thread "main" 
[error] main: java.awt.AWTError: Cannot load AWT toolkit: gnu.awt.gtk.GtkToolkit not found in [file:/usr/share/jed
[error] main: it/jedit.jar, core:/]
[error] main:    at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.4.0.0)
[error] main:    at ja
[error] main: va.awt.Component.getToolkit() (/usr/lib/libgcj.so.4.0.0)
[error] main:    at java.awt.Component.getFontMetrics(jav
[error] main: a.awt.Font) (/usr/lib/libgcj.so.4.0.0)
[error] main:    at org.gjt.sp.jedit.gui.SplashScreen.SplashScreen() (Unkno
[error] main: wn Source)
[error] main:    at org.gjt.sp.jedit.GUIUtilities.showSplashScreen() (Unknown Source)
[error] main:    at org.gjt.sp.
[error] main: jedit.jEdit.main(java.lang.String[]) (Unknown Source)
```

Anyone know what to do with this?
It works on my laptop with the exact same ubuntu-setup as this computer.  :-|

---

### Post by Goophy on 2005-06-09
Gah, I just had to install JDK.
Typically easy problems.  :???:

---

### Post by TransmogriBenno on 2005-08-03
How did you install the SDK, exactly? Did you need to download it from Sun?

I would have assumed that since jEdit is available as a .deb (and thus can check dependencies, etc) it should work fine out of the box, but clearly this is not the case.

Why can't the gij RE use the GtkToolKit? It runs other Java programs just fine.

I'm rather confused...

---

