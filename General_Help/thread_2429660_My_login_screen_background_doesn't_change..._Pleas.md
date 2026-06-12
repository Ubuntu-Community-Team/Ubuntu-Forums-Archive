---
title: "My login screen background doesn't change... Please help!"
date: 2019-10-21
forum: General Help
---

### Post by michaelmcole on 2019-10-21
Hi all,
Ubuntu 19.10 on a System76 "Kudu" laptop.

I wanted to change my login and lock-screen background image to a jpg I have.
I edited the /usr/share/gnome-shell/theme/gdm3.css as so;

```
background: url(file:///usr/share/backgrounds/lock-screen.jpg);



```

Now my lock-screen background changes as expected, but the login-screen background doesn't.  I tried several different jpg's but always get the same result, the login screen-never changes!

Is the login-screen background specified somewhere else?  I've read online that changing this entry changes the background for _**both**_ lock and login screens, but I could be wrong.

---

### Post by Skaperen on 2019-10-21
does the login screen have a menu pop-up with a list of users?  if so, it probably is showing the background of the user currently selected.  try changing the user selection to a user with a different background.  i use Xfce instead of Gnome, so if it does something else, i won't be of any further help.

---

### Post by deadflowr on 2019-10-22
What does the full section show for the #lockDialogGroup in the gdm3.css file?

FWIW, it's just the login screen.
The lock screen is set by the user in Settings > Background.
The login screen has the dialog box for the password field.
The lock screen is just a wallpaper that covers the screen, but has no password field.
Pressing Enter while in the lock screen will reveal the login screen to input the password to restore/unlock the session.
[https://help.ubuntu.com/stable/ubuntu-help/shell-lockscreen.html.en]("https://help.ubuntu.com/stable/ubuntu-help/shell-lockscreen.html.en")

Myself, I have only used .png files, as that is the file type it uses by default.
(when in Rome and all that)
Works well with those, so...

---

