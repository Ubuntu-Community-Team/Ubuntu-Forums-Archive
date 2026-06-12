---
title: "Php configuration."
date: 2013-02-02
forum: General Help
---

### Post by pcrio2 on 2013-02-02
Hello, i have ubuntu 12.04 installed with php 5.3.10 that came with ubuntu, the question is.

How do i configure this version of php, if it doenst give you the option when its installing?

Is there some path i should go to run the command ./configure?

Thank You [-o<

---

### Post by SeijiSensei on 2013-02-02
The version in the repositories is a compiled binary.  You would only use ./configure if you were compiling your own copy of PHP from the source code.

The configuration file for PHP is called php.ini.  Ubuntu installs separate versions of this file for the Apache PHP module and for the php command-line program.  They are in separate directories under /etc/php5.

If you need to install additional PHP modules to support things like PostgreSQL these are distributed as separated packages with names like php5-pgsql.  Run the command "apt-cache search php5-*" to see a list.

---

### Post by pcrio2 on 2013-02-02
Thank you SeijiSensei, so it means that i cant reconfigure the php to enable XPM support in php5-gd? I read in the php manual, if i want to enable XPM i have to write **--with-xpm-dir=DIR **in the configuration file (./configure) am i right?


> **SeijiSensei said:**
> The version in the repositories is a compiled binary.  You would only use ./configure if you were compiling your own copy of PHP from the source code.

The configuration file for PHP is called php.ini.  Ubuntu installs separate versions of this file for the Apache PHP module and for the php command-line program.  They are in separate directories under /etc/php5.

If you need to install additional PHP modules to support things like PostgreSQL these are distributed as separated packages with names like php5-pgsql.  Run the command "apt-cache search php5-*" to see a list.

---

### Post by SeijiSensei on 2013-02-03
It depends on how the php5-gd package was compiled.  Luckily for you it appears that XPM support was [compiled in by the maintainers]("https://launchpad.net/ubuntu/precise/+package/php5-gd"), so it should "just work" if you install the php5-gd module with apt-get or the graphical package manager.

In the vast majority of cases, the packagers compile software with the widest collection of options available.  The only omissions I've seen is where something is not covered by an open-source license.  (I recall encountering that issue with php-mcrypt some years ago when some of Ron Rivest's algorithms were still [patented]("http://en.wikipedia.org/wiki/RC5") in the US.  When GIFs were still [covered]("http://www.freesoftwaremagazine.com/articles/gif_now_finally_free") by US patents similar problems arose.)  You should generally assume everything will work without incident.  If it turned out that XPM support was not already included in php5-gd, then you should file a bug report at Launchpad to inform the developers of the omission.

---

