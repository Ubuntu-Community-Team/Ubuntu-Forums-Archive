---
title: "How to change default settings for guest session?"
date: 2013-06-09
forum: General Help
---

### Post by gigenieks on 2013-06-09
Hello!

I want to change following settings:
[LIST]
[*]Configure Launcher icons (add, remove, reorder)
[*]Change Wallpaper
[*]Change some basic settings in Chromium browser
[*]Disable Amazon suggestions in Dash [Privacy >> Include Online Search Results *off*]
[/LIST]

Anybody know how to do this?

---

### Post by Isamu715 on 2013-06-09
[This thread]("http://ubuntuforums.org/showthread.php?t=1566078") contains instructions for customizing the guest session.

---

### Post by Frogs Hair on 2013-06-09
I would check for updated information because there are no supported versions of Ubuntu from 2010 and Ubuntu now uses Gnome 3 which was not in use at the time of the post. The instructions may be fine , but be careful.

---

### Post by Cheesemill on 2013-06-09
It may be possible by editing/creating files in the /etc/skel directory as everything in it is copied to the guest users home directory.

---

### Post by gigenieks on 2013-06-09
Thread provided is really old (almost 3 years)... 
Anybody else?

---

### Post by gigenieks on 2013-06-10
Bump

---

### Post by gigenieks on 2013-06-12
Done it with this:
> **p-dh said:**
> I appreciate all of the discussion about customizing the guest session. I have been looking for a way to have a easily cusomizable guest session... I realize that I haven't created anything new here; just put together the pieces differently from the posts in this thread.

Anyhow, the steps are as follows:
> 
[LIST]
[*]Create the directory /etc/guest-session/skel
[*]While logged on under an admin account, start a guest session
[*]Make any changes to the guest session that you want using whatever tools/utilities you wish
[*]Change back to admin account and open a terminal
[*]cd to /tmp and find the temporary guest home directory (guest-XXXXX).
[*]Copy the files in the temporary guest home directory to /etc/guest-session/skel using the command: ‘sudo cp -rT /tmp/guest-XXXXX /etc/guest-session/skel’.
[*]Log out of the guest session and login again to check.
[/LIST]
To update the settings, repeat steps 2-7 as necessary.


It works.

---

