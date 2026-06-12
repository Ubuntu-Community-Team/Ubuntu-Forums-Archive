---
title: "Sendmail Hostname Issue - Appears to be a common though difficult issue"
date: 2006-09-12
forum: General Help
---

### Post by Ashiro on 2006-09-12
I've done a raft of searching into this and performed all of the recommended solutions.  I'm beginning to reach a point where I can see myself cry like a baby with frustration.

When I try and use sendmail via Nagios it fails and when I look in my mail.err log I find the following:

> 
Sep 12 03:50:18 localhost sendmail[19406]: My unqualified host name (localhost) unknown; sleeping for retry
Sep 12 03:50:49 localhost sendmail[19411]: My unqualified host name (localhost) unknown; sleeping for retry
Sep 12 03:51:20 localhost sendmail[19415]: My unqualified host name (localhost) unknown; sleeping for retry
Sep 12 03:51:51 localhost sendmail[19419]: My unqualified host name (localhost) unknown; sleeping for retry
Sep 12 03:52:22 localhost sendmail[19426]: My unqualified host name (localhost) unknown; sleeping for retry
Sep 12 03:52:53 localhost sendmail[19430]: My unqualified host name (localhost) unknown; sleeping for retry


Now I've done a search on this and come across a number of things I can do:
1. Check /etc/hosts contains my hostname - which I've done:
> 
127.0.0.1 localhost essential-monitor


2. Check "/etc/mail/local-host-names" contains my hostname - Checked.
> 
localhost
localhost


3. Check "hostname" is set - I type "hostname" and get:
> essential-monitor

So all seems to check out fine but I still get these errors.  I'm completely at a loss and would be very grateful to any kind soul willing to help point me in the right direction.

---

### Post by veugelenw on 2007-10-22
I have the same issue over here. I'm using Kubuntu Feisty

---

### Post by jamesT0723 on 2007-10-31
:)
[FIX] FROM:www-data@localhost,Sendmail,smarthost block, PHP


Sendmail can be configured in a way to change the FROM:www-data@localhost. In my case this is what was causing the messages to be rejected by a "Smart Host".

We are Running Server 6.06

After installing sendmail with apt-get
edit the php.ini file and ensure that;
sendmail_path =/usr/sbin/sendmail -t -i

My first success was using the -f option.
sendmail_path =/usr/sbin/sendmail -t -i [email]-fmailer@yourdomain.com[/email]
This allowed messages to delivered, but viewing the "full header" of the received message revealed an "X-Authentication-Warning:"

There is a better way. Check this out:
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch21_:_Configuring_Linux_Mail_Servers](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch21_:_Configuring_Linux_Mail_Servers)
Especially the section titled; Using Sendmail to Change the Sender's Email Address

---

