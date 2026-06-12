---
title: "I cannot save a file because I don't have 'permission' to do so."
date: 2008-01-19
forum: General Help
---

### Post by innoBy on 2008-01-19
[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html)

However when I got to save, I cannot save because I do not have permissions to do so. How do I make sure I'm logged on as "god" on my system?

---

### Post by jleaker01z on 2008-01-19
add gksudo before gedit on that particular line in your instructions

---

### Post by innoBy on 2008-01-19
I gots it working anyways, but still, I've already given myself root permissions and it didn't work....anywho I still need to know how.

---

### Post by jleaker01z on 2008-01-19
You can switch to SuperUser mode by entering "su -" into a terminal.  The password it asks for is not your regular password, but the root password, which you would need to set via System>Administration>Users/Groups if you havent done so already.

Note tho, that loggin in as superuser is NOT recommended.  It would be very easy to mess up your entire installation that way.  The recommended way is to add sudo, or gksudo, before the command you want to have root priviliges.

---

