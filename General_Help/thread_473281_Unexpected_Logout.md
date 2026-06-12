---
title: "Unexpected Logout"
date: 2007-06-13
forum: General Help
---

### Post by mdvigi7536 on 2007-06-13
Just installed Ubuntu Feisty.  When I was setting up the screensaver,  all of a sudden the screen flashed black, then some text I couldn't read, and all of a sudden I was back at the login screen.

It happened again when I was doing something else.

I'm concerned, because I am giving this computer to someone and don't want it to be getting in the habit of logging itself off and erasing all their work!  What can I do to make sure it doesn't restart itself or whatever it's doing?!

Thanks for the help.

--Mike

---

### Post by airblade on 2007-06-15
The way you describe this, it looks like the X server is restarting itself for some reason.
Check your /var/log/Xorg log.

---

