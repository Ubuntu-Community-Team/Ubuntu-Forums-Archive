---
title: "Texlive installation"
date: 2014-02-01
forum: General Help
---

### Post by sunnyengineeer on 2014-02-01
Hello,

I'm a user of Lubuntu edition, I wanted to install LATEX on my Laptop, So I tried sudo-apt get install texlive-full, but since it takes a hell lot of space (Around 2 GB), but I have only around 1.5 GB in my Lubuntu drive which can be used for it....
...Since Texlive contains many languages, which I'll not be using at all, So is it possible to install in such a way that only English language packs are installed, so that I can satisfy the contraints...

...Any suggestion...

---

### Post by raja.genupula on 2014-02-01
[http://hoast.dk/how-tos/install-latex-in-ubuntu/](http://hoast.dk/how-tos/install-latex-in-ubuntu/)

---

### Post by Impavidus on 2014-02-01
Start with installing **texlive** from the repositories, which will pull in some packages that you'll probably need. It says it "provides a decent selection of the TeX Live packages which should suffice for the most common tasks." Then add whatever you want in addition to that whenever the need arises.

Additional advice: I noticed that in case of TeX the packages from the repos are often (very) old, so if you want a more recent version or if you want a specific package without pulling in a whole collection of them, consider manual installation. Just for some packages, for example when the version in the repos has a nasty bug that has been fixed on the version on ctan, not for everything. You can put them in /usr/local/share/texmf/, which is included automatically and takes precedence over files in /usr/share/tex*.

---

