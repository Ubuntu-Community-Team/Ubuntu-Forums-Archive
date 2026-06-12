---
title: "Problem sending email"
date: 2007-05-19
forum: General Help
---

### Post by Donnw on 2007-05-19
I have a problem sending email to one particular address using thunderbird 2.0.0.0. on Ubuntu 7.04. The messages are sent successfully but do not arrive.  Sending to the same email address works ok if I use Thunderbird on Windows.  There does not seem to be a problem sending to other email addresses.  Does anyone have an idea why this is hapenining?

---

### Post by mbradlcu on 2007-05-20
do you get a return undeliverable message? if so what do the headers say? what type of server are you connecting to with your client? The biggest help would be to have access to the destination's mail.log. If that's possible running:
```
tail -f /var/log/mail.log
```
(assuming it's a *nix box)
while sending an email to it would be very reveling!

from what you've found it seems like it's a problem limited to your Linux client.. I would look into if the client has a way of specifying a source domain.. or maybe specifying a FQDN on your LInux box. I think this is done by editing the /etc/hostname,, rebooting would be the easiest way for it to take effect.

have fun!

---

### Post by qwerty2 on 2007-05-30
I am having simillar problems, email is taking up to 2 days to be delivered, when I run top heres the output

95:40.79 qmail-send
85:14.94 clamd
63:17.41 qmail-lspawn
11:22.65 multilog

When I run tail -f /var/log/mail.log

The system just hangs until I hit Ctrl C

Is the tail command correct? how do I flush the queue

---

### Post by rax_m on 2007-05-30
Hi.. 

sorry not sure how to solve your mail issues, but the -f option on tail implies that tail should wait and as soon as an update comes through to the file it should display on the screen. In otherwords, tail -f will never complete until you hit Ctrl C. This is normal. 

Rax

---

### Post by qwerty2 on 2007-05-30
Hi Rax

Thanks for the reply, how can I find where the mail is jammed, can you recommend any commands to try and slove the problem.

Obviousley tail -f isnt helping how do I view the logfile/s

Are these figures telling of the problem
95:40.79 qmail-send
85:14.94 clamd
63:17.41 qmail-lspawn
11:22.65 multilog

Its as though the queue is just groing and going, any help would be great, baie dankie

---

### Post by beermad on 2007-05-30
> **Donnw said:**
> I have a problem sending email to one particular address using thunderbird 2.0.0.0. on Ubuntu 7.04. The messages are sent successfully but do not arrive.  Sending to the same email address works ok if I use Thunderbird on Windows.  There does not seem to be a problem sending to other email addresses.  Does anyone have an idea why this is hapenining?

Are you sending mail from your Linux system through sendmail or through your ISP's SMTP server?
If you're using sendmail, it could be that the particular recipient's email service is rejecting the email because it can't resolve your email domain against your own IP address.

I have a similar sort of problem when sending emails to people with AOL mailboxes, although in my case although I get bounces the email **does** actually arrive OK, though it sometimes takes a few days.

If this is the cause of your problem, reconfiguring Thunderbird to use SMTP should fix it.

---

### Post by Donnw on 2007-06-05
I finally fixed my email delivery problem. The out going information that the recipient sees had one letter wrong for my email address. I think that this was being filtered by some ISPs as potenhtial spam. Its working ok now. Thanks for all the help

---

