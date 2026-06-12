---
title: "Mdadm Undelivered Mail Notifications"
date: 2007-07-24
forum: General Help
---

### Post by Ryoojin83 on 2007-07-24
I have my server up and running using Ubuntu 6.10 Server.  
I have postfix up and running and I can email myself just fine using (all mail is delivered without problem)
  -->  echo "test content" | sendmail <my email address>@gmail.com
But my server has a tendency to kill my hard drives or some reason and I want mdadm to email me when I have a degraded array event.  It used to work, but randomly just stopped sending me emails (even test messages wouldn't work).  I reinstalled postfix and reconfigured mdadm using 
  -->  dpkg-reconfigure mdadm
I tied my gmail address to root in /etc/aliases
Now what I run 
  -->  mdadm -Fs1t 
I tries to send me a message but fails, then sends me the 'Undelivered Mail' email to my gmail address.  Here is the email I receive at my gmail account.


"""
This is the mail system at host <my host name>.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to <postmaster>

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                  The mail system

<my gmail address>: host gmail-smtp-in.l.google.com[64.233.163.27]
   said: 550-5.7.1 [<my ip address>] The IP you're using to send email is not
   authorized  550-5.7.1 to send email directly to our servers. Please use
   550 5.7.1 the SMTP relay at your service provider instead. 7si30055353nzn
   (in reply to end of DATA command)

Final-Recipient: rfc822; <my gmail address>
Action: failed
Status: 5.7.1
Remote-MTA: dns; gmail-smtp-in.l.google.com
Diagnostic-Code: smtp; 550-5.7.1 [<my ip address>] The IP you're using to send
   email is not authorized  550-5.7.1 to send email directly to our servers.
   Please use  550 5.7.1 the SMTP relay at your service provider instead.
   7si30055353nzn


---------- Forwarded message ----------
From: mdadm monitoring <root@<mydomain.com>>
To: <my gmail address>
Date: Tue, 24 Jul 2007 11:18:41 -0500 (CDT)
Subject: DegradedArray event on /dev/md2:<hostname>
This is an automatically generated mail message from mdadm
running on <hostname>

A DegradedArray event had been detected on md device /dev/md2.

Faithfully yours, etc.
"""


What makes me even MORE confused, is when I tried to generate this message just now...it worked fine... then I tried it again, and I got the undeliverable mail message again.  sooo sometimes it works (once so far) and sometimes it doesn't work (23 times)
When I read the message it sounds like gmail just doesn't allow me to send from my server,  but I have a script running that emails me about ip changes, and that sends just fine.

---

### Post by Ryoojin83 on 2007-07-24
When I run 'mdadm -Fs1t'  I get 7 messages, two automatically generated test message for each of my 3 RAIDs, and 1 degraded array event for my bad raid.  but ALL of them are the Mail Delivery System Undeliverable message notifications

---

### Post by Ryoojin83 on 2007-07-24
And now it randomly works...  AHHH annoying... guess its good that it works again though.

---

