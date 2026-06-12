---
title: "object oriented embeded perl"
date: 2007-04-22
forum: General Help
---

### Post by pircjo on 2007-04-22
I am trying to set up object oreinted emperl on Dapper and I have installed libhtml-embperl-perl using the SPM and changed the config file. I getn the following message in the log file when I try to access the embperl test page I set up: failed to resolve handler `HTML::EmbperlObject': Can't load '/usr/lib/perl5/auto/HTML/Embperl/Embperl.so' for module HTML::Embperl: /usr/lib/perl5/auto/HTML/Embperl/Embperl.so: undefined symbol: ap_configtestonly at /usr/lib/perl/5.8/DynaLoader.pm line 225.\n at /usr/lib/perl5/HTML/EmbperlObject.pm line 26\nCompilation failed in require at /usr/lib/perl5/HTML/EmbperlObject.pm line 26.\nBEGIN failed--compilation aborted at /usr/lib/perl5/HTML/EmbperlObject.pm line 26.\nCompilation failed in require at (eval 168) line 3.\n

I then included the following line in apache2.conf after reading the suggestion on the web: LoadModule  embperl_module  /usr/lib/perl5/auto/HTML/Embperl/Embperl.so

It causes this message when I try to restart apache: 
Syntax error on line 440 of /etc/apache2/apache2.conf:
Cannot load /usr/lib/perl5/auto/HTML/Embperl/Embperl.so into server: /usr/lib/perl5/auto/HTML/Embperl/Embperl.so: undefined symbol: ap_configtestonly

I think that it has something to do with: ap_configtestonly

---

### Post by qirtaiba on 2008-04-16
This seems to be a bug with the package of libhtml-embperl-perl; you should probably report it but as a workaround you can install libembperl-perl instead, which is just a newer version of  libhtml-embperl-perl that performs better anyway.  It is mostly backwards-compatible with the older version.

---

