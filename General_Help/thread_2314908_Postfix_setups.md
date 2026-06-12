---
title: "Postfix setups"
date: 2016-02-24
forum: General Help
---

### Post by ryan205 on 2016-02-24
Hi guys, I have used Linux a fair bit... But have 2 things I want to setup and wondered if I could have some help...

1st I have an exchange server.. I want to build an smtp relay on a vps to send from the exchange to the relay and then he relay sends out the mail for it.

2nd an anti spam filter for my exchange server. 

If if there is any really simple tutorials that people could point me to for these that would be brilliant .

thanks

---

### Post by TheFu on 2016-02-24
Scrollout F1

But I know ZERO about Exchange.

---

### Post by SeijiSensei on 2016-02-25
I run a mail filtering host using [MailScanner]("http://www.mailscanner.info/") ahead of an Exchange server at one client's site.  I only run RedHat flavors on servers, typically CentOS, for which installation of MailScanner is pretty easy.  However the current maintainer also releases [Debian/Ubuntu versions]("https://s3.amazonaws.com/mailscanner/release/v4/deb/MailScanner-4.85.2-3.deb.tar.gz") as well.  Uncompress the gzip archive and run the install.sh script.

MailScanner uses spamassassin to scan for spam and can use any of a variety of anti-virus programs to scan for malware.  I use [clamd]("https://help.ubuntu.com/community/ClamAV#Run_ClamAV_as_a_Daemon") for the latter.  It's faster than the other ClamAV-based scanners, and in our case, we are also running a Squid HTTP proxy on the machine that submits every downloaded object to clamd for scanning as well.

You would need to set up Postfix so it forwards all its mail to the Exchange server with the directive
```
relayhost = exchange.example.com
```
and configure Exchange to use the Linux box as its default relay as well.

You would then point your domain's MX record to the Linux box.  Inbound mail will be scanned for spam and viruses and passed to Exchange as appropriate.  You might want to disable scanning of outbound messages if you trust that your local network doesn't have machines infected with malware.  For instance, we exempt mail from localhost and messages originating on the Exchange server from spam scanning with rules
```

From:     127.0.0.1         yes
From:     ip.of.exch.srvr   yes

```
in a file called spam.whitelist.rules in MailScanner's rules directory.  See the extensively commented configuration file /etc/MailScanner/MailScanner. conf for details.

---

### Post by ryan205 on 2016-02-25
Lovely thank you for that! That's really helped out a lot for the incoming anti spam!! 

In terms of the smtp outbound relay for exchange How would I setup postfix to do this? It needs to send to the smtp really via a send connector over 587 then out from the mail relay on 25 as smtp

---

### Post by SeijiSensei on 2016-02-25
Exchange can use SMTP in both directions over port 25 as well.  That's how we have things configured at my client's site.  Why isn't that possible for you?

See: [https://support.microsoft.com/en-us/kb/265293](https://support.microsoft.com/en-us/kb/265293)

I guess you need the "SMTP connector."  That's not an extra-cost item is it?  Microsoft sure makes things complicated at times.

---

### Post by ryan205 on 2016-02-25
Hiya,

No this is because port 25 is blocked on my server... 

So I know you can use Ubuntu as a smtp relay but need a guide on how to set it up so I can send mail to it from my exchange... 

So I have a Windows vps with exchange running... Called mail.domain.com 
I them want my Linux Ubuntu vps called smtp.domain.com 

I then want exchange to use smtp. As a send connector to my Linux server over 587 auth smtp it then sends mail from the Linux server out over 25...

I've seen it done a few times but just don't know where I can find a guide

---

### Post by SeijiSensei on 2016-02-25
Well, that's going to be tricky with MailScanner.  It runs an instance of Postfix, sendmail, or exim as an SMTP listener.  Since it will be accepting mail from outside, it needs to listen on port 25.  

If you don't need to scan outgoing mail, then you could run two instances of Postfix, one tied to MailScanner on port 25, and another one that is bound to port 587.  I'd limit that one to accepting traffic only from the Exchange server either with a Postfix rule, or using iptables like this:

```
/sbin/iptables -A INPUT -p tcp -s ip.of.exch.srvr --dport 587 -j ACCEPT
/sbin/iptables -A INPUT -p tcp --dport 587 -j REJECT
```

Since this server is likely to be Internet-facing you're going to want a decent set of firewall rules that only accepts inbound traffic on port 25 and rejects anything else.  Just incorporate the rules above into your firewall ruleset.

I think it's actually possible to do this with one Postfix instance.  [This post]("http://serverfault.com/questions/481477/in-postfix-how-to-enforce-tls-auth-over-587-while-leaving-tls-optional-for-25") may give you some ideas.  You probably should read through the [Ubuntu Postfix guide]("https://help.ubuntu.com/community/Postfix") if you haven't done so already.

---

### Post by ryan205 on 2016-02-25
Any way we could hook up over Skype etc so you could lend a hand?

---

### Post by QIII on 2016-02-25
I doubt he'll do that.  He knows that will rob the rest of the community of the opportunity to learn.

Please.  If you start it on the Forums, have the courtesy to leave it here for other members to see the resolution.  This is a community.

Thanks.

---

### Post by ryan205 on 2016-02-25
Sorry I didn't mean it like that. was just so I can get some live help whilst building. Sorry to rough anyone up!

---

### Post by SeijiSensei on 2016-02-25
Not to be harsh, but people pay me for assistance like that.  :D

---

