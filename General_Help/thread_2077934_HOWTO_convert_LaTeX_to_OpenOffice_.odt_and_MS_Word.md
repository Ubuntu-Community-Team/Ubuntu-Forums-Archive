---
title: "HOWTO convert LaTeX to OpenOffice .odt and MS Word .doc"
date: 2012-03-26
forum: General Help
---

### Post by gcordoba on 2012-03-26
Hi, Ubuntu 11.10 here.
I used the simplest way:
$> latex foo.tex
$> mk4ht foo.tex

It worked aparently fine. However, when I needed to split an equation using \begin{multline}
....
\end{multline}
the equation is not splited, despite the dvi version shows the correct spliting.

Does anyone have a tip to split equations that works in mk4ht?

Thanks

---

### Post by gcordoba on 2012-03-26
Hi, I found a workaround:

\begin{equation}
\begin{split}
....
\end{split}
\end{equation}

The only problem is that you need to edit the equation in LibreOffice in order to delete the numbering (# "(2)"}), otherwise you will have a double numbering for the same equation.

---

### Post by gcordoba on 2012-03-26
Btw, the resulting equation format is ugly.

---

### Post by seddonym on 2012-10-01
Here is an easy way to do it:
[http://linuxsagas.wordpress.com/2008/12/08/latex-to-openoffice/](http://linuxsagas.wordpress.com/2008/12/08/latex-to-openoffice/)

---

### Post by Chris_82 on 2012-10-29
On Ubuntu 12.04 a simple install of tex4ht with apt-get is enough.
dvipng will also be installed.

tex4ht package version is 20090611-1.1.
So far no issues.

---

