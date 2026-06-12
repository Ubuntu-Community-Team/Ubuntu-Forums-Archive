---
title: "GFax"
date: 2005-08-31
forum: General Help
---

### Post by gdcondor on 2005-08-31
Hi,

I've an hylafax server on another computer and i'm trying to install GFax under Hoary.
In universe there is Gfax 0.4 which is a really old version :(

I've tried to install Gfax 0.7 from the deb downloaded on gfax.cowlug.org but there is a lot of dependancy problem with mono :( :(

```
Dépaquetage de gfax (à partir de gfax_0.7.3-1_i386.deb) ...
dpkg : des problèmes de dépendances empêchent la configuration de gfax :
 gfax dépend de mono-jit (>= 1.0.5) | mono-mint (>= 1.0.5) ; cependant :
  Paquet mono-jit n'est pas installé.
  Paquet mono-mint n'est pas installé.
 gfax dépend de libgconf-cil (>= 1.0.4) ; cependant :
  Paquet libgconf-cil n'est pas installé.
 gfax dépend de libglib-cil (>= 1.0.4) ; cependant :
  Paquet libglib-cil n'est pas installé.
 gfax dépend de libgnome-cil (>= 1.0.4) ; cependant :
  Paquet libgnome-cil n'est pas installé.
 gfax dépend de libgtk-cil (>= 1.0.4) ; cependant :
  Paquet libgtk-cil n'est pas installé.
 gfax dépend de mono-assemblies-base (>= 1.0.5) ; cependant :
  Paquet mono-assemblies-base n'est pas installé.
 gfax dépend de efax | hylafax-server ; cependant :
  Paquet efax n'est pas installé.
  Paquet hylafax-server n'est pas installé.
dpkg : erreur de traitement de gfax (--install) :
 problèmes de dépendances - laissé non configuré
Des erreurs ont été rencontrées pendant l'exécution :
 gfax
``` 

Any idea ??? Or maybe another facsimile client compatible with hylafax ? (But a client in GTK not Tk or QT ...)

Thanks for your help !!

---

