---
title: "XFCE Applications Menu problem after 7.04 -&gt; 7.10 update"
date: 2008-01-14
forum: General Help
---

### Post by xunil76 on 2008-01-14
ok, so i just recently upgraded from Xubuntu 7.04 to 7.10, and i'm having some problems with my Applications Menu.  some of the items that were there are no longer there (such as my "Disk Usage Analyzer" and the "Search For Files..." launcher), and i cannot for the life of me figure out how to add them back.

the items still show up in /usr/share/applications, and i have tried the "fix" over at this site: [XFCE Menu Items](http://tehpost.blogspot.com/2006/09/xubuntu-xfce-menu-items.html), but the items will still not show up in the Applications Menu.  I have even replaced the line that says "OnlyShowIn=GNOME" with "OnlyShowIn=GNOME;XFCE" to no avail.  and yes, i have restarted X with a ctrl+alt+bksp to reload the desktop environment....nothing.

i don't understand how something as ***_simple_*** as dragging & dropping an icon onto a menu to create a copy of it can be ***_so difficult_***.......even windows lets you do this, FFS.  this is really annoying the ***_hell_*** out of me.......  ](*,) ](*,) ](*,) ](*,)

don't worry, i still have no intentions of going back to winblows  ;)  but stupid crap like this is really disheartening at times......  :(

---

### Post by xunil76 on 2008-01-16
bump

---

### Post by xunil76 on 2008-01-17
boomp

---

### Post by kpkeerthi on 2008-01-17
Not sure if it would help. You could try either or both
1. Delete/Rename the hidden .xfce folder (if there is one) in your $HOME
2. sudo dpkg-reconfigure xfce4-panel

(I'm not in front of linux. so I'm guessing the package name and the folder name)

---

### Post by xunil76 on 2008-01-18
> **kpkeerthi said:**
> Not sure if it would help. You could try either or both
1. Delete/Rename the hidden .xfce folder (if there is one) in your $HOME
2. sudo dpkg-reconfigure xfce4-panel

(I'm not in front of linux. so I'm guessing the package name and the folder name)

1:  couldn't find a folder named .xfce anywhere on my system
2:  this did not work

any other ideas?  like i said, the applications are all still there, and i can access them via /usr/share/applications, but that's a HUGE p.i.t.a.

---

