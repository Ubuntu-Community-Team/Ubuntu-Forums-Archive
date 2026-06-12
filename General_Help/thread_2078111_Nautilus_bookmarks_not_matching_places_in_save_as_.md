---
title: "Nautilus bookmarks not matching places in save as dialog boxes"
date: 2012-10-30
forum: General Help
---

### Post by NautiusMaximus on 2012-10-30
I have added some bookmarks to the left-hand pane in my Nautilus file browser.

I was expecting those bookmarks to show up as the list of places in the left-hand pane of the "Save as" dialog in other applications. Sometimes they do, and sometimes they don't. If I choose "Save as" from LibreOffice or gedit, then they are there as expected. However, if I choose "Save as" from either Chrome or Firefox browsers, the bookmarks are missing.

If it makes any difference, the bookmarks are to network drives, mounted via the "Connect to server..." dialog in Nautilus, using ssh.

Any idea what's going on here? It would be really helpful to be able to save to these drives from a web browser, which is currently impossible.

I'm using Ubuntu 12.04.

Many thanks
NM

---

### Post by NautiusMaximus on 2012-11-03
Bump?

---

### Post by lrouxc4 on 2012-11-15
I am having the same issue. Anybody?

I am sure there is some explanation for it but I have not found one.  It is very irritating to save to a local folder, then cut and paste to the network folder.

I'm on 12.04

---

### Post by endle on 2012-11-17
Same problem. Inconsistency in what shortcuts show up in Save dialogue browser.

This is also affecting the  Bookmarks in Gedit sidebar when Folder Browser plugin is enabled.
I used to be able to bookmark an SFTP folder in Nautilus and then browse to it in Gedit. Now these two do not sync up, which makes me very sad because I used that feature on a daily basis.

At any rate, so far I have determined that Gedit is getting its  bookmarks from:
~/.config/gtk-3.0/bookmarks 

I added a few additions to that file and those would also show up in a few other "Save" dialogues from other applications.
I am not sure where the other applications are getting their bookmarks from.
Anyone else have a clue?

---

### Post by daconstenla on 2012-11-29
I have had the same problem and I found a solution:

In my home folder ~/ I have a file called .gtk-bookmarks wich include bookmarks from dialogs (save, open...) and in ~/.config/gtk-3.0/bookmarks I have the nautilus bookmarks so I have linked .gtk-bookmarks with ~/.config/gtk-3.0/bookmarks and now I have the same bookmarks in both

If you are in the same situation, remove your .gtk-bookmarks and create a symbolic link
```

rm ~/.gtk-bookmarks
ln -s ~/.config/gtk-3.0/bookmarks ~/.gtk-bookmarks

```

---

### Post by tjombka on 2013-01-15
Thanks a lot

---

