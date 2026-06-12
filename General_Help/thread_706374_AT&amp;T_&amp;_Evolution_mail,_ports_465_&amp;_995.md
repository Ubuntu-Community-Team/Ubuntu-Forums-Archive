---
title: "AT&amp;T &amp; Evolution mail, ports 465 &amp; 995 ?"
date: 2008-02-24
forum: General Help
---

### Post by derek45 on 2008-02-24
I've been doing online chat with AT&T tech support all morning trying to setup EVOLUTION MAIL with AT&T (DSL) 

I can't send or receive,  when I try,  I get this error message

Error while Fetching Mail.

Unable to connect to POP server pop.att.yahoo.com: No support for requested authentication mechanism.

AT&T settings....


[LIST=1]
[*]Open your email client program.
[*]Locate the email account settings for your particular client.
[*]Change the **POP server** to **pop.att.yahoo.com**.
[*]Change the **SMTP server** to **smtp.att.yahoo.com**.
[*]Check the option labeled **Use an encrypted connection (SSL)** and change the **SMTP port** to **465**.
[*]Check the option labeled **Use an encrypted connection (SSL)** and change the **POP3 port** to **995**.
[*]Confirm the above settings before clicking **OK**.[/LIST]  



I tried searching,  but did not find an answer.



How do I set this up.   I had Evolution set up before,  but wiped my HD, started over, and forgot how I got it running last time.



THANKS !

---

### Post by derek45 on 2008-02-24
I found the answer.

All you have to do is put :465 ,and :995 after the pop and smtp info.

example:

**smtp.att.yahoo.com:465**

---

### Post by davidkahn on 2008-05-08
Port 465 is the standard port for SSL encrypted SMTP & port 995 is the standard port for SSL encrypted POP.  I believe that Evolution uses these ports by default, just as it uses ports 25 and 110 for unencrypted connections.  However, adding the ports as :465 and :995 does no harm, other than requiring re-entry of passwords because it thinks that the server has changed.

---

### Post by mdpalow on 2008-06-11
> **derek45 said:**
> I found the answer.

All you have to do is put :465 ,and :995 after the pop and smtp info.

example:

**smtp.att.yahoo.com:465**

Thank you for this. After a lot of time spent trying to figure out why I couldn't connect to Yahoo! mail plus, this was the posting that got it working for me. 

My port numbers are different, but I couldn't find where to put them. Now it works. Thanks again...

---

