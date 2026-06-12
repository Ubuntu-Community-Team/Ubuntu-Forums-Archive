---
title: "perl-doc install fails"
date: 2005-10-23
forum: General Help
---

### Post by argos on 2005-10-23
I just finished a default install of ubuntu 5.10 but it seems perl-doc is not installed.  when I enter perldoc perldoc instead of getting a list of information related to perl documents I am told I need to install the perl-doc package.  I then run:
     apt-get install perl-doc 
but this fails I am told the perl-doc package is not available.  I then tried to uninstall perl but using apt-get to do this lists a lot of other packages that will be removed at the same time.  So I figured I would try to re-install perl hoping perl-doc would be installed at the same time but that made no difference.  So, how should I go about installing perl-doc without removing perl?

---

### Post by phup on 2005-10-23
I know it's not cool to use a gui when you can type a bunch of stuff on a command line, but I used the synaptic package manager to find and install perl-doc and it worked fine.

---

### Post by argos on 2005-10-23
I tried the synaptic package manager and it also fails to install perl-doc.  I selected search entered "perl-doc" it brought up perl-base.  I selected the option to reinstall perl but it failed to install perl-doc.  I see that the base-perl package is installed and it mentions that perl-doc is not installed but when I search for perl-doc all I get back is 'base-perl'.  so I guess I need a way to force either apt-get or the synaptic package manager to just install perl-doc...

---

