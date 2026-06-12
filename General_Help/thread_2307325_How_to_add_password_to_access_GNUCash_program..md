---
title: "How to add password to access GNUCash program."
date: 2015-12-23
forum: General Help
---

### Post by gilloz on 2015-12-23
I have install GNUcash Financial Software.  How can I add a password to prevent anyone else from having access to my financial account?  Right now, I open the program and it goes directly to my checking account.

---

### Post by Vladlenin5000 on 2015-12-24
Are you intending to let other people use your own Ubuntu user account?
If not there's no need for any program specific password.
If so, why? Just create users for the other people sharing the same computer. The others won't be able to access GNUCash with your settings because those are stored in your profile and in your profile only.

---

### Post by HermanAB on 2015-12-24
UNIX is designed as a multi-user system and maintains a separate home data directory for each user.

Don't give other people access to your computer account.  If you have to give them access to the computer, make them a separate user account.

If you have to share data between different user accounts, make a separate directory with a separate group ID and make everybody that needs to share, members of that group, then for good measure, put a link on their desktop to the share.

---

### Post by gilloz on 2015-12-24
Thanks guys for your responses.  After using Quicken for so many years I've gotten use to always entering a password to access my Quicken account, which seemed, to me, logical.  Since my Quicken no longer functions in Windows 10 and I've use Ubuntu, off and on, for several years, I was looking for another way of accessing my financial programs.  No, I haven't upgraded to Windows 10 yet and am being very hesitant about doing it at this time.  BTW, I have two desktops, one with Windows 7 and the other with Ubuntu 14.04LTS.  I was Dual booting between these two OS's until I acquired the second desktop.  Anyway, thanks for the info and will follow through as both of you suggested.  Happy Holidays.

NOTE  Everything I have read Online about Quicken 2014 being not compatible with Windows 10 is what I am going on, at this time.

---

