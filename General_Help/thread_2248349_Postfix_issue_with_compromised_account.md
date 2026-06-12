---
title: "Postfix issue with compromised account"
date: 2014-10-14
forum: General Help
---

### Post by Bob_OHara on 2014-10-14
Hi

We are moving our domains about 27 in all to a Postfix based server with a Zpanel control panel and Roundcube webmail. Suddenly we have a compromised account sending thousands of spam. Any way to determine which email account on the server it originates from? The from address is that of the supposed sender.

Bob

---

### Post by Bob_OHara on 2014-10-14
FYI here are some postfix logs but they don't show the senders account just the spammers addy. Again wondering if any way to track down:

Oct 14 07:33:20 custhost1 postfix/qmgr[986]: B2C8D1E01887: from=<kmcgrath@upperuwchlan-pa.gov>, size=2646, nrcpt=50 (queue active)
Oct 14 07:33:20 custhost1 postfix/qmgr[986]: BBCFC1E013CA: from=<kmcgrath@upperuwchlan-pa.gov>, size=2646, nrcpt=50 (queue active)
Oct 14 07:33:20 custhost1 postfix/qmgr[986]: BECB61E00AF2: from=<kmcgrath@upperuwchlan-pa.gov>, size=2646, nrcpt=50 (queue active)
Oct 14 07:33:20 custhost1 postfix/qmgr[986]: B998A1E01B75: from=<kmcgrath@upperuwchlan-pa.gov>, size=2636, nrcpt=50 (queue active)
Oct 14 07:33:20 custhost1 postfix/qmgr[986]: 7F9731E01119: from=<kmcgrath@upperuwchlan-pa.gov>, size=2646, nrcpt=50 (queue active)
Oct 14 07:33:20 custhost1 postfix/qmgr[986]: 73A271E010FE: from=<kmcgrath@upperuwchlan-pa.gov>, size=2646, nrcpt=50 (queue active)
Oct 14 07:33:20 custhost1 postfix/qmgr[986]: 709261E01CA9: from=<kmcgrath@upperuwchlan-pa.gov>, size=2636, nrcpt=50 (queue active)
Oct 14 07:33:20 custhost1 postfix/qmgr[986]: 772A61E01162: from=<kmcgrath@upperuwchlan-pa.gov>, size=2646, nrcpt=50 (queue active)
Oct 14 07:33:20 custhost1 postfix/qmgr[986]: 75D181E00F02: from=<kmcgrath@upperuwchlan-pa.gov>, size=2646, nrcpt=50 (queue active)
Oct 14 07:33:20 custhost1 postfix/qmgr[986]: 70DCB1E010C6: from=<kmcgrath@upperuwchlan-pa.gov>, size=2646, nrcpt=50 (queue active)
Oct 14 07:33:20 custhost1 postfix/qmgr[986]: 73DB91E010C7: from=<kmcgrath@upperuwchlan-pa.gov>, size=2646, nrcpt=50 (queue active)
Oct 14 07:33:20 custhost1 postfix/qmgr[986]: 7AC6A1E00C51: from=<kmcgrath@upperuwchlan-pa.gov>, size=2646, nrcpt=50 (queue active)
Oct 14 07:33:20 custhost1 postfix/qmgr[986]: 716001E01123: from=<kmcgrath@upperuwchlan-pa.gov>, size=2646, nrcpt=50 (queue active)
Oct 14 07:33:21 custhost1 postfix/qmgr[986]: 71E4C1E0076A: from=<kmcgrath@upperuwchlan-pa.gov>, size=2646, nrcpt=50 (queue active)
Oct 14 07:33:21 custhost1 postfix/qmgr[986]: 761AA1E01A2E: from=<kmcgrath@upperuwchlan-pa.gov>, size=2646, nrcpt=50 (queue active)
Oct 14 07:33:21 custhost1 postfix/qmgr[986]: 78C751E01124: from=<kmcgrath@upperuwchlan-pa.gov>, size=2646, nrcpt=50 (queue active)
Oct 14 07:33:21 custhost1 postfix/qmgr[986]: 772831E01C9A: from=<kmcgrath@upperuwchlan-pa.gov>, size=2636, nrcpt=50 (queue active)
Oct 14 07:33:21 custhost1 postfix/qmgr[986]: 79ABA1E01116: from=<kmcgrath@upperuwchlan-pa.gov>, size=2646, nrcpt=50 (queue active)
Oct 14 07:33:21 custhost1 postfix/qmgr[986]: 7BEEA1E01884: from=<kmcgrath@upperuwchlan-pa.gov>, size=2646, nrcpt=50 (queue active)
Oct 14 07:33:21 custhost1 postfix/qmgr[986]: 74CD51E007BB: from=<kmcgrath@upperuwchlan-pa.gov>, size=2646, nrcpt=50 (queue active)
Oct 14 07:33:21 custhost1 postfix/qmgr[986]: 7DC4A1E013C3: from=<kmcgrath@upperuwchlan-pa.gov>, size=2646, nrcpt=50 (queue active)
Oct 14 07:33:21 custhost1 postfix/qmgr[986]: F1C301E00A0E: from=<kmcgrath@upperuwchlan-pa.gov>, size=2646, nrcpt=50 (queue active)
Oct 14 07:33:22 custhost1 postfix/qmgr[986]: F1DD31E01111: from=<kmcgrath@upperuwchlan-pa.gov>, size=2646, nrcpt=50 (queue active)
Oct 14 07:34:03 custhost1 postfix/smtp[10837]: 4B6D11E01729: to=<viviane@techs.com.br>, relay=mail.techs.com.br[186.232.248.4]:25, delay=39993, delays=35133/4859/0.58/0.71, dsn=4.7.1, status=SOFTBOUNCE (host mail.techs.com.br[186.232.248.4] said: 501 5.7.1 <kmcgrath@upperuwchlan-pa.gov>... Sender refused by the DNSBL b.barracudacentral.org (in reply to RCPT TO command))
Oct 14 07:34:09 custhost1 postfix/smtp[10301]: 4A3ED1E01025: to=<tijolo@techs.com.br>, relay=mail.techs.com.br[186.232.248.4]:25, delay=40229, delays=35363/4865/0.56/0.37, dsn=4.7.1, status=SOFTBOUNCE (host mail.techs.com.br[186.232.248.4] said: 501 5.7.1 <kmcgrath@upperuwchlan-pa.gov>... Sender refused by the DNSBL b.barracudacentral.org (in reply to RCPT TO command))
Oct 14 07:34:37 custhost1 postfix/smtp[10971]: D39341E018C6: to=<wmotizuki@techs.com.br>, relay=mail.techs.com.br[186.232.248.4]:25, delay=39945, delays=35053/4891/0.58/0.59, dsn=4.7.1, status=SOFTBOUNCE (host mail.techs.com.br[186.232.248.4] said: 501 5.7.1 <kmcgrath@upperuwchlan-pa.gov>... Sender refused by the DNSBL b.barracudacentral.org (in reply to RCPT TO command))

---

### Post by SeijiSensei on 2014-10-14
Do you have log entries that show the origin of these messages?  Does your server relay mail for your clients, or do they only use Roundcube on the local machine?  

I'd be concerned you are running an open relay, but there isn't enough information in what you've given us to be sure.  Run the tests here: [http://mxtoolbox.com/problem/smtp/smtp-open-relay](http://mxtoolbox.com/problem/smtp/smtp-open-relay)

---

### Post by Bob_OHara on 2014-10-14
Ran the Open Relay tests on several sites early yesterday before this even happened including MX toolbox and a few that tested 20 different formats and all came back negative. Since this occurred access to SMTP has been blocked except for our Relay IP's listed in postfix and the Spamwall spamfilter our customers receive email from. So the issue itself should not reoccur. Looking for 2 things:

1) A way to track down the compromised account; probably a webmail account. Found this command line but had no success running it:

[root@somedomain /]# grep "dovecot" /var/log/mail.log |grep "Aborted login" |cut -d "," -f 3 |cut -d ":" -f 4 |sort -n |uniq -c

2) Another reply had said the from address: [email]kmcgrath@upperuwchlan-pa.gov[/email] - was not even a legitimate sender. If there a way to 
block these in postfix? Someone had suggested using fail2ban:

[http://www.howtoforge.com/fail2ban_debian_etch](http://www.howtoforge.com/fail2ban_debian_etch)

Bob

---

### Post by Bob_OHara on 2014-10-14
Here's what I have determined from doing a grep for the message ID for one of the spam messages. It appears a webmail account was compromised but looking for clarification to see if I'm correct. Here's a section of the log. As you can see if says sasl method=LOGIN then gives the username which is the same on all. What does this indicate. Was it logged in via the webmail, from his PC, or elsewhere?

Bob

root@custhost1:~# grep 123A51E01CDD /var/log/mail.log
Oct 13 20:41:03 custhost1 postfix/smtpd[5331]: 123A51E01CDD: client=unknown[162.                                                                             216.193.51], sasl_method=LOGIN, sasl_username=bgabrys@franklinpa.gov
Oct 13 20:41:04 custhost1 postfix/cleanup[6662]: 123A51E01CDD: message-id=<>
Oct 13 20:41:04 custhost1 postfix/qmgr[986]: 123A51E01CDD: from=<kmcgrath@upperu                                                                             wchlan-pa.gov>, size=2636, nrcpt=50 (queue active)
Oct 13 21:27:07 custhost1 postfix/error[11679]: 123A51E01CDD: to=<gsuabednars@ho                                                                             tmail.com>, relay=none, delay=2764, delays=1.9/2763/0/0.01, dsn=4.4.2, status=de                                                                             ferred (delivery temporarily suspended: lost connection with mx1.hotmail.com[65.

---

### Post by SeijiSensei on 2014-10-14
Do you have a corresponding entry in the Apache access logs for 162. 216.193.51?

---

