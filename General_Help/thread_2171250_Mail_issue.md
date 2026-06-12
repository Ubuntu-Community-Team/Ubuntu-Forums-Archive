---
title: "Mail issue"
date: 2013-08-29
forum: General Help
---

### Post by Da_Panther on 2013-08-29
Hey everyone,

You are always helpful here, so I throw this one at you hoping you come through again!

I was up and running using mail in the terminal between users (local only). I was working on trying to get myself a DNS set up so I could use my laptop as a mail server, but obviously, no such thing as a free DNS. So, I scrapped that idea, after I had installed sendmail .... and I think I may have messed something up when I removed sendmail, because now when I use mail to send a message, I cannot Ctrl-D to send - it just blinks the cursor and does not send. I can keep typing the body of my message though. When I Ctrl-C out of mail it gives me 

Cannot open file /home/swordfish/dead.letter: No such file or directory

Any ideas?

Thanks a lot!!

---

### Post by SeijiSensei on 2013-08-30
You still need a "mail transfer agent" like Postfix or sendmail to process and deliver the message.  I'm a long-standing sendmail user, but if you want to be consistent with Ubuntu defaults, install Postfix.

---

### Post by Da_Panther on 2013-08-30
Alright. So now the mail program accepts my Ctrl+D operation and exits normally. However, the mail is not sent to the destination user, nor is a mail not sent email generated. Whats the next step?

---

### Post by Da_Panther on 2013-08-31
*bump* I would appreciate if anyone can help me, or point me to the right informations at least :) thanks

---

### Post by SeijiSensei on 2013-08-31
Did you reinstall Postfix?

What do you see in /var/log/mail.log?

---

### Post by Da_Panther on 2013-08-31
postfix is reinstalled. 

the mail.log is empty. there are two other files, mail.err and mail.err.1

Here is my mail.err.1 (only file with text in it)

```
Aug 29 17:22:42 swordfishBook sendmail[12079]: My unqualified host name (swordfishBook) unknown; sleeping for retry
Aug 29 17:24:02 swordfishBook sendmail[12079]: unable to qualify my own domain name (swordfishBook) -- using short name
Aug 29 17:24:22 swordfishBook sm-mta[12150]: My unqualified host name (swordfishBook) unknown; sleeping for retry
Aug 29 17:24:24 swordfishBook sm-msp-queue[12157]: My unqualified host name (swordfishBook) unknown; sleeping for retry
Aug 29 17:25:42 swordfishBook sm-mta[12150]: unable to qualify my own domain name (swordfishBook) -- using short name
Aug 29 17:25:44 swordfishBook sm-msp-queue[12157]: unable to qualify my own domain name (swordfishBook) -- using short name
Aug 29 17:26:24 swordfishBook sendmail[13259]: My unqualified host name (swordfishBook) unknown; sleeping for retry
Aug 29 17:27:44 swordfishBook sendmail[13259]: unable to qualify my own domain name (swordfishBook) -- using short name
Aug 29 17:40:21 swordfishBook sm-msp-queue[13409]: My unqualified host name (swordfishBook) unknown; sleeping for retry
Aug 29 17:41:41 swordfishBook sm-msp-queue[13409]: unable to qualify my own domain name (swordfishBook) -- using short name
Aug 29 18:00:21 swordfishBook sm-msp-queue[13750]: My unqualified host name (swordfishBook) unknown; sleeping for retry
Aug 29 18:01:41 swordfishBook sm-msp-queue[13750]: unable to qualify my own domain name (swordfishBook) -- using short name
Aug 29 18:20:21 swordfishBook sm-msp-queue[18633]: My unqualified host name (swordfishBook) unknown; sleeping for retry
Aug 29 18:21:41 swordfishBook sm-msp-queue[18633]: unable to qualify my own domain name (swordfishBook) -- using short name
Aug 29 18:40:21 swordfishBook sm-msp-queue[18824]: My unqualified host name (swordfishBook) unknown; sleeping for retry
Aug 29 18:41:41 swordfishBook sm-msp-queue[18824]: unable to qualify my own domain name (swordfishBook) -- using short name
Aug 29 18:43:19 swordfishBook sendmail[18866]: My unqualified host name (swordfishBook) unknown; sleeping for retry
Aug 29 18:48:05 swordfishBook sendmail[20553]: My unqualified host name (swordfishBook) unknown; sleeping for retry
Aug 29 18:49:25 swordfishBook sendmail[20553]: unable to qualify my own domain name (swordfishBook) -- using short name
Aug 29 19:00:21 swordfishBook sm-msp-queue[22288]: My unqualified host name (swordfishBook) unknown; sleeping for retry
Aug 29 19:01:41 swordfishBook sm-msp-queue[22288]: unable to qualify my own domain name (swordfishBook) -- using short name
Aug 29 19:15:50 swordfishBook sm-mta[1410]: My unqualified host name (swordfishBook) unknown; sleeping for retry
Aug 29 19:15:51 swordfishBook sm-msp-queue[1430]: My unqualified host name (swordfishBook) unknown; sleeping for retry
Aug 29 19:17:10 swordfishBook sm-mta[1410]: unable to qualify my own domain name (swordfishBook) -- using short name
Aug 29 19:17:11 swordfishBook sm-msp-queue[1430]: unable to qualify my own domain name (swordfishBook) -- using short name
Aug 29 19:40:26 swordfishBook sm-msp-queue[3702]: My unqualified host name (swordfishBook) unknown; sleeping for retry
Aug 29 19:41:46 swordfishBook sm-msp-queue[3702]: unable to qualify my own domain name (swordfishBook) -- using short name
Aug 30 15:27:22 swordfishBook sendmail[6662]: My unqualified host name (swordfishBook) unknown; sleeping for retry
Aug 30 15:33:20 swordfishBook postfix/master[12004]: fatal: bind 127.0.0.1 port 25: Address already in use
Aug 30 15:45:58 swordfishBook postfix/sendmail[13883]: fatal: Recipient addresses must be specified on the command line or via the -t option
Aug 30 15:46:21 swordfishBook postfix/sendmail[13908]: fatal: Recipient addresses must be specified on the command line or via the -t option
Aug 30 15:46:25 swordfishBook postfix/sendmail[13911]: fatal: usage: sendmail [options]
```



EDIT:

/usr/bin/mailutils-config: 109: /usr/bin/mailutils-config: mu: not found

I have a feeling that my mailutils.rc file was deleted, and was never recreated. Soes someone have an example of one so I can remake mine, or if there is a way for mailutils to generate it? thanks.

---

### Post by SeijiSensei on 2013-08-31
I don't know about the mailutils file, but the problem in error.log is that you don't have a name service entry for your machine.  The simplest solution is to add an entry to /etc/hosts for "swordfishbook."

However a more serious problem seems to be that you have both sendmail and Postfix installed.  Purge both packages, then install Postfix again.

---

### Post by Da_Panther on 2013-09-01
I purged both. Reinstalled Postfix, and checked my /etc/hosts file. My swordfishBook entry was linked to 127.0.1.1 ... so I tried to set it for 127.0.0.1 like LocalHost, but still no joy. 

I just want to make sure I have everything...
I have the MUA - mailutils.
I have the MTA - Postfix
Is the MDA included in one of these two packages? And if so, how do I check their various config files?

---

### Post by Da_Panther on 2013-10-24
Sorry to revisit an old topic, I actually managed to make some progress in this issue. 

I started looking around in a few of the files (/etc/aliases, /etc/procmail/ and so on). 
I made a few tweaks. Now I am able to send and recieve mail normally for all my users, but my root still gets the message "you have new mail" when I log in. However, when I give the mail command, it says "no mail for root".... 
This is the last thing to fix here, so if anyone has any ideas, I would appreciate it!

---

