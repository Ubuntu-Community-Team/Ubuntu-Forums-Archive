---
title: "Install of package with pear fails"
date: 2015-02-11
forum: General Help
---

### Post by ulty2 on 2015-02-11
I was following a document on how to setup snort and associated programs in ubuntu, and ran into trouble with some php install for the BASE part of the install.  The first command to run was:

sudo apt-get install -y apache2 libapache2-mod-php5 php5 php5-mysql php5-common \
php5-gd php5-cli php-pear

Which went fine, then:

sudo pear install -f Image_Graph

I received a few warnings but per the instructions those are to be expected and aren't a problem (apparently), then the problem:

Starting to download Image_Graph-0.8.0.tgz (367,646 bytes)
...........................................................................done: 367,646 bytes
could not extract the package.xml file from "/build/buildd/php5-5.5.9+dfsg/pear-build-download/Image_Graph-0.8.0.tgz"
Download of "pear/Image_Graph" succeeded, but it is not a valid package archive
Error: cannot download "pear/Image_Graph"

I did some googling but didn't really find anything useful.

---

