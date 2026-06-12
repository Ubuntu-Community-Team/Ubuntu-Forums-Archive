---
title: "Install a latex-package?"
date: 2005-09-30
forum: General Help
---

### Post by Midget on 2005-09-30
Where do I put the files when I want to install a latex-package (wrapfig)?

---

### Post by Leif on 2005-10-01
here's how I do it :

- create a directory to store all your extra latex packages in, eg. /home/leif/texmf

- sudo emacs /etc/texmf/texmf.d/05TeXMF.cnf
- set TEXMFLOCAL=/home/leif/texmf, save & exit
- sudo update-texmf
- sudo texhash

if anybody knows of a simpler way, please tell !

---

### Post by Midget on 2005-10-01
[QUOTE=Leif]
- create a directory to store all your extra latex packages in, eg. /home/leif/texmf
- sudo emacs /etc/texmf/texmf.d/05TeXMF.cnf
- set TEXMFLOCAL=/home/leif/texmf, save & exit
- sudo update-texmf
- sudo texhash
[/QUOTE]

I have done all this, but I still get an error when I try to compile the .tex. It may be because I use the package wrong, but I'm not sure. I'll try to figure it out, and I'll let you know if I find a way to solve this.

---

### Post by Midget on 2005-10-01
[QUOTE=Midget]I have done all this, but I still get an error when I try to compile the .tex. It may be because I use the package wrong, but I'm not sure. I'll try to figure it out, and I'll let you know if I find a way to solve this.[/QUOTE]

And now it works. I forgot to define the package at the beginning of the .tex-file.

---

### Post by parktownprawn on 2005-10-01
[QUOTE=Leif]here's how I do it :
- create a directory to store all your extra latex packages in, eg. /home/leif/texmf
- sudo emacs /etc/texmf/texmf.d/05TeXMF.cnf
- set TEXMFLOCAL=/home/leif/texmf, save & exit
- sudo update-texmf
- sudo texhash
if anybody knows of a simpler way, please tell ![/QUOTE]
I think that just putting ```
export TEXINPUTS= ~/texmf:
```
in .bashrc should do the trick.
another way is just to put the file in /usr/local/share/texmf/
(which will also make the package globally available)  
and run texhash:
```

sudo mkdir -p  /usr/local/share/texmf/tex/latex/
sudo cp yourstyle.sty   /usr/local/share/texmf/tex/latex/
sudo texhash

```
see [http://wiki.ubuntu.com//LaTeX](http://wiki.ubuntu.com//LaTeX)

---

### Post by kolesarm on 2006-05-03
thanks a lot, the last option worked for me. i was quite conused, as i previously only used latex under ms windows

---

