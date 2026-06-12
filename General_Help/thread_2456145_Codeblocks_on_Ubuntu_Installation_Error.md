---
title: "Codeblocks on Ubuntu: Installation Error"
date: 2021-01-05
forum: General Help
---

### Post by deicool on 2021-01-05
Hello

I downloaded Codeblocks from the following website:

[http://www.codeblocks.org/downloads/26](http://www.codeblocks.org/downloads/26)

It won't install properly and open.

I tried reinstalling and throws up the following error:




Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 codeblocks : Depends: libtinyxml2.6.2v5 but it is not going to be installed
              Depends: libwxbase3.0-0v5 (>= 3.0.4+dfsg) but it is not going to be installed
              Depends: libwxgtk3.0-gtk3-0v5 (>= 3.0.4+dfsg-10~) but it is not going to be installed
 codeblocks-contrib : Depends: libboost-system1.62.0 but it is not installable
                      Depends: libgamin0 but it is not going to be installed
                      Depends: libhunspell-1.4-0 but it is not installable
                      Depends: libwxbase3.0-0v5 (>= 3.0.2+dfsg) but it is not going to be installed
                      Depends: libwxgtk3.0-0v5 (>= 3.0.2+dfsg) but it is not installable
                      Depends: codeblocks (= 20.03) but 20.03-3 is to be installed
                      Recommends: valgrind but it is not going to be installed
                      Recommends: cppcheck but it is not going to be installed
                      Recommends: cscope but it is not going to be installed
                      Recommends: cccc but it is not going to be installed
 codeblocks-libwxcontrib0 : Depends: libwxbase3.0-0v5 (>= 3.0.2+dfsg) but it is not going to be installed
                            Depends: libwxgtk3.0-0v5 (>= 3.0.2+dfsg) but it is not installable
 libcodeblocks0 : Depends: libwxbase3.0-0v5 (>= 3.0.2+dfsg) but it is not going to be installed
                  Depends: libwxgtk3.0-0v5 (>= 3.0.2+dfsg) but it is not installable
 libwxsmithlib0 : Depends: libwxbase3.0-0v5 (>= 3.0.2+dfsg) but it is not going to be installed
                  Depends: libwxgtk3.0-0v5 (>= 3.0.2+dfsg) but it is not installable
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).



Any ideas what to do?

Thank You
Deepak

---

### Post by Frogs Hair on 2021-01-05
Support request, moved to *General Help*.

---

### Post by #&amp;thj^% on 2021-01-05
> **deicool said:**
> Hello

I downloaded Codeblocks from the following website:

[http://www.codeblocks.org/downloads/26](http://www.codeblocks.org/downloads/26)

It won't install properly and open.

I tried reinstalling and throws up the following error:




Any ideas what to do?

Thank You
Deepak

Is there some reason you can't just use what's in the repos?
```
apt search codeblocks
Sorting... Done
Full Text Search... Done
codeblocks/focal 20.03-3 amd64
  Code::Blocks integrated development environment (IDE)

codeblocks-common/focal,focal 20.03-3 all
  common files for Code::Blocks IDE

codeblocks-contrib/focal 20.03-3 amd64
  contrib plugins for Code::Blocks IDE

codeblocks-dev/focal 20.03-3 amd64
  Code::Blocks development files (SDK)

libcodeblocks0/focal 20.03-3 amd64
  Code::Blocks shared library

python3-knitpy/focal,focal 0.1.1~git20180430-1 all
  report generation tool with Python

texlive-pictures/focal,focal 2019.20200218-1 all
  TeX Live: Graphics, pictures, diagrams



```
If you went as far as installing/adding the PPA you have to be using Xenial 16.04, after that 18.04 20.04 is now in the repos.

---

