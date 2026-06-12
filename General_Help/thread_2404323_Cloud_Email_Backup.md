---
title: "Cloud Email Backup"
date: 2018-10-22
forum: General Help
---

### Post by monosyllabicbabbling on 2018-10-22
This isn't a specifically Ubuntu question except that's where I want the solution to run. I've got a lot of history in email servers in the cloud (i.e. someone else's computer). I'm looking for some way to make a local backup of all that data, preferably one I could easily access/search. [br]1[/br]  [br]1[/br]  There are two products I know of that do exactly what I want but they're both Windows only MailStore and MailShelf.   [br]1[/br][br]1[/br]  I tried to get Thunderbird to do what I wanted, but failed. Pop is no good since it doesn't see folders, and folders are important. Using Thunderbird with IMAP should theoretically be able to download everything, but it doesn't actually do it. Even if it did, there's no way for me to be sure it did,  and finally the cloud server would still be controlling so if something was deleted in the cloud TB would delete it locally as well.   [br]1[/br][br]1[/br]  There do seem to be a number of linux console tools that do the first half of what I want (imapsync, imap-backup,  more?) but I'm not sure how I'd access/search the mail after the messages were down. There arealso enterprise products (Piler, MailArchiva) which are probably overkill, and would be a hassle to setup anyway.  [br]1[/br] [br]1[/br]  Is anyone out there willing to share the solution they have for this problem?

---

### Post by HermanAB on 2018-10-23
The easiest way to make a backup of a cloud is on another cloud.  Open an email account with Google, Yahoo or MS and set your real email to BCC to the other and then you don't have to worry about it anymore.

In order to copy existing mail, open both accounts using the IMAP protocol and then click drag and drop the mail from the one to the other.  (Do not forward or copy the mail, since that will change all the headers - click-drag-drop will copy the mail while keeping it exactly the same.)

---

### Post by monosyllabicbabbling on 2018-10-23
Thanks I had considered that but I really want a local backup so it's under my control. Two seperate places that are both not mine is probably better than one, but I'm hoping to do better.

I suppose I could run my own mail server and duplicate/synchronize accounts on it, but I was looking for a simpler solution.

---

### Post by HermanAB on 2018-10-23
The absolutely easiest mail server to install yourself is Citadel.  Installing it takes about 20 minutes, if your network is configured properly:
[http://www.citadel.org/doku.php](http://www.citadel.org/doku.php)

Citadel is very old and mature, has an efficient database back-end and can handle enormous amounts (terrabytes) of mail.  You can easily set up Citadel to fetch your mail from the cloud mail server.

(In contrast, installing Postfix will take you about two weeks of reading documents, trying and retrying).

---

