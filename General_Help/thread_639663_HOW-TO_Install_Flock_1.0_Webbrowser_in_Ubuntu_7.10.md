---
title: "HOW-TO: Install Flock 1.0 Webbrowser in Ubuntu 7.10 with flash support"
date: 2007-12-13
forum: General Help
---

### Post by billgoldberg on 2007-12-13
Well, since it’s not in the repositories you are going to have to download it on [the flock website]("http://www.flock.com").

- download it to your desktop
- right click the file and choose “extract here”
- rename the folder to .flock (don’t forget the dot)
- copy/paste it to the home folder
- hover mouse above the main menu and choose edit menu.
- choose internet on the left and pick “new item” on the right.

Fill this in:
Type: application
Name: Flock 1.0
Command: /home/username/.flock/flock
Comment: Flock Web Browser
Click the icon: and give this /home/username/.flock/icons/mozicon128.png

Done. You now have a nice entry for it in applications -> internet.

The next thing you need to do is install flash for Flock.

The flash installer for linux doesn’t let you pick to install it to flock, so I needed to get down and dirty with nautilus, but I found a why do make flash work.

- go to terminal and type:
sudo nautilus

-navigate to
/usr/lib/mozilla/plugins

- copy the file that mentiones flash

- navigate to /home/username/.flock/plugins

- paste the file

- restart browser

Done. I just copied all the files from /usr/lib/mozilla/plugins hoping that it would enable totem support for flock, but that didn’t seem to work.

---

### Post by K.Mandla on 2007-12-20
Moved to General Help.

---

