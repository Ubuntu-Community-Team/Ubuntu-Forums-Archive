---
title: "[SOLVED] The simplest way to buffer and forward local mail to a smtp server?"
date: 2007-10-05
forum: General Help
---

### Post by cannontrodder on 2007-10-05
Our ISP's smtp server fell over last weekend and although we got it fixed pretty quickly, it caused real problems with our messageboard as it tried to and timed-out from connecting to send outgoing mail on each post.

What I need to do is have the mail stored locally on the server and then have the server try (and retry on fail) to send the mail out to the ISP SMTP server. That would save our users having to wait about a minute for the SMTP connection to fail.

I'm bewildered by the various components in setting up an email system but I suppose all I need is something to cache mail locally and repeatedly retry to send it out. Can anyone suggest something fairly lightweight that could achieve this?

---

### Post by kidders on 2007-10-07
Hi there,

Rather than going out of your way to find something lightweight, I would suggest going for something widely recognised ... especially if you find mail servers confusing. If you're using the same software as millions of other people, help is always much easier to find.

I would suggest using Postfix which, although capable of a wide variety of things, can be configured to accept and relay email to another server. Postfix is reliable, scalable, and very commonly used.

---

### Post by cannontrodder on 2007-10-07
Thanks for the reply kidders.

The good thing about using Postfix is that if my needs change, the extra functionality will be there for me. All I need to really do is configure it to only accept connections locally and then have it forward if/when our outgoing relay is available. Thanks again for the pointer, I'm off to read up on Postfix!

I'll tag a post on here on what I did so others can do the same if they find this via search.

---

### Post by cannontrodder on 2007-10-07
Ok, seems pretty simple (for what I wanted to do):

sudo apt-get install postfix

(when asked, I left the FQD it asked for as the default as this machine simply needs to buffer emails locally and forward them on if the external SMTP relay is working)

sudo postconf -e 'relayhost = MYRELAYHERE'
sudo postconf -e 'mynetworks_style = host'

..set MYRELAYHERE to be the ip or hostname of the external SMTP relay. The host setting on mynetworks_style only allows connections from the local machine (ie my messageboard)

---

