---
title: "mumble-server-web issue"
date: 2014-02-16
forum: General Help
---

### Post by mtweldon on 2014-02-16
I've got the server itself working and the -web installed, but when I go to localhost/mumble-server it just downloads the generated htm/php code as "download"

Any suggestions on how to resolve this?

---

### Post by mtweldon on 2014-02-17
Well resolved that error, didn't end up having php5 installed, thought I had.

getting this error now in the apache log:

[Mon Feb 17 12:04:13 2014] [error] [client 127.0.0.1] PHP Warning:  require(Ice.php): failed to open stream: No such file or directory in /usr/share/mumble-server-web/www/weblist.php on line 15
[Mon Feb 17 12:04:13 2014] [error] [client 127.0.0.1] PHP Fatal error:  require(): Failed opening required 'Ice.php' (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/mumble-server-web/www/weblist.php on line 15

Ice installs at /usr/share/Ice-3.4.2/

---

