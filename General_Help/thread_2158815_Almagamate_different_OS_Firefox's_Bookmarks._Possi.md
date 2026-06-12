---
title: "Almagamate different OS Firefox's Bookmarks. Possible? Ideas/Suggestions?"
date: 2013-06-30
forum: General Help
---

### Post by mikodo on 2013-06-30
Hello everyone.

I am replacing my one and only desktop computer disk with 2 new ones, and with that am going to create a /MEDIA partition on the bigger platter and symlink it with /mnt in the / partition on the smaller SSD, that is going to boot and hold the /root distros.

I regulary have Xubuntu LTS and Debian Stable Xfce installed and will continue with that. I usually have 4-5 others too, but I don't save anything important in those and they are "expendable",  Xubuntu LTS and Debian stable Xfce are not. So, with Xubuntu, [I can backup Mozilla Firefox Bookmarks with this]("http://support.mozilla.org/en-US/kb/restore-bookmarks-from-backup-or-move-them?redirectlocale=en-US&redirectslug=back-up-bookmarks-or-move-them-to-another-computer"), and I assume I can do it with Debian's Iceweasel instance of Firefox, too. I cannot do it for both and try to install the backup instances to each, because of this warning:

***Caution: Restoring bookmarks from a backup will overwrite your current set of bookmarks with the ones in the backup file.***

Question:

 Anyone have any ideas how I can have one instance of "Bookmarks" that is always accessible to both distro's and stop me having to continually reboot to find one bookmark that is only in the other distro? The only thing I can think of is to have one distro running in a VBox .vdi for a quick jump into, which is not what I really want, as both are important "on the metal installs", for me. 

It just dawned on me that this is really two questions.

1. How can I amalgamate the two sets of Bookmarks I have now and save them for installation to the new installs (Xubuntu and Debian), and
2. How can I continue to have both distro's Bookmarks amalgamated and accessible to each.

Ideas welcome.

I have to go, so I will just throw this out to you guys.

Thanks.

---

### Post by ajgreeny on 2013-06-30
You can very easily link the hidden ~/.mozilla folder in one of the OSs to the other OS and thus actually use the same configuration folder for both.  However, if the systems have different versions of firefox you may have some problems with add-ons in particular, but also other small files etc etc in the config.

The alternative is just to link the file that holds the bookmarks which is ~/.mozilla/firefox/********.default/places.sqlite (**********.default** will be a random alphanumeric name)

---

### Post by Cheesemill on 2013-06-30
You could run into issues trying to share your profile if your OS's use different versions of Firefox.

I'd recommend just setting up [Firefox Sync]("https://support.mozilla.org/en-US/kb/firefox-sync-take-your-bookmarks-and-tabs-with-you") on all of the installations.

---

### Post by mikodo on 2013-06-30
Absolutely fantastic!

I went to the store and came back and here are my answers waiting for me, again. This talk of "Ubuntu Community" not being what it used to be, leaves me thinking it must have been "out of this world", because it has been nothing short of "fantastic" for me, since 8.04. 

Thanks guys.

;p

---

