---
title: "nagios-plugins + nagios-nrpe-server install is removing MySQL installtion"
date: 2012-10-21
forum: General Help
---

### Post by s3xynanigoat on 2012-10-21
Hi, I have an Ubuntu 12.04 64-bit postfix/clamav/spamassisin/courier mail server.  I have the server setup and running smooth by following this tutorial...

[http://www.pixelinx.com/2010/10/creating-a-mail-server-on-ubuntu-using-postfix-courier-ssltls-spamassassin-clamav-and-amavis/](http://www.pixelinx.com/2010/10/creating-a-mail-server-on-ubuntu-using-postfix-courier-ssltls-spamassassin-clamav-and-amavis/)

I also have an Ubuntu 12.04 64-bit Nagios Server.  I have used this tutorial to help with that install...

[http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=194](http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=194)

Both machines are VMs running on ESX 4.1.  Whenever I install the nrpe-server and plugin packages on the mail server the MYSQL installation on (mail) it gets removes.  In turn, this also is breaking my ClamAV and SpamAssasin install.  

If I run 'mysql' from the command prompt I'm told it's not installed.  If I reinstall MySQL I'm not taken through the setup process and all my previously configured options, password, and databases are there.  This would be fine but the system still seems borked because I can no longer start the courier imap services with...[COLOR=#000000][B]

/[/B][/COLOR]etc[COLOR=#000000]**/**[/COLOR]init.d[COLOR=#000000]**/**[/COLOR]courier-imap restart 
[COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]init.d[COLOR=#000000]**/**[/COLOR]courier-imap-ssl restart

In fact, these two plugins seem to break the whole SASL process as I can't authenticate into POP3 either.  

Now I read something about nrpe-server-plugin being sent to the Universal repository, and maybe that's the issue here.  But I would like to know if anyone could help me to better understand what's happening here.  I am new to *nix but am versed in servers and networking.  

My install process on the mail server is as follows...

Create VM > Uninstall Apparmor > Install VMTools > Follow (above) Postfix guide > Test Email functionality > Follow NRPE plugin examples from (above) nagios tutorial

Immediately after the NRPE install is when I see the ClamAV and Spamassasin service stopping in the /var/log/mail.log file.  At that point I check MySQL and it's gone.  

Please, someone shed some light on this for me.  

Thanks in advance, Andrew.

---

### Post by s3xynanigoat on 2012-10-22
Maybe this is not the correct sub forum to ask this question.  Would a moderator be able to move this to the server forum?  Thank you.

---

