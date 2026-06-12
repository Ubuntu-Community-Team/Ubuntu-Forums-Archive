---
title: "how to remove .sh graphic drivers ?"
date: 2012-12-11
forum: General Help
---

### Post by West201 on 2012-12-11
Google Chrome is producing very choppy pages, and according to this post ( [http://askubuntu.com/questions/161450/google-chrome-not-rendering-webpages-correctly]("http://askubuntu.com/questions/161450/google-chrome-not-rendering-webpages-correctly") ) it's better to install AMD beta drivers. The .zip includes a .sh.. Would I be able to remove it if it doesn't work ? Or upgrade when the release is final ?

---

### Post by Mark Phelps on 2012-12-12
Unless you have one of the "HD" series AMD cards, the new AMD drivers won't work with it.  To see what you have, open a terminal, enter "lspci" (without the quotes) -- and look for the line containing "VGA".  That will show the make and model AMD chipset in use.

Installing and removing drivers is not a simple process of running a "setup" program as it is in Windows.  If you install these and they do not work, you will need to go through a lot of work to remove them.

---

