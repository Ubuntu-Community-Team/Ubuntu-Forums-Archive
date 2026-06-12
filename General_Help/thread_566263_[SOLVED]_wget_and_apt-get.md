---
title: "[SOLVED] wget and apt-get"
date: 2007-10-03
forum: General Help
---

### Post by measekite on 2007-10-03
[COLOR=Black]i have used apt-get many times to download and install programs.  I have not used but have seen wget and I assume that stands for web get.[/COLOR]

[COLOR=Blue]What is the difference between wget and apt-get and when is it appropriate to use one over the other?[/COLOR]

---

### Post by drf_av on 2007-10-03
apt-get is an interface to download and install packages, wget is an interface to download files.
So, shortly, if you need to install an application you have to type apt-get install <package>, if you need to download a file you type wget <url>.
They have 2 completely different purposes

---

### Post by C.A.T.S. CEO on 2007-10-03
apt-get is very different from wget.  apt-get downloads and installs .debs from repositories.  Wget downloads any file off the internet, .jpg, .iso, etc.  

wget is just a command-line downloader

---

### Post by kevdog on 2007-10-03
wget is similar to an ftp program, in that it can download web pages or files from the command line.  apt-get is a program that downloads packages from the ubuntu repository (similar to synaptic) but only on the command line.  A similar program to apt-get would be aptitude.

The two programs are in no way similar.  wget is often used in scripts to downloaded either files or web pages.  The web pages can then be parsed (usually with sed/grep) and information extracted from them -- for example getting you wan address from whatsmyip.com.  

Apt-get is just for updating and maintaining repositories.

---

### Post by singalen on 2007-10-03
wget is completely different: it's a http/ftp downloader, nothing more.
Try man on each, that's informative :)

---

### Post by Steveway on 2007-10-03
And for more information:
man wget
man apt

---

### Post by Vlet on 2007-10-03
wget is like going to a hardware store and buying parts for your new patio, apt-get is like hiring a contractor to do it for you :)

---

