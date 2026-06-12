---
title: "Missing pgfopts for latex"
date: 2012-11-16
forum: General Help
---

### Post by LukeusMaximus on 2012-11-16
pdflatex reports that I am missing pgfopts.sty but I have so far failed to install it manually. I've tried downloading pgfopts.zip, extracting it in the /usr/share/texmf folder and then running texhash (and then again with root). I've tried using "yum install texlive-pgfopts" but it doesn't exist. I've tried creating a /home/<user>/texmf directory and unzipping the pgfopts.zip in there but texhash doesn't look in that directory.

Any ideas on how I can get this to work?

---

### Post by Impavidus on 2012-11-16
According to the README, just unpacking the zip only works if you have the pgfopts.tds.zip, which contains all files in the correct directories to get it working. With the file you downloaded it's slightly more complicated, but not too difficult. Unfortunately there're no detailed installation instructions, but this standard way usually works.

Extract the zip file in whatever directory you like (your home directory for example). It will create a directory with the files```
pgfopts.dtx
pgfopts.ins     
pgfopts.pdf
README
```Go into that directory and type```
latex pgfopts.ins
```This will produce the file pgfopts.sty and a log file. Copy the .sty file to a place where LaTeX can find it. I'd suggest /usr/local/share/texmf/tex/latex/pgfopts/ (you'll need sudo for this). It's customary to put LaTeX packages that are not installed as Ubuntu packages somewhere in /usr/local/share/texmf, which is in the default path used by LaTeX. Then run```
sudo texhash
``` and it should work.

Of course, you can remove the files you put in /usr/share/texmf on your first installation attempt.

---

### Post by LukeusMaximus on 2012-11-16
This works! thanks.

---

