---
title: "Help with Host/Domain Causing Mail to be Spamblocked"
date: 2006-10-05
forum: General Help
---

### Post by Nick Wilson on 2006-10-05
hi, I've just found my email on this spam list for the second time in a week: [http://cbl.abuseat.org/lookup.cgi?ip=87.48.90.98](http://cbl.abuseat.org/lookup.cgi?ip=87.48.90.98)

I followed all the instructions to set a proper hostname for my machine the last time this happened but it appears I must have it wrong. Below are relevant files, can someone please offer some advice as to what to do?

```

nick@home:~ > cat /etc/hosts
127.0.0.1 localhost.localdomain localhost
87.48.90.98  home.communicontent.com
...snip...

```

```

nick@home:~ > cat /etc/postfix/main.cf
.....snip....
myhostname = home.communicontent.com
.....snip.....

```

```

nick@home:~ > cat /etc/hostname
home.communicontent.com

```

```

nick@home:~ > hostname -d
communicontent.com
nick@home:~ > hostname -f
home.communicontent.com
nick@home:~ > hostname -s
home

```

and lastly, the results of an email sent to [email]helocheck@cbl.abuseat.org[/email]

> 
Reporting-MTA: dns; home.communicontent.com
X-Postfix-Queue-ID: 6F6DA510237
X-Postfix-Sender: rfc822; [email]nick@performancing.com[/email]
Arrival-Date: Thu,  5 Oct 2006 12:22:08 +0200 (CEST)

Final-Recipient: rfc822; [email]helocheck@cbl.abuseat.org[/email]
Action: failed
Status: 5.0.0
Diagnostic-Code: X-Postfix; host mail.cbl.abuseat.org[216.168.28.54] said: 550
    Your HELO name for IP address 87.48.90.98 was "home.communicontent.com" (in
    reply to RCPT TO command)


I own the communicontent domain, though there is no home subdomain setup and it does not point specifically to my home network yet. 

Can anyone work out where im going wrong here?

many thanks...

---

### Post by dcstar on 2006-10-05
> **Nick Wilson said:**
> 
......
I own the communicontent domain, though there is no home subdomain setup and it does not point specifically to my home network yet. 

Can anyone work out where im going wrong here?

many thanks...

You basically just answered your own question, you are pretending in e-mails to be a domain that doesn't exist - this particular anti-spam place doesn't like that.

Get a DNS entry for "home.communicontent.com" set up and all will be well as it will then give a reverse DNS lookup.

---

### Post by Nick Wilson on 2006-10-05
Is that as simple as just givint it a line in the zone file or does it actually need to resolve to my home ip? (cost that wold be quite a bit more work..)

thanks

---

