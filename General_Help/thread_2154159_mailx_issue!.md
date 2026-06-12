---
title: "mailx issue!"
date: 2013-06-13
forum: General Help
---

### Post by steve701 on 2013-06-13
Hi all: my mailx stopped working after my internet provider reset the modem/IP address couple of days ago.
(it used to work perfectly fine).

But last night when I tried to send mail:  (echo hey | mailx -s "subject" [email]me@mydomain.com[/email])  
it gave back the prompt but no mail was in my inbox nor in the junk.

Today when I try to send, it does not even return the prompt any more!! I have to Ctrl-Z and kill the process.

mailx is from here:
/usr/bin/mailx

Also when I check for sendmail processes, I see 2:
root      2553     1  0 15:51 ?        00:00:00 sendmail: MTA: accepting connections         
root      4351  4341  0 16:17 ?        00:00:00 /usr/sbin/sendmail -i -FCronDaemon -oem root

Does mailx connect with sendmail? Where does it obtain its smtp to send from? How do I debug this issue? I cannot even use -v switch as it seems to be broken.
How can I even remove and reinstall mailx?

Thanks,
Steve

---

### Post by steve701 on 2013-06-15
Issue closed - I configured to use it through gmail mail and now it send fine.

---

