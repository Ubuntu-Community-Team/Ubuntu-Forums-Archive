---
title: "How toload Qgis ?"
date: 2018-08-15
forum: General Help
---

### Post by lift1test on 2018-08-15
From reading it seems i have to add the repository to Ubuntu but when I copy the Ubuntu link from the Qgis site software updater doesn't accept it as a new repository.  I realise I'm probably going about it the wrong way but not overly familiar with Linux.

---

### Post by Yellow Pasque on 2018-08-15
What link are you copying and where are you copying it to? What version of Ubuntu are you running?

---

### Post by lift1test on 2018-08-15
18.4.   The link is from the qgis website saying this is where you get qgis for ubuntu and trying to copy to software updater in settings, other software.  I would appreciate pointers to correct way of installing.

---

### Post by Yellow Pasque on 2018-08-15
I'm not familiar with software updater. I'm old school, so I use the terminal or Synaptic. The example below uses vim, but you can use whatever text editor you'd like:
```
sudo vim /etc/apt/sources.list.d/qgis.conf
```
Now you have a blank text file. Assuming you're trying to get the lastest stable version (3.2.x), copy/paste these lines.
```
deb https://qgis.org/ubuntu bionic main
deb-src https://qgis.org/ubuntu bionic main
```

Save. Quit. Run apt-get update. If you get keyserver warnings, follow instructions at the bottom of this section: [https://www.qgis.org/en/site/forusers/alldownloads.html#debian-ubuntu](https://www.qgis.org/en/site/forusers/alldownloads.html#debian-ubuntu)

---

### Post by lift1test on 2018-08-15
> **Temüjin said:**
> I'm not familiar with software updater. I'm old school, so I use the terminal or Synaptic. The example below uses vim, but you can use whatever text editor you'd like:
```
sudo vim /etc/apt/sources.list.d/qgis.conf
```
Now you have a blank text file. Assuming you're trying to get the lastest stable version (3.2.x), copy/paste these lines.
```
deb https://qgis.org/ubuntu bionic main
deb-src https://qgis.org/ubuntu bionic main
```

Save. Quit. Run apt-get update. If you get keyserver warnings, follow instructions at the bottom of this section: [https://www.qgis.org/en/site/forusers/alldownloads.html#debian-ubuntu](https://www.qgis.org/en/site/forusers/alldownloads.html#debian-ubuntu)
Thank you, I prefer using terminal but not often enough to be easy to use.  Another problem is I would prefer 2.8 because 3.2 is missing add on's that I need.  What do I need to change to get 2.8 please.

---

### Post by Yellow Pasque on 2018-08-15
You mean 2.18.x? That's available in the standard repos. You shouldn't have to add any repos.
But..
If you want to use qgis' own repo, you would use these as your sources:
```
deb https://qgis.org/ubuntu-ltr bionic main
deb-src https://qgis.org/ubuntu-ltr bionic main
```

---

### Post by lift1test on 2018-08-15
> **Temüjin said:**
> You mean 2.18.x? That's available in the standard repos. You shouldn't have to add any repos.
But..
If you want to use qgis' own repo, you would use these as your sources:
```
deb https://qgis.org/ubuntu-ltr bionic main
deb-src https://qgis.org/ubuntu-ltr bionic main
```
Please pardon my ignorance but how do I access the "standard repos"?  I tried [HTML]sudo apt-get qgis[/HTML] but it returned "E: Invalid operation qgis"

---

### Post by howefield on 2018-08-15
> **lift1test said:**
> I tried ```
sudo apt-get qgis
``` but it returned "E: Invalid operation qgis"

You need to use the install option in your command, eg

```
sudo apt-get install qgis
```

---

### Post by Holger_Gehrke on 2018-08-15
apt-get can do a lot of things, but it can't read your mind to find out what you want it to do ;)

It needs an operation before any package name. The operation you want is probably 'install', so the command should read ```
sudo apt-get install qgis
```By the way, apt (and apt-get) have manual pages which you can read by entering 'man apt' or 'man apt-get'. Also the command line completion could help; type 'sudo apt-get 'and hit the tabulator-key twice to get a list of the apt-get operations the command line completion knows about.

Holger

---

### Post by lift1test on 2018-08-15
Thank you both for being patient with an occasional user, have started it going, hope all goes well and i don't bother you again:(

---

