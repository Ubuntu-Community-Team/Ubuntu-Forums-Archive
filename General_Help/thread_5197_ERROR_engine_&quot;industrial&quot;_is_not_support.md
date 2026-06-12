---
title: "ERROR: engine &quot;industrial&quot; is not supported"
date: 2004-11-16
forum: General Help
---

### Post by viorel on 2004-11-16
I get the following error when launching java programs (like the JBuilder installer or Weka):```
/usr/share/Themes/Human/gtk-2.0/gtkrc:42 Engine 'industrial' is not supported,ignoring
/usr/share/Themes/Human/gtk-2.0/gtkrc:50 Engine 'industrial' is not supported,ignoring
/usr/share/Themes/Human/gtk-2.0/gtkrc:115 Engine 'industrial' is not supported,ignoring
```
Does anyone know why that is and what I could do to fix it?
Thanks!

---

### Post by randy on 2004-11-17
I'm pretty sure that would require adding the code to support themes in the Java Look and Feel.

---

### Post by viorel on 2004-11-17
[QUOTE=randy]I'm pretty sure that would require adding the code to support themes in the Java Look and Feel.[/QUOTE]
 And does anyone have any idea how to do that?

---

### Post by randy on 2004-11-17
I don't know exactly where to start but all my friends who use swing say that writing a look and feel is extremely difficult and time consuming.  You'd probably be able to start by getting the java source code under the new license and start hacking on that.  I'm not sure what the restrictions on the license are though.  Try use SWT, I'm finding it much easier to work with than awt/swing.

---

### Post by viorel on 2004-11-17
That sounds like a little too much work for getting an installer to work. Maybe there is a way of bypassing that? Or using another engine instead of "industrial"?

---

### Post by randy on 2004-11-17
I've never had a program that failed to start because of that, but most of the stuff that I did had a failsafe look and feel.  For me they only appeared as warnings.  You could try changing your them to the default gnome desktop theme.  That might help the problem.

---

### Post by viorel on 2004-11-17
Thanks! I'll see if that works...

---

### Post by TravisNewman on 2004-11-17
You might try installing gtk2-engines-industrial and gtk-engines-industrial from synaptic or apt-get

---

### Post by piedamaro on 2004-11-17
[QUOTE=panickedthumb]You might try installing gtk2-engines-industrial and gtk-engines-industrial from synaptic or apt-get[/QUOTE]
 This is for java look'n feel, I think it supports few engines like pixmap and bluecurve.

If you want something totally integrated with gnome, try java-gnome.

---

### Post by viorel on 2004-11-18
You mean I should just launch the installer with java-gnome?

EDIT: I'll download and install java-gnome  :)

---

### Post by randy on 2004-11-19
Installing java-gnome definitely won't help your problem, even if you can get it to install.  (I vaguely remember there being serious issues on ubuntu with an install from source.  It's in the java-gnome list archives) java-gnome is a programming api, not a program that will magically convert swing guis to gnome guis.

---

