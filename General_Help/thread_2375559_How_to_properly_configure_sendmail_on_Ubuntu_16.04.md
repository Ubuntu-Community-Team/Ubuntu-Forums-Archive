---
title: "How to properly configure sendmail on Ubuntu 16.04(get rid of localhost.localdomain)?"
date: 2017-10-25
forum: General Help
---

### Post by dmitriano on 2017-10-25
I installed sendmail (in default configuration) on Ubuntu 16.04,

 my /etc/hosts contains this (as recommended [here]("https://www.abeautifulsite.net/configuring-sendmail-on-ubuntu-1404")):
```

127.0.0.1       developernote.com
127.0.0.1       localhost.localdomain localhost developernote.com
127.0.1.1       ubuntu.members.linode.com ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```
but the following command:

```
sendmail -t -i -v < body3.txt
```

where body3.txt contains:

```
Subject: test mail to Some Address 5!
From: Me <nx11118@yandex.ru>
To: Vasya <unixappdev@gmail.com>
first line of my message 2

```
produces log messages in /var/log/mail.log containing 'localhost.localdomain' and 'Service unavailable' and the mail does not come to GMail inbox:

```
Oct 25 12:50:21 localhost sendmail[6666]: v9PCoLxI006666: from=dmitriano, size=127, class=0, nrcpts=1, msgid=<201710251250.v9PCoLxI006666@localhost.localdomain>, relay=dmitriano@localhost
Oct 25 12:50:21 localhost sm-mta[6667]: v9PCoLiO006667: from=<dmitriano@localhost.localdomain>, size=364, class=0, nrcpts=1, msgid=<201710251250.v9PCoLxI006666@localhost.localdomain>, proto=ESMTP, daemon=MTA-v4, relay=developernote.com [127.0.0.1]
Oct 25 12:50:21 localhost sm-mta[6667]: STARTTLS=client, relay=gmail-smtp-in.l.google.com., version=TLSv1.2, verify=FAIL, cipher=ECDHE-RSA-AES128-GCM-SHA256, bits=128/128
Oct 25 12:50:21 localhost sm-mta[6667]: v9PCoLiO006667: to=<unixappdev@gmail.com>, ctladdr=<dmitriano@localhost.localdomain> (1000/1000), delay=00:00:00, xdelay=00:00:00, mailer=esmtp, pri=30364, relay=gmail-smtp-in.l.google.com. [IPv6:2a00:1450:400c:c08:0:0:0:1b], dsn=5.0.0, stat=Service unavailable
Oct 25 12:50:21 localhost sm-mta[6667]: v9PCoLiO006667: v9PCoLiP006667: DSN: Service unavailable
Oct 25 12:50:21 localhost sm-mta[6667]: v9PCoLiP006667: to=<dmitriano@localhost.localdomain>, delay=00:00:00, xdelay=00:00:00, mailer=local, pri=30000, dsn=2.0.0, stat=Sent
Oct 25 12:50:21 localhost sendmail[6666]: v9PCoLxI006666: to=Vasya <unixappdev@gmail.com>, ctladdr=dmitriano (1000/1000), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30127, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (v9PCoLiO006667 Message accepted for delivery)

```
I am not pretty sure, but I have an impression that GMail does not accept mail sent with localhost.localdomain, because if I send a mail in the same way to other mail servers it is sent and received fine.

Also it is not clear for me, should I set hosthame in /etc/hosthame? Currently file /etc/hosthame is empty.

How to get rid of this localhost.localdomain and what should I replace it with?

I saw [this solution]("https://serverfault.com/questions/484777/how-to-configure-a-real-domain-name-for-sender-address"), but it does not work for me, I am still getting localhost.localdomain in mail.log.

The following command:

```
endmail -t -i -v -f unixappdev@gmail.com < body3.txt
```

produces this log:

```
Oct 25 13:43:05 localhost sendmail[7086]: v9PDh5oH007086: Authentication-Warning: localhost.localdomain: dmitriano set sender to [EMAIL="unixappdev@gmail.com"]unixappdev@gmail.com[/EMAIL] using -f
Oct 25 13:43:05 localhost sendmail[7086]: v9PDh5oH007086: from=unixappdev@gmail.com, size=127, class=0, nrcpts=1, msgid=<201710251343.v9PDh5oH007086@localhost.localdomain>, relay=dmitriano@localhost
Oct 25 13:43:05 localhost sm-mta[7087]: v9PDh53q007087: from=<unixappdev@gmail.com>, size=467, class=0, nrcpts=1, msgid=<201710251343.v9PDh5oH007086@localhost.localdomain>, proto=ESMTP, daemon=MTA-v4, relay=developernote.com [127.0.0.1]
Oct 25 13:43:06 localhost sm-mta[7087]: STARTTLS=client, relay=gmail-smtp-in.l.google.com., version=TLSv1.2, verify=FAIL, cipher=ECDHE-RSA-AES128-GCM-SHA256, bits=128/128
Oct 25 13:43:06 localhost sm-mta[7087]: v9PDh53q007087: to=<unixappdev@gmail.com>, delay=00:00:01, xdelay=00:00:01, mailer=esmtp, pri=30467, relay=gmail-smtp-in.l.google.com. [IPv6:2a00:1450:400c:c08:0:0:0:1a], dsn=5.0.0, stat=Service unavailable
Oct 25 13:43:06 localhost sm-mta[7087]: v9PDh53q007087: v9PDh53r007087: DSN: Service unavailable
Oct 25 13:43:06 localhost sm-mta[7087]: STARTTLS=client, relay=gmail-smtp-in.l.google.com., version=TLSv1.2, verify=FAIL, cipher=ECDHE-RSA-AES128-GCM-SHA256, bits=128/128
Oct 25 13:43:06 localhost sm-mta[7087]: v9PDh53r007087: to=<unixappdev@gmail.com>, delay=00:00:00, xdelay=00:00:00, mailer=esmtp, pri=30000, relay=gmail-smtp-in.l.google.com. [IPv6:2a00:1450:400c:c08:0:0:0:1a], dsn=5.0.0, stat=Service unavailable
Oct 25 13:43:06 localhost sm-mta[7087]: v9PDh53r007087: to=MAILER-DAEMON, delay=00:00:00, mailer=local, pri=30000, dsn=5.1.1, stat=User unknown
Oct 25 13:43:06 localhost sm-mta[7087]: v9PDh53r007087: to=postmaster, delay=00:00:00, mailer=local, pri=30000, dsn=5.1.1, stat=User unknown
Oct 25 13:43:06 localhost sm-mta[7087]: v9PDh53r007087: v9PDh53s007087: return to sender: User unknown
Oct 25 13:43:06 localhost sm-mta[7087]: v9PDh53s007087: to=MAILER-DAEMON, delay=00:00:00, mailer=local, pri=0, dsn=5.1.1, stat=User unknown
Oct 25 13:43:06 localhost sm-mta[7087]: v9PDh53r007087: Saved message in /var/lib/sendmail/dead.letter
Oct 25 13:43:06 localhost sendmail[7086]: v9PDh5oH007086: to=Vasya <unixappdev@gmail.com>, ctladdr=unixappdev@gmail.com (1000/1000), delay=00:00:01, xdelay=00:00:01, mailer=relay, pri=30127, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (v9PDh53q007087 Message accepted for delivery)
```
it is noticeable that ```
verify=FAIL 
```here and still ```
DSN: Service unavailable. 
```Probably it is [something related to TSL]("https://serverfault.com/questions/816965/ubuntu-sendmail-gmail-relay-verify-fail-solved"), but at least I have ca-certificates package installed on my machine.

---

