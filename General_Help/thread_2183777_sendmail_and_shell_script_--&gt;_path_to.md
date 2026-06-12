---
title: "sendmail and shell script --&gt; path to?"
date: 2013-10-26
forum: General Help
---

### Post by danhansendenmark on 2013-10-26
Hello [IMG]http://www.howtoforge.com/forums/images/smilies/wink.gif[/IMG]


I'm running an Ubuntu Server 12.04.2 - just a basic installation. No  Apache, No PHP or anything. I'm doing a shell script and this script  needs to send a mail. 
My port 25 IS open of course. To have the script send a mail on the  Ubuntu Server 12.04.2 I need to define a path for the mail client.  Here's a part of the script:

 echo '============================'
 echo '=         CPU Temp. i$ degrees         ='
 echo '============================'
  /sbin/shutdown -h now
  /usr/sbin/ssmtp [EMAIL="me@myemail.com"]me@myemail.com[/EMAIL] </home/xxx/MyScripts/hotcpu.txt
  echo 'Email Sent.....'
 exit

1. Is "sendmail" the default mail client in Ubuntu Server 12.04? 

2. I need the right path to put into my script. 

3. Will I need to protect the server against spammers? Server is in  network where router uses Fixed IP, LAN/NAT and server is running UFW         

                                                                                       __________________
                Kind Regards
Dan

---

### Post by TheFu on 2013-10-27
sendmail is a full-sized MTA, not an email "client."  Most people are better off using postfix over sendmail as their MTA.
Sending email may or may not require an MTA, it completely depends on the client used.  It is common for a scripting language to use the MTA to send email, but then the MTA must be properly configured for outbound email.  The ISP needs to allow it too.

If you are allowing inbound email ... there is a how-to. As a start, you'll need a domain, DNS service, properly configured MX record(s), ISP that doesn't block SMTP in/out traffic  (or an SMTP proxy service provider).  Email isn't like running a web server.

---

