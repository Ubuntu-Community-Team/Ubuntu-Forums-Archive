---
title: "Evolution won't update IMAP folders"
date: 2014-10-15
forum: General Help
---

### Post by DavidS on 2014-10-15
I use IMAP for my email.  I access my mail server from 2 computers, both using Evolution 3.2.3 on Ubuntu 12.04.  I also access the IMAP server from a Samsung phone and a Google Nexus7 tablet - these are both Android machines, of course, but have different e-mail clients.

Today, neither of my Ubuntu machines will update folders.  Instead, if I display a folder I get an error message saying "You must be working online to complete this operation".  But both Android machines can access my mail without any problem.

I also notice that under "Folder Subscriptions" none are listed (previously they were), and although it shows the name of my mail account in the "Account" dropdown, when I click on "Refresh" there are still no folders listed.

Strangely, when I do a "Send and Receive" it appears to proceed normally.  But I cannot see any new e-mails for the reasons I have already given.

I have not changed any settings in Evolution on either of the 2 Ubuntu machines, and Evolution was working perfectly with my IMAP server until today.

Any suggestions?

---

### Post by buzzingrobot on 2014-10-15
I don't have Evolution installed here now, but I recall that it has a menu option to switch to offline mode, and remember it mysteriously going into offline mode sometimes. Might be worth a look.

---

### Post by DavidS on 2014-10-15
Thanks for the suggestion, but it isn't the answer.  I had already looked at this, and it says that I am on-line.

Both my Ubuntu machines have developed this same problem today.  All 4 of my machines (2 Ubuntu and 2 Android) are connecting to the same IMAP server through the same router, so it would appear to be an Evolution problem.  Yet Evolution has not been updated for some time, so far as I can see, so how is it that both computers are having the same problem simultaneously?  I'm mystified.

---

### Post by nbday on 2014-10-16
This is related to the POODLE SSL(v3) bug.  Many email providers (including fastmail.fm) have simply disabled log-ons using SSL(v3) so you can't connect, and STARTLS (which connects via plain text and switches to encryption afterwards) isn't supported.  This is due to a bug in evolution versions prior to 3.12.  There is a patch for Fedora already for earlier versions.  Ubuntu has disfavored evolution for so long (although they make heavy use of the data-server) that I don't expect rapid relief even for the LTS version (which supplies 3.10.x).  A solution would be to upgrade to 14.10 which is in release candidate status today and works fine here.  Then you get evolution 3.12.7, which works fine with fastmail.fm and charter.net at least.

---

### Post by buzzingrobot on 2014-10-16
One of the weaknesses of every mail client I recall using, including in Linux, is that each presents SSL, TLS, etc. as bare options without explaining the security implications of opting for one over another.  Expectations that users will themselves have that understanding are incorrect, and development and design based on that expectation are inadequate.

Fastmail has posted a nice explanation of Poodle and how it impacts their customers: [http://blog.fastmail.fm/2014/10/15/ssl-3-0-disabled-due-to-security-vulnerability/](http://blog.fastmail.fm/2014/10/15/ssl-3-0-disabled-due-to-security-vulnerability/). It would be nice if all mail providers did the same, rather than turn things off and not tell anyone.

[EDIT: Mozilla explainer here: [https://blog.mozilla.org/security/2014/10/14/the-poodle-attack-and-the-end-of-ssl-3-0/](https://blog.mozilla.org/security/2014/10/14/the-poodle-attack-and-the-end-of-ssl-3-0/) which includes a link to an extension which will disable SSL 3 in Firefox, Thunderbird and other Mozilla products ([https://addons.mozilla.org/en-US/firefox/addon/ssl-version-control/](https://addons.mozilla.org/en-US/firefox/addon/ssl-version-control/))  Firefox 34, due out late November, will not enable SSL 3.]


(I may try the 3.12.7 Evolution release to see if it's eliminated the annoying instances when it seems to lose the connection with the server and posts ugly yellow error messages. That's why I don't use it.)

---

