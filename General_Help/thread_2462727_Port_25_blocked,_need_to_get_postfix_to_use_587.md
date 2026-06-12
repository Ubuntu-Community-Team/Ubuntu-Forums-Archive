---
title: "Port 25 blocked, need to get postfix to use 587"
date: 2021-05-26
forum: General Help
---

### Post by jdstaffon on 2021-05-26
My new ISP blocks port 25 outbound. Before I changed ISPs I would have a cron job on my linux NAS box perform an mdadm command, create a log file and then mail the log
file to me at my Gmail account. It worked slick for years until my new ISP. I have verified port 25 is blocked and that port 587 is open. I followed some suggestions to get Postfix to use a relay and port 587. That doesn't seem to work. I either don't understand what system to use as the relay or my errors are telling me I'm not authorized to use the relay. The following is the script that checks my RAID and then sends me an email with the body being the log file created by the script.

```
##########
# Check for a good internet connection.
wget --spider --quiet [http://yahoo.com](http://yahoo.com)
if [ "$?" != 0 ]; then
  echo "Internet Connection down!" | mail -s "Internet issues" <user>@gmail.com
fi


echo `date` > /tmp/nas-raid-status.log
echo >> /tmp/nas-raid-status.log


/sbin/mdadm --detail /dev/md0 >> /tmp/nas-raid-status.log
echo "-----" >> /tmp/nas-raid-status.log
echo >> /tmp/nas-raid-status.log


echo `date` >> /tmp/nas-raid-status.log


cat /tmp/nas-raid-status.log | mail -s "NAS RAID Status" <user>@gmail.com
##########
```

The following are the entries I added to my main.cf file in /etc/postfix.

```
###########
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = static:<user>@gmail.com:Password
smtp_sasl_security_options = noanonymous
smtp_tls_security_level = encrypt
relayhost = [smtp.gmail.com]:587
###########
```

The following are the errors in /var/log/mail.log

```

May 26 13:07:47 xxxxxxxx postfix/pickup[4909]: D9398E601AA: uid=0 from=<root@xxxxxxxx.com>
May 26 13:07:47 xxxxxxxx postfix/cleanup[5221]: D9398E601AA: message-id=<20210526190747.D9398E601AA@nas>
May 26 13:07:47 xxxxxxxx postfix/qmgr[4910]: D9398E601AA: from=<root@xxxxxxxx.com>, size=1258, nrcpt=1 (queue active)
May 26 13:07:48 xxxxxxxx postfix/smtp[5223]: D9398E601AA: SASL authentication failed; server smtp.gmail.com[172.253.117.109] said: 535-5.7.8 Username and Password not accepted. Learn more at?535 5.7.8  [https://support.google.com/mail/?p=BadCredentials](https://support.google.com/mail/?p=BadCredentials) n12sm14789pjk.48 - gsmtp
May 26 13:07:48 xxxxxxxx postfix/smtp[5223]: connect to smtp.gmail.com[2607:f8b0:400e:c0a::6c]:587: Network is unreachable
May 26 13:07:48 xxxxxxxx postfix/smtp[5223]: D9398E601AA: to=<xxxxxxxx@gmail.com>, relay=none, delay=0.84, delays=0.08/0.02/0.75/0, dsn=4.4.1, status=deferred (connect to smtp.gmail.com[2607:f8b0:400e:c0a::6c]:587: Network is unreachable)
```

---

### Post by HermanAB on 2021-05-26
The best source for information is the Postfix web site:
[http://www.postfix.org/TLS_README.html](http://www.postfix.org/TLS_README.html)

---

### Post by jdstaffon on 2021-05-26
Thanks for the reply. That's a great article. After reading the section that applies to my situation, I'm still confused about one thing. The "relayhost" directive. Is it suppose to be "Gmail/Google" for my example or is it suppose to be my local linux machine that is sending the message to my Gmail account? That's unclear in all of the docs that I've read.

---

### Post by jdstaffon on 2021-05-26
SOLVED: Everything in my configuration files and scripts are correct. It was a configuration change I needed to make on the Gmail side of things. Since I was using two factor authentication on my Gmail, I needed to create an App Password for my linux boxes that were sending the mail to me. Once I did that, it just started working. I followed the Google Help page.

[https://support.google.com/mail/answer/185833?hl=en](https://support.google.com/mail/answer/185833?hl=en)

Following this procedure created a large random password for my Linux boxes. I copied and pasted that password into the line -

[COLOR=#000000][FONT=&quot]smtp_sasl_password_maps = static:<user>@gmail.com:Password[/FONT][/COLOR] 

Thanks!

---

### Post by TheFu on 2021-05-26
> **jdstaffon said:**
> Thanks for the reply. That's a great article. After reading the section that applies to my situation, I'm still confused about one thing. The "relayhost" directive. Is it suppose to be "Gmail/Google" for my example or is it suppose to be my local linux machine that is sending the message to my Gmail account? That's unclear in all of the docs that I've read.

Well, really the relay host should have been the ISP's relay host on port 25.

There are 3 SMTP(s) ports for MTAs like postfix, sendmail, exim.  

[LIST]
[*]25/tcp - this is the default port configured for mail server -to- mail server communications.  This is how random servers can send email to any other random email server on the internet.
[*]465/tcp - authenticated SMTP. This requires a client to authenticate using a userid and password. Often the userid would be the email address, but not necessarily the situation.  This is a client -to- server connection. Generally used only by email clients like Outlook or Thunderbird or K9-Mail or Alpine.
[*]587/tcp - authenticated SMTP.  This requires a client to authenticate using a userid and password. Often the userid would be the email address, but not necessarily the situation. This is a client -to- server connection.  Generally used only by email clients like Outlook or Thunderbird or K9-Mail or Alpine.
[/LIST]
I honestly don't know why there is both 465 and 587 authenticated SMTP.  Perhaps the industry picked one and Microsoft chose the other?  IDK.

It is the 25/tcp - server-to-server port that ISPs typically block to cut back on spammer emails coming from their netblocks.

BTW, sending system emails to gmail really isn't very secure.  Most email isn't encrypted, so it is like a postcard in the mail. There is almost always sensitive information inside system data.

I'd rather see you setup an IMAP server at home, have it poll gmail plus 10 other email accounts and pull all messages local. Then you could connect to your home server over a VPN (you'd run the VPN server) and access all your email in 1, secured, location.  Only 1 port would need to be open for inbound connections, just the VPN server. It isn't like anyone will get your 4K VPN key, right? For a simple, home, VPN server configuration, there is little chance of making a config mistake that let's the world in.  Plus, you could set it up to force all traffic go through your home connection, so no matter where you are in the world, all internet stuff you do would appear to originate from home.

For server-to-server MTA traffic, most of the time, people would setup some other port, say 2525/tcp to receive the email from a relay they run (free Amazon tier is fine).  Then just setup the domain MX DNS records to point at the relay server, which nearly immediately forwards to your home server.  I've been using an email gateway in that way for years.

---

### Post by TheFu on 2021-05-26
If this is really SOLVED, please use the "Thread Tools" button near the top of the page and mark it that way. Help the community find answers and don't waste the time for people seeking to be helpful.  Please.

---

### Post by CharlesA on 2021-05-27
> **TheFu said:**
> 
There are 3 SMTP(s) ports for MTAs like postfix, sendmail, exim.  

[LIST]
[*]25/tcp - this is the default port configured for mail server -to- mail server communications.  This is how random servers can send email to any other random email server on the internet.
[*]465/tcp - authenticated SMTP. This requires a client to authenticate using a userid and password. Often the userid would be the email address, but not necessarily the situation.  This is a client -to- server connection. Generally used only by email clients like Outlook or Thunderbird or K9-Mail or Alpine.
[*]587/tcp - authenticated SMTP.  This requires a client to authenticate using a userid and password. Often the userid would be the email address, but not necessarily the situation. This is a client -to- server connection.  Generally used only by email clients like Outlook or Thunderbird or K9-Mail or Alpine.
[/LIST]
I honestly don't know why there is both 465 and 587 authenticated SMTP.  Perhaps the industry picked one and Microsoft chose the other?  IDK.


I don't think I've ever seen port 465 in use. Most of the mail config I've dealt with uses port 587, including outlook.

Based on what I found [here]("https://www.mailgun.com/blog/which-smtp-port-understanding-ports-25-465-587/"), it looks like port 465 is a legacy port and the smtp specs say to use 25 or 587.

---

### Post by TheFu on 2021-05-27
That's me - Mr. Legacy!   Just checked and my email client does use 587/tcp to connect to my email server(s).  Oddly, an external account by a well-known email service said "default - 465" as the port.

The RFC: [https://datatracker.ietf.org/doc/html/rfc8314](https://datatracker.ietf.org/doc/html/rfc8314)  It says the same as that link.  
RFCs are usually very easy to read. They are written by people with practical knowledge who appreciate simplicity and accuracy.  Every major protocol on the internet is documented in that way.

I didn't look at the RFC and easily could/should have before posting.

---

### Post by rsteinmetz70112 on 2021-05-27
ATT uses 465 but they do a lot of odd things

---

### Post by TheFu on 2021-05-27
> **rsteinmetz70112 said:**
> ATT uses 465 but they do a lot of odd things

Much of AT&T email for customers is outsourced.  They still support domains they had through acquisitions 15 yrs ago!  My little email server got onto AT&T's virus spreading list-o-smtp servers after a friend using their service had his account hacked and sent ME an attachment with a MS-Office virus inside.  I responded back to him, without the attachment and that was sufficient.  I knew hundreds people inside AT&T and companies paid to run their servers at the time, including the people running the email servers for the domain my friend uses (he's still on it today).  Their answer was - fill out the removal form and that will work.  Well, it didn't.  Not for 5 yrs.  Then magically, it did. I think for a few years it was just a data gathering form, not really able to do anything, but I have no proof of that. ;)

If your subnet gets onto a block list, just hope it is one for a company like AT&T which is per-domain and not one of the big block lists like spamhaus.  If my domain was ever added to spamhaus, I'd get some new IP subnets.

---

### Post by SeijiSensei on 2021-05-28
I eventually had to implement DKIM signatures to reach some domains like Yahoo and Verizon. DK about ATT. I don't think anyone I correspond with has them as a provider. Still got a few bellatlantics and the like, but most of those domains were consolidated (under Verizon?). DKIM takes some effort, but it's pretty much mandatory if you have recipients on big services like AOL.

Even then I've had to go through the rigamarole removing my server from blacklists after being blocked for spurious reasons.

---

### Post by rsteinmetz70112 on 2021-05-28
Yahoo basically uses ATT servers because of some agreement they have.   So they publish using port 465

---

