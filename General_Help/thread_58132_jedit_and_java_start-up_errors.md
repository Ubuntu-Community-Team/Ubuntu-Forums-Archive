---
title: "jedit and java start-up errors"
date: 2005-08-18
forum: General Help
---

### Post by amg on 2005-08-18
when trying to run jedit, i receive the following error:
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

It worked recently, earlier this day. THen while working with synaptic, i discovered that jedit was broken, and that synaptic wanted it removed, after deselecting it (so that synaptic didn't touch it, or so i thought), and updating synaptic, it decided to stop working.

any suggestions?

---

### Post by amg on 2005-08-18
oops, minutes later, i updated my version of java, and it worked, sorry for wasting your time peoples.

---

