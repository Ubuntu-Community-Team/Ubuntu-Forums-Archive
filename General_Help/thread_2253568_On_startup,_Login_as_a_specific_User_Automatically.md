---
title: "On startup, Login as a specific User Automatically"
date: 2014-11-20
forum: General Help
---

### Post by Anthony_Anderson on 2014-11-20
I am not new to Ubuntu, but still consider myself new in consideration of the fact I still have a lot to learn. I have a goal, and a few questions.

Some info:
I have XBMC installed
Under the user "xbmc", XBMC is set to run automatically.
I use Grubloader to dual boot windows 7 and Ubuntu.

Goal:
I want to add an entry to Grubloader titled "XBMC" which will start Ubuntu, but automatically log in to the "xbmc" user account.
Is this possible? If so, how would I go about: Adding the entry to grubloader and Running the command to auto login once Ubuntu starts?

To be clear, I want 2 seperate entries for Ubuntu, one that will load normally, and the other that will launch into the "xbmc" user.

---

### Post by deadflowr on 2014-11-20
Grub won't help, since it'll only figure out which kernel version to boot, and not which user session to run.
You can try customizing lightdm to set it so that the user and the session load
Basically you create a file /etc/lightdm/lightdm.conf.d/50-myconfig.conf
Add
```
SeatDefaults]
user-session=name-of-session
autologin=-user=name-of-user
autologin-user-timeout=seconds-to-delay-the-login-here
```

The sessions can be found in /usr/share/xsessions.
The session is a.desktop file, so you'll need to open it with a text editor and the actual name you need is whatever is listed for the Name=, entry.
(And not the name of the .desktop file)

More here
[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

Of course, though the autologin user will login automatically, unless you set the timeout high, and then quickly choose the other user.

You might be able to fore go the user-session entry entirely, since the user account should remember the last session that user logged into, regardless.
Basically once you set a user to log into a particular session, that user will keep logging into that particular session until you change which session the user logs into.
So there really should not be a need for the setting in the conf, my guess.

---

