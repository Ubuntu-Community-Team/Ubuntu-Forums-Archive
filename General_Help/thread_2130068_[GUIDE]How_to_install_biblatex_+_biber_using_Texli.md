---
title: "[GUIDE]How to install biblatex + biber using Texlive"
date: 2013-03-28
forum: General Help
---

### Post by Kotrfa on 2013-03-28
Hi.

I had horrible 3 days when I had problems with new versions of texlive, biber, biblatex on ubuntu (12.10, but it should work everywhere). So here is short guide how to make it work. Maybe it will save some time to somebody.

First thing which is good to know - _**Texlive from official ubuntu repository is rubbish**_.  It lacks some default features as is "tlmgr" (texlive package manager), VERY old versions of packages (for example - biblatex v. 1.7-1 and biber 0.9.9, which are 2 years old).

Biber is back-end for biblatex similarly to bibtex, but bibtex is very old thing - its development stopped at 1996. So today is best thing to use biber, which is much better in all dimensions (like UTF8, better styles...) and biblatex developers also recommend to use biber.

Problem is that there are just some version of these two which are working together  For example - biber 0.9.9 is working with biblatex 1.7 and lower, but biber 1.0 needs biblatex 2.0 and newer etc. Last version of biber 1.5 needs biblatex at least 2.3. 

So here is the solution:

0. Uninstal texlive if you installed it in the past using official repositories (run in terminal: sudo apt-get autoremove texlive texlive-data etc.)

1. Download official last version of texlive, I would recommend you this installation [http://www.tug.org/texlive/acquire-netinstall.html](http://www.tug.org/texlive/acquire-netinstall.html) . You run install script and just press "i" (it takes some time...). All you need you can find in readme file.

2. Now you have full version of texlive with all it's features. Dont forget that you need set the $PATH (you can find this information in readme file in the downloaded texlive package). For those who don't know how to do it, you can google it or for ex. [here]("http://www.cyberciti.biz/faq/unix-linux-adding-path/") . Very shortly: you have to put something like that (it depends on your default shell) "[COLOR=#111111][FONT=Consolas]export PATH=$PATH:[/FONT][/COLOR]/usr/local/texlive/2012/bin/x86_64-linux" to your .bshrc (end its equivalent). I use ZSH, so I put this line: ```
export PATH=/usr/local/texlive/2012/bin/x86_64-linux:$PATH 
``` to ~/.zshrc. The path also depends on your architecture (if you have 32-bit version, you path will be different in "x86_64-linux")!

3. Check it by typing this into terminal: ```
which latex
``` and ```
which biber
```. It should write something like: ```
/usr/local/texlive/2012/bin/x86_64-linux/biber
```. If it gives you "command not found" it means something went wrong. 

4. Now you can find your .tex file (or you can file this example: [ATTACH]240632[/ATTACH] ) and try, if everything works. Export example.zip to your home folder. You can do it by typing in terminal this (in this order):

```
dan@dan530ubu ~ $ cd Example 
dan@dan530ubu ~/Example $ latex biberguide.tex 
dan@dan530ubu ~/Example $ biber biberguide.bcf 
dan@dan530ubu ~/Example $ pdflatex biberguide.tex 

```

5. If you use some editor - for example Texmaker which I use and I recommend it to you, you have to make it in this order also: (pdf)latex - biber - (pdf)latex. You can set your own sequence in the settings.

Hope it helps.


Edit:  If you used old version of biblatex/biber and you created *.bcf file using old version, you must delete it and create/compile it using new version.

---

