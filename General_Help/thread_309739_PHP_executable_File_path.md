---
title: "PHP executable File path"
date: 2006-11-30
forum: General Help
---

### Post by shameerpm on 2006-11-30
Hi all
I am very new to Ububntu Linux
Any body can advise me where is PHP executable file is located on linux ubuntu Lamp server 6.06.1. I mean path to php executable file in linux ubuntu Lamp server 6.06.1. 

Thanks in advance

---

### Post by CyberX on 2006-11-30
Hi.
My php FastCGI configuration uses /usr/bin/php5-cgi
The rest of php is also under /usr/bin/ and the php.ini is in /etc/php5/cgi/

I use Lighttpd instead of Apache, but I suppose it doesn't matter.

---

### Post by az on 2006-11-30
> **shameerpm said:**
> Hi all
I am very new to Ububntu Linux
Any body can advise me where is PHP executable file is located on linux ubuntu Lamp server 6.06.1. I mean path to php executable file in linux ubuntu Lamp server 6.06.1. 

Thanks in advance

If your LAMP server is not executing php scripts, and your browser is offering to download them, it's because you did no install the appropriate libapache-mod-php package (libapache2-mod-php5)

---

