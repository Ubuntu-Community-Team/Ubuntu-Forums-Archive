---
title: "Installing and Configuring Postfix for Mailody"
date: 2007-08-15
forum: General Help
---

### Post by jrickmar on 2007-08-15
On Kubuntu 7.04, I have (sorta) installed postfix to be used as an smtp server.

I use Runbox for my mail, but one of the problems I am having is the smtp server is almost _always_ down when I need to send an email.  I know it's a problem at their end because on [emaildiscussions.com]("http://www.emaildiscussions.com/") others are also having similar problems.  I want to get around this problem and use my computer as a smtp server and send all my emails directly from it instead of connecting to Runbox.

So I did a quick little sudo apt-get install postfix, but I was met with a bunch of options with no idea what to do.  So... I just played with it, trying to get a setting that worked.

So then I opened up Mailody (I love imap, and think that Mailody does a much nicer job than KMail) and put in these settings:

Identity Name: Default
Full Name: <My name...>
Email address: [email]foo@runbox.com[/email]
SMTP-server: localhost
Safety: [x] None [ ] SSL [ ] TLS
[ ] Use Authentication

So then I tried to send a test email to my dummy gmail account, and got this error:

554 5.7.1 <foobar@gmail.com>: Relay access denied 

(obviously my email isn't foo-anything...)

It looks like I'm causing more problems then I'm solving.  Is there any way that I can just make this work?

---

### Post by HermanAB on 2007-08-15
The best information on postfix is at [http://postfix.org](http://postfix.org)

There are several reasons for getting a relay access denied, but usually it means that the account is not defined properly so postfix has no clue who the mail is for and replies with access denied.

BTW, in order to send mail, you would probably need to change your internet account to a 'server' account and pay $10 or per month more, since ISPs usually block ports 25 and 80 to prevent users from running common servers at home.

---

### Post by jrickmar on 2007-08-16
Hmmm, I seem to have it running now.

Well, sorta.

I changed the SMTP-server to 127.0.0.1:25.  Well, the composer window in Mailody finally closed, and I thought everything was fine and dandy...

Until I checked, and the email never made it.  Yeah, they block port 25.

Oh well......

---

### Post by gdzsi on 2008-05-29
your ISP should provide an SMTP server, check that...
or use your neighbour's, friend's, account, blahblah :)

Mailody is awesome by the way...

---

