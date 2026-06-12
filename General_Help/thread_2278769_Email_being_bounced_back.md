---
title: "Email being bounced back"
date: 2015-05-18
forum: General Help
---

### Post by sashi4 on 2015-05-18
Hi team,

Good day to all of you. Today i bumped with another issue, this time it's a little weird. If you noticed the header message, (Final-Recipient: rfc822; [EMAIL="monitor@domainexample.com"]monitor@domainexample.com[/EMAIL]). What is the cause root of this issue?

User <geraldine@abc.org.my> is a valid user, she has sent a mail to another valid user <sashi@abc.org.my>, the question is from where does this address <monitor@domainexample.com> came from? Is this some soft of virus or something like that? How to overcome this issue?

Server - Ubuntu 14.01 LTS
MTA - Postfix 2.11.0

Client : Windows 7 Pro

Can anyone please shed some light, many thanks in advance.




Header
-----------
[HTML]Reporting-MTA: dns; mx1.abc.org.my 
X-Postfix-Queue-ID: 02846906A2C 
X-Postfix-Sender: rfc822; geraldine@abc.org.my 
Arrival-Date: Tue, 19 May 2015 10:41:16 +0800 (MYT) 
 
Final-Recipient: rfc822; monitor@domainexample.com 
Original-Recipient: rfc822;sashi@abc.org.my 
Action: failed 
Status: 5.1.1 
Remote-MTA: dns; mail.domainexample.com 
Diagnostic-Code: smtp; 550 5.1.1 <monitor@domainexample.com>: Recipient address 
    rejected: User unknown in virtual mailbox table
[/HTML]


NDR
------
[HTML]This is the mail system at host mx1.abc.org.my. 
 
I'm sorry to have to inform you that your message could not 
be delivered to one or more recipients. It's attached below. 
 
For further assistance, please send mail to <postmaster> 
 
If you do so, please include this problem report. You can 
delete your own text from the attached returned message. 
 
                   The mail system 
 
<monitor@domainexample.com>: host mail.domainexample.com[216.55.187.235] said: 
    550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User 
    unknown in virtual mailbox table (in reply to RCPT TO command)[/HTML]


UPDATES - This only happens for mail message to & from yahoo.com :sad:
---------------

[HTML]
root@aibd001:/etc/postfix# grep monitor@domainexample.com /var/log/mail.log
May 18 11:16:06 aibd001 postfix/cleanup[25984]: 18A8B906780: redirect: header To: lina arena <linaarena@yahoo.com> from unknown[122.255.108.146]; from=<hamidah@aibd.org.my> to=<linaarena@yahoo.com> proto=ESMTP helo=<[10.10.10.35]>: monitor@domainexample.com
May 18 11:16:22 aibd001 postfix/smtp[26207]: AA97E906782: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=16, delays=7.3/0/8.3/0.72, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 18 14:00:15 aibd001 postfix/cleanup[14373]: 5227C9067FB: redirect: header To: nunik widarty <nunikwidarty@yahoo.com> from unknown[122.255.108.146]; from=<ravis@aibd.org.my> to=<nunikwidarty@yahoo.com> proto=ESMTP helo=<[10.10.10.73]>: monitor@domainexample.com
May 18 14:00:24 aibd001 postfix/smtp[14629]: E60479067FD: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=9.4, delays=6.5/0/2.5/0.39, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 18 14:13:20 aibd001 postfix/cleanup[16329]: 40AD490680A: redirect: header To: nunik widarty <nunikwidarty@yahoo.com> from unknown[122.255.108.146]; from=<ravis@aibd.org.my> to=<sashi@aibd.org.my> proto=ESMTP helo=<[10.10.10.73]>: monitor@domainexample.com
May 18 14:13:28 aibd001 postfix/smtp[16379]: 76F0690680C: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=19, delays=17/0/1.2/0.51, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 18 14:14:19 aibd001 postfix/cleanup[16329]: 528DD90680C: redirect: header To: nunik widarty <nunikwidarty@yahoo.com> from unknown[122.255.108.146]; from=<ravis@aibd.org.my> to=<sashi@aibd.org.my> proto=ESMTP helo=<[10.10.10.73]>: monitor@domainexample.com
May 18 14:14:28 aibd001 postfix/smtp[16379]: BEF6D906811: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=19, delays=18/0/0.82/0.56, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 18 14:29:38 aibd001 postfix/cleanup[18300]: 437DF90681E: redirect: header To: nunik widarty <nunikwidarty@yahoo.com> from unknown[122.255.108.146]; from=<ravis@aibd.org.my> to=<sashi@aibd.org.my> proto=ESMTP helo=<[10.10.10.73]>: monitor@domainexample.com
May 18 14:29:48 aibd001 postfix/smtp[18501]: ED908906820: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=9.8, delays=8.4/0/0.96/0.36, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 18 14:34:34 aibd001 postfix/cleanup[18880]: CA9D6906822: redirect: header To: nunik widarty <nunikwidarty@yahoo.com> from unknown[122.255.108.146]; from=<ravis@aibd.org.my> to=<nunikwidarty@yahoo.com> proto=ESMTP helo=<[10.10.10.73]>: monitor@domainexample.com
May 18 14:34:44 aibd001 postfix/smtp[18923]: AAB47906825: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=10, delays=6.5/0/2.9/0.68, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 18 14:35:21 aibd001 postfix/cleanup[18880]: 896C8906826: redirect: header To: nunik widarty <nunikwidarty@yahoo.com> from unknown[122.255.108.146]; from=<ravis@aibd.org.my> to=<nunikwidarty@yahoo.com> proto=ESMTP helo=<[10.10.10.73]>: monitor@domainexample.com
May 18 14:35:34 aibd001 postfix/smtp[18923]: B1D0C906825: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=13, delays=11/0/1.3/0.32, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 18 16:05:24 aibd001 postfix/cleanup[31116]: 0CF8E906876: redirect: header To: nunik widarty <nunikwidarty@yahoo.com> from unknown[122.255.108.146]; from=<ravis@aibd.org.my> to=<nunikwidarty@yahoo.com> proto=ESMTP helo=<[10.10.10.73]>: monitor@domainexample.com
May 18 16:05:32 aibd001 postfix/smtp[31326]: A5D14906879: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=8.2, delays=5.5/0/2/0.65, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 18 16:33:08 aibd001 postfix/cleanup[1683]: 37169906893: redirect: header From: nunik widarty <nunikwidarty@yahoo.com> from nm48-vm5.bullet.mail.ne1.yahoo.com[98.138.121.117]; from=<nunikwidarty@yahoo.com> to=<ravis@aibd.org.my> proto=ESMTP helo=<nm48-vm5.bullet.mail.ne1.yahoo.com>: monitor@domainexample.com
May 18 16:33:16 aibd001 postfix/smtp[2575]: F06ED906894: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=19, delays=17/0/1.2/0.36, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 18 17:08:48 aibd001 postfix/cleanup[7045]: 48EEC906869: redirect: header To: nunik widarty <nunikwidarty@yahoo.com> from mail-la0-f53.google.com[209.85.215.53]; from=<ravis36@gmail.com> to=<ravis@aibd.org.my> proto=ESMTP helo=<mail-la0-f53.google.com>: monitor@domainexample.com
May 18 17:08:58 aibd001 postfix/smtp[7054]: 2E42490688A: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=21, delays=18/0/2.1/0.35, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 18 17:23:57 aibd001 postfix/cleanup[9034]: AD0B2905EE6: redirect: header From: nunik widarty <nunikwidarty@yahoo.com> from nm37-vm4.bullet.mail.ne1.yahoo.com[98.138.229.132]; from=<nunikwidarty@yahoo.com> to=<sashi@aibd.org.my> proto=ESMTP helo=<nm37-vm4.bullet.mail.ne1.yahoo.com>: monitor@domainexample.com
May 18 17:24:05 aibd001 postfix/smtp[9042]: A96789061C3: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=20, delays=18/0/2.1/0.31, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 18 18:01:42 aibd001 postfix/cleanup[14057]: B9D35906677: redirect: header To: "Nasrullah Md. Irfan" <director.liaison@yahoo.com> from unknown[122.255.108.146]; from=<vasuhi@aibd.org.my> to=<director.liaison@yahoo.com> proto=ESMTP helo=<[10.10.10.33]>: monitor@domainexample.com
May 18 18:01:53 aibd001 postfix/smtp[14069]: 1E99C906896: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=11, delays=6.6/0/3.4/0.86, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 18 18:08:05 aibd001 postfix/cleanup[14940]: 8CBCD9067DF: redirect: header To: Afifa Afroz <afifa_afroz@yahoo.com> from unknown[122.255.108.146]; from=<vasuhi@aibd.org.my> to=<afifa_afroz@yahoo.com> proto=ESMTP helo=<[10.10.10.33]>: monitor@domainexample.com
May 18 18:08:12 aibd001 postfix/smtp[14949]: 772B89068C6: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=17, delays=15/0/1.1/0.34, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 18 18:08:42 aibd001 postfix/cleanup[14940]: 6B7139068C6: redirect: header To: Afifa Afroz <afifa_afroz@yahoo.com> from unknown[122.255.108.146]; from=<vasuhi@aibd.org.my> to=<afifa_afroz@yahoo.com> proto=ESMTP helo=<[10.10.10.33]>: monitor@domainexample.com
May 18 18:08:50 aibd001 postfix/smtp[14949]: 851B49068C8: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=7.6, delays=6.6/0/0.68/0.3, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 18 18:09:41 aibd001 postfix/cleanup[14940]: 5778D9068C8: redirect: header To: Afifa Afroz <afifa_afroz@yahoo.com> from unknown[122.255.108.146]; from=<vasuhi@aibd.org.my> to=<sashi@aibd.org.my> proto=ESMTP helo=<[10.10.10.33]>: monitor@domainexample.com
May 18 18:09:49 aibd001 postfix/cleanup[14940]: E7BC99068C8: redirect: header To: "Nasrullah Md. Irfan" <director.liaison@yahoo.com> from unknown[122.255.108.146]; from=<vasuhi@aibd.org.my> to=<sashi@aibd.org.my> proto=ESMTP helo=<[10.10.10.33]>: monitor@domainexample.com
May 18 18:09:50 aibd001 postfix/smtp[14949]: AE25F9068C9: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=8.6, delays=7.3/0/0.99/0.36, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 18 18:09:57 aibd001 postfix/smtp[14949]: 990E89068CC: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=8.3, delays=7.2/0/0.78/0.31, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 18 18:10:14 aibd001 postfix/cleanup[14940]: DA3C89068CC: redirect: header To: Afifa Afroz <afifa_afroz@yahoo.com> from unknown[122.255.108.146]; from=<vasuhi@aibd.org.my> to=<afifa_afroz@yahoo.com> proto=ESMTP helo=<[10.10.10.33]>: monitor@domainexample.com
May 18 18:10:22 aibd001 postfix/smtp[14949]: 678669068CE: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=7.2, delays=6.2/0/0.7/0.3, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 18 20:28:57 aibd001 postfix/cleanup[31681]: BC2139021EA: redirect: header From: Buddhi <gkhatry_1969@yahoo.com> from nm7-vm3.bullet.mail.ne1.yahoo.com[98.138.91.137]; from=<gkhatry_1969@yahoo.com> to=<rabi@aibd.org.my> proto=ESMTP helo=<nm7-vm3.bullet.mail.ne1.yahoo.com>: monitor@domainexample.com
May 18 20:29:06 aibd001 postfix/smtp[31686]: 967B79068F4: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=21, delays=18/0/1.9/0.82, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 19 01:22:40 aibd001 postfix/cleanup[2227]: D67CD906952: redirect: header From: lindasz Salleh <lindaszsalleh.goldenservices@yahoo.com> from nm27-vm8.bullet.mail.sg3.yahoo.com[106.10.151.135]; from=<lindaszsalleh.goldenservices@yahoo.com> to=<hamidah@aibd.org.my> proto=ESMTP helo=<nm27-vm8.bullet.mail.sg3.yahoo.com>: monitor@domainexample.com
May 19 01:22:51 aibd001 postfix/smtp[2288]: 1C78D906953: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=21, delays=17/0/3.6/0.48, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 19 09:13:36 aibd001 postfix/cleanup[24605]: 1CF18904227: redirect: header From: lina arena <linaarena@yahoo.com> from omp1030.mail.bf1.yahoo.com[98.139.212.221]; from=<linaarena@yahoo.com> to=<hamidah@aibd.org.my> proto=ESMTP helo=<omp1030.mail.bf1.yahoo.com>: monitor@domainexample.com
May 19 09:13:51 aibd001 postfix/smtp[24888]: 1C4B39069A9: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=26, delays=22/0/3.2/0.49, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 19 10:34:42 aibd001 postfix/cleanup[2754]: 9ED38906A0F: redirect: header To: Afifa Afroz <afifa_afroz@yahoo.com> from unknown[122.255.108.146]; from=<geraldine@aibd.org.my> to=<afifa_afroz@yahoo.com> proto=ESMTP helo=<[10.10.10.63]>: monitor@domainexample.com
May 19 10:34:51 aibd001 postfix/smtp[3039]: 7FB0A906A11: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=9.2, delays=6.5/0/2.1/0.57, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 19 10:41:16 aibd001 postfix/cleanup[2714]: 2BC5F906A2A: redirect: header To: Afifa Afroz <afifa_afroz@yahoo.com> from unknown[122.255.108.146]; from=<geraldine@aibd.org.my> to=<sashi@aibd.org.my> proto=ESMTP helo=<[10.10.10.63]>: monitor@domainexample.com
May 19 10:41:25 aibd001 postfix/smtp[4261]: 02846906A2C: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=9.2, delays=7.8/0/0.87/0.52, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 19 11:28:53 aibd001 postfix/cleanup[10549]: C93A5906A5C: redirect: header To: "Nasrullah Md. Irfan" <director.liaison@yahoo.com> from unknown[122.255.108.146]; from=<rabi@aibd.org.my> to=<director.liaison@yahoo.com> proto=ESMTP helo=<[10.10.10.62]>: monitor@domainexample.com
May 19 11:29:04 aibd001 postfix/smtp[10617]: 201EF906A6D: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=11, delays=8.6/0/2.5/0.35, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 19 12:44:54 aibd001 postfix/cleanup[20638]: 05A5F906AB3: redirect: header From: COCI Cambodia <cocicambodia@yahoo.com> from nm6.bullet.mail.bf1.yahoo.com[98.139.212.165]; from=<cocicambodia@yahoo.com> to=<hamidah@aibd.org.my> proto=ESMTP helo=<nm6.bullet.mail.bf1.yahoo.com>: monitor@domainexample.com
May 19 12:45:04 aibd001 postfix/smtp[20647]: 40D5A906AB6: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=21, delays=18/0/2.6/0.67, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 19 13:18:18 aibd001 postfix/cleanup[24813]: 93D52906ACE: redirect: header From: COCI Cambodia <cocicambodia@yahoo.com> from nm30-vm0.bullet.mail.bf1.yahoo.com[98.139.213.126]; from=<cocicambodia@yahoo.com> to=<admin@aibd.org.my> proto=ESMTP helo=<nm30-vm0.bullet.mail.bf1.yahoo.com>: monitor@domainexample.com
May 19 13:18:18 aibd001 postfix/cleanup[24811]: 93381906AC5: redirect: header From: COCI Cambodia <cocicambodia@yahoo.com> from nm30-vm0.bullet.mail.bf1.yahoo.com[98.139.213.126]; from=<cocicambodia@yahoo.com> to=<hamidah@aibd.org.my> proto=ESMTP helo=<nm30-vm0.bullet.mail.bf1.yahoo.com>: monitor@domainexample.com
May 19 13:18:25 aibd001 postfix/smtp[24825]: 02273906ACE: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=19, delays=17/0.01/1.6/0.33, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 19 13:18:25 aibd001 postfix/smtp[24824]: C19D3906ACF: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=17, delays=15/0/1.8/0.31, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 19 13:39:57 aibd001 postfix/cleanup[27680]: 0E5F4906AD2: redirect: header To: "Nasrullah Md. Irfan" <director.liaison@yahoo.com> from unknown[122.255.108.146]; from=<vasuhi@aibd.org.my> to=<director.liaison@yahoo.com> proto=ESMTP helo=<[10.10.10.33]>: monitor@domainexample.com
May 19 13:40:04 aibd001 postfix/smtp[27714]: 4CA96906AF2: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=7.3, delays=6.2/0/0.8/0.33, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 19 14:20:41 aibd001 postfix/cleanup[350]: 418C0906B15: redirect: header From: lina arena <linaarena@yahoo.com> from omp1021.mail.bf1.yahoo.com[98.139.212.212]; from=<linaarena@yahoo.com> to=<hamidah@aibd.org.my> proto=ESMTP helo=<omp1021.mail.bf1.yahoo.com>: monitor@domainexample.com
May 19 14:21:02 aibd001 postfix/smtp[387]: 32CE6906B17: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=32, delays=29/0/1.8/0.32, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 19 14:28:49 aibd001 postfix/cleanup[1444]: D8B0190689D: redirect: header From: lindasz Salleh <lindaszsalleh.goldenservices@yahoo.com> from nm3-vm7.bullet.mail.sg3.yahoo.com[106.10.148.118]; from=<lindaszsalleh.goldenservices@yahoo.com> to=<hamidah@aibd.org.my> proto=ESMTP helo=<nm3-vm7.bullet.mail.sg3.yahoo.com>: monitor@domainexample.com
May 19 14:28:58 aibd001 postfix/smtp[1453]: 65737906B1B: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=19, delays=18/0/0.74/0.33, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 19 14:41:23 aibd001 postfix/cleanup[2961]: DD5D8906B17: redirect: header To: lindasz Salleh <lindaszsalleh.goldenservices@yahoo.com> from unknown[122.255.108.146]; from=<hamidah@aibd.org.my> to=<lindaszsalleh.goldenservices@yahoo.com> proto=ESMTP helo=<[10.10.10.35]>: monitor@domainexample.com
May 19 14:41:32 aibd001 postfix/smtp[2994]: BC3C8906B28: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=8.5, delays=6.9/0/1.1/0.5, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 19 14:43:07 aibd001 postfix/cleanup[2961]: 65056906B28: redirect: header From: lindasz Salleh <lindaszsalleh.goldenservices@yahoo.com> from nm18-vm3.bullet.mail.sg3.yahoo.com[106.10.149.98]; from=<lindaszsalleh.goldenservices@yahoo.com> to=<hamidah@aibd.org.my> proto=ESMTP helo=<nm18-vm3.bullet.mail.sg3.yahoo.com>: monitor@domainexample.com
May 19 14:43:16 aibd001 postfix/smtp[3387]: EA575906B29: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=19, delays=18/0/0.78/0.31, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 19 14:51:24 aibd001 postfix/cleanup[4366]: 8F445906B24: redirect: header To: lindasz Salleh <lindaszsalleh.goldenservices@yahoo.com> from unknown[122.255.108.146]; from=<hamidah@aibd.org.my> to=<lindaszsalleh.goldenservices@yahoo.com> proto=ESMTP helo=<[10.10.10.35]>: monitor@domainexample.com
May 19 14:51:26 aibd001 postfix/cleanup[4366]: 7CF8A906B30: redirect: header From: Juliyana Hussain <juliyanahussain@yahoo.com> from nm2-vm5.bullet.mail.ne1.yahoo.com[98.138.91.224]; from=<juliyanahussain@yahoo.com> to=<vasuhi@aibd.org.my> proto=ESMTP helo=<nm2-vm5.bullet.mail.ne1.yahoo.com>: monitor@domainexample.com
May 19 14:51:40 aibd001 postfix/smtp[4380]: 6930B906B30: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=26, delays=24/0.01/1.6/0.35, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
May 19 14:51:40 aibd001 postfix/smtp[4379]: BF37E906B31: to=<monitor@domainexample.com>, relay=mail.domainexample.com[216.55.187.235]:25, delay=26, delays=23/0/1.6/0.49, dsn=5.1.1, status=bounced (host mail.domainexample.com[216.55.187.235] said: 550 5.1.1 <monitor@domainexample.com>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command))
[/HTML]

---

### Post by SeijiSensei on 2015-05-19
I'd start by talking with your ISP and ensuring you're allowed to send mail.  Maybe your messages are being intercepted upstream.

---

### Post by alex382 on 2015-05-19
And check if all your DNS servers are well configured.

---

### Post by sashi4 on 2015-05-19
Hi Alex,

Thank you. Yes, i have double checked all my DNS server & DNS records.

---

### Post by sashi4 on 2015-05-19
Hi Seiji,

Thank you. The funny part is that if you browse to [http://mail.domainexample.com/](http://mail.domainexample.com/), the page opens up. Thisi s valid & active domain name.

---

### Post by sashi4 on 2015-05-21
Dear Friends,

Kindly accept my apologies, it was my mistake. I was playing around with header_check and this is the cause root of the problem. I am sorry once again to waste everyone's time. Apparently these 2 lines were the culprits.

[HTML]
#/^From:(.*)<(.*)@yahoo.com>(.*)/    REDIRECT monitor@domainexample.com
#/^To:(.*)<(.*)@yahoo.com>(.*)/  REDIRECT monitor@domainexample.com
[/HTML]

---

