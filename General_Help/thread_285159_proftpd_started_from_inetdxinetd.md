---
title: "proftpd started from inetd/xinetd"
date: 2006-10-26
forum: General Help
---

### Post by jlhughes on 2006-10-26
At one point I was using apachefriends.org's xampp package for my web and ftp services.  I decided to stop doing that and start using the apache2 and proftpd available with Ubuntu.

I think I haven't completely removed the original xampp installation of proftpd.

In any event, I am no longer able to ftp to the server. There appears to be no ftp server running. netstat -nap|grep 21 doesn't show anything for port 21.

My /etc/proftpd.conf has the server set as standalone.

However, when I execute /etc/init.d/proftpd restart

I get the message: ProFTPd is started from inetd

Any ideas on how to get this sorted out would be greatly appreciated.

---

### Post by rjl6591 on 2006-10-26
sudo dpkg-reconfigure proftpd

---

### Post by jlhughes on 2006-10-26
Thanks for the quick reply.

I ran sudo dpkg-reconfigure proftpd

I set it standalone and told it use the existing config file. Apparently, that wasn't the best idea.

I was still told ProFTPd cannot start neither in standalone nor in inetd/xinetd mode.

I completely removed proftpd and reinstalled, configuring for standalone. Works now.

---

