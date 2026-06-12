---
title: "Gmail As a SMTP mail server / STARTTLS error"
date: 2008-05-28
forum: General Help
---

### Post by GamingRobot on 2008-05-28
Im new to linux and ubuntu.

I have a server running Ubuntu server 7.10

I am trying to setup SendEmail with smtp.gmail.com on port 465 or 587

here is where i got the information:
[http://mail.google.com/support/bin/a...n&answer=13287](http://mail.google.com/support/bin/a...n&answer=13287)

when i run this command:

sendEmail -f [email]xxxxxxxx@gmail.com[/email] -t [email]xxxxxxxxx@gmail.com[/email] -u 'this is a test' -m 'this is a message test' -s smtp.gmail.com:587 -xu [email]xxxxxxxxx@gmail.com[/email] -xp xxxxxxx

i get this error:
May 24 13:43:48 webserver sendEmail[19171]: NOTICE => Authentication not supported by the remote SMTP server!
May 24 13:43:48 webserver sendEmail[19171]: ERROR => Received: 530 5.7.0 Must issue a STARTTLS command first. y45sm9518823pyg.9

this is a progject to try and send email without a full mail client

Thanks in advance!

---

### Post by nnamdi on 2008-05-28
helo 

you could thunderbird that is what i use and it easyjust go to your snaptics and install it okthen you can configure it to get your gmail and yahoo mail account

---

### Post by sizzam on 2008-05-28
First, install these two packages which are needed for TLS support :
```
sudo apt-get install libio-socket-ssl-perl libnet-ssleay-perl
```

Then:
```
sendEmail -f from@gmail.com -t to@domain.com -u "This is my subject"  -m "Body of my message" -s smtp.gmail.com -o tls=yes -xu username -xp password
```

This command worked for me, I didn't have to specify a port for the SMTP server.

---

