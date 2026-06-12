---
title: "About packages tidy and libtidy-0.99-0"
date: 2008-03-01
forum: General Help
---

### Post by satimis on 2008-03-01
Hi folks,


Ubuntu 7.10 workstation


I need to install "tidy".  


On running;
$ apt-cache search tidy | grep tidy```

csstidy - CSS parser and optimiser
libexporter-tidy-perl - Another way of exporting symbols
libtidy-ruby - Ruby interface to HTML Tidy Library
libtidy-ruby1.8 - Ruby interface to HTML Tidy Library
perltidy - Perl script indenter and reformatter
python-elementtidy - An HTML tree builder for ElementTree based on Tidy
python-utidylib - Python wrapper for TidyLib
tidy-doc - HTML syntax checker and reformatter documentation
tidy-proxy - A small http proxy which tidies html
php5-tidy - tidy module for php5

```

Please advise which repo I have to enable/add on source.list?  TIA


On running;

$ sudo apt-get install php5-tidy```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-tidy: Depends: libtidy-0.99-0 but it is not installable
E: Broken packages

```

Having googled a while.  Can't find the repo which provide this package.  Pls help.  Thanks


B.R.
satimis

---

