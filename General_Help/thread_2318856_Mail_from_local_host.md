---
title: "Mail from local host"
date: 2016-03-30
forum: General Help
---

### Post by Rakesh_vijayan on 2016-03-30
Hi all 

I has been searching for send email alert from server . Is there any easy way to setup configure local smtp to send alert ....

If I can send a single message from  root@localhost to [EMAIL="myemail@gmail.com"]myemail@gmail.com[/EMAIL] problem will be solve .If any body setup this already or know about this topic please 

share it 



Thanks in Advance

---

### Post by TheFu on 2016-03-30
"Easy way"?  Highly subjective.  SMTP is a simple protocol, until spam got involved. All the complexities have been added to make spam harder to send - especially from broadband connections.

Most of the answer depends on your ISP and their mail servers.  A few other people here have setup email from their home systems to their gmail accounts. Look for their posts for a how-to.  It is possible to use your ISP's SMTP-gateway(s) to forward all email, not just to gmail.  This isn't too hard for sending, but all outbound email will definitely have your IP address and may have your ISP email address as the sender (I don't recall).  Basically, you configure the local MTA, usually postfix, to use the ISP as an SMTP relay.  That's relatively simple, if your ISP allows it. [http://justatheory.com/computers/mail/postfix-and-comcast.html](http://justatheory.com/computers/mail/postfix-and-comcast.html)  Most ISPs block outbound port 25 traffic as a way to fight spam.  Port 465 or 587 will be needed if the system connects directly to gmail servers.  

Let me see if I can find a guide ... [https://help.ubuntu.com/community/GmailPostfixFetchmail](https://help.ubuntu.com/community/GmailPostfixFetchmail) ignore the fetchmail part. Easy?  Only you can say.

A little more complex example, that does more than just gmail.
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-as-a-send-only-smtp-server-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-as-a-send-only-smtp-server-on-ubuntu-14-04)

You'll also want to setup /etc/aliases to forward all email from root to the external account.

---

### Post by SeijiSensei on 2016-03-30
First you need to determine whether your ISP will let you send mail.  If you have a residential connection, you may not be able to send mail at all.  For a quick test, try running "telnet gmail-smtp-in.l.google.com 25" from a command prompt.  If you get a reply, you've passed the first hurdle.  If the connection just hangs, you won't be able to send any mail directly and need to talk with your ISP.

If you can connect with gmail, and you simply want to send mail from the local machine to GMail, install Postfix.  However you won't be able to send mail From: root@localhost.  GMail will require you to have a domain like [email]root@example.com[/email].  Once you have a valid domain name, you'll need to configure the program sending the mail to use that rather than root@localhost.

---

### Post by HermanAB on 2016-03-30
There are simple mail forwarders that are good for communication from processes e.g. ssmtp or null-mailer.

---

### Post by Rakesh_vijayan on 2016-04-04
Hi Sengi 

I can telnet > key$ telnet gmail-smtp-in.l.google.com 25
Trying 74.125.68.27...
Connected to gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP a3si40103663pfj.107 - gsmtp



When I Try to send mail from Aws instance I can send the mail by the following command 
> root@vps:/home/smile/public_html# mail -s test [EMAIL="rakeshnalukandathil@gmail.com"]rakeshnalukandathil@gmail.com[/EMAIL] </dev/null
mail: Null message body; hope that's ok
root@vps:/home/smile/public_html#

Same command I use from my local Machine I got the following error 
> root@rvd:~# mail -s test [EMAIL="rakeshnalukandathil@gmail.com"]rakeshnalukandathil@gmail.com[/EMAIL] </dev/null
A Sender: field is required with multiple addresses in From: field.
No such file or directory
. . . message not sent.
root@rvd:~# 



What will be the problem ?

> root@rvd:~# ps -e | grep sendmail
 1241 ?        00:00:00 S21sendmail
 1384 ?        00:00:00 sendmailconfig
28159 pts/28   00:00:00 sendmail
root@rvd:~# 



> root@rvd:~# ps -e | grep postfix

---

### Post by TheFu on 2016-04-04
Try from a different account - NOT root.
Also, did you install postfix or sendmail?  sendmail configs tend to be harder and used for complex setups where many domains are involved.  That's fine if you want/need that, but it will be much harder to configure than ssmtp, HermanAB's suggestion, or postfix.  

It looks like sendmail is installed.  I would remove that and try to get ssmtp working, since that config should be the easiest for this requirement.

---

