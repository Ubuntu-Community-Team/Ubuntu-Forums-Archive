---
title: "Hoary + Apache2 + WebGUI 6.5.6 Problems"
date: 2005-04-22
forum: General Help
---

### Post by FUZiON on 2005-04-22
If anyone else is using this CMS configuration, let me know how to fix this:

From /var/log/apache2/error.log
[Fri Apr 22 02:54:37 2005] [error] Can't locate ModPerl/Registry.pm in @INC (@INC contains: /var/www/WebGUI/lib /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl . /etc/apache2/ /etc/apache2/lib/perl) at /var/www/WebGUI/sbin/preload.perl line 19.\nBEGIN failed--compilation aborted at /var/www/WebGUI/sbin/preload.perl line 19.\nCompilation failed in require at (eval 2) line 1.\n
[Fri Apr 22 02:54:37 2005] [error] Can't load Perl file: /var/www/WebGUI/sbin/preload.perl for server localhost.localdomain:0, exiting...

I used the Pkg manager to dl mod-perl but i don't know what to edit to fix this or where to find the modperl/registry.pm file

Thanks in advance for your help guys!  ](*,)

---

### Post by Ubuntu Warrior on 2005-08-19
Also trying to install WebGUI without success. Seems to be a lot of info at:

[http://www.inertramblings.com](http://www.inertramblings.com)

but alas, hasn't helped me much.

Have tried to modify the Files section in /etc/apache2/apache2.conf as recommended but no luck. Have also set the PerlHandler ModPerl::Registry with no luck. Trying to use WebGUI 5.5.8 (stable).

When trying to start up Apache with:

/etc/init.d $ sudo ./apache2 start

the log gives something about cannot locate various .pm files. This seemed to be a problem with where it was looking in the file system i.e. under /usr/lib/perl5/Apache instead of /usr/lib/perl5/Apache2/Apache, etc. As a quick-and-nasty I have tried to copy the relevant files from /usr/lib/perl5/Apache2/Apache to /usr/lib/perl5/Apache but keep running into further missing files and modules. The obvious thing would probably be to change a path setting somewhere to point to the right place but haven't found any pointers on that yet.

Should I be putting all this effort into installing WebGUI or is there another CMS out there (open source of course) that can do a similar or better job? Would much prefer sudo apt-get install open-source-cms rather than struggling through like I currently am.

---

