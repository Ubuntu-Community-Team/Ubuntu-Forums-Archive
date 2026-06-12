---
title: "Koha with Ubuntu 6.06"
date: 2007-06-01
forum: General Help
---

### Post by cortex33 on 2007-06-01
HI
cannot run installer.pl
receive this message back

Can't locate Install.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /home/michael/koha-2.2.9/installer.pl line 5.
BEGIN failed--compilation aborted at /home/michael/koha-2.2.9/installer.pl line 5.

Coudl someone help me
TNX

---

### Post by cortex33 on 2007-06-02
I have solved the issue , by movinf the rep Koha-2.2.9 from /Home into /etc
but now i'm blocked with this error messages

root@ubuntu:/etc/koha-2.2.9# '/etc/koha-2.2.9/Install.pm'
/etc/koha-2.2.9/Install.pm: line 1: package: command not found
/etc/koha-2.2.9/Install.pm: line 25: use: command not found
/etc/koha-2.2.9/Install.pm: line 26: use: command not found
/etc/koha-2.2.9/Install.pm: line 30: syntax error near unexpected token `('
/etc/koha-2.2.9/Install.pm: line 30: `use Term::ANSIColor qw(:constants);
 
thanks for the help

---

### Post by pete83 on 2007-07-10
Hey, if you're still looking for help for Ubuntu 6.06, see the site here:

[http://matthew.metzger.cc/wiki/index.php?title=Install_Koha_on_Ubuntu_6.06](http://matthew.metzger.cc/wiki/index.php?title=Install_Koha_on_Ubuntu_6.06)

also, if you are using the new Ubuntu release, try this guide:

[http://ssac.carleton.ca/dev/index.php/2007/05/14/installing-koha-228-on-ubuntu-704-feisty-fawn/](http://ssac.carleton.ca/dev/index.php/2007/05/14/installing-koha-228-on-ubuntu-704-feisty-fawn/)

I haven't tried it yet, but it looks like a promising program.

---

