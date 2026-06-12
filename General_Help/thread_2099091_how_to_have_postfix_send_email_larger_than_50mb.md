---
title: "how to have postfix send email larger than 50mb"
date: 2012-12-28
forum: General Help
---

### Post by zauny on 2012-12-28
I need some guidance. My one of Execs wants to send and 
receive emails with attachment of 100MB at least. I have 
gotten Postfix to send and receive emails with attachment 
of 50MB, however whenever I change message_size_limit to a 
size larger than 50MB Postfix stop processing emails (the 
emails stay in the queue then get rejected after awhile).   
  Any assistance will be greatly appreciated…

---

### Post by lisati on 2012-12-28
Assuming that you've set your copy of Postfix to allow attachments of that size, it's possible that the recipient's server is rejecting or deferring delivery. Are you able to post a copy of the non-delivery report?

---

### Post by zauny on 2012-12-28
kindly see below for my size setting in Postfix...

root@mail:~# postconf |grep size
berkeley_db_create_buffer_size = 16777216
berkeley_db_read_buffer_size = 131072
body_checks_size_limit = 51200
bounce_size_limit = 50000
header_size_limit = 102400
mailbox_size_limit = 0
message_size_limit = 50000000

Below is the error message I get...

 [FONT=Consolas]Your message did not reach some or all of the intended recipients.[/FONT]
  [FONT=Consolas] [/FONT]
  [FONT=Consolas]      Subject:    FW: testing[/FONT]
  [FONT=Consolas]      Sent: 28/12/2012 08:39 AM[/FONT]
  [FONT=Consolas] [/FONT]
  [FONT=Consolas]The following recipient(s) cannot be reached:[/FONT]
  [FONT=Consolas] [/FONT]
  [FONT=Consolas]      'Edward Young' on 28/12/2012 08:40 AM[/FONT]
  [FONT=Consolas]            552 5.3.4 Error: message file too big[/FONT]
  [FONT=Consolas] [/FONT]

---

### Post by rnerwein on 2012-12-28
> **zauny said:**
> I need some guidance. My one of Execs wants to send and 
receive emails with attachment of 100MB at least. I have 
gotten Postfix to send and receive emails with attachment 
of 50MB, however whenever I change message_size_limit to a 
size larger than 50MB Postfix stop processing emails (the 
emails stay in the queue then get rejected after awhile).   
  Any assistance will be greatly appreciated…
hi
have a look in /var/log/mail.*
but i think the problem is on your provider size. most of them limited the size of receiving mails.
fake -> use the split command for your huge mail-file to send parts of the allowed size ;-)
cheers

---

### Post by zauny on 2012-12-28
my issue is, Postfix stop processing emails when I set the message_size_limit to a 
size larger than 50MB. All emails remain in queue (mailq).

---

### Post by cariboo on 2012-12-28
You may want to look at [this]("http://www.postfix.org/DEBUG_README.html") howto, to debug your problem.

---

### Post by zauny on 2012-12-28
Thanks for all the assistance guys :grin:...

I found the solution to my problem:

in  the main.cf file (found under /etc/postfix ) the message_size_limit  must be equal to or less than the virtual_mailbox_limit. I had not set  my virtual_mailbox_limit (therefore it was set to default which is 50MB.) Which is why I was able to increase the message_size_limit to 50MB and Postfix still process email; but when the message_size_limit was increase to more than 50MB it stop processing emails. 

After I set the virtual_mailbox_limit size to 1.5 times the size of what I want the largest email to be I was able to increase the message_size_limit to my desired size. 

Thanks again for all the assistance... :p

---

