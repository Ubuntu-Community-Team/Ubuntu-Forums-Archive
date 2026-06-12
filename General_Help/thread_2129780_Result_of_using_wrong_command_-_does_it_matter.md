---
title: "Result of using wrong command - does it matter?"
date: 2013-03-27
forum: General Help
---

### Post by nickdc on 2013-03-27
In some kind of mental aberration I've just invoked "regedit" instead of "gedit", thus: gksudo regedit /etc/php5/apache2/php.ini   :oops:

Instead of the gedit window I was expecting, a little wine notification popped up saying my configuration has been updated, and a whole screed of errors ran through in the terminal:
```
fixme:storage:create_storagefile Storage share mode not implemented.
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
fixme:iphlpapi:NotifyAddrChange (Handle 0x248e8cc, overlapped 0x248e8b0): stub
wine: configuration in '/root/.wine' has been updated.
regedit: setValue failed to open key PHP
regedit: setValue failed to open key Date
regedit: setValue failed to open key filter
regedit: setValue failed to open key iconv
regedit: setValue failed to open key intl
regedit: setValue failed to open key sqlite
regedit: setValue failed to open key sqlite3
regedit: setValue failed to open key Pcre
regedit: setValue failed to open key Pdo
regedit: setValue failed to open key Pdo_mysql
regedit: setValue failed to open key Phar
regedit: setValue failed to open key Syslog
regedit: setValue failed to open key mail function
regedit: setValue failed to open key SQL
regedit: setValue failed to open key ODBC
regedit: setValue failed to open key Interbase
regedit: setValue failed to open key MySQL
regedit: setValue failed to open key MySQLi
regedit: setValue failed to open key mysqlnd
regedit: setValue failed to open key OCI8
regedit: setValue failed to open key PostgreSQL
regedit: setValue failed to open key Sybase-CT
regedit: setValue failed to open key bcmath
regedit: setValue failed to open key browscap
regedit: setValue failed to open key Session
regedit: setValue failed to open key MSSQL
regedit: setValue failed to open key Assertion
regedit: setValue failed to open key COM
regedit: setValue failed to open key mbstring
regedit: setValue failed to open key gd
regedit: setValue failed to open key exif
regedit: setValue failed to open key Tidy
regedit: setValue failed to open key soap
regedit: setValue failed to open key sysvshm
regedit: setValue failed to open key ldap
regedit: setValue failed to open key mcrypt
regedit: setValue failed to open key dba
regedit: setValue failed to open key xsl
```

Wine seems to be fuctioning ok still, and most of the above seems to be errors and failures, but I just wanted to check with more experienced users that I can safely ignore it. If not, what do I need to do to put things back as they were?

---

### Post by Impavidus on 2013-03-27
Regedit is a wine related program (I don't use wine myself), which edited some settings for root (as you ran it with gksudo). That's why it reports success updating /root/.wine. You never run wine as root (or do you? I believe wine even refuses to run when it detects it's run by root, unless you disabled that security feature), so I don't think anything can be harmed. You could delete /root/.wine if you like to clean things up.

---

### Post by nickdc on 2013-03-27
Thanks for that. No, I never run it as root. Rarely run it at all now, having recently set up a virtual Windows machine.

---

