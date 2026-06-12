---
title: "sqlite3-ruby install error on Ubuntu"
date: 2014-03-17
forum: General Help
---

### Post by jang3 on 2014-03-17
I have the following error during sqlite3-ruby install:

> Building native extensions.  This could take a while...ERROR:  Error installing sqlite3-ruby:
    ERROR: Failed to build gem native extension.


/usr/bin/ruby1.8 extconf.rb
checking for sqlite3.h... no
sqlite3.h is missing. Try 'port install sqlite3 +universal' or 'yum install sqlite3-devel'
*** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of
necessary libraries and/or headers.  Check the mkmf.log file for more
details.  You may need configuration options.


Provided configuration options:
    --with-opt-dir
    --without-opt-dir
    --with-opt-include
    --without-opt-include=${opt-dir}/include
    --with-opt-lib
    --without-opt-lib=${opt-dir}/lib
    --with-make-prog
    --without-make-prog
    --srcdir=.
    --curdir
    --ruby=/usr/bin/ruby1.8
    --with-sqlite3-dir
    --without-sqlite3-dir
    --with-sqlite3-include
    --without-sqlite3-include=${sqlite3-dir}/include
    --with-sqlite3-lib
    --without-sqlite3-lib=${sqlite3-dir}/lib




Gem files will remain installed in /usr/lib/ruby/gems/1.8/gems/sqlite3-ruby-1.3.1 for inspection.
Results logged to /usr/lib/ruby/gems/1.8/gems/sqlite3-ruby-1.3.1/ext/sqlite3/gem_make.out

sqlite3.h is located in /usr/include/


> sudo gem install sqlite3-ruby --without-sqlite3-include=/usr/include
doesn't work


> ERROR:  While executing gem ... (OptionParser::InvalidOption)
    invalid option: --without-sqlite3-include=/usr/include
Ubuntu 10.04

---

### Post by TheFu on 2014-03-17
If you are a ruby programmer, then using rbenv or rvm is a "best practice" - which will keep the OS ruby stuff away from your ruby stuff, including gems.
The first few chapters of this free book explains: [http://ruby.railstutorial.org/chapters/beginning](http://ruby.railstutorial.org/chapters/beginning)

I've setup Ruby-on-Rails on Ubuntu before - here's a guide: [http://blog.jdpfu.com/2012/07/18/ruby-on-rails-environment-on-ubuntu-12-04](http://blog.jdpfu.com/2012/07/18/ruby-on-rails-environment-on-ubuntu-12-04) Things may have changed slightly since then.

10.04 is nearing EOL. Desktop 10.04 supported ended about a yr ago.  The Ruby-on-Rails guys are hyper-new with their coding - almost to the point of abuse, IMHO. That means it may not be possible to run newer gems on 4 yr old released versions of Ubuntu.

---

### Post by cariboo on 2014-03-19
You may get better help here, than in [ULAOSC.]("http://ubuntuforums.org/forumdisplay.php?f=434")

---

