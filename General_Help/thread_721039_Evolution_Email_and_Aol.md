---
title: "Evolution Email and Aol"
date: 2008-03-10
forum: General Help
---

### Post by Niteowler on 2008-03-10
I have a couple of old Aol email accounts that I've had for a long time so really they are my primary email clients.  I set Evolution email and I can send just fine but I can't seem to receive email.  I set up the server as imap.aol.com with ssl encryption and the authentication type is password.  Surely there are people who use Evolution email for aol email accounts.  Ideas anyone?

---

### Post by Shazaam on 2008-03-10
Did you try smtp.aol.com with no encryption?

---

### Post by Niteowler on 2008-03-11
Yes I tried with no encryption with the same result.

---

### Post by dcstar on 2008-03-11
> **Niteowler said:**
> I have a couple of old Aol email accounts that I've had for a long time so really they are my primary email clients.  I set Evolution email and I can send just fine but I can't seem to receive email.  I set up the server as imap.aol.com with ssl encryption and the authentication type is password.  Surely there are people who use Evolution email for aol email accounts.  Ideas anyone?

**Exactly** what happens when you do a Send/Receive?, and **exactly** how have you set up the account?

---

### Post by forestpixie on 2008-03-11
I've no problems - have it setup to use uk site though - found the port numbers searching for a thunderbird howto

hope that helps some

---

### Post by scramasax on 2008-03-11
> **Niteowler said:**
> I have a couple of old Aol email accounts that I've had for a long time so really they are my primary email clients.  I set Evolution email and I can send just fine but I can't seem to receive email.  I set up the server as imap.aol.com with ssl encryption and the authentication type is password.  Surely there are people who use Evolution email for aol email accounts.  Ideas anyone?

It could be down to the ports you're using.  (I see the last poster is also suggesting that).

According to this guy, you need:

imap.aol.com (port 143)
smtp.aol.com (port 587)

[http://members.aol.com/adamkb/aol/mailfaq/imap/](http://members.aol.com/adamkb/aol/mailfaq/imap/)

So in evolution you'd enter the IMAP server as:

imap.aol.com:143

and you'd enter the SMTP server as:

smtp.aol.com:587

In other words, just add the port number in on the end of the server name after a colon.

---

### Post by Niteowler on 2008-03-11
I researched before I set up Evolution Email.  I have incoming mail set to" imap.aol.com:143" and outgoing set to "smtp.aol.com:587".  When I click the send/receive button a send/receive box comes up with blue bars going across with a cancel button.  At the bottom of the page it says "checking for new mail" but it just sits there.  I waited for almost ten minutes and nothing.  I have two different aol accounts setup in Evolution.  Think there is a conflict because of that?  It seems as though it looks for the mail in both accounts at the same time because it says both names with a blue progress bar beside each name.  I can send email with both screen names.

---

### Post by forestpixie on 2008-03-13
did you try unenabling one of them to see if the other worked?

---

### Post by Niteowler on 2008-03-14
Yeah, I deleted one account and it still just sits there saying "checking for new mail" at the bottom.  One time the message went away after about 5 minutes after I started Evolution but no mail showed up.  Same result as earlier.

---

