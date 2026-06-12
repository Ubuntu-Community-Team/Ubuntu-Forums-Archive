---
title: "what is the different between emacs (X11) and emacs (GTK)"
date: 2008-03-28
forum: General Help
---

### Post by kelvin911 on 2008-03-28
what is the different between Emacs 21.4a (X11) and Emacs 22 (GTK) ??

Do I need to install both to have emacs installed?

---

### Post by lloyd_b on 2008-03-28
> **kelvin911 said:**
> what is the different between Emacs 21.4a (X11) and Emacs 22 (GTK) ??

Do I need to install both to have emacs installed?
 
Emacs X11 is written to run using the base X11 libraries - it doesn't require GTK (or QT, or any other special toolkit).  Emacs GTK *does* require the GTK libraries in order to work, and in exchange gains some functionality (for instance, GTK themes will affect Emacs GTK, but not Emac X11).

If you're using a Gnome based system such as Ubuntu, it's probably best to install the GTK version (Gnome uses GTK heavily).

It may turn out that Emacs GTK requires the Emacs X11 to be installed, but you shouldn't have to worry about it - if GTK depends on X11, then the package manager (Synaptic, Adept, apt-get, whatever) should sort it out for you.

Lloyd B.

---

