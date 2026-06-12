---
title: "'kbuildsycoca4 running...' error"
date: 2015-08-02
forum: General Help
---

### Post by antbyrd on 2015-08-02
I have recently been messing with PostgreSQL and pgAdmin III, and I think this has something to do with this error.

I am currently trying to install the _pycharm-community_ package and run into this problem that I must 'ctrl + C' out of:

[CENTER]**brilliant@Ame-WhitthouseStation:~$ kbuildsycoca4 running...**
**Error: "/var/tmp/kdecache-brilliant" is owned by uid 1000 instead of uid 0.**
**kbuildsycoca4(18877) VFolderMenu::loadDoc: Parse error in "/home/brilliant/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu" , line 1 , col 1 : "unexpected end of file"**[/CENTER]

The *uid 1000* is what makes me think that this is from PostgreSQL, because I recall seeing my user (brilliant) with that ID when looking at some setting dealing with PostgreSQL (with package-created user *postgres* being 0). After a bit of searching, I see that I may be able to fix my issue by changing the permission back to *uid 0*, so I run:

[CENTER][B]sudo chown root.root /var/tmp/kdecache-brilliant

[/B]
[/CENTER]
While that did get rid of the error message, it did not get rid of my 'ctrl + C' process-ending need. I am quite new to Linux/Ubuntu, so I look forward to your guidance! Thank you for your time, it means a lot.



_***SOLVED:***_ I guess that changing of ownership did due the trick. It did not work for me initially, but after doing a system update|upgrade, I reinstalled pycharm-community and it ran fine, no errors at all.

---

