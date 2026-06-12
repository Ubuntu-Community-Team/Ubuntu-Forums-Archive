---
title: "Creating Domain Email Addresses For Better Deliverability Inside Linux Command"
date: 2020-10-06
forum: General Help
---

### Post by aaronesteban on 2020-10-06
I've heard that it's best to create your own domain name address emails for better deliverability, versus using FREE ESP's such as Google, Yahoo, Hotmail, etc.. I'm referring to domain email addresses such as:


[EMAIL="info@mysite.com"]info@mysite.com[/EMAIL]
[EMAIL="shop@mysite.com"]shop@mysite.com[/EMAIL]
[EMAIL="contact@mysite.com"]contact@mysite.com[/EMAIL]
[EMAIL="sales@mysite.com"]sales@mysite.com[/EMAIL]
etc., etc.


I know that you can do this relatively easily in Linux command line by installing Roundcube, SquirrelMail, iRedMail, etc., etc., but I'm wondering what is the easiest and quickest way to do so after installing Postfix?


Do I need to install these additional apps or is there an easier way to just use Postfix to set up my domain email address and the SPF, DKIM, DMARC, records right after?


Any referring tutorials could also be helpful if you know of any to follow. Thanks again team!

---

### Post by TheFu on 2020-10-07
Running an email server on the internet isn't a small effort.  The protocol is really easy, but all the stuff added on to fight spam makes it 10x harder today than it was 25 yrs ago.

Before we start, you probably cannot run a useful email server on a residential connection. Most ISPs block all port 25 traffic in and out from their customers.  Do you have a business ISP or will you be running the email server at a VPS somewhere in their data center?  The days of running a web+email server at home for access to the world are long ended.

Besides that, you need:
[LIST=1]
[*]a paid, registered domain name.
[*]a public DNS server. The Registar record points to the public DNS so the world can find your different systems.
[*]a hosting system for the postfix daemon that allows inbound and outbound port 25/tcp. The public DNS points different services, like MX, to the specific system to provide that service.  MX is Mail eXchange.
[/LIST]

1 --> 2 --> 3.  That before any anti-spam stuff like SPF, DHCP IP address blocking, DKIM signatures get involved.

If your home computer is on a DHCP network (as set by the ISP), nobody will accept email from it. If the IP address isn't static, nobody will accept email from it even if it is a business.

If your setup doesn't meet all those requirements above, let's stop now.  Some references if you want to know more:
[LIST]
[*][https://ubuntu.com/server/docs/mail-postfix](https://ubuntu.com/server/docs/mail-postfix)
[*][https://www.linuxbabe.com/mail-server/setup-basic-postfix-mail-sever-ubuntu](https://www.linuxbabe.com/mail-server/setup-basic-postfix-mail-sever-ubuntu)
[*][https://www.vultr.com/docs/how-to-install-postfix-dovecot-and-roundcube-on-ubuntu-20-04](https://www.vultr.com/docs/how-to-install-postfix-dovecot-and-roundcube-on-ubuntu-20-04)
[/LIST]

Vultr is a VPS provider that uses SSDs for all storage and has $5/month VPS offers. A number of my friends use them for play systems they spin up for a day or two at a time.  email servers don't need hardly any CPU or RAM or storage.

1 last thing.  If the IP address you get from a provider is already on a spam block list, I'd request another ASAP. No need to fight someone else's battle to get off the world-wide spamming email lists.  I got on a single list from 1 ISP years ago. Took about 4 yrs to get off and I knew people inside that ISP.

---

### Post by aaronesteban on 2020-10-07
Hi TheFu, and thank you for your help first off.

I do apologize that I forgot to include that I've already set everything up as far as hosting and a domain name goes.

I'm using Digital Ocean as my main VPS hosting provider, have already connected my domain name from CheapDomain to my Digital Ocean, and already have PostFix installed.
I'm just trying to figure out if I really need to install the whole Webmin/VirtualMin setup to create domain email addresses or if I can just simply create these domain email addresses right after installing Postfix.

What would you recommend I do after having Postfix installed? I just need the domain email address and the SPF, DKIM, & DMARC records to go with the new setup.

Oh, and BTW, I am already using Amazon SES as my main SMTP server to send email.

Thanks again for your support.



> **TheFu said:**
> Running an email server on the internet isn't a small effort.  The protocol is really easy, but all the stuff added on to fight spam makes it 10x harder today than it was 25 yrs ago.

Before we start, you probably cannot run a useful email server on a residential connection. Most ISPs block all port 25 traffic in and out from their customers.  Do you have a business ISP or will you be running the email server at a VPS somewhere in their data center?  The days of running a web+email server at home for access to the world are long ended.

Besides that, you need:
[LIST=1]
[*]a paid, registered domain name.
[*]a public DNS server. The Registar record points to the public DNS so the world can find your different systems.
[*]a hosting system for the postfix daemon that allows inbound and outbound port 25/tcp. The public DNS points different services, like MX, to the specific system to provide that service.  MX is Mail eXchange.
[/LIST]

1 --> 2 --> 3.  That before any anti-spam stuff like SPF, DHCP IP address blocking, DKIM signatures get involved.

If your home computer is on a DHCP network (as set by the ISP), nobody will accept email from it. If the IP address isn't static, nobody will accept email from it even if it is a business.

If your setup doesn't meet all those requirements above, let's stop now.  Some references if you want to know more:
[LIST]
[*][https://ubuntu.com/server/docs/mail-postfix](https://ubuntu.com/server/docs/mail-postfix)
[*][https://www.linuxbabe.com/mail-server/setup-basic-postfix-mail-sever-ubuntu](https://www.linuxbabe.com/mail-server/setup-basic-postfix-mail-sever-ubuntu)
[*][https://www.vultr.com/docs/how-to-install-postfix-dovecot-and-roundcube-on-ubuntu-20-04](https://www.vultr.com/docs/how-to-install-postfix-dovecot-and-roundcube-on-ubuntu-20-04)
[/LIST]

Vultr is a VPS provider that uses SSDs for all storage and has $5/month VPS offers. A number of my friends use them for play systems they spin up for a day or two at a time.  email servers don't need hardly any CPU or RAM or storage.

1 last thing.  If the IP address you get from a provider is already on a spam block list, I'd request another ASAP. No need to fight someone else's battle to get off the world-wide spamming email lists.  I got on a single list from 1 ISP years ago. Took about 4 yrs to get off and I knew people inside that ISP.

---

### Post by TheFu on 2020-10-07
Webmin/VirtualMin is never needed. those just provide more attack vectors.  I've never used them after seeing the CVEs long ago.

Seems like you know more than me about manually setting this stuff up. I've been using scrollout as an email gateway and zimbra as the real server for about 12 yrs.  Before that, I used postfix + dovecot + squirrelmail.  Zimbra changed my life, but it is a hog.  I don't allow zimbra directly on the internet. That seems too risky to me.

---

### Post by SeijiSensei on 2020-10-07
In /etc/postfix/main.cf, add your domain to the mydestination directive.  Make sure the inet_interfaces directive includes your server's external IP address.  Restart Postfix.

From another machine, try "telnet yourserver.domain.name 25" and see if you can begin an SMTP session.

I usually just set up ordinary Linux accounts for my mail recipients so that mail for [email]username@domain.name[/email] is stored in /var/spool/mail/username and thus easily accessible via IMAP with Dovecot.  If you have a lot of users, Postfix can use a database.  SPF is something you add to your DNS records.  For DKIM, you'll need to use opendkim.  I downloaded the [source]("https://sourceforge.net/projects/opendkim/files/") for version 2.10.3 and compiled it myself, then followed the instructions to interface it with my SMTP exchanger.  (I use sendmail.)

---

