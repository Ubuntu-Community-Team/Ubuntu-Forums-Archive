---
title: "Internal Error 500"
date: 2008-05-02
forum: General Help
---

### Post by Black Mage on 2008-05-02
When I try to read CGI scripts, I get an an internal server error 500.
So I went to the logs and it says this:

( Exec format error: exec of '/var/www/cgi-bin/test.pl' failed
Premature end of script headers: test.pl

Here is what my setup look like.

The server running is Apache2. In the /etc/apache2/sites-available, I am using the default. In the default file, I have the scripts locations set as:

ScriptAlias /cgi-bin/ /var/www/cgi-bin/
<Directory "/var/www/cgi-bin/">
AllowOverride None
Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
Order allow,deny
Allow from all
</Directory>

So what else could I be doing wrong?

---

