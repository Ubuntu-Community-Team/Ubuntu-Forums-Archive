---
title: "Open File Dialog Default Window Size"
date: 2006-11-01
forum: General Help
---

### Post by lee_connell on 2006-11-01
Is there a way to set the default open file dialog size when opening files or saving files in gnome?  I resize the window but when I go to open or save again it defaults back to original size.

thanks

---

### Post by BungaMan on 2006-11-11
I'd like to know this as well.  The default size is too small for me as I'd like to see as much as possible without having to scroll.  Simply see and click.

For the benefit of other readers:
[http://bugzilla.gnome.org/show_bug.cgi?id=325477](http://bugzilla.gnome.org/show_bug.cgi?id=325477)
[http://gnomesupport.org/forums/viewtopic.php?t=10833](http://gnomesupport.org/forums/viewtopic.php?t=10833)

---

### Post by fx5 on 2006-11-29
I patched gtk to make the file dialog bigger.

You can try this with edgy:
```
cd /tmp
wget http://www.fx5-1.de/~fx5/libgtk-x11-2.0.so.0.1000.6
sudo mv /usr/lib/libgtk-x11-2.0.so.0.1000.6 /usr/lib/libgtk-x11-2.0.so.0.1000.6.old
sudo cp libgtk-x11-2.0.so.0.1000.6 /usr/lib/
```

---

