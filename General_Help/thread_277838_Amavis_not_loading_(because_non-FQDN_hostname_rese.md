---
title: "Amavis not loading (because non-FQDN hostname reset on machine reboot)"
date: 2006-10-15
forum: General Help
---

### Post by linux_newbie_1888 on 2006-10-15
Just began setting up my home webserver to have mail capabilities (Postfix plus Amavis/Spamassassin, later to add Dovecot and SquirrelMail) using official tutorial: [https://help.ubuntu.com/community/PostfixAmavisNew](https://help.ubuntu.com/community/PostfixAmavisNew)

1) As advised in last section of tutorial, I need to test my setup before going onto the next step.

Upon trying *telnet localhost 10024* I get connection refused. Upon trying *sudo /etc/init.d/amavis restart* it appears amavis is not even running - error about hostname must be a fully qualified domain name.

IF I then enter command *sudo hostname mydomain.com*, again try *sudo /etc/init.d/amavis restart* (restarts successfully), and lastly try to telnet again.. it works.

BUT on sys shutdown or restart, this same error (and its resolution) appears.

Essentially, **my hostname (set to "ubuntu" on startup) needs to be *permanently* changed**. Hopefully then Amavis will load successfully at startup and allow this telnet connection as standard. _How can I action this, please?_

2) An additional situation is that I cannot open /var/log/mail.log - either by using *gksudo gedit mail.log* or with *gedit mail.log* - I get an "Xlib connection to :0.0 refused by server" error both times. _Should this be of any concern?_

Lisa.

---

### Post by ngms27 on 2006-10-18
I simply added 

$myhostname = 'myhost.mydoman';

to the 50-user file

Works a treat

JonnyT

---

