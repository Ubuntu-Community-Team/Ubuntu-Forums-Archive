---
title: "No French Accents"
date: 2008-01-04
forum: General Help
---

### Post by flonks on 2008-01-04
Hi all,

I surfed a lot, but my problems seems not to be covered by the other posts on this topic, so here we go:

I have problems with French accents in LaTeX files (.tex):

- I _CAN_ type French accents in the gnome apps and in vi (terminal) and my old files (created on a fedora core 4 system) are shown correctly
- Pdflatex only produces garbage when I compile these files
- When I view the same files with KDE apps (e.g. kile), I even see the garbage directly in the source

This is independent of my language settings, i.e. whether my desktop is in English (my preferred setting) or French. Also, it doesn't matter whether I set LANG to fr_FR.UTF-8 or en_US.UTF-8 or even plain old "C".

Here is the content of /etc/environment (with the Desktop set to French):

[chris ~]$ cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="fr_FR.UTF-8"
LANGUAGE="fr_FR:fr:en_GB:en"

The files are located on VFAT file system mounted with:
UUID=4355-42CC  /X-Change       vfat    defaults,utf8,umask=007,uid=chris,gid=1000 0       1

Any idea? Help is appreciated, thanks a lot :)

Christian

---

### Post by flonks on 2008-01-04
Sorry, seems that I posted too fast. With the help of friend (thanks Jean-Michel) I found the problems. Actually two problems:

My old files were still encoded in ISO-8859-1 and needed to be transcoded into UTF-8, which can be done with 

iconv --from-code ISO-8859-1 --to-code utf8 input.tex  > output.tex

This solves the display problem in the KDE apps. And the pdflatex problem can be solved by changing a package option in the .tex file:

\usepackage[utf8]{inputenc}

instead of

\usepackage[latin1]{inputenc}

Thanks anyway!

Christian

---

