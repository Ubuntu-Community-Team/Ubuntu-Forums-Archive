---
title: "Permissions for sharing a /home directory"
date: 2006-10-29
forum: General Help
---

### Post by Raito on 2006-10-29
I am dual booting Xubuntu and Fedora Core. Installed Xubuntu first, then Fedora Core then Xubuntu again. The problem is with the /home directory. It was originally created by the ubuntu user and the ubuntu sokuban has full privaleges of it. On Fedora Core I made another user named sokuban with the same home directory however Fedora Core complains I don't have the right permissions for the home directory and doesn't let me log in I then went on ubuntu and let everyone have read and write privaleges for /home and that seems to let me log in


But is using this crazy solution bad in any way?

What would be the proper way to give them both the same permissions?

---

### Post by chavo on 2006-10-29
Just make sure your user has the same gid on each distro. Some distros start at 500 and others seem to start at 1000. I always make sure my gid is 1001 and my home dir is owned by chavo.1001.

---

### Post by Raito on 2006-10-29
Well I made the sokuban on Fedora Core 1000. 

The sokuban on Xubuntu is relatively fine, however the Fedora Core one has problems. 

Now every time I log in, the background is black and a million popups come up saying how some setting could not be found or something. The two icons ont he desktop (computer and home) were working and I could open nautilus from them. However I had no start bar. I then Ctr-Alt-Backspace'd my way back to gdm and I logged in with my secondary user. That works fine. But sokuban seems screwed.

Maybe this is a Fedora Core problem, (but Fedora Core doesn't have a really good forum T_T) But anyone know what happened? If I make the sokuban have any other gid other than 1000 it is ok. All my preferences are loadable and saveable. (Only if the home directory is writable by everyone though.)

What should I do?

(The problem with making the home directory writable by everyone is that it complains every time I log in about how /home directories should be owned by the user, have 644 permissions, and not be writable by anyone else.)

---

### Post by taurus on 2006-10-29
In theory, you can share the same /home with two different Linux distros (or as many as you wish) but actually it's not!!!  Once distro will do things a little differently than the other distro to /home and I guess you just found out about that.  Therefore, to be safe and sound, should have it own /home while you can mount the other distro's /home somewhere else and have access to it.

---

### Post by Raito on 2006-10-30
Oh, I didn't know that. I guess I'll use the /home directory only for things that were auto added and user preferences and have a shared directory for personal files.

---

