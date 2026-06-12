---
title: "Miktex packages trouble"
date: 2007-11-27
forum: General Help
---

### Post by elektronaut on 2007-11-27
[COLOR="Blue"][EDIT] My fault, I forgot to execute *sudo mktexlsr*. Admin, please delete this thread.[/COLOR]

Hi,

I've been installing miktex-tools on Edgy because I need some special package and I don't know how to locate it in TexLive. It is successfully installed as you can see:
```
me@mycomputer:~$ mpm --print-package-info=classicthesis|grep sty
title: A thesis style as homage to "The Elements of Typographic Style"
/usr/local/share/texmf/tex/latex/classicthesis/classicthesis-ldpkg.sty
/usr/local/share/texmf/tex/latex/classicthesis/classicthesis.sty
```
But *latex * doesn't find it, when it is invoked by Kile. What can I do?

---

