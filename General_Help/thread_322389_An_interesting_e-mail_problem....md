---
title: "An interesting e-mail problem..."
date: 2006-12-20
forum: General Help
---

### Post by AndrewS on 2006-12-20
Hi

I have an interesting e-mail problem - it might not be strictly a Linux issue, but it seems to be related.  The situation is as follows:

I have two PCs; they are both dual boot (W98/Edgy; XP/Edgy)
The PCs are connected to the internet through a D-Link router (DSL-524T)
I use Thunderbird as the e-mail programme on both machines, and under both OS
I cannot send e-mail from Windows to a virgin.net account from either PC
I can send e-mail to this address from Edgy on both machines
My ISP is Freeserve (aka Wanadoo, aka Orange)
FWIW, I cannot send e-mail from the Orange web based mail page either (to the virgin.net address)

Any thoughts?  I suspect the router, but thought I'd post this before digging out the old Speedlink USB modem.

TIA

Andrew

---

### Post by koenn on 2006-12-20
```
cannot send e-mail from Windows to a virgin.net account from either PC
I can send e-mail to this address from Edgy on both machines
FWIW, I cannot send e-mail from the Orange web based mail page either (to the virgin.net address)
```

What do you get that tells you you can not send the email ?

---

### Post by AndrewS on 2006-12-20
Koenn

I've no reason to doubt that it is sent (well, there's a copy in the Sent folder), and I don't get a non-delivery message.  But the person I'm sending it to is expecting it, and it never arrives.

[I just re-read my posting - it wasn't totally clear...]

Andrew

---

### Post by koenn on 2006-12-20
weird indeed. 
I can't think of anything that could explain it. 

You could try to see what happens if you "hand-deliver" a msg at the virgin.net server (both from your ubuntu system and from windows.)
see [http://www.yuki-onna.co.uk/email/smtp.html](http://www.yuki-onna.co.uk/email/smtp.html)

What you'd be doing is talk to the mail server as if you were an other mail server , and see what it replies. Maybe it says something that gives a clue. 

virgin.net mail server is inbound.virgin.net.cust.securehostedemail.com. - , so you'd go 
```
telnet 64.97.139.1 25
```

you can aslo try this via Freenet's mail server, which is the mail server that you handles any mail you send out.

---

### Post by rotten777 on 2006-12-20
Be careful that your ISP isn't blocking SMTP traffic other than on their own server.

Try using another server possibly with authentication. 

Try the telnet method and post the output.

---

### Post by AndrewS on 2006-12-20
Thanks, I'll give those things a try (tomorrow, it's late!).

Andrew

---

### Post by AndrewS on 2006-12-21
Koenn

I think I must be missing something here (I've never used telnet before)...  I typed

telnet 64.97.139.1 25

in a terminal, and got the following:

andrew@ubuntu:~$ telnet 64.97.139.1 25
Trying 64.97.139.1...
Connected to 64.97.139.1.
Escape character is '^]'.
554 Please check your SMTP server is set to smtp.orange.co.uk. Further help is available at [http://help.orange.co.uk/sessionBegin.do?solutionId=kb4473](http://help.orange.co.uk/sessionBegin.do?solutionId=kb4473)
Connection closed by foreign host.

Am I doing something wrong here?

Thanks again

Andrew

---

### Post by rotten777 on 2006-12-21
"smtp.orange.co.uk"

Change your SMTP server to that ;)

---

### Post by AndrewS on 2006-12-21
This is going to sound really stupid, but where do I change it???

---

### Post by AndrewS on 2006-12-21
A new development - I got a friend who also has a freeserve account to try to e-mail the same virgin.net address.  He got a non-delivery message:

delivery temporarily suspended: host
   inbound.virgin.net.cust.securehostedemail.com[64.97.139.1] refused to talk
   to me: 554 n076.sc1.cp.net Service not available - access denied

Any thoughts?

Andrew

---

### Post by koenn on 2006-12-22
re post #7: you did it right. The answer you get is from the virgin mail server. It's telling you that mail from you to virgin.net should come from smtp.orange.co.uk. Probably it checked you're ip address, figured it belongs to orange.co.uk, and decided you're not the mail server for orange.co.uk so you have no business trying to relay msg's the virgin mail server. 

as rotten777 says in post #8: configure Thunderbird with the correct server.

Open Thunderbird, 
in the "Folders" section on the left, click on the account in question (you@your.mail.domain)
in the main pane, find "Accounts" and click "view settings for this account"
click "Outgoing Server (SMTP)"
check (and correct) the info; you're SMTP server should be smtp.orange.co.uk


The delivery failure your friend got is basically the same as the one you got : 554 : Transaction failure

Let's first see if your thunderbird is configured correctly, then we'll take it from there

---

### Post by AndrewS on 2007-01-09
koenn, rotten777

Thanks for your replies on this - sorry I haven't got back sooner.  I'm still not sure why, but changing the SMTP server from smtp.freeserve.com to smtp.orange.co.uk did the trick.  My friend with the virgin.net account asked their "help desk" about it and was told:

[COLOR="Blue"]I would like to confirm that these domains (Freeserve) now may have been blocked by number of spam companies due to the amount of spam that comes from those domains. It seems Tucows have blocked them as well, so you may not receive email sent from that domain.


We have nothing to do with any of this and I would advise you to contact Freeserve and get them to call Tucows to get them removed from the spam block. [/COLOR]
Not sure what Tucows is, and are they likely to have imposed this block?  Could they do this?

Thanks again

Andrew

---

### Post by koenn on 2007-01-09
Thansks for the feedback - it's always nice to see how a post eventually reaches a sollution.

What the virgin mail server did is :
- check the IP address weher an email originates from
- look it up in DNS to establish the domain that owns that ipaddress
- look up in DNS what mail servers exist for that domain, and
- only accept the msg if it comes from one of those mail servers

It's an anti-spam measure: spammers will try to use any mail server, or connect directly to the mail server of the final destination domain, much like you did with the telnet - to get their spam delivered.

According to the helpdesk reply, they also use blacklists.

Tucows is just an other domain,like that apparenly was blacklisted by Virgin. It has nothing to do with you or Freeserve being blocked - they're telling *your friend* that *she* will not receive email form any tucows address.

---

### Post by AndrewS on 2007-01-10
OK, I think that's a bit clearer.  May have something to do with the fact that "Freeserve" were taken over by Wanadoo who in turn were bought by Orange?  While looking through some other e-mail accounts last night, I noticed that I still have an old dial-up account with Freeserve (etc) which I use occasionally.  When I re-activated that recently, the mail servers must have been changed to pop/smtp.orange.co.uk.  It never occurred to me to try and send an e-mail from that account to the virgin.net address!

Andrew

---

