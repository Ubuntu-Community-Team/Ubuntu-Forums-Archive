---
title: "php 5.2/3 on latest Ubuntu Server"
date: 2016-01-26
forum: General Help
---

### Post by bazianm on 2016-01-26
Hi,

I have to put together a server for a client. He has been using a php app that uses register globals so it cannot run on php later than 5.3. His host is, not surprisingly, phasing out 5.2 (that's what it is currently running on) and moving on. 

I have convinced the client that he has to upgrade the application (which I did not write) but that is going to take longer than we have and the application is mission critical. So, I need to put together a server for him to use in the meantime.

I would prefer, if possible, to use latest ubuntu to get as much in terms of security as I can. So, the question is, how would I go about installing a LAP stack with php 5.3 on Ubuntu Server 14.04 or 15.04.

Thanks for the assistance.

---

### Post by dragonfly41 on 2016-01-26
Using phpfarm is one option for running multiple versions of PHP

[http://thejibe.com/blog/14/02/phpfarm](http://thejibe.com/blog/14/02/phpfarm)

---

### Post by bazianm on 2016-01-26
Thanks for the reply. I saw a post somewhere else on this where they recommended just using ubuntu 12.04. Would that be a problem? Is it unsafe?

---

### Post by dragonfly41 on 2016-01-26
Well I still keep an old image of 12.04 in one partition on my development laptop but only to use as an internal OS for recovery purposes instead of LiveUSB (which is slower).

Another route might be to dualboot 12.04 and 15.04 so that you can migrate quickly.

Or run 12.04 as virtual machine on VirtualBox inside Ubuntu 14.04 / 15.04.

But personally I would drop 12.04 and move on.

---

### Post by dragonfly41 on 2016-01-26
It appears that you might be able to *emulate* register_globals

[http://php.net/manual/en/faq.misc.php#faq.misc.registerglobals](http://php.net/manual/en/faq.misc.php#faq.misc.registerglobals)

[http://stackoverflow.com/questions/16706098/enable-register-globals-in-php-5-4](http://stackoverflow.com/questions/16706098/enable-register-globals-in-php-5-4)

---

