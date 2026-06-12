---
title: "How to increase verbosity of apache error messages"
date: 2006-08-08
forum: General Help
---

### Post by mxc on 2006-08-08
Hi there,

I am used to there being lots of info in the apache error logs on other distros. I have been trying to install symfony framwork on our apache server but just keep getting 500 internal server error messages. There seems to be nothing in the /var/log/apache/error.log.

The apache2.conf file looks ok so not sure why the errors aren't being logged. I might be the framework is interception them. But I thought I would just ask if anyone knew whether Ubuntu has set the log reporting for apache quiet low and if so how to increase it.

thanks

---

### Post by oleonav on 2006-08-21
Hi mxc,

I had the same problems as you had. Look at the following page: [http://www.symfony-project.com/trac/wiki/SymfonyUbuntu]("http://www.symfony-project.com/trac/wiki/SymfonyUbuntu")

The key to the problem is changing the configuration value of magic_quotes_gpc = On to magic_quotes_gpc = Off in /etc/php5/apache2/php.ini

Good luck,

oleonav

---

