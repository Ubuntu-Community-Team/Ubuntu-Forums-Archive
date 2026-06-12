---
title: "Yandex Email- Can't Send Via SMTP"
date: 2019-01-08
forum: General Help
---

### Post by sasafrass452 on 2019-01-08
NOTE TO MODS: I'm not sure where to post this, so please move if appropriate!

I'm in the process of changing my email provider, so I'm trying out Yandex. I set up the account in Thunderbird as instructed, but it won't send for some unknown reason. I tried other settings, but to no avail. Also, their website says the trash empties itself every 31 days. If anyone here uses Yandex, can you confirm this? I'm asking because Mail.com(which is not my primary email) has a setting to empty folders after a designated period, but it doesn't work. If anyone can help, I'd appreciate it!

---

### Post by sasafrass452 on 2019-01-09
Anyone?

---

### Post by SeijiSensei on 2019-01-09
What do you have as the outbound server for the Yandex account?  If your trying to send mail with a Yandex address, but you're still using your previous provider's SMTP server, the message may be refused.

Look in Edit > Account Settings > Outgoing Server and make sure you're using the Yandex server for mail sent via your Yandex account.

---

### Post by sasafrass452 on 2019-01-09
As I said, I set up the account as instructed. There doesn't seem to be an explaination for why it doesn't work. I tried all other setting configurations available to send with, but nothing works. Unless I missed something? I just can't figure out what....

> **SeijiSensei said:**
> What do you have as the outbound server for the Yandex account?  If your trying to send mail with a Yandex address, but you're still using your previous provider's SMTP server, the message may be refused.

Look in Edit > Account Settings > Outgoing Server and make sure you're using the Yandex server for mail sent via your Yandex account.

---

### Post by SeijiSensei on 2019-01-10
You said you were changing providers? Can you send mail from Thunderbird using that prior account?

One quick test is to see if outbound SMTP traffic is blocked by your provider.  Open a terminal and type

```
telnet gmail-smtp-in.l.google.com 25
```

You should get a banner like this in reply:

```
220 mx.google.com ESMTP l126si1416983qkb.210 - gsmtp
```

If the connection hangs, your provider is likely blocking outbound SMTP traffic, a pretty common restriction to block spambots on ISP's networks.  You'll have to contact your provider.

---

### Post by Ars_Ivci on 2019-01-10
My settings:
smtp.yandex.com
port: 465
auth method: Normal password
conn security: SSL/TLS

No problems.

---

### Post by sasafrass452 on 2019-01-10
Yes, of course I can send with my primary account(VFEmail). But they are terminating the free service, which is why I'm switching to another provider. I don't use Gmail. I even googled my problem with Yandex, but found nothing so far.

> **SeijiSensei said:**
> You said you were changing providers? Can you send mail from Thunderbird using that prior account?

One quick test is to see if outbound SMTP traffic is blocked by your provider.  Open a terminal and type

```
telnet gmail-smtp-in.l.google.com 25
```

You should get a banner like this in reply:

```
220 mx.google.com ESMTP l126si1416983qkb.210 - gsmtp
```

If the connection hangs, your provider is likely blocking outbound SMTP traffic, a pretty common restriction to block spambots on ISP's networks.  You'll have to contact your provider.

---

### Post by SeijiSensei on 2019-01-10
Run the same test replacing gmail-smtp-in.l.google.com with the address of the SMTP server Yandex told you to use.

---

### Post by sasafrass452 on 2019-01-10
This is exactly how I set it up, but it doesn't work. No idea why....

> **Ars_Ivci said:**
> My settings:
smtp.yandex.com
port: 465
auth method: Normal password
conn security: SSL/TLS

No problems.

---

### Post by him610 on 2019-01-10
I just went through this same exercise for a friend with provider Comcast and email application Thunderbird. Your settings look similar to mine. After you change the outgoing email settings, you may need to reboot; although, I did not need to. Do you ever get to the point where yandex asks for your email password?

---

### Post by sasafrass452 on 2019-01-10
Yes, it did ask for my password, but the connection failed. There's no indication as to why.

> **him610 said:**
> I just went through this same exercise for a friend with provider Comcast and email application Thunderbird. Your settings look similar to mine. After you change the outgoing email settings, you may need to reboot; although, I did not need to. Do you ever get to the point where yandex asks for your email password?

---

### Post by sasafrass452 on 2019-01-11
Well, I tried this, but it doesn't tell me anything. Here's my result:

telnet smtp.yandex.com 25
Trying 213.180.204.38...
Connected to smtp.yandex.ru.
Escape character is '^]'.
220 smtp1o.mail.yandex.net ESMTP (Want to use Yandex.Mail for your domain? Visit [http://pdd.yandex.ru](http://pdd.yandex.ru))
421 4.4.2 smtp1o.mail.yandex.net Error: timeout exceeded
Connection closed by foreign host.

> **SeijiSensei said:**
> You said you were changing providers? Can you send mail from Thunderbird using that prior account?

One quick test is to see if outbound SMTP traffic is blocked by your provider.  Open a terminal and type

```
telnet gmail-smtp-in.l.google.com 25
```

You should get a banner like this in reply:

```
220 mx.google.com ESMTP l126si1416983qkb.210 - gsmtp
```

If the connection hangs, your provider is likely blocking outbound SMTP traffic, a pretty common restriction to block spambots on ISP's networks.  You'll have to contact your provider.

---

### Post by SeijiSensei on 2019-01-11
From your earlier posting, it looks like Yandex wants an encrypted connection on port 465.  At least we know you're not being blocked in any way.

I'd check to make sure you're using the correct username in the encrypted login transaction.

Edit > Preferences > Account Settings > Server Settings > username

---

### Post by sasafrass452 on 2019-01-11
An encrypted password doesn't work, either. And yes, it's the correct username. Nothing works, & I'm nearly ready to give up. If I'm going to be forced to use the webmail only, I also need to know if the trash empties itself every 31 days, as their website claims. Mail.com has a similar function, but it doesn't work, despite a setting to do so. This is important to me, because I don't keep any emails & I'd rather not have to delete emails twice. And since many email providers charge a monthly fee, my options are quite limited.

> **SeijiSensei said:**
> From your earlier posting, it looks like Yandex wants an encrypted connection on port 465.  At least we know you're not being blocked in any way.

I'd check to make sure you're using the correct username in the encrypted login transaction.

Edit > Preferences > Account Settings > Server Settings > username

---

### Post by sasafrass452 on 2019-01-13
Well, I decided to try Mailspring to see if sending from Yandex would work. Not surprisingly, it didn't.... I was then presented with a log file basically saying I'm a spammer, despite not doing anything with the account except a few test messages that I sent from the web interface. The log file then directed me to a webpage requesting a mobile phone number- which I don't have- to unlock the account, or to contact Yandex. Since I'm not likely to get a response, I decided to close the account. I've signed up at Safe-mail.net, & am waiting for approval, so I'll see how that goes....

---

