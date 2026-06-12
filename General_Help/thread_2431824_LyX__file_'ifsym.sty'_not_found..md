---
title: "LyX : file 'ifsym.sty' not found."
date: 2019-11-22
forum: General Help
---

### Post by j-lavau on 2019-11-22
Trying to convert the work into ubuntu, I state that the LyX packet seems uncomplete.
ubuntu 19.4, Lyx 2.3.2.
Error messages when I try to compile into pdf :
LaTeX Error: Option clash for package tipa.
 LaTeX Error: File `ifsym.sty' not found.
 LaTeX Error: Option clash for package tipa.
 LaTeX Error: File `ifsym.sty' not found.

Please help to clarify the problem !

Lavau

J'utilise LyX, là sous Ubuntu 19.4
 LyX y est disponible, version 2.3.2.
 Pour travailler la 9e édition de ce manuel
 [http://www.lulu.com/shop/http://www.lulu.com/shop/jacques-lavau](http://www.lulu.com/shop/http://www.lulu.com/shop/jacques-lavau)
 /microphysique-quantique-transactionnelle-principes-et-
 applications/paperback/product-24093451.html
 je tente ici une compilation en pdf, et le message d'erreur est :
 LaTeX Error: Option clash for package tipa.
 LaTeX Error: File `ifsym.sty' not found.
 LaTeX Error: Option clash for package tipa.
 LaTeX Error: File `ifsym.sty' not found.

 Le livre est déclaré en American Mathematical Society (AMS) Book.
 Je présume que le package sous Ubuntu est incomplet.

 Merci d'avance de vos avis,

Lavau

---

### Post by Impavidus on 2019-11-22
Has the Ubuntu package **texlive-fonts-extra** been installed? It's the ubuntu package that includes a lot of extra font stuff for TeX & friends, like LyX. It includes the LaTeX package ifsym. You can install it from the repositories using Ubuntu Software, Synaptic, apt or whatever you like.

---

