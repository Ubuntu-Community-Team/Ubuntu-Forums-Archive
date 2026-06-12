---
title: "teTeX: ä and ö unavailable in encoding T1"
date: 2005-08-09
forum: General Help
---

### Post by sento on 2005-08-09
Hey!

Why do I get this error message when I try to convert my tex-file, which contains ä and ö letters, to pdf-file using pdflatex:
! LaTeX Error: Command \textcurrency unavailable in encoding T1.

I'm using packages:
\usepackage[latin1]{inputenc}
\usepackage[T1]{fontenc}
\usepackage{times}
\usepackage[finnish]{babel}

When I use MikTex on WindowsXP or teTeX on Fedora Core3 to convert the same file to pdf, I get no error messages.

Thanks!

---

### Post by GTvulse on 2005-08-09
[QUOTE=sento]Hey!

Why do I get this error message when I try to convert my tex-file, which contains ä and ö letters, to pdf-file using pdflatex:
! LaTeX Error: Command \textcurrency unavailable in encoding T1.

I'm using packages:
\usepackage[latin1]{inputenc}
\usepackage[T1]{fontenc}
\usepackage{times}
\usepackage[finnish]{babel}

When I use MikTex on WindowsXP or teTeX on Fedora Core3 to convert the same file to pdf, I get no error messages.

Thanks![/QUOTE]

Be aware that Ubuntu uses UTF-8 encodings by default. You'll need to convert your file to latin1 encoding or use the utf8 inputenc driver, which AFAIK, was  experimental last time I checked (I haven't used  LaTeX for a couple of years already, so take my words with a grain of salt).

You can have your text editor make the encoding conversion automatically and either vim or Emacs/Xemacs with integrated Mule will do it for you. Or you can use a conversion utility such as iconv or recode. In the case of a text editor, doing it with vim is almost trivial. Emacs and Xemacs can be a pain in the caboose.

---

### Post by sento on 2005-08-09
Encoding conversion from UTF-8 to latin1 solved the problem. Thanks!

---

