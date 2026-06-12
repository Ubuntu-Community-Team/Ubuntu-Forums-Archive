---
title: "Lots of problems in Firefox"
date: 2008-04-16
forum: General Help
---

### Post by Kajayacht on 2008-04-16
Ok I've been having several problems with Firefox 
number 1, all my bookmarks are gone, when I try to add new bookmarks or restore my bookmarks from a backup, nothing happens
number 2, videos from sites like youtube aren't playing
number 3 the go back one page and go forward one page keys are not working

Yes I've tried uninstalling and reinstalling several times and it didn't help with anything.

I'm rather new to linux still so does anyone know what to do?

---

### Post by Old Marcus on 2008-04-16
Not sure about one or three, but I may be able to help with 2.

Although it seems pretty obvious, have you installed the flash player plugin for firefox?

---

### Post by Kajayacht on 2008-04-16
Yeah, flashplayer is installed.
I don't know, I think there might be a problem with ubuntu or gnome itself because when I click on that button to shutdown, all my toolbars disappear.

So I think I might just reinstall ubuntu, it's going to be annoying though

---

### Post by benmarvin on 2008-04-16
Here's what fixed the Youtube video problem for me:
```

wget http://launchpadlibrarian.net/13155153/flashplugin-nonfree_9.0.115.0ubuntu6%7Enolibflashsupport_i386.deb
sudo dpkg -i flashplugin-nonfree_9.0.115.0ubuntu6~nolibflashsupport_i386.deb
sudo apt-get remove libflashsupport
```

---

### Post by Kajayacht on 2008-04-17
Well, I just reinstalled ubuntu and everything's fine now.

---

