---
title: "evolution and gmail sync?"
date: 2007-06-24
forum: General Help
---

### Post by bcdixit on 2007-06-24
Hello,
i have recently started using Ubuntu and evolution as my mail client.
I want to know if it is possible to sync up my mailbox in evolution with gmail.
for example,
if i delete a email in my evolution inbox (received earlier thru POP), then would it be possible for that same email  to be automatically sent to the trash bin in gmail when access my gmail account thru the web?

thanx
-bcd

---

### Post by davidsiegel on 2007-07-02
I don't think this is possible with POP - but it's gmail, why delete *anything*?

---

### Post by khedron on 2007-07-02
Yes, this is a limitation of POP - all it can do is check for new emails and download them. A newer protocol called IMAP can do what you want, but GMail doesn't support it.

This may or may not be useful, but you can delete (or archive) any email that you *download* from GMail. Check the "POP and forwarding" section of your GMail settings.

---

### Post by xuanyou on 2008-01-12
gmail recently added IMAP support.

imap.googlemail.com
smtp.googlemail.com

username: [your username]

both require encryption (SSL).

imap uses "password" authentication
smtp uses "plain" authentication

managed to sync evolution with gmail in less than 5 minutes from first configuration. =)

have fun!

---

### Post by David Oxland on 2008-01-21
I'm having much the same trouble as bcdixit:
 I've tried getting imap and pop to work but test for auth mechanisms always times out.  I had Evolution doing this one year ago but now that I'm trying to use it again; just completely stopped at this point

Keep getting "Host lookup failed: [email]smtp@gmail.com[/email]: Name or service not known" and more often "connection timed out".

neither send or receive will link 

any help or source of help would certainly be appreciated
Thanks

---

### Post by Kevanx on 2008-01-26
I'm pretty new to IMAP, but my first suggestion would be to check out the server - why is Evolution trying to communicate with [email]smtp@gmail.com[/email]? Go Edit>Preferences, then Edit your gmail account settings and make sure your SENDING and RECEIVING pages look right, particularly the server fields. Both should be ****.googlemail.com with **** being SMTP for sending, and IMAP for receiving. The **** should also match the SERVER TYPE box for each page.

This may seem rudimentary, but double checking is always a good idea.

---

### Post by narf y akim on 2008-01-26
Yes, I have followed the instructions of xuanyou and it works great! Thanks!

---

### Post by David Oxland on 2008-01-27
Thanks Kevanx
Tried deleting the whole account and doing it again with both 

imap.gmail.com and smtp.gmail.com
and 
imap.googlemail.com and smtp.gmail.com

still the failure of smtp gives could not connect with [email]smpt@gmail.com[/email]  
This "@" makes me think that the error is embedded somewhere else  and the 
imap types both time out with "unable to connect with imap server imap.gmail.com"

Anyway I'm still stopped but would like to get a win if possible
Thanks

---

### Post by Kevanx on 2008-01-27
Okay, I feel as though this is a really silly suggestion on my part, but have you tried smtp.googlemail.com instead of smtp.gmail.com? Your last post suggests that you tried smtp.gmail.com which probably won't work. I suspect this is just a typo, but still. If receiving works, then it's probably a tiny setting with the SMTP settings. Mine works fine like this:
Server Type - SMTP
server smtp.googlemail.com
CHECKED BOX - server requires authentication
Use Secure Connection - SSL
Authentication Type - PLAIN
Username: your gmail username without the @gmail.com part,

If that all looks good, I have no idea - perhaps a port forwarding issue with your firewall/router, but that would surprise me.

Also, double check in your gmail account under SETTINGS > FORWARDING AND POP/IMAP
that "IMAP is ENABLED" is selected and saved.

---

### Post by David Oxland on 2008-01-27
I should have explained about gmail.com vs googlemail.com
 I have found both listed in different Google sites
It seemed  that the google.mail was from Europe Google whereas the N American site gives gmail.com
thanks again Kevanx

what's also mistifying is that when the failure occurs it says failed to contact [email]smtp@gmail.com[/email] which makes me think that this is embedded somewhere deeper. unless Evolution converts this?

---

### Post by AndyCooll on 2008-01-27
> **David Oxland said:**
> I should have explained about gmail.com vs googlemail.com
 I have found both listed in different Google sites
It seemed  that the google.mail was from Europe Google whereas the N American site gives gmail.com
thanks again Kevanx

what's also mistifying is that when the failure occurs it says failed to contact [email]smtp@gmail.com[/email] which makes me think that this is embedded somewhere deeper. unless Evolution converts this?

The error is there in the error message itself, i.e. your smtp settings. It should be smtp.gmail.com (No "@" in it).

The difference between Googlemail and Gmail is a red herring. The full email address I was given was  Googlemail. However the imap settings I use are gmail ones (imap.gmail.com, smtp.gmail.com). Just be consistent.

:cool:

---

### Post by David Oxland on 2008-01-27
That's what I'm saying Andy;
  I don't put the @ in the server statment.  It just comes back in the failed attempt message
I enter smtp.gmail.com. but the failure says '"failed to connect, timed out with [email]smtp@gmail.com[/email]."
I didn't write that @ in. 
 Honest!

---

### Post by AndyCooll on 2008-01-27
> **David Oxland said:**
> That's what I'm saying Andy;
  I don't put the @ in the server statment.  It just comes back in the failed attempt message
I enter smtp.gmail.com. but the failure says '"failed to connect, timed out with [email]smtp@gmail.com[/email]."
I didn't write that @ in. 
 Honest!

Ok, let's check a few more settings. In that same "Sending email" tab do you have "Server requires authentication" ticked, if not do so. And are you using TLS encryption?
And have you added your username in the format "yourusername@gmail.com" (without the speech marks).

And finally, in GoogleMail itself, under settings is your display language "English (US)", and have you enabled IMAP on the "Forwarding and Pop/IMAP tab?

:cool:

---

### Post by David Oxland on 2008-01-27
yes authentication is checked and I've tried TLS as well as the prescribed SSL and no encryption as well.  Once on check for supported type I actually did get a responce, but only once. All other attempts timed out

---

### Post by AndyCooll on 2008-01-27
Hmmm ...I think I'll have to sleep on this (it's 3.30am here).

Here's a couple of Googlemail pages that it may be worth you having a look at. They were what I used when I set up IMAP:

[URL="http://mail.google.com/support/bin/answer.py?answer=75725"]Getting started with IMAP for Gmail
[/URL]
[Configuring other mail clients]("http://mail.google.com/support/bin/answer.py?answer=78799")

:cool:

---

### Post by David Oxland on 2008-01-27
Yessir
These have been my primary working docs

---

### Post by cpikel on 2008-02-09
Hi there.  New to the forums and Ubuntu, but had similar issues setting up gmail.  Turns out that smtp.gmail.com doesn't use the default port for encrypted authentication.  Try using this for your smtp address and see if it works.  Came right up for me:

smtp.gmail.com:993

In other mail programs the setup allows you to select the port, but evolution doesn't seem to have that option so typing it into the address seems the only way.  Hope this helps and isn't a repeat.

Christian

---

### Post by cpikel on 2008-02-09
ok, so I left my brain at home today.  993 is the imap port.  SMTP is 587.

Sorry for the confusion.

---

### Post by David Oxland on 2008-03-12
Thanks for the reply Christian; Tried your solution and no go . I finally switched to Thunderbird which has been working well for me
Thanks again

---

### Post by ireneshusband on 2008-04-08
I just set this up today without too much problem. Here are what your settings should be:

Receiving email:
Server type: IMAP
Server: imap.gmail.com:993
Username: [email]yourusername@gmail.com[/email] (You have to include the "@gmail.com"!)
Use secure connection: SSL encryption
Authentication type: Password

Sending email:
Server type: SMTP
Server: smtp.gmail.com:587
Server requires authentication: yes
Use secure connection: TLS encryption
Authentication: plain
Username: [email]yourusername@gmail.com[/email]

---

