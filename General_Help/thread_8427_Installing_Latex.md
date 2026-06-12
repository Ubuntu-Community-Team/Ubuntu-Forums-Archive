---
title: "Installing Latex"
date: 2004-12-17
forum: General Help
---

### Post by Denis the P. on 2004-12-17
Hi Everyone!

I am just a little bit more than a newbie to Linux. My Ubuntu system is now up and running after having some modem issues....

I now need to use Latex for word processing and have to install tetex, but when I look at the /linux/ubuntu/pool for tetex there is a lot of files there. Which ones do I need to install to get a Latex system all set?

Thank you all!

---

### Post by WW on 2004-12-17
tetex-base
tetex-bin
tetex-extra

---

### Post by Denis the P. on 2004-12-17
thank you!

...but do I need all the related packages in tetex-bin or most of them are already in the Ubuntu install?

---

### Post by kleeman on 2004-12-17
You may also find latex-xft-fonts improves fonts. Also check out lyx-qt which is a nice latex frontend

---

### Post by WW on 2004-12-17
I'm not sure what you mean by "all the related packages in tetex-bin".  If you mean all of packages that tetex-bin depends on, then probably most of them are already installed.  You can either try installing the three packages in Synaptic or with the command```
$ sudo apt-get install tetex-base tetex-bin tetex-extra
```  Either way, if additional packages must be installed to satisfy dependencies, you will be told before the download begins, and you will have the opportunity to cancel the installation. (If you use apt-get and all the dependencies are satisfied, it will start downloading immediately.)

---

### Post by Denis the P. on 2004-12-21
Thank you! I have discovered the wonders of Synaptic...!!!

---

### Post by ubuntu_demon on 2004-12-22
You might want to install kile or texmaker

see :

LaTeX
[http://www.ubuntuforums.org/showthread.php?t=6696](http://www.ubuntuforums.org/showthread.php?t=6696)

---

### Post by limontii7887 on 2007-05-15
> **WW said:**
> tetex-base
tetex-bin
tetex-extra


[weather solar blood pressure build pollution](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/index.php)

---

### Post by awarberg on 2007-10-22
The tetex packages have been moved to [TexLive]("http://www.tug.org/texlive/").

Here is a command to install the latex environment along with Texmaker, which is a great editor:

```
sudo apt-get install texlive texmaker
```

Best regards,
Andreas Warberg

---

### Post by dotjan on 2007-11-03
I have installed these packages but when i make a .tex file and compile it, I see only an aux en log file and no pdf file :(

In Texmaker when I compile with pdflatex: no pdf output file
In Kile: there is an pdf file

and in shell: "pdflatex test.tex" : no pdf output

what do I wrong?

---

### Post by dotjan on 2007-11-03
after reboot it works... strange

---

### Post by dotjan on 2007-11-03
lol, the problem was that i didn't have text, only latextags

---

