---
title: "Configure error; no KDE libraries installed"
date: 2013-01-31
forum: General Help
---

### Post by rdh61 on 2013-01-31
Hi,

I am trying to install Kradview (dicom viewer) using the instructions here:

[http://www.orcero.org/irbis/kradview/]("http://www.orcero.org/irbis/kradview/")

This does not work.

./configure gives the following error:

```
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE libraries installed. This will fail.
So, check this please and use another prefix!
```

I have Googled for a solution but can't find anything that works. People seem to be having similar problems for years.

Anyone got a solution?

Many thanks.

---

### Post by SeijiSensei on 2013-01-31
Try installing a single KDE application like dolphin from the repositories.  That will bring in the KDE libraries as dependencies without all the other applications or the desktop.  Or you might simply choose to try KDE in toto by installing kubuntu-desktop from the repositories.

I'm surprised there is no Ubuntu version of this program as it appears to have been around for years.  I see RPM's and Debian debs, but the only suggestion for Ubuntu is compiling from source as described [here]("http://ptspts.blogspot.com/2011/09/how-to-install-kradview-on-ubuntu-lucid.html").  If you decide to try that, you'll need to install the "build-essential" package as well which contains the gcc compiler and associated tools.  You might want to follow [this method]("https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages") to recommend adding this package to Ubuntu.

---

### Post by rdh61 on 2013-02-02
Thanks for your suggestions SeijiSensei. Unfortunately even after installing kubuntu-desktop, I get the same error message.

---

### Post by SeijiSensei on 2013-02-02
You also need the development files.  

```
sudo apt-get install libqt3-headers kdelibs4-dev
```

See [this page](http://ptspts.blogspot.com/2011/09/how-to-install-kradview-on-ubuntu-lucid.html) for details.

---

### Post by rdh61 on 2013-02-04
> **SeijiSensei said:**
> You also need the development files.  

```
sudo apt-get install libqt3-headers kdelibs4-dev
```



Thanks. Synaptic says I already have libqt3-headers installed, and also kdelibs5-dev (but not kdelibs4-dev, which isn't listed).

---

