---
title: "Latest Ruby on Rails without orphaned files"
date: 2006-07-09
forum: General Help
---

### Post by tibbe on 2006-07-09
I would like to install the latest RubyGems and with it the latest version of Ruby on Rails. Is there a way to track what files get installed and store that information in a Debian package so they can later be removed? Note: RubyGems has its own installation script (in other words not "make install").

---

### Post by quedigg on 2006-07-09
yes , use synaptic to install ruby (use ruby package  without version postfix) ,aslo you will find Gem on the packages .


After installing it ,open the terminal and type ```
gem install rails --include-dependencies
```.
gem will install all other packages .

and happying coding !

---

### Post by tibbe on 2006-07-10
As far as I can see there is no RubyGems package.

---

