---
title: "Simplest option for SMTP Relay"
date: 2014-10-02
forum: General Help
---

### Post by ketrel2 on 2014-10-02
I'm looking for the simplest method to set up an SMTP relay.
The server already exists, and my issue is this.

I have some hardware that can sent SMTP alerts, but does not support SSL/TLS.
I would like to set up a relay such that I can relay over SSL/TLS

I don't need any other functionality, so whatever the absolute simplest way to get to having a functioning SMTP relay is what I'm looking to do.

It's for the sole purpose of SSL.

---

### Post by tgalati4 on 2014-10-02
A quick search:

esmtp - user configurable relay-only MTA
esmtp-run - user configurable relay-only MTA - the regular MTA

Unfortunately email and simple cannot be used in the same sentence.  There is a minimum level of understanding that is required:  [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

More searching:

[http://opensourcehacker.com/2013/01/02/sendmail-using-nullmailer-and-gmail-account-on-linux-server/](http://opensourcehacker.com/2013/01/02/sendmail-using-nullmailer-and-gmail-account-on-linux-server/)

[http://ctrlq.org/code/19589-send-mail-php](http://ctrlq.org/code/19589-send-mail-php)

There seems to be a common thread of using gmail to accept the smtp message (using a custom gmail account just for this purpose) and set up forwarding rules in gmail to send via ssl to your final email destination.  I have done this with some embedded devices.  Be mindful that gmail has limits on number of emails/hour, per day, etc to reduce spam.  So as long as you don't have too many messages, this might be a viable method until you find a better solution.

---

### Post by ketrel2 on 2014-10-02
> **tgalati4 said:**
> 

There seems to be a common thread of using gmail to accept the smtp message (using a custom gmail account just for this purpose) and set up forwarding rules in gmail to send via ssl to your final email destination.  I have done this with some embedded devices.  Be mindful that gmail has limits on number of emails/hour, per day, etc to reduce spam.  So as long as you don't have too many messages, this might be a viable method until you find a better solution.

Gmail requires SSL/TLS now I believe, so that's not an option.

As far as esmtp, that doesn't look like it would work.
I need it to be a relay server, not a relay command.

EDIT: So far, my searching looks like postfix may be the only option?

---

### Post by tgalati4 on 2014-10-02
I think you are correct.  SSL is now enforced for gmail acounts.  However, there is a provision for smtp-relay:  [https://support.google.com/a/answer/176600?hl=en](https://support.google.com/a/answer/176600?hl=en)

And it says SSL is optional, so you might try that.  It does require a static IP though.

Perhaps your hardware manufacturer could update the firmware to support SSL for SMTP messages?  I would send an email with such a request.  Assuming your hardware has some sort of support.

I did find one other option:  SSL tunneling.  I have not used it so I don't know how difficult it is to set up:  [https://www.stunnel.org/index.html](https://www.stunnel.org/index.html)

As Agony Units (AU's) approach postfix setup levels, you might as well set up your own mail server.

This service may still be available:

SMTP Server: aspmx.l.google.com  (and it is still in the table in the link I posted above)
SMTP Port: 25
User: [[email protected]]
Pass: [yourpassword]

Some ISP's block outbound port 25 (to curb spam from all of those infected Windows boxen).  I can ping the aspmx address, so there are electrons still spinning there.  It's worth a shot.  I think this relay is limited to 99 emails/day, but I am not sure.

---

### Post by ketrel2 on 2014-10-03
Yeah, I do have a domain I point towards my home location.  If there's no simple relay solutions, perhaps a full fledged mail server and a few spf records would help here.

If I go the full SMTP server route, which would be the easiest to setup would you say?

---

### Post by tgalati4 on 2014-10-03
Did the aspmx server work from the previous post?

None of the Mail Transport Agents (MTA's) are easy to set up.  You might consider setting up a send-only MTA for this purpose:

[http://askubuntu.com/questions/7993/how-can-i-setup-a-mail-transfer-agent](http://askubuntu.com/questions/7993/how-can-i-setup-a-mail-transfer-agent)

You can search for tutorials on postfix or sendmail.  They are fractured, involve different distros, and include configuration of services you may not need.  So read, learn, and proceed carefully.

---

### Post by ketrel2 on 2014-10-03
> **tgalati4 said:**
> Did the aspmx server work from the previous post?

None of the Mail Transport Agents (MTA's) are easy to set up.  You might consider setting up a send-only MTA for this purpose:

[http://askubuntu.com/questions/7993/how-can-i-setup-a-mail-transfer-agent](http://askubuntu.com/questions/7993/how-can-i-setup-a-mail-transfer-agent)

You can search for tutorials on postfix or sendmail.  They are fractured, involve different distros, and include configuration of services you may not need.  So read, learn, and proceed carefully.


The gmail one isn't an option, it needs to come from a specific domain for my setup.

For the send only MTA, doesn't that require using commands on the server itself rather than a SMTP server I can connect to?

I need to point out that the device sending is a hardware device and not a service on my ubuntu server.

---

### Post by SuaSwe on 2014-10-03
Postfix is actually quite simple to configure and use, once you get used to it. :D 

What type of device are you sending from/to? Did you say that you have a server configured already? What mail server is configured at the server side?

---

### Post by ketrel2 on 2014-10-03
> **SuaSwe said:**
> Postfix is actually quite simple to configure and use, once you get used to it. :D 

What type of device are you sending from/to? Did you say that you have a server configured already? What mail server is configured at the server side?

Device is an Axis camera (that doesn't appear to be getting the update that adds SSL SMTP functionality).  

What I have right now is:
-Ubuntu server running as a samba fileserver for my network and a Minecraft server
-External shared hosting webserver (SSL/TLS required)

What I originally wanted to do was setup a relay on the ubuntu server, but since that appears to be more trouble than it's worth...
What I want to do now is setup a SMTP server on the ubuntu server (which is on the same local network as the camera)

---

