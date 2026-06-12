---
title: "How to add bookmark (i.e., shortcut) permanently to file manager display?"
date: 2021-05-28
forum: General Help
---

### Post by VanillaMozilla on 2021-05-28
I have Ubuntu 20.04 with flashback, Files 3.36.3-stable (aka Nautilus).

I have a network drive that is mounted automatically in /mnt/.

The file manager shows "Home", "Documents", etc.  I need it to also show the network drive.

The file manager home page, here:  [https://wiki.gnome.org/action/show/Apps/Files](https://wiki.gnome.org/action/show/Apps/Files)
shows a network drive appearing in the side panel.  That would be wonderful, and that's essentially what I had in Ubuntu 18.04.  How do I get that again?  I need it in list view and icon view.

---

### Post by Dennis N on 2021-05-28
(Using Nautilus 3.36, Ubuntu 20.04)

Browse to folder on other drive you want to bookmark. Right click on the folder in the path. There should be "Add to bookmarks" in the menu. See screenshot.

---

### Post by VanillaMozilla on 2021-05-28
Thanks.  There should be a menu item, but there isn't.

However, I got it the hard way.
ln -s /mnt/<dirname>,
and added a line to .config/gtk-3.0/bookmarks to put it in the side bar and the Places menu.

---

### Post by TheFu on 2021-05-28
> I have a network drive that is mounted automatically in /mnt/.
If you are using autofs, then use the --ghost option in the auto.master file. For example:
```
/-      /etc/auto.misc --timeout=60 [COLOR="#FF0000"]--ghost[/COLOR]
```
This will make a directory for the mount "seen" by all programs, including GUI stuff, before the mount happens.

Be extremely careful with that symbolic link. I can think of a few negative results.  If you weren't using automounter, amd or autofs, then it is probably ok.  I.e, using a typical /etc/fstab entry.  Any other method ... well ... There are so many caveats when using other methods it is scary.

---

### Post by VanillaMozilla on 2021-06-03
Not autofs.  Just cifs and samba-client.  It is mounted from /etc/fstab.

What kind of negative results do you have in mind?  This is a link to a samba share.  The share and the link are unlikely to ever be deleted.

---

### Post by TheFu on 2021-06-03
I had a bunch of negative-negatives in my other post.  Think that broke the understanding.    The bad stuff can happen if you DO use autofs with soft/symlinks. Much clearer wording that way.

---

### Post by VanillaMozilla on 2021-06-03
No, it was understood all right, although I thought I'd leave it open in case there were some gotchas that I didn't know about.

Thanks for the replies.  I'm marking this solved.

---

