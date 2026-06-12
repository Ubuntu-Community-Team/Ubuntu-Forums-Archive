---
title: "Phpmyadmin"
date: 2007-03-20
forum: General Help
---

### Post by olpe on 2007-03-20
Hi!

I am having strange problem with ubuntu package of phpmyadmin. When I browse table and try to delete an entry from it outcomes the pop-up windown asking me to confirm deletion. If I press OK and try to delete the row, nothing happens. It seems that it stucks in eternal loop or something, nothing shows to mysql logs. 

Well if I write the same exact sql command with SQL-tab, everythin works just great.

The problem is not the rights but the deletation of one entry from the browse list.

One more thing, the tab Empty works just fine. Can anyone help?

---

### Post by Brazen on 2007-03-20
First of all, don't use Edgy for your servers; use Dapper.

Second of all, for php application like phpMyAdmin (or Joomla, Gallery2, or Torrentflux, etc), I just download the source files and alias them into my website directory.  You lose the update advantages of apt-get, but it's an acceptable trade-off for me; plus I like to do the Apache configuration a little differently.

Anyway, doing it this way, I have not had a single problem with phpMyAdmin.  This doesn't really solve the issue at hand, but it might be something to consider.

---

