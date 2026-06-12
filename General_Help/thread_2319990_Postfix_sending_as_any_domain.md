---
title: "Postfix sending as any domain"
date: 2016-04-09
forum: General Help
---

### Post by joe207 on 2016-04-09
I have setup a postfix server on Ubuntu Server 14.04.4, but it will SEND mail as any domain, not just its own domain.

How do I stop this spammers dream behaviour, note it is not an _**open **_relay, however, once STARTTLS and LOGIN are done then it is an "authenticated" Open Relay.

Example below of a message that was happily delivered to my gmail INBOX, not spam, despite failing both SPF and DMARC.

I have done quite a lot of searching on this but can only find stuff on INBOUND Sender Validation, not outbound. Please advise how to correct this in postfix s it only sends mail as mydomain.tld not *@*.

thanks in advance.

```

                                                                                                                                                                                                                                                               
Delivered-To: [me]@gmail.com
Received: by 10.114.81.70 with SMTP id y6csp547970ldx;
        Sat, 9 Apr 2016 04:36:50 -0700 (PDT)
X-Received: by 10.182.245.138 with SMTP id xo10mr6206569obc.56.1460201810068;
        Sat, 09 Apr 2016 04:36:50 -0700 (PDT)
Return-Path: <Bill.Gates@microsoft.com>
Received: from mail.mydomain.tld (mail.mydomain.tld. [1xx.2xx.3xx.4xx])
        by mx.google.com with ESMTPS id nz3si5793830obc.61.2016.04.09.04.36.49
        for <[me]@gmail.com>
        (version=TLS1_2 cipher=ECDHE-RSA-AES128-GCM-SHA256 bits=128/128);
        Sat, 09 Apr 2016 04:36:50 -0700 (PDT)
Received-SPF: fail (google.com: domain of Bill.Gates@microsoft.com does not designate 1xx.2xx.3xx.4xx as permitted sender) client-ip=1xx.2xx.3xx.4xx;
Authentication-Results: mx.google.com;
       spf=fail (google.com: domain of Bill.Gates@microsoft.com does not designate 1xx.2xx.3xx.4xx as permitted sender) smtp.mailfrom=Bill.Gates@microsoft.com;
       dmarc=fail (p=NONE dis=NONE) header.from=microsoft.com
Received: by mail.mydomain.tld (Postfix, from userid 33)
    id AA149A195; Sat,  9 Apr 2016 11:36:49 +0000 (UTC)
To: me <[me]@gmail.com>
Subject: Spoofing Test
X-PHP-Originating-Script: 0:rcmail.php
MIME-Version: 1.0
Content-Type: multipart/alternative;
 boundary="=_635b2fe0c1859179debc37f12450925b"
Date: Sat, 09 Apr 2016 12:36:49 +0100
From: Bill Gates <Bill.Gates@microsoft.com>
Organization: Microsoft
Message-ID: <89dc4da9b6df0e8c9d75b3c45ac8062f@mydomain.tld>
X-Sender: Bill.Gates@microsoft.com
User-Agent: Roundcube Webmail/0.9.5


--=_635b2fe0c1859179debc37f12450925b
Content-Transfer-Encoding: 7bit
Content-Type: text/plain; charset=UTF-8


 


this message should fail to send... 


-- 


B Gates 
--=_635b2fe0c1859179debc37f12450925b
Content-Transfer-Encoding: quoted-printable
Content-Type: text/html; charset=UTF-8


<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN">
<html><body style=3D'font-family: Arial,Helvetica,sans-serif'>
<p>this message should fail to send...</p>
<p>&nbsp;</p>
<div>-- <br />
<p><span style=3D"font-size: small;">B Gates</span></p>
</div>
</body></html>


--=_635b2fe0c1859179debc37f12450925b--

```

---

### Post by SeijiSensei on 2016-04-09
I'm a little confused here.  Who would be sending these messages?  If you require authentication to connect, wouldn't these senders need an account on your machine to send mail?  Where the did sample you posted originate? Somewhere outside your network or on the box itself?  If the latter, it's probably because most mail sent from localhost is trusted by default.

Have you read this completely: [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html)

---

