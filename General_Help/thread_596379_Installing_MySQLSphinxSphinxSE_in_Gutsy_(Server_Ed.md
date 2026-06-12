---
title: "Installing MySQL/Sphinx/SphinxSE in Gutsy (Server Edition)"
date: 2007-10-29
forum: General Help
---

### Post by Nathan Malone on 2007-10-29
I have been trying for several hours now to install/compile [[COLOR="Blue"]SphinxSE[/COLOR]](http://www.sphinxsearch.com/doc.html#sphinxse) (a plugin for MySQL that requires that I "re-compile" MySQL) as well as [[COLOR="Blue"]Sphinx[/COLOR]](http://www.sphinxsearch.com/), the standalone fulltext search program that SphinxSE interfaces with, and have been having a lot of problems with the installation, particularly the SphinxSE installation (the part which required re-compiling MySQL).

I installed the latest version of Ubuntu 7.10 (Gutsy - Server Edition) on a spare computer I had, and that went just fine. I checked the option to install "LAMP" (basically, it installed Apache/PHP/MySQL on top of the Linux installation). After doing that, I think I was able to successfully install Sphinx (the standalone application), although it would only work if I disabled support for MySQL (possibly due to the problem described in the next paragraph in regards to not being able to re-compile MySQL).

However, I was unable to re-compile MySQL with the SphinxSE "plugin" (sorry of I'm messing up on the technical terms here...). I tried a variety of ways to install it, mainly based on the following URLs:

[[COLOR="Blue"]http://www.sphinxsearch.com/doc.html#sphinxse-installing[/COLOR]](http://www.sphinxsearch.com/doc.html#sphinxse-installing) (Instructions in Sphinx manual)
[[COLOR="Blue"]http://sphinxsearch.com/forum/view.html?id=165[/COLOR]](http://sphinxsearch.com/forum/view.html?id=165) (a users experience installing it on Ubuntu)

I got several error messages, some of which mentioned an error with readline, others of which were permissions errors (chmod'ing the directory to 777 got past those errors, but more errors appeared).

So, basically, I am asking if anyone would be willing to either write down some instructions for compiling and installing MySQL with SphinxSE, or perhaps give a few pointers on how it is done. If I have directions on how to do it in Ubuntu, I wouldn't have a problem, but I am having trouble patching together directions from the generic directions for Linux in general.

FYI, the version specs are below:

Ubuntu 7.10 (Gutsy) - Server Edition
MySQL 5.0.45 (from "sudo apt-get source mysql-server")
Sphinx 0.9.7

If anyone can post directions, I can try them, and then post whatever errors it spits out, or I could even open up the SSH port, if that would be helpful. I would ultimately like to be able to do this myself, however, so I will be able to do it in the future.

Thank you all!

---

