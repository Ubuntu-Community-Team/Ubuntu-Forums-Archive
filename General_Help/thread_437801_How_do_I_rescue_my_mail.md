---
title: "How do I rescue my mail?"
date: 2007-05-09
forum: General Help
---

### Post by Doffen on 2007-05-09
Hi,

I have been using Dapper Drake, but now I cannot boot it (long story). So after testing the 'live' Feisty Fawn, I've decided to install it, but before deleting my current Ubuntu partitions I would like to try rescuing my old e-mail in Dapper Drake. 

Feisty 'live' can see and read my Dapper partitions, but as a newbie I don't know how (best) to move and save my Evolution mail file (there is only one big file in /var/mail...) - to a NTFS partition or try burning it to a DVD disc - and what to do to with it afterwards. Would it suffice to drop it in the new /var/mail directory under Feisty?

Tips appreciated...!

Doffen

---

### Post by Josh1 on 2007-05-09
What mail client do you use?

---

### Post by Doffen on 2007-05-09
Hi,

Evolution - mentioned above...
However, since I lost access to Dapper, I've been using Thunderbird, and now I am not sure which I prefer...

---

### Post by rturner on 2007-05-09
I use mutt, but it keeps mail in /var/mail, like evolution.  So you could copy that file, which contains all your emails to a network share, or wherever you can access it and put it back in after the new install.  I just installed Thunderbird, but I'm not too familiar with it.  It keeps the mail files under .thunderbird in your home directory.  So I'm sure you could probably read your old mail with Thunderbird, but I'm not sure how.  The Thunderbird Inbox is a file, not a directory, so maybe you could put your old mail in the same area and get Thunderbird to treat it like another place to archive mail.

---

### Post by Doffen on 2007-05-09
> **rturner said:**
>  (...) The Thunderbird Inbox is a file, not a directory, so maybe you could put your old mail in the same area and get Thunderbird to treat it like another place to archive mail.

Thanks for confirming that I only need to save the one file. Will be interesting to see if Thunderbird can read it 'off hand'. I will try to have Feisty 'live' transfer it to a NTFS partition before I run amok with partitioning etc. :) Thanks again!

Doffen

---

### Post by umarvlie on 2007-05-09
Thunderbird is very flexible in the way it allows for backup/restore and migrate mail files even from other mail programs: [Thunderbird FAQ]("http://www.mozilla.org/support/thunderbird/faq")

I changed from Windows XP to Ubuntu (on both i use(d) Thinderbird) and it works perfect.

---

### Post by Doffen on 2007-05-09
Well, I tried to use the Ubuntu 'live' desktop to move my mail file to a Windows partition, but Ubuntu said it was not my file and refused to do it. Since I cannot boot to my old Dapper installation, how do I convince Feisty 'live' that I do indeed own and have permission to handle the file?


Doffen

---

### Post by Doffen on 2007-05-10
Any takers?

---

