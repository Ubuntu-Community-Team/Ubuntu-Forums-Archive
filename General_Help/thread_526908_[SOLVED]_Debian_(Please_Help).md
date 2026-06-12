---
title: "[SOLVED] Debian (Please Help)"
date: 2007-08-16
forum: General Help
---

### Post by Ambby on 2007-08-16
I posted a post before about debian,i dont need the full operating system,i just need the debian program i guess,that adds itself to my applications menu,i need it so i can find the emulators that i install.


Can someone help?


Thanks!

---

### Post by kevinlyfellow on 2007-08-16
I'm confused by what you're looking for.  If you want a barebones debian, try the netinstall [http://www.debian.org/releases/etch/debian-installer/](http://www.debian.org/releases/etch/debian-installer/)

Or are your trying to virtualize debian?

Or are you looking for a specific app, in which case go here [packages.debian.org]("packages.debian.org")

---

### Post by Ambby on 2007-08-16
This is what im trying to do.


[http://img.photobucket.com/albums/v165/ambbychan/DebianMenu.png](http://img.photobucket.com/albums/v165/ambbychan/DebianMenu.png)


Just go to that,i need the debian menu or whatever it is,not the os.

---

### Post by kevinlyfellow on 2007-08-16
```
sudo apt-get install menu menu-xdg
```

That should do it :-)  If it doesn't let me know

---

### Post by hikaricore on 2007-08-16
Thank you for being more clear with this thread.
**However in the future if your thread is closed, do not open a new one in it's place.**
Respond to the moderator who closed your thread with a reason why it should be reopened,
or where you think it might be better placed on the forum so it can be moved and reopened.


About your question, install the package that page tells you to then restart X.
I think this is specific enough.  Though I don't understand why configuring Gnome to use the
"Debian Menu" is of any importance.  You can add new entries for whatever application you
installed that isn't being listed without this installed.

---

### Post by bodhi.zazen on 2007-08-16
```
sudo apt-get install menu
```

you may need to log out and back in to see the changes

---

### Post by kevinlyfellow on 2007-08-16
> **hikaricore said:**
> About your question, install the package that page tells you to then restart X.
I think this is specific enough.

Actually, the site's suggestion didn't work, it needed an extra package.

---

### Post by hikaricore on 2007-08-16
> **kevinlyfellow said:**
> Actually, the site's suggestion didn't work, it needed an extra package.

My apologies, I glanced quickly and thought it listed both packages.  >.<

---

### Post by Ambby on 2007-08-16
Sweet,the terinal worked fine,thanks alot!

---

