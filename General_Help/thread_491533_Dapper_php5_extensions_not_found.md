---
title: "Dapper: php5 extensions not found"
date: 2007-07-03
forum: General Help
---

### Post by randyrando on 2007-07-03
Hello,

I am trying to use the curl and tidy_file_repair functions in php5.  I am using Dapper.  I have installed all the correct libraries (according to synaptic)

When I try to run a program using these functions I get the 
" Fatal error: Call to undefined function tidy_repair_file() ...."  for example.

I have tried messing with php.ini, no such luck.  The one thing I do notice is a descrepancy when i look at the output of phpinfo(), it reports:

Build Date => May 22 2007 20:22:45
Server API => Command Line Interface
Virtual Directory Support => disabled
Configuration File (php.ini) Path => /etc/php5/cli/php.ini
PHP API => 20041225
PHP Extension => 20050922

if I ask php-config --entension-dir it reports:

$ php-config --extension-dir
/usr/lib/php5/20051025

Sure enough, they are there.  So why can't the cli version find them?  I also get the same error if I run it from within firefox....or if I use the cgi version.....sigh...

I must be doing something stupid, anyone know what it is?  Thanks for the help.

---

