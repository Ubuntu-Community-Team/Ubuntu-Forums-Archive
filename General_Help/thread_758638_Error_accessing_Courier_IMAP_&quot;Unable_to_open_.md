---
title: "Error accessing Courier IMAP: &quot;Unable to open this mailbox&quot;"
date: 2008-04-18
forum: General Help
---

### Post by ostorezio on 2008-04-18
I have this nasty problems since installing Courier-IMAP, a couple of weeks ago, I really did a good deal of Googling on it, but never been able to find a solution.

I'm running courier-imap 4.1.3 on Ubuntu Gutsy

The client I'm using is Thunderbird 2.0.0.12

I configured courier as a plain-vanilla IMAP server, I'm not using neither POP nor SMTP.

When I try to open my (empty for now) imap store from Thunderbird I get a popup with the following error (I had similar erros from Outlook):

     "The current command did not succeed. The mail server responded: Unable to open this mailbox.."

The mail.log file reports no relevant errors:

Apr 16 11:35:49 cevrin imapd: Connection, ip=[::ffff:127.0.0.1]
Apr 16 11:35:53 cevrin imapd: LOGIN, user=ezio_im, ip=[::ffff:127.0.0.1], protocol=IMAP

The home folder of ezio_im contains Maildir only (created by courier-imap):

[FONT="Courier New"]ezio_im@cevrin:~$ ls -la Maildir/
total 12
drwxr-xr-x 3 ezio_im ezio_im 4096 2008-04-17 09:52 .
drwx------ 3 ezio_im ezio_im 4096 2008-04-16 15:58 ..
drwx------ 6 ezio_im ezio_im 4096 2008-04-15 09:25 .Trash
ezio_im@cevrin:~$ ls -la Maildir/.Trash/
total 32
drwx------ 6 ezio_im ezio_im 4096 2008-04-15 09:25 .
drwxr-xr-x 3 ezio_im ezio_im 4096 2008-04-17 09:52 ..

-rw-r--r-- 1 ezio_im ezio_im   43 2008-04-15 09:25 courierimapacl
drwx------ 2 ezio_im ezio_im 4096 2008-04-15 09:25 courierimapkeywords
-rw-r--r-- 1 ezio_im ezio_im   15 2008-04-15 09:25 courierimapuiddb
drwx------ 2 ezio_im ezio_im 4096 2008-04-15 09:25 cur
-rw------- 1 ezio_im ezio_im    0 2008-04-15 09:25 maildirfolder
drwx------ 2 ezio_im ezio_im 4096 2008-04-15 09:25 new
drwx------ 2 ezio_im ezio_im 4096 2008-04-16 16:07 tmp[/FONT]

I also wiresharked my Thunderbird-IMAP conversation, here we go:

[FONT="Courier New"]* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2005 Double Precision, Inc.  See COPYING for distribution information.
1 login ezio_im MyPassword
1 OK LOGIN Ok.
3 namespace
* NAMESPACE (("INBOX." ".")) NIL (("#shared." ".")("shared." "."))
3 OK NAMESPACE completed.
4 lsub "" "INBOX.*"
4 OK LSUB completed
5 lsub "" "#shared.*"
5 OK LSUB completed
6 lsub "" "shared.*"
6 OK LSUB completed
7 list "" "INBOX"
* LIST (\Unmarked \HasChildren) "." "INBOX"
7 OK LIST completed
8 list "" "INBOX.Trash"
* LIST (\HasNoChildren) "." "INBOX.Trash"
8 OK LIST completed
9 create "INBOX.Trash"
9 NO Cannot create this folder.
10 select "INBOX"
10 NO Unable to open this mailbox.
[/FONT]
The offending commands seem to be 9 & 10 ... I'm not such an IMAP expert, what are they actually trying to do? What's wrong on my server?

I read something about IMAP namespaces that are a little tricky, could this be the case?

Cheers,

                     Ezio
Turin, Italy

---

### Post by ostorezio on 2008-04-23
The Maildir folder was invalid.

Here's the solution:

>A valid maildir is created by the maildirmake command.

---

