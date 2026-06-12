---
title: "Fetchmail Problems - yahoo incorrect headers"
date: 2007-08-25
forum: General Help
---

### Post by Rescue9 on 2007-08-25
Didn't really know where to put this... if this isn't the right place, please move

I'm have lots of problems and I can't diagnose. Every now and then yahoo screws with things on their end, so I'm not even sure it's my problem. Everything was working fine about a week ago till I got a headerless email message. I deleted it thinking everything was cool, but after that fetchmail wouldn't get anything from yahoo. The worst part was that it would delete the mail from the yahoo server, so I'm not even sure how many emails I lost.

I'm using FreePOPs 0.0.99, and fetchmail-6.3.8 (using the source to test, but was using the ubuntu package for feisty).

Here's the fetchmail log from yahoo down:
```
fetchmail: 6.3.8 querying localhost (protocol POP3) at Sat 25 Aug 2007 08:08:50 AM CDT: poll started
Trying to connect to 127.0.0.1/2000...connected.
fetchmail: POP3< +OK FreePOPs/0.0.99 pop3 server ready
fetchmail: POP3> CAPA
fetchmail: POP3< +OK ANSWER FOLLOW
fetchmail: POP3< TOP
fetchmail: POP3< USER
fetchmail: POP3< UIDL
fetchmail: POP3< .
fetchmail: localhost: opportunistic upgrade to TLS failed, trying to continue.
fetchmail: POP3> USER rescue9@yahoo.com
fetchmail: POP3< +OK PLEASE ENTER PASSWORD
fetchmail: POP3> PASS *
fetchmail: POP3< +OK ACCESS ALLOWED
fetchmail: selecting or re-polling default folder
fetchmail: POP3> STAT
fetchmail: POP3< +OK 1 1024
1 message for rescue9@yahoo.com at localhost (1024 octets).
fetchmail: POP3> LIST 1
fetchmail: POP3< +OK 1 1024
fetchmail: POP3> RETR 1
fetchmail: POP3< +OK ANSWER FOLLOW
reading message rescue9@yahoo.com@localhost.localdomain:1 of 1 (1024 octets)
fetchmail: incorrect header line found while scanning headers
fetchmail: line: <!--web36610-->
.................................................................................................fetchmail: message rescue9@yahoo.com@localhost.localdomain:1 was not the
expected length (99730 actual != 1024 expected)
 flushed
fetchmail: POP3> DELE 1
fetchmail: POP3< +OK MESSAGE MARKED FOR DELETION
fetchmail: POP3> QUIT
fetchmail: POP3< +OK BYE BYE, UPDATING
fetchmail: 6.3.8 querying localhost (protocol POP3) at Sat 25 Aug 2007 08:08:53 AM CDT: poll completed
fetchmail: not swapping UID lists, no UIDs seen this query
fetchmail: Deleting fetchids file.
fetchmail: normal termination, status 0
fetchmail: Deleting fetchids file.

```

My /etc/fetchmailrc file reads as such:
```
###################### BEGIN rescue@corridor9.net########################

poll pop.gmail.com port 995 proto pop3
user "mademt@gmail.com" password "YouDon'tNeedThis" ssl is "c9rescue" here

poll pop.gmail.com port 995 proto pop3
user "madfireman@gmail.com" password "YouDon'tNeedThis" ssl is "c9rescue" here

poll localhost port 2000 proto pop3
user "rescue9@yahoo.com" password "YouDon'tNeedThis" is "c9rescue" here

###################### END rescue@corridor9.net##########################


```

A bit redundant, but /var/log/mail.info shows (NOTE: This was with 6.3.6 ubuntu package, not the source as listed above):
```
Aug 25 07:42:06 sulaco fetchmail[28834]: starting fetchmail 6.3.6 daemon
Aug 25 07:42:08 sulaco fetchmail[28834]: 1 message for rescue9@yahoo.com at localhost (1024 octets).
Aug 25 07:42:09 sulaco fetchmail[28834]: reading message rescue9@yahoo.com@localhost.localdomain:1 of 1 (1024 octets) (log message incomplete)
Aug 25 07:42:09 sulaco fetchmail[28834]: incorrect header line found while scanning headers
Aug 25 07:42:09 sulaco fetchmail[28834]:  flushed
Aug 25 07:42:10 sulaco fetchmail[28834]: sleeping at Sat 25 Aug 2007 07:42:10 AM CDT for 300 seconds

```

Freepops is NOT setup for chroot jail.

Any help would be greatly appreciated as a majority of my mail goes through the yahoo server. BTW, fetching gmail servers work fine.

---

### Post by SPr on 2007-08-25
fetchmail: localhost: opportunistic upgrade to TLS failed, trying to continue.

This is a shot in the dark:
does Yahoo use a secure connection? Are you trying to use a secure connection?

---

### Post by Rescue9 on 2007-08-25
Naw... thats not it. I set sslproto ssl123 in the fetchmailrc file so it wouldn't try to upgrade to TLS. I think the upgrade basically means "if it's available use it, otherwise just get it normally". 

Even after that I got the following when fetching mail:
```
fetchmail: 6.3.8 querying localhost (protocol POP3) at Sat 25 Aug 2007 09:48:31 AM CDT: poll started
Trying to connect to 127.0.0.1/2000...connected.
fetchmail: POP3< +OK FreePOPs/0.0.99 pop3 server ready
fetchmail: POP3> CAPA
fetchmail: POP3< +OK ANSWER FOLLOW
fetchmail: POP3< TOP
fetchmail: POP3< USER
fetchmail: POP3< UIDL
fetchmail: POP3< .
fetchmail: POP3> USER rescue9@yahoo.com
fetchmail: POP3< +OK PLEASE ENTER PASSWORD
fetchmail: POP3> PASS *
fetchmail: POP3< +OK ACCESS ALLOWED
fetchmail: selecting or re-polling default folder
fetchmail: POP3> STAT
fetchmail: POP3< +OK 3 5120
3 messages for rescue9@yahoo.com at localhost (5120 octets).
fetchmail: POP3> LIST 1
fetchmail: POP3< +OK 1 2048
fetchmail: POP3> RETR 1
fetchmail: POP3< +OK ANSWER FOLLOW
reading message rescue9@yahoo.com@localhost.localdomain:1 of 3 (2048 octets)
fetchmail: incorrect header line found while scanning headers
fetchmail: line: <!--web36611-->
.................................................................................................fetchmail: message rescue9@yahoo.com@localhost.localdomain:1 was not the expected length (100126 actual != 2048 expected)
 flushed
fetchmail: POP3> DELE 1
fetchmail: POP3< +OK MESSAGE MARKED FOR DELETION
fetchmail: POP3> LIST 2
fetchmail: POP3< +OK 2 1024
fetchmail: POP3> RETR 2
fetchmail: POP3< +OK ANSWER FOLLOW
reading message rescue9@yahoo.com@localhost.localdomain:2 of 3 (1024 octets)
fetchmail: incorrect header line found while scanning headers
fetchmail: line: <!--web36604-->
.................................................................................................fetchmail: message rescue9@yahoo.com@localhost.localdomain:2 was not the expected length (99752 actual != 1024 expected)
 flushed
fetchmail: POP3> DELE 2
fetchmail: POP3< +OK MESSAGE MARKED FOR DELETION
fetchmail: POP3> LIST 3
fetchmail: POP3< +OK 3 2048
fetchmail: POP3> RETR 3
fetchmail: POP3< +OK ANSWER FOLLOW
reading message rescue9@yahoo.com@localhost.localdomain:3 of 3 (2048 octets)
fetchmail: incorrect header line found while scanning headers
fetchmail: line: <!--web36610-->
.................................................................................................fetchmail: message rescue9@yahoo.com@localhost.localdomain:3 was not the expected length (99788 actual != 2048 expected)
 flushed
fetchmail: POP3> DELE 3
fetchmail: POP3< +OK MESSAGE MARKED FOR DELETION
fetchmail: POP3> QUIT
fetchmail: POP3< +OK BYE BYE, UPDATING
fetchmail: 6.3.8 querying localhost (protocol POP3) at Sat 25 Aug 2007 09:48:43 AM CDT: poll completed
fetchmail: not swapping UID lists, no UIDs seen this query
fetchmail: Deleting fetchids file.
fetchmail: normal termination, status 0
fetchmail: Deleting fetchids file.

```

Like I said... I'm not so sure that yahoo didn't screw with the web interface to prevent fetchmail from working so we have to pay for the pop service. They liked doing that a lot with pidgin (gaim) in the past.

Either way... I cna't verify this so I have to assume that it's a problem on my end. Would be nice to know if others are dropping mail.

---

### Post by SPr on 2007-08-25
Free Yahoo accounts don't have POP3 access.

---

### Post by Rescue9 on 2007-08-25
> **SPr said:**
> Free Yahoo accounts don't have POP3 access.
Gee... really. :-P 

Thats why I've been using freepops. It's been working for well over 3 years now, so unless yahoo changed something in their web client, it should still work.

---

### Post by Rescue9 on 2007-08-25
Finally.... after searching for days I found this post:
[http://forums.mozillazine.org/viewtopic.php?t=578578&](http://forums.mozillazine.org/viewtopic.php?t=578578&)

It seems that yahoo changed the header information in the web interface to specifically block freepops, ypops, and webmail extensions from working. This is simply my opinion and not fact. Would be nice to see if people who have pop access are having the same problem.

---

### Post by Rescue9 on 2007-08-25
Don't know who all this helps... but here's what I found.

[http://freepops.diludovico.it/freepops-english/6272-yahoo-classic-accounts-failing.html](http://freepops.diludovico.it/freepops-english/6272-yahoo-classic-accounts-failing.html)

---

### Post by Rescue9 on 2007-08-25
WOOHOO!!!! FIXED IT!

Ok... here's the deal.

The Problem: Yahoo changed some code which messed up the freepopsd; this caused fetchmail to not find the correct headers and flush the message without delivering it. It also deleted it fromt he yahoo server... potentially big issue if you don't realize there is some problem with your yahoo mail not showint up.

The solution: If you're running feisty, you need to manually edit the /usr/share/freepops/lua/yahoo.lua and change the line:
```
strCmdMsgView = "%sym/ShowLetter?box=%s&PRINT=1&Nhead=f&toc=1&MsgId=%s&bodyPart=%s",
```
to read
```
 strCmdMsgView = "%sya/download?box=%s&PRINT=1&Nhead=f&MsgId=%s&bodyPart=%s",
```

Then restart freepops and restart fetchmail. It should fetch all unread messages in your inbox again.
Hope this helps.

---

### Post by rfurman24 on 2007-09-06
> **Rescue9 said:**
> WOOHOO!!!! FIXED IT!

Ok... here's the deal.

The Problem: Yahoo changed some code which messed up the freepopsd; this caused fetchmail to not find the correct headers and flush the message without delivering it. It also deleted it fromt he yahoo server... potentially big issue if you don't realize there is some problem with your yahoo mail not showint up.

The solution: If you're running feisty, you need to manually edit the /usr/share/freepops/lua/yahoo.lua and change the line:
```
strCmdMsgView = "%sym/ShowLetter?box=%s&PRINT=1&Nhead=f&toc=1&MsgId=%s&bodyPart=%s",
```
to read
```
 strCmdMsgView = "%sya/download?box=%s&PRINT=1&Nhead=f&MsgId=%s&bodyPart=%s",
```

Then restart freepops and restart fetchmail. It should fetch all unread messages in your inbox again.
Hope this helps.

Thanks a bunch. I just built a new computer and installed Ubuntu with my old /home directory and reinstall all my apps on from the previous computer. When I went to use my yahoo account it no longer worked. I thought I had done something wrong but It seems that yahoo had made some kind of change the same day I got the new computer going. After installing different freepops and even trying webmail nothing worked until I found this post.

---

