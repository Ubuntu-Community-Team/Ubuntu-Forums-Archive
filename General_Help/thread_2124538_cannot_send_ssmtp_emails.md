---
title: "cannot send ssmtp emails"
date: 2013-03-11
forum: General Help
---

### Post by emaillo on 2013-03-11
[FONT=arial][SIZE=3]Hi folks !![/SIZE]

[SIZE=3]I have an ubuntu Amazon EC2's instance and a godday domain.[/SIZE]

[SIZE=3]When I try to send emails from ubuntu using the godaddy's smtp I get this error from /va/log/mail.err[/SIZE][COLOR=#000000]: 
[/COLOR][/FONT][COLOR=#000000][FONT=arial][SIZE=3][FONT=arial]sSMTP[6871]:STARTTLS not working
sSMTP[6871]: Cannot open smtpout.secureserver.net:80[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][SIZE=3][FONT=arial]The /etc/ssmtp/ssmtp.conf configuration is
UseSTARTTLS=YES
root=noreplay@mydomain.com
mailhub=smtpout.secureserver.net:80
[/FONT][/SIZE][FONT=arial]AuthUser=noreplay@mydomain.com
[/FONT][FONT=arial]AuthPass=xxxxxxxx
[/FONT][FONT=arial]UseTLS=YES
[/FONT][FONT=arial]rewriteDomain=mydomain.com
[/FONT][FONT=arial]hostname=domU-22-21-18-0A-67-33.compute-1.internal
[/FONT][/FONT][/COLOR]
I can reach smtpout.secureserver.net via telnet

[COLOR=#000000][FONT=arial][SIZE=3][FONT=arial]Any idea?[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][SIZE=3][FONT=arial]Thank you

EMC[/FONT][/SIZE][/FONT][/COLOR]

---

### Post by dave0109 on 2013-03-11
Reaching the port via telnet is one thing.  Using STARTTLS is another - the SSL connection is negotiated once the normal connection has been made.  You'll need to get more information about why the SSL is "not working" in order to debug further.

Are you sure about the port number?  Port 80 is usually for HTTP, and port 25 would be SMTP.  Of course, some services make use of port 80 to get through firewalls, so it might be unrelated.  Worth asking though.

---

