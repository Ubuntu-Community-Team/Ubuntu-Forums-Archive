---
title: "Configure Postfix SMTP on a co-location server"
date: 2007-12-05
forum: General Help
---

### Post by mrgordonz on 2007-12-05
Hi Gurus,

I have just recently placed a server in a co-location data centre.  The server is running Ubuntu Server 6.0.6.  In addition, I have installed VMware server and created a few virtual machines.

On the VMs I have installed an application (J2EE web application) which needs to be able to send emails to users. As part of the application config I need to specify the SMTP server which will be used for relaying emails.  This is normally not an issue because the application is most often installed on customer sites (behind the firewall) and we just specify their SMTP server, and Bob's your uncle.

But in the co-location facility I need to setup my own SMTP server (the co-lo people said they don't normally give access to an SMTP server for co-lo customers).

I followed the instructions on this site: [http://my.opera.com/Contrid/blog/show.dml/478684](http://my.opera.com/Contrid/blog/show.dml/478684) to set up Postfix - it was pretty easy and seemed to install OK.

But it won't work :(.  I know that Postfix is running - when I do a ```
netstat -l
```
I can see that something is listening on port 25.  From the VM I can telnet to the host on port 25.

I *think* that the problem is one of authentication - the web application needs to authenticate itself to Postfix before Postfix will relay an email.

How do I configure an account in Postfix?

I have never configured an SMTP server, and my knowledge of Linux is limited.

---

### Post by mrgordonz on 2007-12-05
I have managed to get things sorta working.  The application log file (on the VM) no longer throws the following exception:

<someaddress@somedomain> Recipient address rejected: User unknown in local recipient table

I had to edit two files:

/etc/postfix/main.cf
/etc/mailname

I added another domain to each of these files, and restarted Postfix.  Now when the application sends an email to an address at the second domain, I don't see any exceptions in the application log file.  But the email never arrives.

Any ideas?

---

### Post by mrgordonz on 2007-12-05
Here is a snippet from the Postfix log file:

```
Dec  5 23:44:09 ozsabasvr01 postfix/smtpd[25196]: connect from unknown[xxx.xxx.xxx.xxx]
Dec  5 23:44:09 ozsabasvr01 postfix/smtpd[25196]: 65EB4398050: client=unknown[xxx.xxx.xxx.xxx]
Dec  5 23:44:09 ozsabasvr01 postfix/cleanup[25199]: 65EB4398050: message-id=<11479213.1196862009609.JavaMail.SYSTEM@ozsabavm02>
Dec  5 23:44:09 ozsabasvr01 postfix/qmgr[25114]: 65EB4398050: from=<admin@domain1.com>, size=683, nrcpt=1 (queue active)
Dec  5 23:44:09 ozsabasvr01 postfix/smtpd[25196]: disconnect from unknown[xxx.xxx.xxx.xxx]
Dec  5 23:44:09 ozsabasvr01 postfix/local[25200]: 65EB4398050: to=<paul.hobbs@domain2.com>, relay=local, delay=0, status=bounced (unknown user: "paul.hobbs")
Dec  5 23:44:09 ozsabasvr01 postfix/cleanup[25199]: 7C6F7398054: message-id=<20071205134409.7C6F7398054@vmhost.domain1.com>
Dec  5 23:44:09 ozsabasvr01 postfix/qmgr[25114]: 7C6F7398054: from=<>, size=2339, nrcpt=1 (queue active)
Dec  5 23:44:09 ozsabasvr01 postfix/qmgr[25114]: 65EB4398050: removed
Dec  5 23:44:09 ozsabasvr01 postfix/local[25200]: 7C6F7398054: to=<admin@domain1.com>, relay=local, delay=0, status=bounced (unknown user: "admin")
Dec  5 23:44:09 ozsabasvr01 postfix/qmgr[25114]: 7C6F7398054: removed
```

The web application tried to send an email to me ([EMAIL]paul.hobbs@domain2.com[/EMAIL]).  It was sent from [email]admin@domain1.com[/email].

The log file is saying ```
status=bounced (unknown user: "paul.hobbs")
```

I have no idea why it is doing this.  Help!

---

