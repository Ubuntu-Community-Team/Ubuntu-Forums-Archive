---
title: "Apache, php, mysql phpmyadmin"
date: 2005-10-22
forum: General Help
---

### Post by KupernikuZ on 2005-10-22
Hi

I installed Breezy for a few days ago. Since then I worked about 24 hrs a day to setup Apache, php, mysql and phpmyadin. Nothing works.
I tried (many times!) to run
apt-get install apache2
apt-get install php5.0-mysql

and until now, the apache-server still wont show php pages :-(

Also tried to remove the packages and installed apache1 and php4, but still no result.

Then I downloaded the php 5 from php.org, and apache from apache.org.
Installed the apache 1.3.
Then I would install the php, but that requires lex.
Then I simply run
apt-get install flex, but there are no such packages anymore.

What can I do to install php and mysql?

Regards
"KupernikuZ"

---

### Post by KupernikuZ on 2005-10-23
Now I messed up... 
I think I was to tired yesterday... I deleted the /etc/apache library. Oops!
Tried apt-get remove apache  and apt-get clean apache
Then apt-get install apache  but that results in this output:

> 
Not replacing deleted config file /etc/apache/httpd.conf

Not replacing deleted config file /etc/apache/srm.conf

Not replacing deleted config file /etc/apache/access.conf

Can't open config file /etc/apache/httpd.conf.

Ingen sådan fil eller filkatalog (Translatet to english: no such file)

Can't open config file /etc/apache/httpd.conf.

Ingen sådan fil eller filkatalog (Translatet to english: no such file)

/usr/share/apache/postinst.common: line 7: /etc/apache/httpd.conf: Ingen sådan fil eller filkatalog (Translatet to english: no such file)

/usr/share/apache/postinst.common: line 7: /etc/apache/httpd.conf: Ingen sådan fil eller filkatalog (Translatet to english: no such file)

/usr/share/apache/postinst.common: line 7: /etc/apache/httpd.conf: Ingen sådan fil eller filkatalog (Translatet to english: no such file)

/usr/share/apache/postinst.common: line 7: /etc/apache/httpd.conf: Ingen sådan fil eller filkatalog (Translatet to english: no such file)


Well... How do I install the apache again? ](*,)

---

### Post by bl4ckm0r3 on 2005-10-23
why don't you try this?

[http://www.apachefriends.org/en/xampp-linux.html]("http://www.apachefriends.org/en/xampp-linux.html")

---

### Post by Wombley on 2005-10-23
Try this - it'll purge the configuration files then try to reinstall:
```

dpkg --purge apache
apt-get install apache

```

---

### Post by LorenzoD on 2005-10-23
[QUOTE=Wombley]Try this - it'll purge the configuration files then try to reinstall:
```

dpkg --purge apache
apt-get install apache

```[/QUOTE]

Yes, I would do that. The Ubuntu packages for Apache (1 and 2), PHP (4 and 5) as well as MySQL should all work fine. If after re-installing you still have problems you may want to provide some information about what is going wrong.

---

### Post by KupernikuZ on 2005-10-24
Thanks a lot.

Now I have my Apache again :-)

But now I would like to install the MySQL server. I just typed:
apt-get install mysql-server
That gave me this output:
  mysql-server-4.1: Depends: mysql-common-4.1 (>= 4.1.12-1ubuntu3) cant be installed
                    Depends: mysql-client-4.1 (>= 4.1.12-1ubuntu3) would not be installed
                    Depends: libdbi-perl cant be installed


:confused: 

Then I tried 
apt-get install mysql-common
That worked fine.
Then I would try
apt-get install mysql client  (and the same about libdbi-perl)

Those results in tis output:
  mysql-client-4.1: Depends: libdbi-perl men den kan ikke installeres
                    Depends: libdbd-mysql-perl (>= 1.2202) men den kan ikke installeres (english: cannot be installed)
                    Depends: mysql-common-4.1 (>= 4.1.12-1ubuntu3) men den kan ikke installeres (english: cannot be installed)
                    Depends: libmysqlclient14 (>= 4.1.12-1ubuntu3) men 4.1.12-1ubuntu1 forventes installeret  (english: may be installed)
E: Ødelagte pakker (english: broken packages)

Wel... How do I fix that? I'm little confused now. 
I tried both apt-get remove and dpkg --purge those packages but nothing realy works :-(

Do anyone have a tip for that? 

Regards

---

