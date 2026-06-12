---
title: "log in windows error"
date: 2007-01-03
forum: General Help
---

### Post by vict44 on 2007-01-03
--------------------------------------------------------------------------------

hi sup... i need help i just installed ubuntu yesturday on my laptop and im dual bootin with win xp pro edition but i noticed a pop up window told me to get some updates so i clicked on install and they where downloading normaly so i decided to play a bit a game called super dunno what it's a copy of mario bros old game with tux pinguin on it anyways when i quited to see the dl progress i saw all the screen extremly expanded so much that i had to move the cursor to see parts of my desktop i restarted and on the boot screen selected ubuntu when it finished loading the black screen and asked me for the user and password i typed them but suddenly all the screen went black and in a flash something about an error was displayed in a form very similar to the bios or boot screen and returned me to the log in window i have about 1 hour typing my user n pw but the error persists does anyone know why is this happening?, do i have to reformat? did i did wrong dl the game from the add and remove thing at the ubuntu top bar? i had never used linux b4 it's very similar to windows so i dunno much about it i need help plz desperatly... and just when i was thinkin on moving into ubuntu for a while

---

### Post by jordanmthomas on 2007-01-03
Try this:
press ctrl - alt - f2
(you can get back to your graphical session by hitting ctr - alt - f7)
log in on this screen

First, try restarting gdm:
```
sudo /etc/init.d/gdm restart
```
If that does not seem to work type this:
```
sudo dpkg-reconfigure xserver-xorg
```
go through, answering all the questions.  The defaults are usually going to be fine, but if you know something is wrong, change it.
Then, restart gdm
```
sudo /etc/init.d/gdm restart
```

Does this help?

---

