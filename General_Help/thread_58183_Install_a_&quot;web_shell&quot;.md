---
title: "Install a &quot;web shell&quot;"
date: 2005-08-19
forum: General Help
---

### Post by cudjoe on 2005-08-19
Hi all,

I would like to have a remote accessI would like to have a shell console embedded in a web page, so that I can administrate my PC with any browser.

I tested [php-shell]( http://freshmeat.net/projects/phpshell/)  but it doesn't allow commands that involve interaction (such as 'vi', or even 'top') nor tab completion.

I then found [cgi-shell](http://cgi-shell.binaervarianz.de/)  but I can't make it work.

My apache2 seems well configured ( juste changed default cgi-bin place )

```
ScriptAlias /cgi-bin/ /var/www/cgi-bin/
<Directory "/var/www/cgi-bin/">
	AllowOverride None
	Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
	Order allow,deny
	Allow from all
</Directory>
```

In README, installation looks straightforward !
[I]- How to install?
  make
  make install   (you have to be root)[/I]


Here are the installed files.

```
$ ll -R /var/www/cgi-bin/
/var/www/cgi-bin/:
total 4.0K
drwxr-xr-x  2 mathieu mathieu 4.0K Aug 18 19:08 shell/

/var/www/cgi-bin/shell:
total 604K
-rw-r--r--  1 mathieu mathieu  18K Sep 21  2003 COPYING
-rw-r--r--  1 mathieu mathieu 1.5K Sep 21  2003 Makefile
-rw-r--r--  1 mathieu mathieu  374 Sep 21  2003 README
-rwxr-xr-x  1 root    root     21K Aug 18 18:57 cgi-shell*
-rwxr-xr-x  1 mathieu mathieu 488K Sep 21  2003 cgi-shell-server*
-rwxr-xr-x  1 mathieu mathieu  975 Sep 21  2003 cgi-shell-start.php*
-rwxr-xr-x  1 mathieu mathieu 1.1K Sep 21  2003 cgi-shell-start.pl*
-rw-r--r--  1 mathieu mathieu 5.3K Sep 21  2003 libcgishellc.c
-rw-r--r--  1 mathieu mathieu 1.7K Sep 21  2003 libcgishellc.h
-rw-r--r--  1 root    root    4.5K Aug 18 18:57 libcgishellc.o
-rw-r--r--  1 mathieu mathieu 1.2K Sep 21  2003 libcgishells.c
-rw-r--r--  1 mathieu mathieu 1.1K Sep 21  2003 libcgishells.h
-rw-r--r--  1 mathieu mathieu 6.7K Sep 21  2003 main.c
-rw-r--r--  1 root    root    6.1K Aug 18 18:57 main.o
-rw-r--r--  1 mathieu mathieu 4.9K Sep 21  2003 server.c
```



I then launch :

*[http://localhost/cgi-bin/shell/cgi-shell-start.pl?p=5000](http://localhost/cgi-bin/shell/cgi-shell-start.pl?p=5000)*

which contains :
```
$ cat cgi-shell-start.pl
#!/usr/bin/perl -w
use strict;
use CGI qw(:standard);
use CGI::Carp qw(fatalsToBrowser);

my $port = param("p");
print("Content-type: text/plain\n\nStarting server ... ");
my $server_ret = system("./cgi-shell-server -p $port");
print("returned $server_ret");
exit 0;
```


...and get nothing.

Does anybody know what I should configure, launch ? or better does someone have a working solution for remote web shell access ?

Many thanks to all, who read my long message :)

cudjoe

---

