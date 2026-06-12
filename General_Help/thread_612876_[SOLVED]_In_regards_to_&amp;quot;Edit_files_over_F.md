---
title: "[SOLVED] In regards to &amp;quot;Edit files over FTP&amp;quot;"
date: 2007-11-14
forum: General Help
---

### Post by altonbr on 2007-11-14
**This is for people who want to edit/save FTP files with gEdit.**

The topic was originally posted here, but it's now closed: [http://ubuntuforums.org/showthread.php?t=322681](http://ubuntuforums.org/showthread.php?t=322681)

Run: ```
$ gconf-editor
``` and follow this path: "apps > gedit-2 > preferences > editor > save > writable_vfs_schemes". Double click 'writable_vfs_schemes', click the '+ Add' button and type in 'ftp'.

Now you can right-click a file on a FTP server in Nautilus and edit/save it with gEdit!

This was a conversation between pbor and I on irc.gnome.org#gedit.
> (11:43:31 AM) brett_alton: so can gEdit not edit over ftp:// ???
(11:45:23 AM) brett_alton: I'm amazed it can not because it can edit over ssh:// and webdav
(11:48:29 AM) pbor: brett_alton: it can
(11:48:53 AM) pbor: brett_alton: but it's disabled by default because gnome-vfs ftp support is pretty buggy
(11:49:08 AM) pbor: (especially when editing many ftp files at once)
(11:49:22 AM) pbor: brett_alton: you can enable ftp files editing in gconf
(11:50:27 AM) pbor: just add ftp to the list in **/apps/gedit-2/preferences/editor/save/writable_vfs_scheme**s
(11:53:58 AM) brett_alton: great, thanks pbor! May I paste those instructions on ubuntuforums.org?
(11:54:13 AM) pbor: sure!
(11:54:37 AM) pbor:** *just be clear that we didn't do that just to annoy users...***
(11:55:00 AM) pbor:*** it's disabled because we actually do think ftp support is not robust enough***
(11:55:12 AM) pbor: [SIZE="4"]**so "use it at your own risk"**[/SIZE]

---

